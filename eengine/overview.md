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

The diagram below shows the general structure of a covert channel evaluation experiment. The Data Processing Framework targets all elements of the experimental flow, except for the sender and receiver applications, which are built on top of the Application Library.

![Experiment flow diagram](./uploads/figures/flow.png)

