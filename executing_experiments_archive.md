[Back to Home](/home)

[One Level Up](/executing-experiments/general)
___

# Covert Channel
_____
![CovertChannelFlow.svg](/uploads/ab713d59ca79fc8044ca199783e13d1a/CovertChannelFlow.svg)

**Figure 1:**
Possible flows for covert channel experiments. 
Squares with solid lines illustrate scripts, squares with dashed lines configuration files.
Solid arrows illustrate the flow, dashed arrows indicate which configuration files are read by a script.
_____

## Generate Experiments

In order to generate a new experiment, run the Matlab script *A\_GenerateExperiment.m*.
Before doing so, a proper configuration file *Aconf\_Experiment.m* has to be created.
A template for this configuration file *Aconf\_Experiment.m.template* can be found in the same directory.
Detailed information on the configuration and the execution script can be found within the scripts.

## Run Experiments
After the experiment has been successfully generated there are a few configuration files which need to be created.

### Toolflow Configuration

Global toolfow settings are defined in *toolflow.conf.local*, whereas it can be generated from a template called *toolflow.conf.local.template*.
This configuration file has to be placed in the root directory of the *physsec\_framework* repository.

### Backup Configuration

The backup settings are set in the *backup.conf.local* which needs to be placed in the directory *./physsec\_framework/[Attack Type]/[Attack Media]/*.
A template for this configuration file *backup.conf.local.template* is available in the same directory.

### Platform Configuration

Two files for the platform specific configuration have to be present in *./physsec\_framework/[Attack Type]/[Attack Media]/config\_platform/[Platform]*.
The *parameters.conf* defines all the important parameters of the platform, for example the number of cores or the execution concept.
*configure.sh* is used to make configurations of the platform before the experiment is run.
This script will be copied and automatically executed by the framework.
Templates for these two files can be found in *./physsec\_framework/[Attack Type]/[Attack Media]/config\_platform/Template*.
Make sure the *PLATFORM\_SCHED\_TAGS* are properly set according to the settings in the schedule generator in the *physsec\_dataprocessing* framework.

### Experiment Configuration

All experiment execution specific parameters can be set in the experiment configuration file.
The name of this file can be freely chosen but it has to reside in the directory *./physsec\_framework/[Attack Type]/[Attack Media]/config\_experiment/*.
A template for this configuration can be found in the same directory (*experiment.conf.local.template*).

After the configuration files are created, the experiments can be run manually or automatically:

* Consecutive manual execution of *0.1\_preprocess\_experiment.sh*, *0.2\_run\_experiment.sh* and *0.3\_postprocess\_experiment.sh*
* Execution of *0.0\_execute\_experiment.sh*

## Capacity Bound
TODO TBD 

TODO: Block diagram

Possible flows for covert channel capacity bound calculations.
The left illustrates the flow for noise free channels, the right side for noisy channels.

## Performance Analyse
There are several scripts for a performance analysis:
  
* *B\_SingleAnalysis.m* with the corresponding configuration file *Bconf\_SingleAnalysis.m* (template in the same directory) for analysing a single run of the experiment.
* *C\_PerformanceAnalysis.m* with the corresponding configuration file *Cconf\_PerformanceAnalysis.m* (templates in the same directory) for analysing the performance a bundle of different experiments.
* *C\_GeneralAnalysis.m* with the corresponding configuration file *Cconf\_GeneralAnalysis.m* (templates in the same directory) for general analysis of a bundle of different experiments.
* TODO: *D\_*

For detailed information check the scripts.
Results and intermediate results are saved as *.dat* files in the experiment directory tree.

## Configuration Option

_____
| **Source Coding** |         None        |  2-nary Manchester |
| ----------------- | ------------------- | ------------------ |
|	       None       | :white_check_mark:  | :white_check_mark: | 
|        2to1       | :white_check_mark:  |       :x:          |
|        3to1       | :white_check_mark:  |       :x:          |
|        4to1       | :white_check_mark:  |       :x:          |
|        5to1       | :white_check_mark:  |       :x:          |
Possible (source coding / line coding) combinations for thermal covert channel experiments.
_____
|       **Line Coding**       |       **pwm**      |    **rect**        |     **rect_vm**    |
| --------------------------- | ------------------ | ------------------ | ------------------ |
| None (all source codings)   | :white_check_mark: |         :x:        |         :x:        |
| None (source coding "None") |         :x:        | :white_check_mark: | :white_check_mark: |
| 2-nary Manchester           | :white_check_mark: | :white_check_mark: | :white_check_mark: |
Possible (line coding / signaltype) combinations for thermal covert channel experiments.
_____
| **Source Coding** |       **None**     | **RZ\_govcons\_cmd\_sec** |
| ----------------- | ------------------ | ------------------------- |
|	       None       | :white_check_mark: |    :white_check_mark:     | 
|        2to1       | :white_check_mark: |            :x:            |
|        3to1       | :white_check_mark: |            :x:            |
|        4to1       | :white_check_mark: |            :x:            |
|        5to1       | :white_check_mark: |            :x:            |
Possible (source coding / line coding) combinations for frequency covert channel experiments.
_____
|    **Line Coding**    |        **cmd**     |       **util**     |
| --------------------- | ------------------ | ------------------ |
| RZ\_govcons\_cmd\_sec | :white_check_mark: |         :x:        |
Possible (line coding / signaltype) combinations for frequency covert channel experiments.
_____
|   **Signaltype**  | **freq-cc\_conservative** |   **loadgen\_bc**  |   **loadgen\_mt**  |  **loadgen\_pwm**  |   **loadgen\_st**  |
| ----------------- | ------------------------- | ------------------ | ------------------ | ------------------ | ------------------ |
| frequency cmd     |    :white_check_mark:     |         :x:        |         :x:        |         :x:        |         :x:        |
| frequency util    |    :white_check_mark:     |         :x:        |         :x:        |         :x:        |         :x:        |
| thermal pwm       |            :x:            |         :x:        |         :x:        | :white_check_mark: |         :x:        |
| thermal rect      |            :x:            | :white_check_mark: | :white_check_mark: |         :x:        | :white_check_mark: |
| thermal rect\_vm  |            :x:            |         :x:        |         :x:        |         :x:        |         :x:        |
Possible (signaltype / source application) combinations.
_____
|   **SNK Applications**  |     **thermal**    |   **thermal\_vm**  |    **frequency**   |      **power**     |
| ----------------------- | ------------------ | ------------------ | ------------------ | ------------------ |
| *meter\_thermal\_adb*   | :white_check_mark: |          :x:       |         :x:        |         :x:        | 
| *meter\_freq\_cpuinfo*  |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_freq\_freqinfo* |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_freq\_sysfs*    |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_freq\_sysfsdbg* |         :x:        |          :x:       | :white_check_mark: |         :x:        | 
| *meter\_power*          |         :x:        |          :x:       |         :x:        | :white_check_mark: |
| *meter\_thermal*        | :white_check_mark: |          :x:       |         :x:        |         :x:        |
Possible (sink application / attack media) combinations.
_____

____
[Back to Home](/home)

[One Level Up](/executing-experiments/general)
