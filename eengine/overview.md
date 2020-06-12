[:back:](/home)
---

# ExOT Experiment Ecosystem

The figure below illustrates the structure of an experiment setup with ExOT:

![ExOT Experiment Setup Overviewl](../uploads/figures/execution_blockdiag.svg)

In this page, we will describe the different components and their purpose:

## Experiment Engine

### Experiment

### Configuration file

### Environment description file

### Experiment data

### Driver

## Experiment Environment

The experiment environment is defined in the descriptor files in the [./desc]() directory.
It can consist of one or multiple zones.
Each zone defines a (physical or virtual) machine.
During the experiment, the different applications are launched in the respective zones, defined in the descriptor files.
The machines used in an environment have to comply to following demands from the framework:
* Root access to the framework 
* Be able to run the respective applications.
* TODO shell emulators (screen tmux) - driver constraints

### Zone(s)

### Source app

### Sink app

### Jammer app(s)

## Experiment Host
This machine has checkouts of all the necessary repositories, needed for the experiment execution. 
These repositories are (at least but not limited to):
* [Datprocessing Repository]()
* Application Repositories (e.g. for [pure Unix]() and [Android]() platforms)

Furthermore, this platform fullfills all the prerequesits to run the framework:

## Backup
The Backup machine is simply a longterm storage for the experiment data.
It has to be a storage server which is accessible via ethernet using TODO for data transfer.


