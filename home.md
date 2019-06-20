# App Lib library

Welcome to the application library's knowledge base. The library has been originally created to support the development and evaluation of covert and side channels, with primiary focus on extendability and ease of use.

# ToC

#### Basics

1. [How to use the library?](1.-Basics/How-to-use-the-library%3F)
2. [How to contribute to the library?](1.-Basics/How-to-contribute-to-the-library%3F)
3. [Framework overview](1.-Basics/Framework-overview)

#### How-to's

1. [Docker-based development environment](2.-How-to's/Dockerised-build-environment)
2. [Building applications](2.-How-to's/Building-applications)
3. [Creating process network components](2.-How-to's/Creating-process-network-components)
4. [Creating metering modules](2.-How-to's/Creating-metering-modules)

#### Documentation

1. [The core framework](3.-Documentation/The-core-framework)
2. [Provided components](3.-Documentation/Provided-components)
3. [Available metering modules](3.-Documentation/Available-metering-modules)
4. [Utilities](3.-Documentation/Utilities)
5. [Platform specific primitives](3.-Documentation/Platform-specific-primitives)

# TEC Security Experimental Framework

## Experiment Ecosystem
The experiment framework ecosystem consists of three parts, which are described in the following sections.

### Host
This machine has checkouts of all the necessary repositories, needed for the experiment execution. 
These repositories are (at least but not limited to):
* [Datprocessing Repository]()
* Application Repositories (e.g. for [pure Unix]() and [Android]() platforms)

Furthermore, this platform fullfills all the prerequesits to run the framework:

* TODO

### Environment
The experiment environment is defined in the descriptor files in the [./desc]() directory.
It can consist of one or multiple zones.
Each zone defines a (physical or virtual) machine.
During the experiment, the different applications are launched in the respective zones, defined in the descriptor files.
The machines used in an environment have to comply to following demands from the framework:
* Root access to the framework 
* Be able to run the respective applications.
* TODO shell emulators (screen tmux) - driver constraints

### Backup
The Backup machine is simply a longterm storage for the experiment data.
It has to be a storage server which is accessible via ethernet using TODO for data transfer.

## Experiment Flow

### Generating an Experiment

### Executing an Experiment

### Analysisng an Experiment

### Restoring an Experiment

