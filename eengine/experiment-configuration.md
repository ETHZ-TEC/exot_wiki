[:back:](/home)
---

# Experiment configuration

The experiment configuration is written in TOML for readability and extendability. 
The python eengine takes advantage of the TOML module to parse the files.
In this page, we explain all the different sections of a ExOT experiment configuration file in detail. 
Please also have a look at the [examples provided in the ExOT eengine repository](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/configurations/examples/).

## Root
| Parameter                  | Description                                                                         |
| -------------------------- | ----------------------------------------------------------------------------------- |
| `name`                     | Name of the experiment, also used to name the experiment root directory.            |
| `save_path`                | Path relative to the experiment root path, where the experiment is stored. By default it is `./data`. |
| `backup_path`              | Path relative to the experiment root path, where the local experiment backup is stored. By default it is `./data/_backup/`. |
| `experiment_exists_action` | Action that is performed when the experiment already exists if the `write()` method is invoked. Options are `overwrite`, `update`, `move`, `halt` |

## EXPERIMENT
| Parameter                  | Description                                                                         |
| -------------------------- | ----------------------------------------------------------------------------------- |
| `type`                     | Type of experiment, for example `PerformanceExperiment`. For detailed information see the [experiment type page](./experiment-types) |
| `channel`                  | Channel that is analysed, for example `PowerCC` or `ThermalSC`. For detailed information, refer to the [channel analyses page](./channel). |

### EXPERIMENT.PHASE
Phases are groups of runs in an experiment. 
The definition of the phases varies for the different experiment types.

#### Application execution 
Definition of one phase `test` with one run named `dropbox2`:

```toml
[EXPERIMENT.PHASES.test]
repetitions=4

[EXPERIMENT.PHASES.test.dropbox2]
schedules=[
           'configurations/examples/RepetiTouch/Sony_Xperia_Z5_Dropbox.rpt',
           'configurations/examples/RepetiTouch/Samsung_Galaxy_S5_SM-900H_Dropbox.rpt'
          ]
durations=[44.7,30.3]
environments=['Z5', 'S5']
```


| Phase Parameter | Type | Description |
| --------- | ---- | ----------- |
| `repetitions` | `int` | Number of repetitions of the runs in this phase. |
| Runs | `str` | Define each run manually. |

| Run Parameter | Type | Description |
| --------- | ---- | ----------- |
| `schedules` | `list` of `str` | Paths relative to the experiment engine path to the schedule file used in this run. |
| `durations` | `list` of `float` | Duration of each schedule in seconds. |
| `environments` | `list` of `str` | The environment the respective schedule is used in. |

#### Frequency sweep
One phase named `sweep`:

```toml
sweep = {length_seconds = 10,  repetitions = 1, frequencies = [0,1,5,10], signal=[-1,0]}
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| length_seconds | int, float | Length of the input wave in seconds | 
| `repetitions` | `int` | Number of repetitions of the runs in this phase. |
| `frequencies` | `list` of numeric values | Which input frequencies will be evaluated in this phase. | 
| `signal` | - | Definition of the used signal, can be a literal definition like in the example or a function. |


#### Performance analysis
Definition of two phases `train` and `eval`, which evaluate the performance for three symbol rates:

```toml
train = {bit_count = 150, symbol_rates = "[100, 500, 5000]", repetitions = 2}
eval  = {bit_count = 500, symbol_rates = "[100, 500, 5000]", repetitions = 2}
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `bit_count` | `int` | Number of bits sent for each symbol rate. | 
| `symbol_rates` | `list` of numeric values as `str` | Defines all symbol rates which should be evaluated in this phase. Also `range` and list concatenations and other simple python commands are allowed. | 
| `repetitions` | `int` | Number of repetitions of the runs in this phase. |

#### Exploratory analysis
For these experiments, the phases are often not defined in the TOML configuration file, but dynamically generated using python code.
An example could be:

```python
rdp_signals = [
                  pd.DataFrame(
                      # 10 periods of a rectangular waveform with 1Hz
                      data=np.hstack([np.full([20,1], 0.50), np.resize([1,0],[20,1])]), 
                      columns=['timestamp', 't440p']
                  ),
                  pd.DataFrame(
                      # 10 periods of a rectangular waveform with 2Hz
                      data=np.hstack([np.full([20,1], 0.25), np.resize([1,0],[20,1])]), 
                      columns=['timestamp', 't440p']
                  )
              ]
experiment.config.EXPERIMENT.PHASES = AttributeDict.from_dict(
    {'test':{'rdpstreams':rdp_signals,'repetitions':2}}
)
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `rdstreams` | `pd.DataFrame` | Raw data stream used to generate the schedule files for the source application. |
| `repetitions` | `int` | Number of repetitions of the runs in this phase. |



### EXPERIMENT.LAYERS
The layers are specified one by one, as shown in the example bellow:
```toml
src = {name = "BitsetCoding", params = {bitset_length = 64}}
lne = {name = "MultiN", params = {N = 64}}                  
rdp = {name = "DirectActivation", params = {}}              
io  = {name = "TimeValue", params = {timebase = "ns"}}      
```

| Parameter                  | Type | Description |
| -------------------------- | ---- | -------------------------------------------------------------------------- |
| `name`                     | `str` | Name of the layer. |
| `params`                   | `dict' | Dictonary holding all the layer parameters. For detailed information please see the [information flow page](./information-flow) |

### EXPERIMENT.GENERAL
| Parameter                  | Type | Description |
| -------------------------- | ---- | -------------------------------------------------------------------------- |
| `latency`                  | `int` | Maximal cpu-dma-latency in microseconds, to prohibit deep sleep states. |
| `fan`                      |  `bool` or `int` |Fan control parameter. Depending on the platform and the driver, either a `boolean` value or an `int` between `0` and `255`. |
| `governors`                | `str` | Specifies the governor which should be used. |
| `frequencies`              | 'numeric' or 'str' | If the userspace governor is used, this parameter defines the target frequency. The value can either be one value defined in the list of frequencies in the environment descriptor file, "min" or "max". |
| `sampling_period`          | 'numeric' | Sampling period of the sink application in seconds. |
| `delay_after_spawn`        | 'numeric' | Waiting time in seconds, after the applications are ready to start the execution. |
| `delay_after_auxiliary`    | 'numeric' | Waiting time in seconds, after the jammer applications started the execution.     |
| `active_wait`              | `bool` | Use an active wait (might cause interference) or sleep-wait (might cause delay in the start of the application. |

#### Overwriting general settings
General experiment settings might change for different environments.
Therefore, general application settings can be overwritten for specific applications.
An example, where the settings for the `ARMv8` environment are overwritten:

```toml
[EXPERIMENT.GENERAL.ARMv8]
fan = "255"
sampling_period = 225e-6
```

#### Application timing

![Application timing](../uploads/figures/app_timing.svg)

## ENVIRONMENTS

###  ENVIRONMENTS.\<PLATFORM NAME\>.APPS
The sink and the source applications are defined as in the following example:
```toml
snk = {executable = "meter_cache_ff", zone = "host"}
src = {executable = "generator_cache_read_st", zone = "host"}
```

| Parameter                  | Description                                                                       |
| -------------------------- | --------------------------------------------------------------------------------- |
| `executable`               | Executable to be used. Has to be situated in the application directory  of the environment zone, specified in the environemnt descriptor file. |
| `zone`                     | Zone in which the application is executed. |

### ENVIRONMENTS.\<PLATFORM NAME\>.src and ENVIRONMENTS.<PLATFORM NAME>.snk
See application configuration nodes and examples.

### ENVIRONMENTS.\<PLATFORM NAME\>.APPS.<JAMMER NAME>
Standalone jammer applications are defined according to the bash command that is invoked to start them.
For example, the following defines the use of the `ffmpeg` application to convert a `mp4` video in an endless loop:

```toml
[ENVIRONMENTS.Haswell.APPS."ffmpeg"]
executable = "ffmpeg"
type = "standalone"
start_individually = true
zone = "host"
args = [
"-y",
"-loglevel", "error",
"-stream_loop", "-1",
"-i", "media/video.mp4",
"-c:v", "libx264",
"-b:v", "1000k",
"-f", "null", "/dev/null"
]
```


