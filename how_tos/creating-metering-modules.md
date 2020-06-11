[:back:](/home)
---

# Creating meter modules

In the context of the application library, measuring some shared state can be most effectively accomplished with the help of __metering modules__. These encapsulate all the required configuration, setup, and measurement procedures in a way that can be most readibly used with the rest of the library. The biggest advantage of using _metering modules_ is their integration with the _meter host_, a component that can combine individual _meter modules_ into larger measurement applications. ["Assembling metering modules"](how-tos/assembling-metering-modules) shows how these are integrated in the host component.

### Requirements

> __Note__: The requirements may change in the coming future. However, any changes should only impact the way that settings structures are configured, and should be backwards-compatible. Upgrading should be quite trivial, as long as the first requirement is satisfied.

A meter module has to satisfy a minimal set of requirements:

1. It must have a settings structure named `settings`, which can provide defaults, and can also be empty. For greatest compatibility and ease of use, one can use fundamental data types as well as simpler data types from the Standard Template Library, including:
    + simple data types: integers (signed/unsigned, long, long long), floating-point numbers, char's, enums and enum classes, booleans;
    + `std::string`'s;
    + standard containers: vectors, arrays, maps, sets and lists of the data types above;
2. It must have a static member function *configure(settings&) : clipp::group*, that configures the `settings` class provided by reference, and returns a command-line interface configuration group. It can return an empty one too;
3. It must have a constructor that takes the `settings` structure by reference;
4. It must have a *measure()* function that takes no arguments. The function can return most data types, preferably one that is [trivial](https://en.cppreference.com/w/cpp/language/copy_constructor#Trivial_copy_constructor). Most existing modules return `std::vector`s of *int* or *double*;
5. It should provide a *names_and_units()* function that returns a vector of `std::string`s if the user wants to facilitate the process of adding headers to log files;
6. The module should follow the [RAII (Resource Acquisition is Initialisation) idiom](https://en.cppreference.com/w/cpp/language/raii): the module should be perfectly usable after instantiation, and the life cycle of the resources it acquires should be limited to the lifetime of the module. If resources cannot be acquired, the module should fail and throw an exception.
7. The module class must inherit from the empty `covert::modules::module` base class for type-checking purposes.
8. It must have a member type called `return_type` that declares the type returned by the `measure()` function.

> __Note__: the last requirement is not absolutely necessary and may be removed in the future, but still can be improve clarity.

### Example

As an example, we will walk through the creation of a metering modules that returns the number of processes visible in *procfs*.

Firstly, the class for the module has to be declared. It is also preferred to declare the alias for the return type at the beginning of the class definition. Member variables can also be specified here, preferably as *private*.

```c++
struct NewModule : covert::modules::module {                              // l.1
    using return_type = unsigned int;                                     // l.2
```

Next, we declare our settings member class. In this particular case it will be empty. The associated *configure* function will also return empty.

```c++
    struct settings {};                                                   // l.3
    static clipp::group configure(settings &s) {                          // l.4
        return clipp::group{};                                            // l.5
    }                                                                     // l.6
```

The constructor can be declared next. Since there is usually no default constructor, the one taking a parameter should be specified as *explicit*. In this simple example, we will not do anything, as the module does not acquire any resources.

```c++
    explicit NewModule(settings &s) {}                                    // l.7
```

The primary functionality of the module is contained in the *measure* function. Here, we will use the utilities specified in the *filesystem.h* header file. The *grep_directory(dir, regex)* function gives the paths of files/directories in *dir* that match the regular expression *regex*. The number of directories matching */proc/\d+$* gives the number of processes available in *procfs*.

```c++
    return_type measure() {                                               // l.8
        static std::string directory{"/proc"};                            // l.9
        static std::string regex{"/proc/\\d+$"};                          // l.10
                                                                          // l.11
        auto files = covert::utilities::grep_directory(directory, regex); // l.12
        return files.size();                                              // l.13
    }                                                                     // l.14
```

The next function provides the string used for logging.

```c++
    std::vector<std::string> names_and_units() {                          // l.15
        return std::vector{"open_processes"};                             // l.16
    }                                                                     // l.17
}                                                                         // l.18
```

__The module is now complete!__ It can be integrated with other modules seamlessly via `covert::components::meter_host_logger` or `covert::components::meter_host`.
