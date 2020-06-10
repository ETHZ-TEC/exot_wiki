The library provides a generic way of combining multiple individual metering modules together. As long as the modules conform to the requirements listed in ["Creating metering modules"](2.-How-to's/Creating-metering-modules), they can be incorporated into larger components.

### Principles

The __meter host__ is a class template, where meter modules are provided as variadic template parameters. The definition of the class template is:

```c++
template <typename Duration, typename... Meters>
class meter_host_logger : public Meters...,
                          public covert::framework::IProcess,
                          public covert::framework::Producer<
                              details::meter_token_type<Duration, Meters...>>;
```

As we can see, the `meter_host_logger` will inherit publicly from all supplied `Meters` types. The `meter_token_type` helper defines the token type produced by the component. As shown below, its a tuple of a Duration object (e.g. `std::chrono::microseconds`) and all individual Meters' return types.

```c++
template <typename Duration, typename... Meters>
using meter_token_type = std::tuple<Duration, typename Meters::return_type...>;
```

The "combining" of meter modules takes place in several locations:

1. The meter host's *settings* structure has inherits from all modules' settings ([link to source](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/components/meter_host_logger.h#L84)).
  ```c++
  struct settings : Meters::settings ... { /* meter's own settings */ }
  ```
2. The modules' *configure* functions are added to a top-level configuration using a fold expression ([link](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/components/meter_host_logger.h#L157)). The individual modules' *configure* functions are supplied with the meter host's *settings* structure; however, they only access their relevant parts, since they access it through their private base references. Therefore there are no name clashes between modules.
  ```c++
  (..., total.push_back(std::move(Meters::configure(conf))));
  ```
3. A static assertion determines if the supplied template parameters satisfy the requirements (presence of a *measure()* function).
  ```c++
  static_assert((covert::modules::has_meter_function<Meters>::value && ...),
                 "Mixins need to provide a measure() function.");
  ```
4. Individual *measure()* functions are combined in the meter host's *measure()* function.
  ```c++
  inline token_type measure() {
    return std::make_tuple(
        std::chrono::duration_cast<Duration>(
            std::chrono::steady_clock::now().time_since_epoch()),
        std::move(Meters::measure())...);
  }
  ```
5. Variable names and units are combined in a similar fashion.

The *meter_host_logger* has a number of compile-time options, which can be set with preprocessor defines before including the header file. These include:

1. *METER_SET_AFFINITY*: enable core pinning of the main meter process,
2. *METER_USE_STATISTICS*: log timing statistics (mean and standard deviation of intervals and offsets),
3. *METER_LOG_SYSTEM_TIME*: log system time alongside the typical token.

### Example

```c++
using MeterHost = covert::components::meter_host_logger<std::chrono::milliseconds, Module1, Module2, Module3>;

MeterHost::settings settings;
MeterHost meterHost(settings);
```
