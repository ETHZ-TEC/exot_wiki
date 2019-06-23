The design of the library and the core framework is motivated by the typical channel model found in this field of research, shown below.

![A typical channel model](../uploads/figures/channel-model.png)

The library implements a subset of the *process network* model of computation, and allows combining the different components of the channel model into linear process networks. One possible realisation of a channel is shown below.

![The process network model](../uploads/figures/process-network.png)

For further information about the library's design considerations please refer to the [original thesis](../uploads/documents/app_lib_thesis.pdf).

The core framework of the library [provides](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/tree/master/include/covert/framework) the building blocks necessary for using the *process network* model:

> __Note:__ At the moment no extended documentation for all the core framework's features is provided. Please refer to the linked files to view the complete documentation.

1. **Nodes**: Components that encapsulate reading/writing interfaces and contain the executable processes of the network. The definition of the node classes for token producers, consumers, and processors are available in [include/framework/node.h](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/node.h).
2. **Interfaces**: Abstractions of the underlying communication mechanism that enforce the formalism of the *process network* MoC. These are defined in [include/framework/interface.h](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/interface.h).
3. **Queues**: Queues are the primary containers through which the process network nodes communicate. The library provides, in [include/framework/queue.h](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/queue.h), a thread-safe `LockingQueue` template as well as a `TimeoutLockingQueue`, which defines extended queue access semantics (with methods like *try_read* and *try_write_for*) that can "circumvent" traditional blocking reads and writes. These are available at [include/framework/queue.h](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/queue.h).
4. **Connectors**: High level utilities that connect nodes together, verify their compatibility and create the necessary queues. The connector template functor and functions are available at [include/framework/connect.h](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/connect.h).
5. **Executors**: Utilities, provided in [include/framework/executor.h](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/executor.h), that facilitate executing the nodes' processes on system and user-space threads. 
6. **State**: Lastly, the framework [provides](https://gitlab.ethz.ch/tec/research/benchmark_suite/app_lib/blob/master/include/covert/framework/state.h) a simple way of holding local and global state, with thread-safe access.
