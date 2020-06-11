[:back:](/home)
---

> Note: This page is partly outdated and needs to be updated!

# Building applications

The way in which applications are built with the help of the library is quite straightforward. A number of ready-to-use applications are available in the [Unix applications repository](https://gitlab.ethz.ch/tec/public/exot/app_unx).

The following example shows how to construct a frequency and utilisation metering application. It is based on the [_procfs_ utilisation](https://gitlab.ethz.ch/tec/public/exot/app_lib/blob/master/include/exot/meters/utilisation_procfs.h), [_sysfs_ frequency](https://gitlab.ethz.ch/tec/public/exot/app_lib/blob/master/include/exot/meters/frequency_sysfs.h), and [relative frequency](https://gitlab.ethz.ch/tec/public/exot/app_lib/blob/master/include/exot/meters/frequency_rel.h) metering modules.

Firsly, the used header files have to be included. These will primarily consist of:

- The header file combining all core framework's headers.
  ```c++
  #include <covert/framework/all.h>
  ```
- Header files for command-line parsing and logging support.
  ```c++
  #include <exot/utilities/cli.h>
  #include <exot/utilities/logging.h>
  ```
- The used components. In the case of a metering application, these will include metering module host and the individual modules.
  ```c++
  #include <exot/components/meter_host_logger.h>
  #include <exot/meters/frequency.h>
  #include <exot/meters/utilisation.h>
  ```

Inside the *main* function it is useful to create aliases to the used classes, such that the namespaces do not have to be included and changes can be easily applied. In this case we create aliases for the metering modules, and create a type alias for the meter host logger. Please refer to other wiki pages for further information on how to [combine](2.-How-to's/Assembing-metering-modules) and [create](2.-How-to's/Creating-metering-modules) metering modules.

```c++
int main(int argc, char** argv) {
  using exot::modules::frequency_rel;
  using exot::modules::frequency_sysfs;
  using exot::modules::utilisation_procfs;
  using meter_type =
      exot::components::meter_host_logger<std::chrono::microseconds,
                                            utilisation_procfs, frequency_sysfs,
                                            frequency_rel>;
  using exot::utilities::CLI;
  using exot::utilities::Logging;
```

The next steps involve:

1. creating the command-line interface object,
2. creating settings objects for components and logging,
3. adding the individual command-line configurations to the master configuration, and
4. parsing the command-line arguments.

```c++
  CLI cli;

  meter_type::settings meter_settings;
  Logging::settings Logging_settings;

  cli.add_configurations(meter_type::configure(meter_settings),
                         Logging::configure(Logging_settings));

  if (!cli.parse(argc, argv)) return 1;
```

If the parsing was successful, the global state handlers can be initialised:

```c++
  exot::framework::init_global_state_handlers();
```

And components can be instantiated with the configured settings:

```c++
  Logging logging(Logging_settings);
  meter_type meter(meter_settings);
```

The last step involves creating the executor object and spawning the node processes.

```c++
  exot::framework::ThreadExecutor exec;
  exec.spawn(meter);
  exec.join();

  return 0;
}
```

The executor contains a [variadic template function](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/executor.h#L79) that allows spawning any number of node processes with a simple interface:

```c++
exec.spawn(component1, component2, component3, ...);
```

And can also be used for spawning arbitrary callable objects:

```c++
exec.spawn([]() {
    std::cout << "Spawned by passing a lambda" << std::endl;
});

struct Functor {
    void operator()(int arg) {
        std::cout << "Spawned by passing a functor with " << arg << std::endl;
    }
}

Functor f;

exec.spawn(f, 1); // prints "Spawned by passing a functor with 1"
exec.spawn(f, 2); // prints "Spawned by passing a functor with 2"
```

Additionally, the `ThreadExecutor` can be used to spawn callables on specialised threads with:

```c++
exec.spawn_with_properties(2 /* cpu */,
                           SchedulingPolicy::Fifo,
                           90 /* priority */,
                           [](const char* msg) {
                             std::cout << "msg = " << msg << std::endl;
                           },
                           "Hello, World!"
);
```
