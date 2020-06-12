[:back:](/home)
---

# Overview

The *Application Library* facilitates the creation of sending and receiving applications that interoperate with the entire Experiment Orchestration Toolkit.

The library is implemented in C++17, and takes advantage of many modern language features. It broadly uses generic programming and compile-time code generation as well as avoids complex class hierarchies. The library can be rather easily extended. It has been successfully applied in creating sender and receiver applications for, among others, cache-based, thermal, and power covert channels.

The library provides a way of creating application based on the process networks model of computation, where individual nodes are connected together and pass data via queues. Its design details are described in a [white paper](http://pub.tik.ee.ethz.ch/people/miedlp/2020-05-22_ExOT_Whitepaper.pdf).

## Terminology

- __Framework__ → The core of the application library that implements the process networks model of computation and is described in detail on the [dedicated wiki-page](./core-framework).

- *Computational model terminology* → The implemented model of computation uses the terms:

    1) __Node__ → a single element of the process network;

    2) __Process__ → a class, which has access to the global state and can be executed;

    3) __Interface__ → an abstraction of the transmission media between the nodes, can be either a *Writer* or a *Reader* interface;

    4) __Producer__, __Consumer__, __Processor__ → refer to nodes that provide writing, reading, or both interfaces;

    5) __Executor__ → an executor can spawn a __Process__ or any callable object, for example in a new system thread;

- __Component__ → A *component* is a single self-contained element of the process network model. A component is an implementation of a __Process__ and a __Producer__, a __Consumer__, or a __Processor__ (depending on the configuration of input/output interfaces it has). A component can be *spawned* by an __Executor__.

- __Module__ → The term *module* is used to refer to encapsulated pieces of functionality, which are smaller than __Components__ and which cannot be directly executed. The library defines __Generator__ and __Meter__ modules, which either impose some kind of a load on the system, or measure one or more of its properties.

- __Host__ → A *host* is a __Component__ that can combine one or more __Modules__ into a single __Component__. The library features hosts for load-generating and metering modules.

- __Generator__ → A *generator* is a __Module__ that imposes a load on the system.

- __Meter__ → A *meter* is a __Module__ that reads or measures one or more properties of the system.

- __Primitive__ → *Primitives* are facilities provided in the library that are architecture- and/or platform-specific, and which target low-level features of a system. Examples of *primitives* are specialised clocks, counters, cache manipulators or memory ordering functions.

- __Utilities__ → The library provides a wide range of generic *utilities* that power other parts of the library, but can also be used independently. Examples include functions for working with files and directories, formatting text, performing platform identification, or meta-programming facilities.

- __Configuration__ and __Settings__ → A *settings* structure defines parameters of a __Module__, __Component__ or any other *configurable* object. These settings structures can be *configured* externally from a JSON string or file. A class that can be configured in this way is refered to as a __Configurable__. A *configurable* has its own namespace for accessing parameters in the __Config__.

- __Config__  → The *config* is JSON-formatted data that can be provided to __Configurable__ *modules* and *components*, which access their respective data using their pre-defined namespaces. All JSON data types can be read into many data types in the C++ STL.

## Structure

The repository structure reflects the core parts of the library and consists of the following folders:

- [**framework**](https://gitlab.ethz.ch/tec/public/exot/app_lib/tree/master/include/exot/framework) → includes the highly templated implementation of the core framework, including nodes, interfaces, queues, connectors, executors, and the state holder.
- [**components**](https://gitlab.ethz.ch/tec/public/exot/app_lib/tree/master/include/exot/components) → includes the classes or class templates of main components, including hosts for generator and metering modules.
- [**meters**](https://gitlab.ethz.ch/tec/public/exot/app_lib/tree/master/include/exot/meters) → includes a large number of metering modules for system state ranging from the state of the cache, to CPU core temperatures.
- [**generators**](https://gitlab.ethz.ch/tec/public/exot/app_lib/tree/master/include/exot/generators) → includes a few generator modules (and convenient base classes for them) for imposing load on the CPU or its subsystems.
- [**primitives**](https://gitlab.ethz.ch/tec/public/exot/app_lib/tree/master/include/exot/primitives) → includes a number of platform-specific facilities for timing, memory ordering, and access to caches and special CPU features.
- [**utilities**](https://gitlab.ethz.ch/tec/public/exot/app_lib/tree/master/include/exot/utilities) → includes a vast array of generic-purpose and specialised utilities.

## Namespaces

The project's main namespace is `exot`. It is further divided into sub-namespaces:

- `exot::framework` for core framework code,
- `exot::components` for the components,
- `exot::modules` for modules, both meters and generators,
- `exot::primitives` for the primitives as described above,
- `exot::utilities` for all utilities.

Occassionally, inline namespaces or special `details` namespaces are used. These are considered internal.
