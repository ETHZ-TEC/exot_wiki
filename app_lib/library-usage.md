[:back:](/home)
---

# Using the library

## CMake

This project uses [CMake](https://cmake.org/) as the build tool. It is
strongly encouraged that CMake is used for building all software based on the
library. The project's build configuration file defines the library target
called **exot** and a separate target that includes all modules: **exot-modules**.

The library requires a number of third-party libraries:
[fmt](https://github.com/fmtlib/fmt) for string formatting,
[spdlog](https://github.com/gabime/spdlog) for logging,
[clipp](https://github.com/muellan/clipp) for command-line parsing, and
[doctest](https://github.com/onqtam/doctest) for testing. These are provided
as git submodules in the repository. To import them during cloning, run `git
clone --recursive <repo-url>`, to do that after the library has been imported,
make sure to run `git submodule update --init --recursive` to sync the
dependent repositories. To use the library at a specific tag or commit, git
submodules can also be utilised.

To use the library, include the repository in your project's path, and import
it in the project's CMakeLists.txt using `add_subdirectory`:

```cmake
cmake_minimum_required(VERSION 3.6)
project(project-that-uses-the-library VERSION 0.0.0 LANGUAGES CXX)

add_subdirectory(<path/to/library>)

# ...

target_link_libraries(<target/name> exot)
# target_link_libraries(<target/name> exot exot-modules)

```

### Configuration

The library's CMakeLists.txt file provides a number of configuration parameters. During the configuration step of CMake's workflow, all configured options will be clearly printed to the console. The parameters determine general options for the library, functionality of certain components, and the characteristics of the default timing source.

These values can be set from the console during the invocation of the configuration step of the CMake workflow, by passing, for example, `-DMETER_SET_AFFINITY=1` or `-DEXOT_TIME_SOURCE=4`.

#### General

Three general options for the ExOT library project, set with either `ON` or `OFF`, are:

| Name | Default value | Description |
| --- | --- | --- |
| `exot_use_fibers` | `OFF` | Enable and use `Boost::fiber`? |
| `enable_clang_format` | `ON` | Enable and use code auto-formatting? |
| `enable_clang_tidy` | `OFF` | Use the static analyser? |

#### Functional

The options that enable or disable certain functionalities of generators and meter hosts, set with either `0` or `1` (for *off* and *on*, respectively), are:

| Name | Default value | Description |
| --- | --- | --- |
| `GENERATOR_HOST_PERFORM_VALIDATION` | `0` | Perform token validation? |
| `GENERATOR_HOST_PROVIDE_TIMING_STATISTICS` | `0` | Provide time keeper statistics? |
| `METER_SET_AFFINITY` | `1` | Set meter host affinity? |
| `METER_USE_STATISTICS` | `0` | Provide time keeper statistics? |
| `METER_LOG_SYSTEM_TIME` | `0` | Log system time? |
| `METER_NOW_FROM_TIMER` | `1` | Take timestamp from time keeper? |

#### Timing

Notably, the build file defines the two options, which configure the default timing source and serialisation.

```cmake
set(EXOT_TIME_FENCE 0 CACHE STRING "The default timing fence")
set(EXOT_TIME_SOURCE 4 CACHE STRING "The default timing source")
set_property(CACHE EXOT_TIME_FENCE PROPERTY STRINGS 0 1 2 3)
set_property(CACHE EXOT_TIME_SOURCE PROPERTY STRINGS 0 1 2 3 4 5)
```

| Value | Name | Description |
| --- | --- | --- |
| 0 | *SteadyClock* | Clock using the `std::chrono::steady_clock` from C++ Standard Template Library |
| 1 | *MonotonicCounter* | Monotonic counter using the `clock_gettime` function from Linux'es *<time.h>* header with value `CLOCK_MONOTONIC`. |
| 2 | *MonotonicClock* | Monotonic clock using the `clock_gettime` function from Linux'es *<time.h>* header with value `CLOCK_MONOTONIC`. |
| 3 | *TimeStampCounter* | A simple counter using the timestamp counter accessed via the `rdtsc` instruction, without very strict serialisation. *Only available on x86_64 architectures.* |
| 4 | *HardwarePerformanceCounter* | A counter based on Linux'es *perf* events using the hardware CPU performance counter. |
| 5 | *SoftwarePerformanceCounter* | A counter based on Linux'es *perf* events using the software CPU clock. |

The values for `EXOT_TIME_SOURCE` correspond to the enumeration values in `TimingSourceType` at [exot/utilities/timing_source.h#L61](https://gitlab.ethz.ch/tec/public/exot/app_lib/blob/master/include/exot/utilities/timing_source.h#L61).

#### Timing serialisation

| Value | Name | Description |
| --- | --- | --- |
| 0 | *Atomic* | Atomic fence via C++ STL `atomic_thread_fence` with acquire-release memory order. |
| 1 | *Weak* | Fencing done via architecture-specific sequence of load and memory fence. |
| 2 | *Strong* | Fencing done via architecture-specific full fences (e.g. `cpuid` and `mfence` sequence on *x86_64*.) |
| 3 | *None* | No serialisation applied. |

The values for `EXOT_TIME_FENCE` correspond to the enumeration values in `TimingFenceType` at [exot/utilities/timing_source.h#L51](https://gitlab.ethz.ch/tec/public/exot/app_lib/blob/master/include/exot/utilities/timing_source.h#L51).

## Requirements

To successfully compile one needs:

- *CMake* ~> 3.6, preferably one that understands the C++17 standard (~> 3.8);
- a recent C++ standard library, conforming to the C++17 standard. This could be
  the GNU libstdc++ from [GCC 8](https://gcc.gnu.org/projects/cxx-status.html#cxx17) and higher (libstdc++.so.6.0.23 and higher).
  Please refer to the wiki for [futher guidelines](./library-usage);
- (optionally) *Boost* libraries, with *Boost/fiber* available,
  enabled by passing -Dexot_use_fibers to the CMake command.

> __Note__: The new Docker-based container and user-script can be used to obtain a ready development environment capable of cross-compiling. Please refer to the [dedicated wiki page](compilation/environment).

## Toolchains

The build process can be driven by *toolchain files*, which can wrap compiler,
linker, and other environment parameters and tasks necessary for building the
library and applications. If no *toolchain file* is provided, the build will
be performed with the system compiler, or the one defined with environment
variables `CC`/`CXX`. The repository contains, in
cmake/toolchains, a number of toolchains for dynamic and
static linkage, and for cross-compilation.

## Building

A number of build configurations are available: *Debug*, *Release*,
*RelWithDebInfo*. To configure the build with the desired configuration, run:

```bash
# Debug configuration, with symbols, static analysis, and no optimisation
cmake -DCMAKE_TOOLCHAIN_FILE=<path/to/toolchain> \
      -DCMAKE_BUILD_TYPE=Debug -Bbuild/Debug -H.
# Release build, no symbols, no debug statements, high optimisation
cmake -DCMAKE_TOOLCHAIN_FILE=<path/to/toolchain> \
      -DCMAKE_BUILD_TYPE=Release -Bbuild/Release -H.
```

Then, to compile specific targets, choose the build folder and run:

```bash
cmake --build build/Debug --target <target name> -- -j 0
```

To build and execute the library tests, run:

```bash
cmake --build  <path/to/build> --target exot-test
./path/to/build/exot/exot-test
```

---

## Additional features

There is a number of CMake modules provided in the repository. Some relevant to the end-user include:

- *configure_clang_format(_enable_ _target_)*
- *configure_clang_tidy(_enable_)*
- *print_build_info()*
- *print_target_properties(_target_ _property_)*
- *sanitizers*
    + *target_add_sanitizer(_target_ _sanitizer_)*
    + *target_disable_sanitizers(_target_)*
    + *add_sanitizer_targets(_target_)*

Enabling the *clang-format* code autoformatter and the *clang-tidy* static analyser can be accomplished with CMake options `enable_clang_format` and `enable_clang_tidy`, which can be set in another *CMakeLists.txt* file, or by passing them as variables during the CMake configuration step.

*print_target_properties(_target_ _property_)* can be used to inspecting  target's properties, for example:

```CMake
 print_target_properties(target LINK_LIBRARIES)
 print_target_properties(target COMPILE_OPTIONS)
```

### Sanitizers

Sanitizer runtimes can be added to build targets using the *target_add_sanitizer* function. Only compatible sanitizers can be set, an error will be produced if the user attempts to combine incompatible ones.

For example, to add the *memory sanitizer* to a target, the user can include in their *CMakeLists.txt* file:

```cmake
add_executable(exe "src/target.cpp") # some target
target_add_sanitizer(exe memory)
```

Alternatively, the user can create separate targets with one or all sanitizers enabled by specifying:

```cmake
add_sanitizer_target(exe memory)
add_sanitizer_targes(exe)
```

These will add separate build targets named *exe_with_memory_sanitizer*, *exe_with_thread_sanitizer*, etc., for a target *exe*.

The following table lists the possible sanitizer combinations.

| No. |  Sanitizer combination | Compatibility |
|:--- | ---------------------- | ------------- |
| 1.  | leak      + memory     | NOT ALLOWED   |
| 2.  | leak      + thread     | NOT ALLOWED   |
| 3.  | leak      + address    | OK            |
| 4.  | leak      + undefined  | OK            |
| 5.  | memory    + leak       | NOT ALLOWED   |
| 6.  | memory    + thread     | NOT ALLOWED   |
| 7.  | memory    + address    | NOT ALLOWED   |
| 8.  | memory    + undefined  | OK            |
| 9.  | thread    + leak       | NOT ALLOWED   |
| 10. | thread    + memory     | NOT ALLOWED   |
| 11. | thread    + address    | NOT ALLOWED   |
| 12. | thread    + undefined  | OK            |
| 13. | address   + leak       | OK            |
| 14. | address   + memory     | NOT ALLOWED   |
| 15. | address   + thread     | NOT ALLOWED   |
| 16. | address   + undefined  | OK            |
| 17. | undefined + leak       | OK            |
| 18. | undefined + memory     | OK            |
| 19. | undefined + thread     | OK            |
| 20. | undefined + address.   | OK            |
