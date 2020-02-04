# Provided components

1. [Logging](#Logging)
1. [Schedule reader](#Schedule-reader)
1. [Meter host w/ logger](#Meter-host-with-a-logger)
1. [Generator host](#Generator-host)

### Logging

- __Name__ → Logging
- __Namespace__ → `"logging"`
- __Class__ → `Logging`
- __Component type__  → Not a component

The logging is set in a uniform fashion in all applications via the `Logging` class, which is configured in the same way as the modules and components. It provides two logs: an *app log*, and a *debug log*. If no filenames are provided in options, the *debug log* will log to `stderr`, and *app log* to `stdout`.

A standalone `Logger` component is also provided. It logs the tokens that it receives to the *app log*. The token type is specified via the `Token` template parameter.

- __Name__ → Logger
- __Namespace__ → `"logging"`
- __Class__ → `Logger<Token>`
- __Component type__  → Producer

For example:

```c++
using logger_t =
    exot::components::Logger<typename meter_t::token_type>;
// or
using generic_logger_t =
    exot::components::Logger<std::vector<unsigned>>;
```

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `debug_log_filename` | *string*, optional | null | The debug log filename
| `app_log_filename` | *string*, optional | null | The app log filename
| `log_level` | *string* | info | The logging level, one of: trace, debug, info, warn, error, critical, off (`spdlog::level::level_enum` used internally).
| `async` | *bool* | false | Use asynchronous logging with a thread pool?
| `async_size` | *unsigned* | 8192 | The asynchronous logging queue size (power of 2)
| `async_thread_count` | *unsigned* | 1 | The number of threds in the asynchronous logging thread pool
| `provide_platform_identification` | *bool* | true | Should provide platform identification in debug log?
| `timestamp_files` | *bool* | false | Should timestamp log files?
| `append_governor_to_files` | *bool* | false | Should append scheduling governor to files?
| `rotating_logs` | *bool* | false | Should rotate log files?
| `rotating_logs_size` | *unsigned* | 100 MiB | Rotating log max size (value specified in bytes, 100 MiB = 104'857'600)
| `rotating_logs_count` | *unsigned* | 10 | Number of rotating log files

### Schedule reader

- __Name__ → Schedule reader
- __Namespace__ → `"schedule_reader"`
- __Class__ → `schedule_reader<Token>`
- __Component type__  → Producer

The schedule reader can be used in sender or load-imposing applications. It reads a schedule file, which consists of whitespace-separated values, and formats them into appropriate token types. The token type is given as a template parameter.

###### Example

```c++
using reader_t =
    exot::components::schedule_reader<typename loadgen_t::token_type>;
```

###### Template

| Parameter  | Description |
|:-----------|:----------- |
| `Token`    | The type of the token to ingest, e.g. `tuple<chrono::nanoseconds, int, int>`

> The token type must have an input stream operator `<<`. Variable-length tokens are also supported. [The library provides a custom overloads for a few types.](https://gitlab.ethz.ch/tec/research/exot/app_lib/blob/develop/include/exot/utilities/istream.h)

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `input_file`        | *string*         | `""`    | Path to the schedule file
| `reading_from_file` | *bool*           | `false` | Should read from file? (Reads from stdin if `false`)
| `read_as_hex`       | *bool*           | `false` | Should interpret input as hexadecimal values?
| `cpu_to_pin`        | *unsigned*, optional | `null`  | Pin process to specified core

### Meter host with a logger

- __Name__ → Meter host (with a logger)
- __Namespace__ → `"host"`
- __Class__ → `meter_host_logger<Duration, Meters...>`
- __Component type__  → N/A

The meter host combines a number of metering modules into a single component. The modules only need to be provided as template parameters. Since we often combine the meter host with a logger component, these two have been joined for the sake of performance and ease of use. *The plain meter host is also available, but is not as well supported.*

###### Example

```c++
using meter_t = components::meter_host_logger<
    std::chrono::nanoseconds, modules::thermal_sysfs, modules::frequency_sysfs>;
```

###### Template

| Parameter  | Description |
|:-----------|:----------- |
| Duration | The duration type used by the host, e.g. `chrono::microseconds`
| Meters... | The meter module types, *variadic*

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `period` | *Duration* | 10 ms | The sampling period
| `cpu_to_pin` | *unsigned* | 0 | The CPU to pin the host process to
| `priority` | *unsigned* | 90 | The [scheduling priority](./Utilities/Multi-threading.md), [0,99]
| `policy` | *string* (`policy_type`) | "Other" | The [scheduling policy](./Utilities/Multi-threading.md)
| `log_header` | *bool* | true | Should log CSV header?
| `start_immediately` | *bool* | false | Should start immediately, or wait for signal? |
| `use_busy_sleep` | *bool* | false | Should wait for signal in a busy sleep loop?
| `busy_sleep_yield` | *bool* | false | Should yield thread in the busy sleep loop?
| `start_check_period` | *unsigned* | 1 | Busy sleep check period, in µs.

###### Static options

The static options below can be turned on with a preprocessor definition before the inclusion of the header file, or during the CMake configuration. For descriptions see the page [Using the library](./Using-the-library#Configuration). The `#define`s are `METER_USE_STATISTICS`, `METER_SET_AFFINITY`, `METER_LOG_SYSTEM_TIME`, `METER_NOW_FROM_TIMER`.

```c++
struct MeterOptions {
  static constexpr bool use_statistics = static_cast<bool>(METER_USE_STATISTICS);
  static constexpr bool set_affinity = static_cast<bool>(METER_SET_AFFINITY);
  static constexpr bool log_system_time = static_cast<bool>(METER_LOG_SYSTEM_TIME);
  static constexpr bool now_from_timer = static_cast<bool>(METER_NOW_FROM_TIMER);
};
```

### Generator host

- __Name__ → Generator host
- __Namespace__ → `"generator"`
- __Class__ → `generator_host<Duration, Generator>`
- __Component type__  → Consumer

The generator host encapsulates common functionality, which allows generators to be much more compact and reduces code duplication. It is responsible for creating worker threads, timers, and keeping track of the schedule, dictated by the tokens it receives.

For available generators, see the page ["Available generator modules"](./Available-generator-modules).

Each worker thread receives its assigned core, the core's index in the cores set, and a decomposed subtoken (token without duration). Then each worker uses these pieces of information to generate some load (or sleep).

The workers use the functions provided by the generator module, and are described by the following lambda ([exot/components/generator_host.h#L209](https://gitlab.ethz.ch/tec/research/exot/app_lib/blob/develop/include/exot/components/generator_host.h#L209)):

```c++
[this, core, index] {
  /* Uses the comma operator to access the subtoken while holding
   * the shared lock. */
  auto decomposed = this->decompose_subtoken(
      (std::shared_lock{subtoken_mtx_}, subtoken_), core, index);

  this->generate_load(decomposed, enable_flag_, core, index);
}
```

###### Template

| Parameter  | Description |
|:-----------|:----------- |
| Duration | The duration type used by the host, e.g. `chrono::microseconds`
| Generator | The generator module

###### Example

```c++
using loadgen_t =
    exot::components::generator_host<std::chrono::nanoseconds,
                                     exot::modules::generator_utilisation_mt>;
```

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `set<int>` | null | The CPU cores allocated for workers
| `cpu_to_pin` | *unsigned* | Max - 1 | The CPU to pin the host process to
| `worker_policy` | *string* (`policy_type`) | "Other" | The [scheduling policy](./Utilities/Multi-threading.md) of workers
| `self_policy` | *string* (`policy_type`) | "Other" | The [scheduling policy](./Utilities/Multi-threading.md) of the host
| `worker_priority` | *unsigned* | 90 | The [scheduling priority](./Utilities/Multi-threading.md), [0,99] of the workers
| `self_priority` | *unsigned* | 99 | The [scheduling priority](./Utilities/Multi-threading.md), [0,99] of the host
| `use_busy_sleep` | *bool* | false | Should wait for signal in a busy sleep loop?
| `busy_sleep_yield` | *bool* | false | Should yield thread in the busy sleep loop?
| `start_check_period` | *unsigned* | 1 | Busy sleep check period, in µs.

###### Static options

The static options can be turned on with a preprocessor definition before the inclusion of the header file, or during the CMake configuration. For descriptions see the page [Using the library](./Using-the-library#Configuration). The `#define`s are `GENERATOR_HOST_PERFORM_VALIDATION`, `GENERATOR_HOST_PROVIDE_TIMING_STATISTICS`.

## Other

A number of simpler components are also provided in the library.

##### Function nodes

Three component class templates are given:

- `function_consumer<InputToken>`
- `function_producer<OutputToken>`,
- `function_processor<InputToken, OutputToken>`.

They take either the input or output (or both) tokens as template parameters. The constructors take callable objects with signatures `InputToken → void`, `void → OutputToken`, or `InputToken → OutputToken`, respectively. The default constructors are deleted. They can be used as follows:

```c++

auto producer = exot::components::function_producer<int>([]() -> int {
    return std::this_thread::sleep_for(1s), static_cast<int>(rand());
});

auto processor = exot::components::function_processor<int, int>([](int in) -> int {
    return in * 2;
});

auto count = 0ull;
auto consumer = exot::components::function_consumer<int>([&](int in) {
    std::cout << "Token #" << count++ << ", value = " << in << std::endl;
});

auto connector = exot::framework::Connector();
auto executor = exot::framework::ThreadExecutor();

connector.pipeline(producer, processor, consumer);
executor.spawn(producer, processor, consumer);

exot::framework::GLOBAL_STATE->start();
std::this_thread::sleep_for(12s);

/* Should print random numbers to the console: Token #0, value = ... */
```

##### Domain adapters

Domain adapters are special nodes that bridge nodes based on userspace threads (via Boost::fiber) and system threads. Two class templates are available: `FiberToThread<Token>` and `ThreadToFiber<Token>`. These are necessary because the timeout locking queues for the fibers and regular threads are different. Otherwise, a deadlock might appear.