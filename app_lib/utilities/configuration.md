# Configuration

The *utilities/configuration.h* header contains some of the most important helpers in the library, namely the `configurable` class and JSON (de)serialisation utilities.

This page contains information about the following:

- [Configurable classes](#The-configurable-class)
- [Common configuration helpers](#Helpers)
- [JSON serialisation](#Serialisation)

## The `configurable` class

The `configurable` class is a mixin class that streamlines configuring options from JSON data. It is meant to be used in a [CRTP](https://en.wikipedia.org/wiki/Curiously_recurring_template_pattern) fashion (see [below](#Usage)).

The class provides the following interface:

```C++
template <typename D>
struct configurable : configurable_base {
 public:
  const char* name() const;
  void set_json(const nlohmann::json& root);
  nlohmann::json get_json() const;
  const nlohmann::json& get_json_const_ref() const;
  void configure();
  std::string describe();
 protected:
  constexpr D& derived();
  constexpr const D& derived() const;
  nlohmann::json::json_pointer get_json_pointer() const;
  nlohmann::json& get_json_ref();
  template <typename T> bool bind_and_describe_data(
      const char* key, T& to, std::string&& description = std::string{});
}
```

Importantly, the `name()` and `configure()` public methods need to be implemented in the classes deriving from `configurable`.

- __`name()`__ specifies the name(space) of the configurable class. The value will be looked up in the first level of the JSON configuration data. For example, the configuration for a class with `name()` returning `"myClass"` could look like:
    ```json
    {
        "myClass": {
            "variable_1": 1,
            "variable_2": 2
        }
    }
    ```
- __`configure()`__ specifies how the JSON data is linked with the internal data of the class. For that purpose the function template `bind_and_describe_data` should be used, and provided:
    - the lookup key for accessing the JSON data (`const char* key`), e.g. `"variable_1"` in the short example above,
    - a reference (`T& to`) to the member variable,
    - an optional, but helpful description (`std::string&& description`), which will be used in the self-reporting accessed via the `describe()` method. The entire description will be built from each call to `bind_and_describe_data`.

The type helper class template `is_configurable` and the variable template `is_configurable_v` can be used to determine whether a class is configurable with the provided facilities.

### Usage

Please refer to the how-to ["Creating a configurable class"](../Guides/Creating-a-configurable-class.md) for a detailed example.

Configurable classes (those deriving from `configurable`) can be manipulated with a number of function templates:

- Setting the JSON data in one or more (`Ts...`) configurable classes:
    ```c++
    template <typename U, typename... Ts>
    inline void set_json(U json, Ts&&... ts);
    ```
- Executing the `configure()` method in one or more configurable classes:
    ```c++
    template <typename... Ts>
    inline void only_configure(Ts&&... ts)
    ```
- Setting the JSON and configuring the one or more classes in a single call:
    ```c++
    template <typename U, typename... Ts>
    inline void configure(U json, Ts&&... ts);
    ```

## Helpers

The configuration header file also provides the following:

- Sorting and deduplicating vectors (contained type must have comparison operators) via:
    ```c++
    template <typename T>
    void sort_and_deduplicate(std::vector<T>& vector);
    ```
- Bootstrapping of cores. The function checks hardware concurrency, initialises the *vector* if provided an empty one, and checks if any of the specified cores are out of range.
    ```c++
    void bootstrap_cores(std::vector<unsigned>& cores);
    ```
- A function to generate header descriptions (for individual variables/columns). It accepts exactly four arguments:
    ```c++
    template <typename... Ts>
    std::string generate_header(Ts&&... ts);
    ```
    1. A name string, typically the output of a *configurable's* `name()`.
    2. The variable being produced, can be a name or a number.
    3. The dimension of the variable, e.g. which core is being represented. It can also be a pointer, to account for addresses, which will be casted to (void*).
    4. The unit of the variable, e.g. Hz, Watts.

    It produces header descriptions in the form `{1}:{2}:{3}:{4}`.

## Serialisation

The library uses the highly intuitive, idiomatic, and modern JSON C++ library [nlohmann/json](https://github.com/nlohmann/json).

The configuration header provides a helper function `get_from_json_to` which is used internally in `bind_and_describe_data`. The function template has the following signature:

```c++
template <typename T, typename K>
inline void get_from_json_to(const nlohmann::json& json, K key, T& ref);
```

It includes amends the default assignment operations provided by *nlohmann/json* with checks and safer handling of iterable (and eraseable) data types. The function will look for a `key` (`K`: a `const char*` string or a `json_pointer`) in the JSON data (`json`) and assign it to the variable provided by reference, `ref`.

> The library also specifies a definition for the JSON pointer to the root configuration. It is by default set to `""`, meaning the root of the JSON data. It can be, however, changed if required, so that instead of:
> ```json
> {"configurable_0": {"variable_0": 0}}
> ```
> By setting `POINTER_TO_ROOT_CONFIG` to `"config"` we can have:
> ```json
> {
>   "some_data": 0,
>   "some_other_data": 1,
>   "config": {"configurable_0": {"variable_0": 0}}
> }
> ```

### Serialising custom types

Please refer to the how-to ["Serialising custom types"](../Guides/Serialising-custom-types.md) for a detailed example of how to (de)serialise custom types to JSON by extending `nlohmann::adl_serializer` or providing custom `to_json` and `from_json` functions.

The header defines serialisers for:

- `std::optional<T>` types, which can be set to `null` or the value of type `T`.
- `std::chrono::duration<Rep, Period>`, which converts between duration objects (with specific `Rep` and `Period` types) and seconds represented as floating point numbers.
- `exot::utilities::SchedulingPolicy`, the scheduling polity enumeration class,
- `spdlog::level::level_enum`, the logging level.

Moreover, throughout the library, there are serialisers for:

- `exot::modules::power_msr::rapl_domain`, the Intel RAPL domain enumeration (in the *include/exot/meters/power_msr.h* header).
- `exot::modules::utilisation_procfs::cpu_state`, the CPU state as described in *procfs* (in the *include/exot/meters/utilisation_procfs.h* header).