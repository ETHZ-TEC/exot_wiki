[:back:](/home)
---

# Experiment types

+ [Exploratory experiments](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/notebooks/examples/demo_exploratory_experiment.ipynb) can be used for example to to get to know the data leak characteristics. Only require an `io` layer, the signal can be generated dynamically by the user.
+ [Frequency sweep experiments](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/notebooks/examples/demo_frequency_sweep_experiment.ipynb) can be used to determine the channel spectras of continuous channels with frequency sweeps.
+ [Performance experiment](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/notebooks/examples/demo_performance_experiment_with_interference.ipynb) are used to evaluate the performance of a data lean/communication channel under controlled conditions.
+ [Application execution experiment](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/notebooks/examples/demo_app_exec_experiment.ipynb) can be used to characterise the effects of an application execution on a platform. For example, monitor the temperature trace, power consumption, cache accesses, etc. caused by the execution of an application.

# Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::experiment::_base`](#namespaceexot_1_1experiment_1_1__base) | 
`namespace `[`exot::experiment::_factory`](#namespaceexot_1_1experiment_1_1__factory) | 
`namespace `[`exot::experiment::_mixins`](#namespaceexot_1_1experiment_1_1__mixins) | 
`namespace `[`exot::experiment::app_exec`](#namespaceexot_1_1experiment_1_1app__exec) | 
`namespace `[`exot::experiment::exploratory`](#namespaceexot_1_1experiment_1_1exploratory) | 
`namespace `[`exot::experiment::frequency_sweep`](#namespaceexot_1_1experiment_1_1frequency__sweep) | 
`namespace `[`exot::experiment::performance`](#namespaceexot_1_1experiment_1_1performance) | 
`class `[`exot::experiment::_base::Experiment::Type`](#classexot_1_1experiment_1_1__base_1_1Experiment_1_1Type) | Experiment types

# namespace `exot::experiment::_base` {#namespaceexot_1_1experiment_1_1__base}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::experiment::_base::Experiment`](#classexot_1_1experiment_1_1__base_1_1Experiment) | 
`class `[`exot::experiment::_base::Run`](#classexot_1_1experiment_1_1__base_1_1Run) | 

# class `exot::experiment::_base::Experiment` {#classexot_1_1experiment_1_1__base_1_1Experiment}

```
class exot::experiment::_base::Experiment
  : public SubclassTracker
  : public Pickleable
  : public Configurable
  : public Loggable
  : public track
  : public serialise_stub
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`channel`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a99b6b2c3070db0e8d450a48ce1c71a87) | 
`public  `[`drivers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a225a56fe5c5e2a0fce2fadf1b013beb2) | 
`public  `[`run_type`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afd12ca899670493b4e915097067c2052) | 
`public None `[`__init_subclass__`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a16d7e3fa508d3032817c2efccbc801f0)`(cls,* args,** kwargs)` | 
`public def `[`config`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a9996a4d67e7cd5b8d1d9a4c8b6b3da3d)`(self,value)` | 
`public def `[`config`](#classexot_1_1experiment_1_1__base_1_1Experiment_1ad010f1865e929e22456f4a0a0a1cbf9b)`(self)` | 
`public def `[`run_type`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afeb1ec5ef6add0b9b9cc9f538a1b1c4e)`(self)` | Get the associated Run type
`public def `[`run_type`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aac95266bc882a6989739b50131d43b3d)`(self,value)` | Set the associated Run type
`public def `[`__init__`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a342fa624f317fc5863f9fee195b3c45f)`(self,* args,** kwargs)` | Initialise an Experiment object
`public None `[`bootstrap`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a33a673a50a00c4b41f9302c3262bb9f1)`(self,** kwargs)` | Parse configuration and create experiment layers using a layer factory
`public bool `[`bootstrapped`](#classexot_1_1experiment_1_1__base_1_1Experiment_1af10540afb73495e22ed45856f91279a9)`(self)` | Are the experiment layers bootstrapped?
`public AttributeDict `[`layers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1ab00b8e0278e3a26a0dcc6f431faad25e)`(self)` | Get experiment layers
`public AttributeDict `[`layers_with_runtime_encoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a75ed63fe1bc39abc4b2705be38358b83)`(self)` | Get experiment layers that require configuration at runtime
`public AttributeDict `[`layers_with_runtime_decoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7d8e29e0876d7e6e1cc43a96ff593783)`(self)` | Get experiment layers that require configuration at runtime
`public None `[`configure_layers_encoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a79e6f718d2e625e1aec981c69246c25d)`(self,**t.Any kwargs)` | Configure layers with runtime-configurable encoding
`public None `[`configure_layers_decoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa6ddd4a0a23753f33a6fa44b6695c367)`(self,**t.Any kwargs)` | Configure layers with runtime-configurable decoding
`public str `[`__repr__`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a4ba498d6bae66d050bb52bb46865c4ac)`(self)` | Get a string representation of the Experiment
`public list `[`required_config_keys`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a399922f6a6056200528daf6179f1bffd)`(self)` | Gets the required config keys
`public float `[`estimated_delays_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a2ef877035f06143634300c612a00a0e9)`(self)` | Gets the estimated duration of the defined delays
`public None `[`validate`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a4906a91b8ceee6c52bd1679b5b16d186)`(self)` | Check if the supplied Experiment config is valid
`public AttributeDict `[`environments`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a33cf3af19166807f3df7655022ac98cc)`(self)` | Get available environments
`public def `[`environments`](#classexot_1_1experiment_1_1__base_1_1Experiment_1addef21e569c30af8879f0f1fb52ff795)`(self,t.Mapping value)` | Set available environments
`public t.Mapping `[`environments_apps_zones`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a665566412a6e83c2a43ebc225d4b35c2)`(self)` | Get a mapping with environments, apps, zones and zone configs
`public list `[`available_environments`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a344515cd4404ee9ff0e3c164cce9072a)`(self)` | Get names of available environments
`public AttributeDict `[`environment_config_general`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a18223bdd0b93fe70b2e5eac55f653bc2)`(self,str env)` | Provides an environment-specific proxy to the general experiment config
`public t.Optional[str] `[`name`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a174e03c45355e9402d7afe5a129d22d7)`(self)` | Get experiment name
`public t.Optional[Path] `[`save_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa43150be01f91ea150913a19cca20a51)`(self)` | Get save path for experiments
`public t.Optional[Path] `[`log_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1ac19747e4bb6eff6ed3c99deace8dce56)`(self)` | Get experiment log path
`public t.Optional[Path] `[`path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a5871801f02d6c5785eb1c4fab2c4479c)`(self)` | Get the save path of the particular Experiment
`public t.Optional[Path] `[`root_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a4a43ab4e38274c96d945a96bffa6ac4f)`(self)` | Get the exot root path
`public Path `[`remote_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7170f47a4b73bfa9b389183b4b769b12)`(self,str env,str zone)` | Get a remote experiment path given an environment and a zone
`public Path `[`remote_save_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a909ee0bc8a555f33977875c09c318866)`(self,str env,str zone)` | Get a remote experiment path given an environment and a zone
`public Channel `[`channel`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a6df8dc3d6ebaf0adbafc1bd925e2ac2b)`(self)` | Get the configured channel
`public None `[`channel`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a034ec8e2bb92023a29a3dba7d2d5500b)`(self,Channel value)` | Set the experiment channel
`public t.Optional[AttributeDict] `[`drivers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a8cc9ca7b706e064049319d359f67a979)`(self)` | Get the experiment drivers
`public None `[`drivers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a9410a7f87cda99291cf614eaeac51532)`(self,]] value)` | Set the experiment drivers
`public t.Dict `[`phases`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a02a980b786cce904ebf887370bb91634)`(self)` | Get experiment phases
`public None `[`phases`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa36706ccd02c83f6f8f766752aca8f24)`(self,t.Dict value)` | Set experiment phases
`public None `[`write`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a04e50fb10fd081badcfbca272b2faaab)`(self)` | Serialise the experiment
`public `[`Experiment`](#classexot_1_1experiment_1_1__base_1_1Experiment)` `[`read`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a488aadcd3cd4a96f188961a4d55e45ba)`(cls,Path path,t.Optional new_root_path,*bool diff_and_replace)` | Read a serialised Experiment and produce an Experiment instance
`public None `[`backup`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7f4c140664161a93e547d82ba87a6af7)`(self,bool _with_logs,bool _with_results)` | Archive an Experiment and, if possible, upload to a backup server
`public None `[`generate`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a54b838056cf807f5a5dd0995fe8dc2c9)`(self)` | Populate the experiment phases and instantiate Run's
`public t.Dict `[`estimated_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa0f45ad4385e4a6bb06a66c71ec602a3)`(self)` | Get durations of experiment phases
`public None `[`estimated_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a75a8ec4e9fa15635d8e2fa5c0ae6bbdb)`(self,t.Dict value)` | Set experiment phases
`public None `[`print_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1acd6064661320a7c745e2836774c817ef)`(self)` | Prints the estimated experiment duration
`public t.Generator `[`map_to_runs`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7029efae953f50ec6a8519882c4d4f2a)`(self,t. Callable,t.Any] function,*bool parallel)` | Map a function to the Runs concurrently
`public dict `[`execution_status`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afa9d0c60fb675ebec900342024c4e0f5)`(self)` | Gets the experiment execution status
`public dict `[`infer_execution_status`](#classexot_1_1experiment_1_1__base_1_1Experiment_1af5503e615e389478440984332185d74d)`(self)` | Infers the execution status from contained Runs, optionally update self and Runs
`public None `[`execute_in_environment`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afc2e5fa7f3503a8eff53393e1f3d8edd)`(self,str env,t.List phases,bool resume)` | Executes the experiment in a specific environment
`public None `[`execute`](#classexot_1_1experiment_1_1__base_1_1Experiment_1addc755a8a5b84d0cb2e089d1d8af7a23)`(self,*t.Optional]] env_phase_mapping,resume)` | Execute the Experiment on a target platform

## Members

#### `public  `[`channel`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a99b6b2c3070db0e8d450a48ce1c71a87) {#classexot_1_1experiment_1_1__base_1_1Experiment_1a99b6b2c3070db0e8d450a48ce1c71a87}

#### `public  `[`drivers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a225a56fe5c5e2a0fce2fadf1b013beb2) {#classexot_1_1experiment_1_1__base_1_1Experiment_1a225a56fe5c5e2a0fce2fadf1b013beb2}

#### `public  `[`run_type`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afd12ca899670493b4e915097067c2052) {#classexot_1_1experiment_1_1__base_1_1Experiment_1afd12ca899670493b4e915097067c2052}

#### `public None `[`__init_subclass__`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a16d7e3fa508d3032817c2efccbc801f0)`(cls,* args,** kwargs)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a16d7e3fa508d3032817c2efccbc801f0}

#### `public def `[`config`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a9996a4d67e7cd5b8d1d9a4c8b6b3da3d)`(self,value)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a9996a4d67e7cd5b8d1d9a4c8b6b3da3d}

#### `public def `[`config`](#classexot_1_1experiment_1_1__base_1_1Experiment_1ad010f1865e929e22456f4a0a0a1cbf9b)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1ad010f1865e929e22456f4a0a0a1cbf9b}

#### `public def `[`run_type`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afeb1ec5ef6add0b9b9cc9f538a1b1c4e)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1afeb1ec5ef6add0b9b9cc9f538a1b1c4e}

Get the associated Run type

#### `public def `[`run_type`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aac95266bc882a6989739b50131d43b3d)`(self,value)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1aac95266bc882a6989739b50131d43b3d}

Set the associated Run type

#### `public def `[`__init__`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a342fa624f317fc5863f9fee195b3c45f)`(self,* args,** kwargs)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a342fa624f317fc5863f9fee195b3c45f}

Initialise an Experiment object

#### `public None `[`bootstrap`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a33a673a50a00c4b41f9302c3262bb9f1)`(self,** kwargs)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a33a673a50a00c4b41f9302c3262bb9f1}

Parse configuration and create experiment layers using a layer factory

#### `public bool `[`bootstrapped`](#classexot_1_1experiment_1_1__base_1_1Experiment_1af10540afb73495e22ed45856f91279a9)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1af10540afb73495e22ed45856f91279a9}

Are the experiment layers bootstrapped?

#### `public AttributeDict `[`layers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1ab00b8e0278e3a26a0dcc6f431faad25e)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1ab00b8e0278e3a26a0dcc6f431faad25e}

Get experiment layers

#### `public AttributeDict `[`layers_with_runtime_encoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a75ed63fe1bc39abc4b2705be38358b83)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a75ed63fe1bc39abc4b2705be38358b83}

Get experiment layers that require configuration at runtime

#### `public AttributeDict `[`layers_with_runtime_decoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7d8e29e0876d7e6e1cc43a96ff593783)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a7d8e29e0876d7e6e1cc43a96ff593783}

Get experiment layers that require configuration at runtime

#### `public None `[`configure_layers_encoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a79e6f718d2e625e1aec981c69246c25d)`(self,**t.Any kwargs)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a79e6f718d2e625e1aec981c69246c25d}

Configure layers with runtime-configurable encoding

#### `public None `[`configure_layers_decoding`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa6ddd4a0a23753f33a6fa44b6695c367)`(self,**t.Any kwargs)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1aa6ddd4a0a23753f33a6fa44b6695c367}

Configure layers with runtime-configurable decoding

#### `public str `[`__repr__`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a4ba498d6bae66d050bb52bb46865c4ac)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a4ba498d6bae66d050bb52bb46865c4ac}

Get a string representation of the Experiment

#### `public list `[`required_config_keys`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a399922f6a6056200528daf6179f1bffd)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a399922f6a6056200528daf6179f1bffd}

Gets the required config keys

Returns:
    list: The required keys

#### `public float `[`estimated_delays_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a2ef877035f06143634300c612a00a0e9)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a2ef877035f06143634300c612a00a0e9}

Gets the estimated duration of the defined delays

Returns:
    float: The estimated delay in seconds

#### `public None `[`validate`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a4906a91b8ceee6c52bd1679b5b16d186)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a4906a91b8ceee6c52bd1679b5b16d186}

Check if the supplied Experiment config is valid

Implements the `validate` method from Configurable.

#### `public AttributeDict `[`environments`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a33cf3af19166807f3df7655022ac98cc)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a33cf3af19166807f3df7655022ac98cc}

Get available environments

#### `public def `[`environments`](#classexot_1_1experiment_1_1__base_1_1Experiment_1addef21e569c30af8879f0f1fb52ff795)`(self,t.Mapping value)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1addef21e569c30af8879f0f1fb52ff795}

Set available environments

#### `public t.Mapping `[`environments_apps_zones`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a665566412a6e83c2a43ebc225d4b35c2)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a665566412a6e83c2a43ebc225d4b35c2}

Get a mapping with environments, apps, zones and zone configs

Returns:
    t.Mapping: A mapping with the following structure:
       - Mapping depth 1: environment name
       - Mapping depth 2: apps in the environment
       - Mapping depth 3: app zone, zone_config, and app_config,
                          standalone, sched

#### `public list `[`available_environments`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a344515cd4404ee9ff0e3c164cce9072a)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a344515cd4404ee9ff0e3c164cce9072a}

Get names of available environments

#### `public AttributeDict `[`environment_config_general`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a18223bdd0b93fe70b2e5eac55f653bc2)`(self,str env)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a18223bdd0b93fe70b2e5eac55f653bc2}

Provides an environment-specific proxy to the general experiment config

Args:
    env (str): The environment

Returns:
    AttributeDict: The root or environment-specific config

#### `public t.Optional[str] `[`name`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a174e03c45355e9402d7afe5a129d22d7)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a174e03c45355e9402d7afe5a129d22d7}

Get experiment name

#### `public t.Optional[Path] `[`save_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa43150be01f91ea150913a19cca20a51)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1aa43150be01f91ea150913a19cca20a51}

Get save path for experiments

#### `public t.Optional[Path] `[`log_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1ac19747e4bb6eff6ed3c99deace8dce56)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1ac19747e4bb6eff6ed3c99deace8dce56}

Get experiment log path

#### `public t.Optional[Path] `[`path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a5871801f02d6c5785eb1c4fab2c4479c)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a5871801f02d6c5785eb1c4fab2c4479c}

Get the save path of the particular Experiment

#### `public t.Optional[Path] `[`root_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a4a43ab4e38274c96d945a96bffa6ac4f)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a4a43ab4e38274c96d945a96bffa6ac4f}

Get the exot root path

#### `public Path `[`remote_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7170f47a4b73bfa9b389183b4b769b12)`(self,str env,str zone)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a7170f47a4b73bfa9b389183b4b769b12}

Get a remote experiment path given an environment and a zone

#### `public Path `[`remote_save_path`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a909ee0bc8a555f33977875c09c318866)`(self,str env,str zone)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a909ee0bc8a555f33977875c09c318866}

Get a remote experiment path given an environment and a zone

#### `public Channel `[`channel`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a6df8dc3d6ebaf0adbafc1bd925e2ac2b)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a6df8dc3d6ebaf0adbafc1bd925e2ac2b}

Get the configured channel

#### `public None `[`channel`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a034ec8e2bb92023a29a3dba7d2d5500b)`(self,Channel value)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a034ec8e2bb92023a29a3dba7d2d5500b}

Set the experiment channel

#### `public t.Optional[AttributeDict] `[`drivers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a8cc9ca7b706e064049319d359f67a979)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a8cc9ca7b706e064049319d359f67a979}

Get the experiment drivers

Returns:
    t.Optional[AttributeDict]: A mapping: env: str -> zone: str -> driver: Driver

#### `public None `[`drivers`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a9410a7f87cda99291cf614eaeac51532)`(self,]] value)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a9410a7f87cda99291cf614eaeac51532}

Set the experiment drivers

Args:
    value (t.Mapping[str, t.Mapping[str, Driver]]):
A mapping: env: str -> zone: str -> driver: Driver

Raises:
    ExperimentTypeError: If keys have wrong types
    ExperimentValueError: If a environment or zone is not available
    WrongDriverError: If a leaf is not a Driver instance

#### `public t.Dict `[`phases`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a02a980b786cce904ebf887370bb91634)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a02a980b786cce904ebf887370bb91634}

Get experiment phases

#### `public None `[`phases`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa36706ccd02c83f6f8f766752aca8f24)`(self,t.Dict value)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1aa36706ccd02c83f6f8f766752aca8f24}

Set experiment phases

#### `public None `[`write`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a04e50fb10fd081badcfbca272b2faaab)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a04e50fb10fd081badcfbca272b2faaab}

Serialise the experiment

#### `public `[`Experiment`](#classexot_1_1experiment_1_1__base_1_1Experiment)` `[`read`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a488aadcd3cd4a96f188961a4d55e45ba)`(cls,Path path,t.Optional new_root_path,*bool diff_and_replace)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a488aadcd3cd4a96f188961a4d55e45ba}

Read a serialised Experiment and produce an Experiment instance

Args:
    path (Path): The path to the serialised experiment
    new_root_path (t.Optional[Path], optional): A new root path
    diff_and_replace (bool, optional): Do file diff and replace values from the instance with those from files?

Returns:
    Experiment: A restored instance of Experiment

Raises:
    WrongRootPathError: If saved and current root paths cannot be resolved

#### `public None `[`backup`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7f4c140664161a93e547d82ba87a6af7)`(self,bool _with_logs,bool _with_results)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a7f4c140664161a93e547d82ba87a6af7}

Archive an Experiment and, if possible, upload to a backup server

Args:
    _with_logs (bool, optional): Backup contained experiment logs?
    _with_results (bool, optional): Backup contained experiments results?

Raises:
    InvalidBackupPathError: If backup path is invalid

#### `public None `[`generate`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a54b838056cf807f5a5dd0995fe8dc2c9)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a54b838056cf807f5a5dd0995fe8dc2c9}

Populate the experiment phases and instantiate Run's

Preconditions:
    - The experiment should be configured and bootstrapped.

#### `public t.Dict `[`estimated_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1aa0f45ad4385e4a6bb06a66c71ec602a3)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1aa0f45ad4385e4a6bb06a66c71ec602a3}

Get durations of experiment phases

#### `public None `[`estimated_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a75a8ec4e9fa15635d8e2fa5c0ae6bbdb)`(self,t.Dict value)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a75a8ec4e9fa15635d8e2fa5c0ae6bbdb}

Set experiment phases

#### `public None `[`print_duration`](#classexot_1_1experiment_1_1__base_1_1Experiment_1acd6064661320a7c745e2836774c817ef)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1acd6064661320a7c745e2836774c817ef}

Prints the estimated experiment duration

#### `public t.Generator `[`map_to_runs`](#classexot_1_1experiment_1_1__base_1_1Experiment_1a7029efae953f50ec6a8519882c4d4f2a)`(self,t. Callable,t.Any] function,*bool parallel)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1a7029efae953f50ec6a8519882c4d4f2a}

Map a function to the Runs concurrently

Args:
    function (t.Callable[[t.Any], t.Any]): A callable with sig. (Any) -> Any
    parallel (bool, optional): run callable concurrently?

Returns:
    t.Generator: The executor map generator

#### `public dict `[`execution_status`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afa9d0c60fb675ebec900342024c4e0f5)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1afa9d0c60fb675ebec900342024c4e0f5}

Gets the experiment execution status

The execution status has the following form:

    {
<phase_key>: {
    <run_key>: [
        (<env name 1>, [True, True, ..., False]),
        (<env name 2>, [True, True, ..., False]),
        ...
    ],
    ...
},
...
    }

Returns:
    dict: A dict with a structure like `phases`, with lists as leaves, containing
tuples (env, [executed runs]).

#### `public dict `[`infer_execution_status`](#classexot_1_1experiment_1_1__base_1_1Experiment_1af5503e615e389478440984332185d74d)`(self)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1af5503e615e389478440984332185d74d}

Infers the execution status from contained Runs, optionally update self and Runs

Args:

Returns:

Raises:
    TypeError: Wrong types provided to keyword arguments

#### `public None `[`execute_in_environment`](#classexot_1_1experiment_1_1__base_1_1Experiment_1afc2e5fa7f3503a8eff53393e1f3d8edd)`(self,str env,t.List phases,bool resume)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1afc2e5fa7f3503a8eff53393e1f3d8edd}

Executes the experiment in a specific environment

Args:
    env (str): The environment
    phases (t.List[str]): The phases to execute
    resume (bool, optional): Resume execution?

Returns:
    None: If no phases are executed

Raises:
    ExperimentAbortedError: Interrupted by the user or options are mismatched
    ExperimentRuntimeError: Failed to send or timed out
    TypeError: Wrong type supplied to 'phases'
    ValueError: Any of the provided phases were not available

#### `public None `[`execute`](#classexot_1_1experiment_1_1__base_1_1Experiment_1addc755a8a5b84d0cb2e089d1d8af7a23)`(self,*t.Optional]] env_phase_mapping,resume)` {#classexot_1_1experiment_1_1__base_1_1Experiment_1addc755a8a5b84d0cb2e089d1d8af7a23}

Execute the Experiment on a target platform

Preconditions:
    - The experiment should be configured and bootstrapped.
    - Drivers should be available and should be able to connect.
    - Each run should be digested.

# class `exot::experiment::_base::Run` {#classexot_1_1experiment_1_1__base_1_1Run}

```
class exot::experiment::_base::Run
  : public Pickleable
  : public Configurable
  : public HasParent
  : public IntermediatesHandler
  : public parent
  : public exot.experiment._base.Experiment
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`logger`](#classexot_1_1experiment_1_1__base_1_1Run_1a0e00fbc6df8b49078ec8e6fe5f963c31) | 
`public  `[`intermediates`](#classexot_1_1experiment_1_1__base_1_1Run_1a146f227bb85a063a1ce444c3a0b0e7ef) | 
`public  `[`ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1ad57f4a2375d65e2e6ea100367a1f623b) | 
`public None `[`__init__`](#classexot_1_1experiment_1_1__base_1_1Run_1a31d19748d09978d14295089d127137a9)`(self,*t.Any args,**t.Any kwargs)` | Initialise a Run
`public dict `[`execution_status`](#classexot_1_1experiment_1_1__base_1_1Run_1a82d9786f7ea33ed00d03362d11e0b5ed)`(self)` | Gets the execution status of the Run
`public dict `[`infer_execution_status`](#classexot_1_1experiment_1_1__base_1_1Run_1a6ef5351c9a506d93a595bd5bb27c7315)`(self,*bool update)` | Infers the execution status from the contained files
`public dict `[`runtime_config`](#classexot_1_1experiment_1_1__base_1_1Run_1abb10061885ef124d90ba73cfc19168ce)`(self)` | Get the last used runtime_config.
`public None `[`runtime_config`](#classexot_1_1experiment_1_1__base_1_1Run_1acdd8e47abfa69fea4d575bd2f5c3e92c)`(self,value)` | Set the rt config
`public str `[`__repr__`](#classexot_1_1experiment_1_1__base_1_1Run_1ab8b664b687ea8dae081c0fb3c6b6dca6)`(self)` | Get a string representation of the Experiment
`public object `[`read`](#classexot_1_1experiment_1_1__base_1_1Run_1a89b676ef4c47e666a741ec440b6cf474)`(cls,Path path,t.Optional parent)` | Read a serialised Run and produce a Run instance
`public None `[`write`](#classexot_1_1experiment_1_1__base_1_1Run_1a352d0dfae22156e6364d84fabbee9c9a)`(self)` | Serialise a Run instance
`public str `[`identifier`](#classexot_1_1experiment_1_1__base_1_1Run_1af222666708748c8ca65b5fc86789b178)`(self)` | Get the save path
`public Path `[`path`](#classexot_1_1experiment_1_1__base_1_1Run_1a4d7ee2eeeab78887558269e196c814b7)`(self)` | Get the save path of the particular Experiment
`public Path `[`env_path`](#classexot_1_1experiment_1_1__base_1_1Run_1ad29e53e073c7202261683716a168847f)`(self,str env,*bool relative)` | Get a specific environment's path
`public Path `[`rep_path`](#classexot_1_1experiment_1_1__base_1_1Run_1abd9ee05d73f75c6d2ac71a5e2bcedde5)`(self,str env,int rep,*bool relative)` | 
`public Path `[`remote_path`](#classexot_1_1experiment_1_1__base_1_1Run_1a7d932955b3fe121bfeccf6b0ef7cee13)`(self,str env,str zone)` | Get a remote path given an environment and a zone
`public Path `[`remote_env_path`](#classexot_1_1experiment_1_1__base_1_1Run_1a2a3d2815c05111367fb1ce65eb908358)`(self,str env,str zone)` | Get a remote environment path given an environment and an zone
`public Path `[`remote_rep_path`](#classexot_1_1experiment_1_1__base_1_1Run_1af5959c54d0298feaac6746e858959b47)`(self,str env,str zone,int rep)` | 
`public t.Mapping[str, Driver] `[`drivers_proxy`](#classexot_1_1experiment_1_1__base_1_1Run_1a9489c231ef642d73dd5f96262f342157)`(self)` | Get a proxy to the Experiment's drivers for a specific environment
`public None `[`drivers_proxy`](#classexot_1_1experiment_1_1__base_1_1Run_1a33a94a5877dc2ede48ff2c76bbc9519a)`(self,t.Mapping value)` | Set a proxy to the Experiment's drivers for a specific environment
`public bool `[`ingested`](#classexot_1_1experiment_1_1__base_1_1Run_1a8fef303f2d90a5cd0e45e49d2daaec18)`(self)` | Has the run performed all decoding steps?
`public None `[`clear_ingest`](#classexot_1_1experiment_1_1__base_1_1Run_1a81fedc2e9c86407d58f9e79fa722b91f)`(self)` | Has the run performed all decoding steps?
`public Path `[`path_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1ac42d403bf8c24ef1d82da1f1d2256044)`(self)` | 
`public None `[`load_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1ab23d55b03ee6ec9cae70a28340f37f98)`(self,t.Optional prefix,bool bundled,** kwargs)` | 
`public None `[`save_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1af828cb6dd672bbff385c1ce2aa1c708b)`(self,t.Optional prefix,bool bundled)` | 
`public None `[`remove_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1a318cb7815c232d1f3c0df462b4c4bd4e)`(self,t.Optional prefix)` | 
`public None `[`update_ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1af095cd1f0af769ca53c649fdc4bc82c3)`(self)` | 
`public bool `[`ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1a7f3617dd2806ce44257120c677ec31fd)`(self)` | 
`public None `[`ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1a8f66271f2c794a0ae141d746a8513467)`(self,tuple value)` | 
`public bool `[`digested`](#classexot_1_1experiment_1_1__base_1_1Run_1a9822501ae10e58978c604d0449a435a2)`(self)` | Has the run performed all encoding steps?
`public None `[`digest`](#classexot_1_1experiment_1_1__base_1_1Run_1a0917f847b1284bda424d751b79df3638)`(self,** kwargs)` | Perform all encoding steps
`public None `[`ingest`](#classexot_1_1experiment_1_1__base_1_1Run_1a33eb07e94ef6c9e0a8f662e1ec413015)`(self,** kwargs)` | Perform all decoding steps
`public bitarray `[`make_random_bitarray`](#classexot_1_1experiment_1_1__base_1_1Run_1aac5161438c15f5463c99e3fdf28d1adc)`(self,t.Optional length)` | Generate a random bit array of specified or configured length
`public np.ndarray `[`make_random_boolarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a6b9a8e2e9529dba4ec033dfac4c70fd1)`(self,t.Optional length)` | Generate a random bool NumPy array of specified or configured length
`public np.ndarray `[`make_random_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a7f511e51f18c42149ef171d630201e9c)`(self,t.Optional length)` | Generate a random bool NumPy array of specified or configured length
`public np.ndarray `[`make_alternating_boolarray`](#classexot_1_1experiment_1_1__base_1_1Run_1ac9b8092cd37f362d52b1cbaadd0810b1)`(self,t.Optional length)` | Generate an alternating NumPy bool array of specified or configured length
`public np.ndarray `[`make_alternating_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a62f69dfd904680754f8f06cc17c77bee)`(self,t.Optional length)` | Generate an alternating binary NumPy int array of specified or configured length
`public bitarray `[`make_alternating_bitarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a6ba4ca3259861e23a7874c8987ea6584)`(self,t.Optional length)` | Generate an alternating bit array of specified or configured length
`public np.ndarray `[`make_constant_boolarray`](#classexot_1_1experiment_1_1__base_1_1Run_1aee970ec0b10bef28771579c9a112993c)`(self,bool value,t.Optional length)` | Generate an constant NumPy bool array of specified or configured length
`public np.ndarray `[`make_constant_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a878c4668fcac531636c43c2a6e94b171)`(self,int value,t.Optional length)` | Generate an constant binary NumPy int array of specified or configured length
`public bitarray `[`make_constant_bitarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a004b7d28315e1697cd0f4c6269070a8e)`(self,bool value,t.Optional length)` | Generate an constant bit array of specified or configured length
`public np.ndarray `[`make_repeated_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1aacffb6333a049971eea63db8546c1cef)`(self,np.ndarray base,t.Optional length)` | Generate a NumPy int array of specified or configured length with a repeated pattern
`public None `[`execute`](#classexot_1_1experiment_1_1__base_1_1Run_1a5d2bad84639f9ce7cc1e254e5cbcd3ae)`(self,str env,resume)` | Execute a single Run in an environment
`public def `[`send`](#classexot_1_1experiment_1_1__base_1_1Run_1a6908001c9abc8e56ffd58f421b2b1d04)`(self,env)` | 
`public def `[`fetch_and_cleanup`](#classexot_1_1experiment_1_1__base_1_1Run_1a74c21cc1a9140d0b5dd9b385c9a9d46d)`(self,env)` | 
`public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1__base_1_1Run_1a4f13076363a1b3fb0ca3ca7a35ee6cf7)`(self,env)` | Get the estimated duration of this Run's execution

## Members

#### `public  `[`logger`](#classexot_1_1experiment_1_1__base_1_1Run_1a0e00fbc6df8b49078ec8e6fe5f963c31) {#classexot_1_1experiment_1_1__base_1_1Run_1a0e00fbc6df8b49078ec8e6fe5f963c31}

#### `public  `[`intermediates`](#classexot_1_1experiment_1_1__base_1_1Run_1a146f227bb85a063a1ce444c3a0b0e7ef) {#classexot_1_1experiment_1_1__base_1_1Run_1a146f227bb85a063a1ce444c3a0b0e7ef}

#### `public  `[`ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1ad57f4a2375d65e2e6ea100367a1f623b) {#classexot_1_1experiment_1_1__base_1_1Run_1ad57f4a2375d65e2e6ea100367a1f623b}

#### `public None `[`__init__`](#classexot_1_1experiment_1_1__base_1_1Run_1a31d19748d09978d14295089d127137a9)`(self,*t.Any args,**t.Any kwargs)` {#classexot_1_1experiment_1_1__base_1_1Run_1a31d19748d09978d14295089d127137a9}

Initialise a Run

Args:
    *args (t.Any): Passed to parent initialisers
    **kwargs (t.Any): Passed to parent initialisers

Raises:
    ExperimentRuntimeError: If not configured or doesn't have a parent

#### `public dict `[`execution_status`](#classexot_1_1experiment_1_1__base_1_1Run_1a82d9786f7ea33ed00d03362d11e0b5ed)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a82d9786f7ea33ed00d03362d11e0b5ed}

Gets the execution status of the Run

The Run's execution status has the form:

    {
<env name>: {
    <rep idx>: True | False,
    ...
},
...
    }

Returns:
    dict: The execution status

#### `public dict `[`infer_execution_status`](#classexot_1_1experiment_1_1__base_1_1Run_1a6ef5351c9a506d93a595bd5bb27c7315)`(self,*bool update)` {#classexot_1_1experiment_1_1__base_1_1Run_1a6ef5351c9a506d93a595bd5bb27c7315}

Infers the execution status from the contained files

Returns:
    dict: The inferred execution status

Args:
    update (bool, optional): Update the Run's own execution status?

Raises:
    TypeError: Wrong type provided to 'update'

#### `public dict `[`runtime_config`](#classexot_1_1experiment_1_1__base_1_1Run_1abb10061885ef124d90ba73cfc19168ce)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1abb10061885ef124d90ba73cfc19168ce}

Get the last used runtime_config.

#### `public None `[`runtime_config`](#classexot_1_1experiment_1_1__base_1_1Run_1acdd8e47abfa69fea4d575bd2f5c3e92c)`(self,value)` {#classexot_1_1experiment_1_1__base_1_1Run_1acdd8e47abfa69fea4d575bd2f5c3e92c}

Set the rt config

#### `public str `[`__repr__`](#classexot_1_1experiment_1_1__base_1_1Run_1ab8b664b687ea8dae081c0fb3c6b6dca6)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1ab8b664b687ea8dae081c0fb3c6b6dca6}

Get a string representation of the Experiment

#### `public object `[`read`](#classexot_1_1experiment_1_1__base_1_1Run_1a89b676ef4c47e666a741ec440b6cf474)`(cls,Path path,t.Optional parent)` {#classexot_1_1experiment_1_1__base_1_1Run_1a89b676ef4c47e666a741ec440b6cf474}

Read a serialised Run and produce a Run instance

Args:
    path (Path): The path of the serialised instance
    parent (t.Optional[object], optional): The parent experiment to set

Returns:
    object: The deserialised instance

#### `public None `[`write`](#classexot_1_1experiment_1_1__base_1_1Run_1a352d0dfae22156e6364d84fabbee9c9a)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a352d0dfae22156e6364d84fabbee9c9a}

Serialise a Run instance

#### `public str `[`identifier`](#classexot_1_1experiment_1_1__base_1_1Run_1af222666708748c8ca65b5fc86789b178)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1af222666708748c8ca65b5fc86789b178}

Get the save path

#### `public Path `[`path`](#classexot_1_1experiment_1_1__base_1_1Run_1a4d7ee2eeeab78887558269e196c814b7)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a4d7ee2eeeab78887558269e196c814b7}

Get the save path of the particular Experiment

#### `public Path `[`env_path`](#classexot_1_1experiment_1_1__base_1_1Run_1ad29e53e073c7202261683716a168847f)`(self,str env,*bool relative)` {#classexot_1_1experiment_1_1__base_1_1Run_1ad29e53e073c7202261683716a168847f}

Get a specific environment's path

#### `public Path `[`rep_path`](#classexot_1_1experiment_1_1__base_1_1Run_1abd9ee05d73f75c6d2ac71a5e2bcedde5)`(self,str env,int rep,*bool relative)` {#classexot_1_1experiment_1_1__base_1_1Run_1abd9ee05d73f75c6d2ac71a5e2bcedde5}

#### `public Path `[`remote_path`](#classexot_1_1experiment_1_1__base_1_1Run_1a7d932955b3fe121bfeccf6b0ef7cee13)`(self,str env,str zone)` {#classexot_1_1experiment_1_1__base_1_1Run_1a7d932955b3fe121bfeccf6b0ef7cee13}

Get a remote path given an environment and a zone

#### `public Path `[`remote_env_path`](#classexot_1_1experiment_1_1__base_1_1Run_1a2a3d2815c05111367fb1ce65eb908358)`(self,str env,str zone)` {#classexot_1_1experiment_1_1__base_1_1Run_1a2a3d2815c05111367fb1ce65eb908358}

Get a remote environment path given an environment and an zone

#### `public Path `[`remote_rep_path`](#classexot_1_1experiment_1_1__base_1_1Run_1af5959c54d0298feaac6746e858959b47)`(self,str env,str zone,int rep)` {#classexot_1_1experiment_1_1__base_1_1Run_1af5959c54d0298feaac6746e858959b47}

#### `public t.Mapping[str, Driver] `[`drivers_proxy`](#classexot_1_1experiment_1_1__base_1_1Run_1a9489c231ef642d73dd5f96262f342157)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a9489c231ef642d73dd5f96262f342157}

Get a proxy to the Experiment's drivers for a specific environment

Returns:
    t.Mapping[str, Driver]: A mapping: zone: str -> driver: Driver

#### `public None `[`drivers_proxy`](#classexot_1_1experiment_1_1__base_1_1Run_1a33a94a5877dc2ede48ff2c76bbc9519a)`(self,t.Mapping value)` {#classexot_1_1experiment_1_1__base_1_1Run_1a33a94a5877dc2ede48ff2c76bbc9519a}

Set a proxy to the Experiment's drivers for a specific environment

Args:
    value (t.Mapping[str, Driver]): A mapping: zone: str -> driver: Driver

#### `public bool `[`ingested`](#classexot_1_1experiment_1_1__base_1_1Run_1a8fef303f2d90a5cd0e45e49d2daaec18)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a8fef303f2d90a5cd0e45e49d2daaec18}

Has the run performed all decoding steps?

#### `public None `[`clear_ingest`](#classexot_1_1experiment_1_1__base_1_1Run_1a81fedc2e9c86407d58f9e79fa722b91f)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a81fedc2e9c86407d58f9e79fa722b91f}

Has the run performed all decoding steps?

#### `public Path `[`path_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1ac42d403bf8c24ef1d82da1f1d2256044)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1ac42d403bf8c24ef1d82da1f1d2256044}

#### `public None `[`load_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1ab23d55b03ee6ec9cae70a28340f37f98)`(self,t.Optional prefix,bool bundled,** kwargs)` {#classexot_1_1experiment_1_1__base_1_1Run_1ab23d55b03ee6ec9cae70a28340f37f98}

#### `public None `[`save_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1af828cb6dd672bbff385c1ce2aa1c708b)`(self,t.Optional prefix,bool bundled)` {#classexot_1_1experiment_1_1__base_1_1Run_1af828cb6dd672bbff385c1ce2aa1c708b}

#### `public None `[`remove_ingestion_data`](#classexot_1_1experiment_1_1__base_1_1Run_1a318cb7815c232d1f3c0df462b4c4bd4e)`(self,t.Optional prefix)` {#classexot_1_1experiment_1_1__base_1_1Run_1a318cb7815c232d1f3c0df462b4c4bd4e}

#### `public None `[`update_ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1af095cd1f0af769ca53c649fdc4bc82c3)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1af095cd1f0af769ca53c649fdc4bc82c3}

#### `public bool `[`ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1a7f3617dd2806ce44257120c677ec31fd)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a7f3617dd2806ce44257120c677ec31fd}

#### `public None `[`ingestion_tag`](#classexot_1_1experiment_1_1__base_1_1Run_1a8f66271f2c794a0ae141d746a8513467)`(self,tuple value)` {#classexot_1_1experiment_1_1__base_1_1Run_1a8f66271f2c794a0ae141d746a8513467}

#### `public bool `[`digested`](#classexot_1_1experiment_1_1__base_1_1Run_1a9822501ae10e58978c604d0449a435a2)`(self)` {#classexot_1_1experiment_1_1__base_1_1Run_1a9822501ae10e58978c604d0449a435a2}

Has the run performed all encoding steps?

#### `public None `[`digest`](#classexot_1_1experiment_1_1__base_1_1Run_1a0917f847b1284bda424d751b79df3638)`(self,** kwargs)` {#classexot_1_1experiment_1_1__base_1_1Run_1a0917f847b1284bda424d751b79df3638}

Perform all encoding steps

#### `public None `[`ingest`](#classexot_1_1experiment_1_1__base_1_1Run_1a33eb07e94ef6c9e0a8f662e1ec413015)`(self,** kwargs)` {#classexot_1_1experiment_1_1__base_1_1Run_1a33eb07e94ef6c9e0a8f662e1ec413015}

Perform all decoding steps

#### `public bitarray `[`make_random_bitarray`](#classexot_1_1experiment_1_1__base_1_1Run_1aac5161438c15f5463c99e3fdf28d1adc)`(self,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1aac5161438c15f5463c99e3fdf28d1adc}

Generate a random bit array of specified or configured length

#### `public np.ndarray `[`make_random_boolarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a6b9a8e2e9529dba4ec033dfac4c70fd1)`(self,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1a6b9a8e2e9529dba4ec033dfac4c70fd1}

Generate a random bool NumPy array of specified or configured length

#### `public np.ndarray `[`make_random_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a7f511e51f18c42149ef171d630201e9c)`(self,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1a7f511e51f18c42149ef171d630201e9c}

Generate a random bool NumPy array of specified or configured length

#### `public np.ndarray `[`make_alternating_boolarray`](#classexot_1_1experiment_1_1__base_1_1Run_1ac9b8092cd37f362d52b1cbaadd0810b1)`(self,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1ac9b8092cd37f362d52b1cbaadd0810b1}

Generate an alternating NumPy bool array of specified or configured length

#### `public np.ndarray `[`make_alternating_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a62f69dfd904680754f8f06cc17c77bee)`(self,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1a62f69dfd904680754f8f06cc17c77bee}

Generate an alternating binary NumPy int array of specified or configured length

#### `public bitarray `[`make_alternating_bitarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a6ba4ca3259861e23a7874c8987ea6584)`(self,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1a6ba4ca3259861e23a7874c8987ea6584}

Generate an alternating bit array of specified or configured length

#### `public np.ndarray `[`make_constant_boolarray`](#classexot_1_1experiment_1_1__base_1_1Run_1aee970ec0b10bef28771579c9a112993c)`(self,bool value,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1aee970ec0b10bef28771579c9a112993c}

Generate an constant NumPy bool array of specified or configured length

#### `public np.ndarray `[`make_constant_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a878c4668fcac531636c43c2a6e94b171)`(self,int value,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1a878c4668fcac531636c43c2a6e94b171}

Generate an constant binary NumPy int array of specified or configured length

#### `public bitarray `[`make_constant_bitarray`](#classexot_1_1experiment_1_1__base_1_1Run_1a004b7d28315e1697cd0f4c6269070a8e)`(self,bool value,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1a004b7d28315e1697cd0f4c6269070a8e}

Generate an constant bit array of specified or configured length

#### `public np.ndarray `[`make_repeated_intarray`](#classexot_1_1experiment_1_1__base_1_1Run_1aacffb6333a049971eea63db8546c1cef)`(self,np.ndarray base,t.Optional length)` {#classexot_1_1experiment_1_1__base_1_1Run_1aacffb6333a049971eea63db8546c1cef}

Generate a NumPy int array of specified or configured length with a repeated pattern

Args:
    base (np.ndarray): The base for the repeated pattern
    length (t.Optional[int], optional): The length

Returns:
    np.ndarray: The generated array

#### `public None `[`execute`](#classexot_1_1experiment_1_1__base_1_1Run_1a5d2bad84639f9ce7cc1e254e5cbcd3ae)`(self,str env,resume)` {#classexot_1_1experiment_1_1__base_1_1Run_1a5d2bad84639f9ce7cc1e254e5cbcd3ae}

Execute a single Run in an environment

Args:
    env (str): An environment name

#### `public def `[`send`](#classexot_1_1experiment_1_1__base_1_1Run_1a6908001c9abc8e56ffd58f421b2b1d04)`(self,env)` {#classexot_1_1experiment_1_1__base_1_1Run_1a6908001c9abc8e56ffd58f421b2b1d04}

#### `public def `[`fetch_and_cleanup`](#classexot_1_1experiment_1_1__base_1_1Run_1a74c21cc1a9140d0b5dd9b385c9a9d46d)`(self,env)` {#classexot_1_1experiment_1_1__base_1_1Run_1a74c21cc1a9140d0b5dd9b385c9a9d46d}

#### `public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1__base_1_1Run_1a4f13076363a1b3fb0ca3ca7a35ee6cf7)`(self,env)` {#classexot_1_1experiment_1_1__base_1_1Run_1a4f13076363a1b3fb0ca3ca7a35ee6cf7}

Get the estimated duration of this Run's execution

Returns:
    t.Optional[float]: the duration in seconds, or None if not digested

# namespace `exot::experiment::_factory` {#namespaceexot_1_1experiment_1_1__factory}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::experiment::_factory::ExperimentFactory`](#classexot_1_1experiment_1_1__factory_1_1ExperimentFactory) | 

# class `exot::experiment::_factory::ExperimentFactory` {#classexot_1_1experiment_1_1__factory_1_1ExperimentFactory}

```
class exot::experiment::_factory::ExperimentFactory
  : public GenericFactory
  : public klass
  : public exot.experiment._base.Experiment
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`make`](#classexot_1_1experiment_1_1__factory_1_1ExperimentFactory_1aa611c611af24815d89a51d354331ef78)`(self,str experiment,* args,** kwargs)` | 

## Members

#### `public def `[`make`](#classexot_1_1experiment_1_1__factory_1_1ExperimentFactory_1aa611c611af24815d89a51d354331ef78)`(self,str experiment,* args,** kwargs)` {#classexot_1_1experiment_1_1__factory_1_1ExperimentFactory_1aa611c611af24815d89a51d354331ef78}

# namespace `exot::experiment::_mixins` {#namespaceexot_1_1experiment_1_1__mixins}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::experiment::_mixins::Ibitstream`](#classexot_1_1experiment_1_1__mixins_1_1Ibitstream) | 
`class `[`exot::experiment::_mixins::Ilnestream`](#classexot_1_1experiment_1_1__mixins_1_1Ilnestream) | 
`class `[`exot::experiment::_mixins::Irawstream`](#classexot_1_1experiment_1_1__mixins_1_1Irawstream) | 
`class `[`exot::experiment::_mixins::Irdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Irdpstream) | 
`class `[`exot::experiment::_mixins::Isymstream`](#classexot_1_1experiment_1_1__mixins_1_1Isymstream) | 
`class `[`exot::experiment::_mixins::Obitstream`](#classexot_1_1experiment_1_1__mixins_1_1Obitstream) | 
`class `[`exot::experiment::_mixins::Olnestream`](#classexot_1_1experiment_1_1__mixins_1_1Olnestream) | 
`class `[`exot::experiment::_mixins::Orawstream`](#classexot_1_1experiment_1_1__mixins_1_1Orawstream) | 
`class `[`exot::experiment::_mixins::Ordpstream`](#classexot_1_1experiment_1_1__mixins_1_1Ordpstream) | 
`class `[`exot::experiment::_mixins::Oschedules`](#classexot_1_1experiment_1_1__mixins_1_1Oschedules) | 
`class `[`exot::experiment::_mixins::Osymstream`](#classexot_1_1experiment_1_1__mixins_1_1Osymstream) | 
`class `[`exot::experiment::_mixins::StreamHandler`](#classexot_1_1experiment_1_1__mixins_1_1StreamHandler) | 
`class `[`exot::experiment::_mixins::StreamType`](#classexot_1_1experiment_1_1__mixins_1_1StreamType) | Stream types

# class `exot::experiment::_mixins::Ibitstream` {#classexot_1_1experiment_1_1__mixins_1_1Ibitstream}

```
class exot::experiment::_mixins::Ibitstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`i_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Ibitstream_1a3af4e57b498bbca809b1e5d6a57f4f79)`(self,value)` | 
`public def `[`i_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Ibitstream_1a43ae08eea7edbb4159cdb46d3dfb43e8)`(self)` | 

## Members

#### `public def `[`i_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Ibitstream_1a3af4e57b498bbca809b1e5d6a57f4f79)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Ibitstream_1a3af4e57b498bbca809b1e5d6a57f4f79}

#### `public def `[`i_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Ibitstream_1a43ae08eea7edbb4159cdb46d3dfb43e8)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Ibitstream_1a43ae08eea7edbb4159cdb46d3dfb43e8}

# class `exot::experiment::_mixins::Ilnestream` {#classexot_1_1experiment_1_1__mixins_1_1Ilnestream}

```
class exot::experiment::_mixins::Ilnestream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`i_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Ilnestream_1a410a5b48dd4b8d512ccf07d37e700266)`(self,value)` | 
`public def `[`i_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Ilnestream_1a1d79f692f46e0cfca851a625a9e43e78)`(self)` | 

## Members

#### `public def `[`i_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Ilnestream_1a410a5b48dd4b8d512ccf07d37e700266)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Ilnestream_1a410a5b48dd4b8d512ccf07d37e700266}

#### `public def `[`i_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Ilnestream_1a1d79f692f46e0cfca851a625a9e43e78)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Ilnestream_1a1d79f692f46e0cfca851a625a9e43e78}

# class `exot::experiment::_mixins::Irawstream` {#classexot_1_1experiment_1_1__mixins_1_1Irawstream}

```
class exot::experiment::_mixins::Irawstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`i_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Irawstream_1a11c5bfe3e8b4c9ed00a7cae6a3bad83b)`(self,value)` | 
`public def `[`i_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Irawstream_1ae219fd463d791d342a7be9a77ae77f7a)`(self)` | 

## Members

#### `public def `[`i_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Irawstream_1a11c5bfe3e8b4c9ed00a7cae6a3bad83b)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Irawstream_1a11c5bfe3e8b4c9ed00a7cae6a3bad83b}

#### `public def `[`i_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Irawstream_1ae219fd463d791d342a7be9a77ae77f7a)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Irawstream_1ae219fd463d791d342a7be9a77ae77f7a}

# class `exot::experiment::_mixins::Irdpstream` {#classexot_1_1experiment_1_1__mixins_1_1Irdpstream}

```
class exot::experiment::_mixins::Irdpstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`i_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Irdpstream_1aa686a8cd5e5f06b3e8ca671dcf5eb5a0)`(self,value)` | 
`public def `[`i_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Irdpstream_1a42c5b074dbcec87f52bdef4becf9321a)`(self)` | 

## Members

#### `public def `[`i_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Irdpstream_1aa686a8cd5e5f06b3e8ca671dcf5eb5a0)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Irdpstream_1aa686a8cd5e5f06b3e8ca671dcf5eb5a0}

#### `public def `[`i_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Irdpstream_1a42c5b074dbcec87f52bdef4becf9321a)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Irdpstream_1a42c5b074dbcec87f52bdef4becf9321a}

# class `exot::experiment::_mixins::Isymstream` {#classexot_1_1experiment_1_1__mixins_1_1Isymstream}

```
class exot::experiment::_mixins::Isymstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`i_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Isymstream_1a478a29f6fbb92873201097ea2dbb3bf4)`(self,value)` | 
`public def `[`i_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Isymstream_1a76f828f178a917f0eb951b091c0a15a4)`(self)` | 

## Members

#### `public def `[`i_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Isymstream_1a478a29f6fbb92873201097ea2dbb3bf4)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Isymstream_1a478a29f6fbb92873201097ea2dbb3bf4}

#### `public def `[`i_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Isymstream_1a76f828f178a917f0eb951b091c0a15a4)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Isymstream_1a76f828f178a917f0eb951b091c0a15a4}

# class `exot::experiment::_mixins::Obitstream` {#classexot_1_1experiment_1_1__mixins_1_1Obitstream}

```
class exot::experiment::_mixins::Obitstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`o_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Obitstream_1a3ce692e4b021663e1a95d69d6cf2556a)`(self,value)` | 
`public def `[`o_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Obitstream_1ae6bcf379faae131aa8cd2e0fd5867920)`(self)` | 

## Members

#### `public def `[`o_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Obitstream_1a3ce692e4b021663e1a95d69d6cf2556a)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Obitstream_1a3ce692e4b021663e1a95d69d6cf2556a}

#### `public def `[`o_bitstream`](#classexot_1_1experiment_1_1__mixins_1_1Obitstream_1ae6bcf379faae131aa8cd2e0fd5867920)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Obitstream_1ae6bcf379faae131aa8cd2e0fd5867920}

# class `exot::experiment::_mixins::Olnestream` {#classexot_1_1experiment_1_1__mixins_1_1Olnestream}

```
class exot::experiment::_mixins::Olnestream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`o_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Olnestream_1ad01e2e9e9ce6593f694af65993438233)`(self,value)` | 
`public def `[`o_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Olnestream_1a687cc746ed71dfcecda4ea760bb9f8b5)`(self)` | 

## Members

#### `public def `[`o_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Olnestream_1ad01e2e9e9ce6593f694af65993438233)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Olnestream_1ad01e2e9e9ce6593f694af65993438233}

#### `public def `[`o_lnestream`](#classexot_1_1experiment_1_1__mixins_1_1Olnestream_1a687cc746ed71dfcecda4ea760bb9f8b5)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Olnestream_1a687cc746ed71dfcecda4ea760bb9f8b5}

# class `exot::experiment::_mixins::Orawstream` {#classexot_1_1experiment_1_1__mixins_1_1Orawstream}

```
class exot::experiment::_mixins::Orawstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`o_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Orawstream_1aaf7a00d42ae66fd19e162a527ec05a47)`(self,value)` | 
`public def `[`o_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Orawstream_1a425b06f9c9c9afe74007d332c8a4a3e5)`(self)` | 

## Members

#### `public def `[`o_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Orawstream_1aaf7a00d42ae66fd19e162a527ec05a47)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Orawstream_1aaf7a00d42ae66fd19e162a527ec05a47}

#### `public def `[`o_rawstream`](#classexot_1_1experiment_1_1__mixins_1_1Orawstream_1a425b06f9c9c9afe74007d332c8a4a3e5)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Orawstream_1a425b06f9c9c9afe74007d332c8a4a3e5}

# class `exot::experiment::_mixins::Ordpstream` {#classexot_1_1experiment_1_1__mixins_1_1Ordpstream}

```
class exot::experiment::_mixins::Ordpstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`o_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Ordpstream_1a3cd230cbaa39a8a03a6b6ed5f66a753c)`(self,value)` | 
`public def `[`o_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Ordpstream_1a43961af37b3d9d59436ff5a49cccb0d7)`(self)` | 

## Members

#### `public def `[`o_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Ordpstream_1a3cd230cbaa39a8a03a6b6ed5f66a753c)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Ordpstream_1a3cd230cbaa39a8a03a6b6ed5f66a753c}

#### `public def `[`o_rdpstream`](#classexot_1_1experiment_1_1__mixins_1_1Ordpstream_1a43961af37b3d9d59436ff5a49cccb0d7)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Ordpstream_1a43961af37b3d9d59436ff5a49cccb0d7}

# class `exot::experiment::_mixins::Oschedules` {#classexot_1_1experiment_1_1__mixins_1_1Oschedules}

```
class exot::experiment::_mixins::Oschedules
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`o_schedules`](#classexot_1_1experiment_1_1__mixins_1_1Oschedules_1acf6bfa5d6f596d7846d0046543547c43)`(self,value)` | 
`public def `[`o_schedules`](#classexot_1_1experiment_1_1__mixins_1_1Oschedules_1a5c4cb71f052ceece27bf8edfc90c11b0)`(self)` | 

## Members

#### `public def `[`o_schedules`](#classexot_1_1experiment_1_1__mixins_1_1Oschedules_1acf6bfa5d6f596d7846d0046543547c43)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Oschedules_1acf6bfa5d6f596d7846d0046543547c43}

#### `public def `[`o_schedules`](#classexot_1_1experiment_1_1__mixins_1_1Oschedules_1a5c4cb71f052ceece27bf8edfc90c11b0)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Oschedules_1a5c4cb71f052ceece27bf8edfc90c11b0}

# class `exot::experiment::_mixins::Osymstream` {#classexot_1_1experiment_1_1__mixins_1_1Osymstream}

```
class exot::experiment::_mixins::Osymstream
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`o_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Osymstream_1ac988195924cbf83481ed903722dcb064)`(self,value)` | 
`public def `[`o_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Osymstream_1a3ae379658b5f067f0cc1c2b5601d6157)`(self)` | 

## Members

#### `public def `[`o_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Osymstream_1ac988195924cbf83481ed903722dcb064)`(self,value)` {#classexot_1_1experiment_1_1__mixins_1_1Osymstream_1ac988195924cbf83481ed903722dcb064}

#### `public def `[`o_symstream`](#classexot_1_1experiment_1_1__mixins_1_1Osymstream_1a3ae379658b5f067f0cc1c2b5601d6157)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1Osymstream_1a3ae379658b5f067f0cc1c2b5601d6157}

# class `exot::experiment::_mixins::StreamHandler` {#classexot_1_1experiment_1_1__mixins_1_1StreamHandler}

```
class exot::experiment::_mixins::StreamHandler
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`i_streams`](#classexot_1_1experiment_1_1__mixins_1_1StreamHandler_1a5cbb8f62c9bcf4c529a27dd45b0c3db5)`(self)` | 
`public def `[`o_streams`](#classexot_1_1experiment_1_1__mixins_1_1StreamHandler_1aa7a4db952b9dee45572cd68db2803c79)`(self)` | 

## Members

#### `public def `[`i_streams`](#classexot_1_1experiment_1_1__mixins_1_1StreamHandler_1a5cbb8f62c9bcf4c529a27dd45b0c3db5)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1StreamHandler_1a5cbb8f62c9bcf4c529a27dd45b0c3db5}

#### `public def `[`o_streams`](#classexot_1_1experiment_1_1__mixins_1_1StreamHandler_1aa7a4db952b9dee45572cd68db2803c79)`(self)` {#classexot_1_1experiment_1_1__mixins_1_1StreamHandler_1aa7a4db952b9dee45572cd68db2803c79}

# class `exot::experiment::_mixins::StreamType` {#classexot_1_1experiment_1_1__mixins_1_1StreamType}

```
class exot::experiment::_mixins::StreamType
  : public IntEnum
```  

Stream types

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::experiment::app_exec` {#namespaceexot_1_1experiment_1_1app__exec}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::experiment::app_exec::AppExecExperiment`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment) | Stub class for an experiment where a src app executes a given schedule.
`class `[`exot::experiment::app_exec::AppExecRun`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun) | 

# class `exot::experiment::app_exec::AppExecExperiment` {#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment}

```
class exot::experiment::app_exec::AppExecExperiment
  : public exot.experiment._base.Experiment
  : public type
  : public AppExec
```  

Stub class for an experiment where a src app executes a given schedule.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`run_type`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a321327889b5408c9eff8a6ada9b79f27) | 
`public  `[`phases`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a6c41a0e8bd8c9fd746e43c88a7680849) | 
`public  `[`estimated_duration`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a2b3a876a037ada9779a75b45b7e10ad1) | 
`public def `[`__init__`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a9db7964e874ede30b810d3be6473b31d)`(self,* args,** kwargs)` | Initialise an Experiment object
`public def `[`validate`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a95094ec41239270e7f339d1bcbdc1965)`(self)` | Validate experiment configuration
`public def `[`generate`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a7bef3254ed0b7f829765fe5953ddbcb5)`(self)` | Populate the experiment phases and instantiate Run's

## Members

#### `public  `[`run_type`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a321327889b5408c9eff8a6ada9b79f27) {#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a321327889b5408c9eff8a6ada9b79f27}

#### `public  `[`phases`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a6c41a0e8bd8c9fd746e43c88a7680849) {#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a6c41a0e8bd8c9fd746e43c88a7680849}

#### `public  `[`estimated_duration`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a2b3a876a037ada9779a75b45b7e10ad1) {#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a2b3a876a037ada9779a75b45b7e10ad1}

#### `public def `[`__init__`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a9db7964e874ede30b810d3be6473b31d)`(self,* args,** kwargs)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a9db7964e874ede30b810d3be6473b31d}

Initialise an Experiment object

#### `public def `[`validate`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a95094ec41239270e7f339d1bcbdc1965)`(self)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a95094ec41239270e7f339d1bcbdc1965}

Validate experiment configuration

#### `public def `[`generate`](#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a7bef3254ed0b7f829765fe5953ddbcb5)`(self)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecExperiment_1a7bef3254ed0b7f829765fe5953ddbcb5}

Populate the experiment phases and instantiate Run's

Preconditions:
    - The experiment should be configured and bootstrapped.

# class `exot::experiment::app_exec::AppExecRun` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun}

```
class exot::experiment::app_exec::AppExecRun
  : public exot.experiment._base.Run
  : public exot.experiment._mixins.StreamHandler
  : public exot.experiment._mixins.Ibitstream
  : public exot.experiment._mixins.Isymstream
  : public exot.experiment._mixins.Ilnestream
  : public exot.experiment._mixins.Irdpstream
  : public exot.experiment._mixins.Irawstream
  : public serialise_save
  : public serialise_ignore
  : public parent
  : public exot.experiment.app_exec.AppExecExperiment
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`i_rawstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a84d7875878434062b5ec954d1001867c) | 
`public  `[`i_rdpstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a7f78af26437273e4ebcab2e0a9bf61c7) | 
`public  `[`i_lnestream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a72744ba19135111d22a536e5d1afacca) | 
`public  `[`i_symstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a572fc3b768e7386c25baac0e2840be16) | 
`public  `[`i_bitstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a92fbaf033b90a9847ce4df7b1d1b5b22) | 
`public def `[`identifier`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a01954d243f5760bcf05980a2a0474f8f)`(self)` | Get the save path
`public object `[`read`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a93159488b633f1e519735ae5833b78bc)`(cls,Path path,t.Optional parent)` | Read a serialised Run and produce a Run instance
`public None `[`write`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a2ffeba66d2a9d0f11062324361ce8e5b)`(self)` | Serialises the AppExecRun
`public def `[`required_config_keys`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a9c7658cfca85982681eac2634f9ce7d2)`(self)` | Gets the required config keys
`public None `[`digest`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1ad735f4e20ce1d2d5b66649484e77aa2c)`(self,*bool skip_checks,** kwargs)` | Perform all encoding operations, propagating the streams to subsequent layers
`public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1aab906859752d89f71b75dff68b0a2629)`(self)` | Write experiment schedules to files
`public None `[`ingest`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1af7c186cb53357427d6d82eee356b3a7d)`(self,*bool skip_checks,** kwargs)` | Perform all decoding operations, propagating the streams to preceding Layers
`public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1ad95fdddd62264682fc105ec54a3d6b19)`(self,env)` | Get the estimated duration of this Run's execution

## Members

#### `public  `[`i_rawstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a84d7875878434062b5ec954d1001867c) {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a84d7875878434062b5ec954d1001867c}

#### `public  `[`i_rdpstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a7f78af26437273e4ebcab2e0a9bf61c7) {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a7f78af26437273e4ebcab2e0a9bf61c7}

#### `public  `[`i_lnestream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a72744ba19135111d22a536e5d1afacca) {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a72744ba19135111d22a536e5d1afacca}

#### `public  `[`i_symstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a572fc3b768e7386c25baac0e2840be16) {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a572fc3b768e7386c25baac0e2840be16}

#### `public  `[`i_bitstream`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a92fbaf033b90a9847ce4df7b1d1b5b22) {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a92fbaf033b90a9847ce4df7b1d1b5b22}

#### `public def `[`identifier`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a01954d243f5760bcf05980a2a0474f8f)`(self)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a01954d243f5760bcf05980a2a0474f8f}

Get the save path

#### `public object `[`read`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a93159488b633f1e519735ae5833b78bc)`(cls,Path path,t.Optional parent)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a93159488b633f1e519735ae5833b78bc}

Read a serialised Run and produce a Run instance

Args:
    path (Path): The path of the serialised instance
    parent (t.Optional[object], optional): The parent experiment to set

Returns:
    object: The deserialised instance

#### `public None `[`write`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a2ffeba66d2a9d0f11062324361ce8e5b)`(self)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a2ffeba66d2a9d0f11062324361ce8e5b}

Serialises the AppExecRun

In addition to the base class'es `write`, the AppExecRun als0 writes an
archive with output streams and writes the schedules to *.sched files.

#### `public def `[`required_config_keys`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a9c7658cfca85982681eac2634f9ce7d2)`(self)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1a9c7658cfca85982681eac2634f9ce7d2}

Gets the required config keys

Returns:
    list: The required keys

#### `public None `[`digest`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1ad735f4e20ce1d2d5b66649484e77aa2c)`(self,*bool skip_checks,** kwargs)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1ad735f4e20ce1d2d5b66649484e77aa2c}

Perform all encoding operations, propagating the streams to subsequent layers

Caveats:
    Since `digest` accesses parent config in `_configure_layers_proxy`, the digest
    step cannot be performed concurrently.

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1aab906859752d89f71b75dff68b0a2629)`(self)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1aab906859752d89f71b75dff68b0a2629}

Write experiment schedules to files

Returns:
    t.List[Path]: a list of paths where schedules were written

#### `public None `[`ingest`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1af7c186cb53357427d6d82eee356b3a7d)`(self,*bool skip_checks,** kwargs)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1af7c186cb53357427d6d82eee356b3a7d}

Perform all decoding operations, propagating the streams to preceding Layers

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1ad95fdddd62264682fc105ec54a3d6b19)`(self,env)` {#classexot_1_1experiment_1_1app__exec_1_1AppExecRun_1ad95fdddd62264682fc105ec54a3d6b19}

Get the estimated duration of this Run's execution

Returns:
    t.Optional[float]: the duration in seconds, or None if not digested

# namespace `exot::experiment::exploratory` {#namespaceexot_1_1experiment_1_1exploratory}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::experiment::exploratory::ExploratoryExperiment`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment) | Stub class for a capacity experiment
`class `[`exot::experiment::exploratory::ExploratoryRun`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun) | 

# class `exot::experiment::exploratory::ExploratoryExperiment` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment}

```
class exot::experiment::exploratory::ExploratoryExperiment
  : public exot.experiment._base.Experiment
  : public type
  : public Exploratory
```  

Stub class for a capacity experiment

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`run_type`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a721f57abb8a6e869677945804551c4e6) | 
`public  `[`phases`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a524fe60b29cf77960ba19e06b8d353ad) | 
`public  `[`estimated_duration`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1af837ef190f01c5ac42cfc397d00738e3) | 
`public def `[`__init__`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a55ce104e76dfb6b000d1c141a30621b3)`(self,* args,** kwargs)` | Initialise an Experiment object
`public def `[`validate`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1abfd6bd9d915814b477899761358bd0ac)`(self)` | Validate experiment configuration
`public def `[`generate`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a1c08241c57cb311e376b06248289dcd3)`(self)` | Populate the experiment phases and instantiate Run's

## Members

#### `public  `[`run_type`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a721f57abb8a6e869677945804551c4e6) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a721f57abb8a6e869677945804551c4e6}

#### `public  `[`phases`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a524fe60b29cf77960ba19e06b8d353ad) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a524fe60b29cf77960ba19e06b8d353ad}

#### `public  `[`estimated_duration`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1af837ef190f01c5ac42cfc397d00738e3) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1af837ef190f01c5ac42cfc397d00738e3}

#### `public def `[`__init__`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a55ce104e76dfb6b000d1c141a30621b3)`(self,* args,** kwargs)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a55ce104e76dfb6b000d1c141a30621b3}

Initialise an Experiment object

#### `public def `[`validate`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1abfd6bd9d915814b477899761358bd0ac)`(self)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1abfd6bd9d915814b477899761358bd0ac}

Validate experiment configuration

#### `public def `[`generate`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a1c08241c57cb311e376b06248289dcd3)`(self)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryExperiment_1a1c08241c57cb311e376b06248289dcd3}

Populate the experiment phases and instantiate Run's

Preconditions:
    - The experiment should be configured and bootstrapped.

# class `exot::experiment::exploratory::ExploratoryRun` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun}

```
class exot::experiment::exploratory::ExploratoryRun
  : public exot.experiment._base.Run
  : public exot.experiment._mixins.StreamHandler
  : public exot.experiment._mixins.Irdpstream
  : public exot.experiment._mixins.Irawstream
  : public exot.experiment._mixins.Ordpstream
  : public exot.experiment._mixins.Orawstream
  : public exot.experiment._mixins.Oschedules
  : public serialise_save
  : public parent
  : public exot.experiment.exploratory.ExploratoryExperiment
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`o_rdpstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a372cc1503ddab699803271a4a9eeee33) | 
`public  `[`o_rawstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a8781b49216b4d235ca61abd64182b90c) | 
`public  `[`o_schedules`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1aa25d1b12d0146feb747fd2f8ad05d93f) | 
`public  `[`i_rawstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a1fcad49a980b94a9f27014ea2f1de3ba) | 
`public  `[`i_rdpstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a31d0a67cfa036c9dccaf62284e71bcb0) | 
`public def `[`identifier`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a6c467103fe0480bf1a2821d2ff3621da)`(self)` | Get the save path
`public object `[`read`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1af2d2ecb616bb11d8fc279d5e3e92ff1b)`(cls,Path path,t.Optional parent)` | Read a serialised Run and produce a Run instance
`public None `[`write`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1adef8ddb3d677f96cd25e123ce41e08d9)`(self)` | Serialises the ExploratoryRun
`public def `[`required_config_keys`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a65976d053bf9fc6a835e93cb3a46c2de)`(self)` | Gets the required config keys
`public None `[`digest`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1ae3bb012096d7262ff0d978fda619cf4e)`(self,*bool skip_checks,bool write_intermediates,** kwargs)` | Perform all encoding operations, propagating the streams to subsequent layers
`public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a90daac67bc95009ca9a18623637edbd0)`(self)` | Write experiment schedules to files
`public None `[`ingest`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a40e6e7d9ef4fadec1776edf43e8f3d7b)`(self,*bool skip_checks,** kwargs)` | Perform all decoding operations, propagating the streams to preceding Layers
`public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a01fe405fd6175be92872366e96fb108b)`(self,env)` | Get the estimated duration of this Run's execution

## Members

#### `public  `[`o_rdpstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a372cc1503ddab699803271a4a9eeee33) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a372cc1503ddab699803271a4a9eeee33}

#### `public  `[`o_rawstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a8781b49216b4d235ca61abd64182b90c) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a8781b49216b4d235ca61abd64182b90c}

#### `public  `[`o_schedules`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1aa25d1b12d0146feb747fd2f8ad05d93f) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1aa25d1b12d0146feb747fd2f8ad05d93f}

#### `public  `[`i_rawstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a1fcad49a980b94a9f27014ea2f1de3ba) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a1fcad49a980b94a9f27014ea2f1de3ba}

#### `public  `[`i_rdpstream`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a31d0a67cfa036c9dccaf62284e71bcb0) {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a31d0a67cfa036c9dccaf62284e71bcb0}

#### `public def `[`identifier`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a6c467103fe0480bf1a2821d2ff3621da)`(self)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a6c467103fe0480bf1a2821d2ff3621da}

Get the save path

#### `public object `[`read`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1af2d2ecb616bb11d8fc279d5e3e92ff1b)`(cls,Path path,t.Optional parent)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1af2d2ecb616bb11d8fc279d5e3e92ff1b}

Read a serialised Run and produce a Run instance

Args:
    path (Path): The path of the serialised instance
    parent (t.Optional[object], optional): The parent experiment to set

Returns:
    object: The deserialised instance

#### `public None `[`write`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1adef8ddb3d677f96cd25e123ce41e08d9)`(self)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1adef8ddb3d677f96cd25e123ce41e08d9}

Serialises the ExploratoryRun

In addition to the base class'es `write`, the ExploratoryRun als0 writes an
archive with output streams and writes the schedules to *.sched files.

#### `public def `[`required_config_keys`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a65976d053bf9fc6a835e93cb3a46c2de)`(self)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a65976d053bf9fc6a835e93cb3a46c2de}

Gets the required config keys

Returns:
    list: The required keys

#### `public None `[`digest`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1ae3bb012096d7262ff0d978fda619cf4e)`(self,*bool skip_checks,bool write_intermediates,** kwargs)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1ae3bb012096d7262ff0d978fda619cf4e}

Perform all encoding operations, propagating the streams to subsequent layers

Caveats:
    Since `digest` accesses parent config in `_configure_layers_proxy`, the digest
    step cannot be performed concurrently.

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a90daac67bc95009ca9a18623637edbd0)`(self)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a90daac67bc95009ca9a18623637edbd0}

Write experiment schedules to files

Returns:
    t.List[Path]: a list of paths where schedules were written

#### `public None `[`ingest`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a40e6e7d9ef4fadec1776edf43e8f3d7b)`(self,*bool skip_checks,** kwargs)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a40e6e7d9ef4fadec1776edf43e8f3d7b}

Perform all decoding operations, propagating the streams to preceding Layers

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a01fe405fd6175be92872366e96fb108b)`(self,env)` {#classexot_1_1experiment_1_1exploratory_1_1ExploratoryRun_1a01fe405fd6175be92872366e96fb108b}

Get the estimated duration of this Run's execution

Returns:
    t.Optional[float]: the duration in seconds, or None if not digested

# namespace `exot::experiment::frequency_sweep` {#namespaceexot_1_1experiment_1_1frequency__sweep}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::experiment::frequency_sweep::FrequencySweepExperiment`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment) | Stub class for a capacity experiment
`class `[`exot::experiment::frequency_sweep::FrequencySweepRun`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun) | 

# class `exot::experiment::frequency_sweep::FrequencySweepExperiment` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment}

```
class exot::experiment::frequency_sweep::FrequencySweepExperiment
  : public exot.experiment._base.Experiment
  : public serialise_save
  : public type
  : public FrequencySweep
```  

Stub class for a capacity experiment

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`run_type`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1afe02987d092233bdc998d11300bb46ba) | 
`public  `[`phases`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a14d8f8cb7bc14c4d68de73a4319402ac) | 
`public  `[`estimated_duration`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1aad90956ef5d23b998a5bed68aaeaea67) | 
`public  `[`spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a1aa5e79e476ea7606f44422dc3755918) | 
`public  `[`p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a131a872d8118d9bde61febc121664a42) | 
`public def `[`__init__`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a5bafcab8827d0b421b37ee1cc9517679)`(self,* args,** kwargs)` | Initialise an Experiment object
`public def `[`write`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac18ae4373ed333997463a306ee6a9b45)`(self)` | Serialise the experiment
`public object `[`read`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a90aecb18598d4786ba3320b17d372544)`(cls,* args,** kwargs)` | 
`public def `[`validate`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a85c2377ee2b045881863c4d76b71947d)`(self)` | Validate experiment configuration
`public def `[`generate`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1af33a5ae7cee20496fc7a5d8cbb2184a8)`(self)` | Populate the experiment phases and instantiate Run's
`public None `[`generate_spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac1831a62f775e860ddf0c39c163d0157)`(self,*t.List phases,t.List envs,t.List reps,** kwargs)` | This function generates following channel:
`public def `[`spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1aaf11b6cc901b5c0829888e24525be37e)`(self,value)` | 
`public def `[`spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ad003dcfe4e6193a227045f9f78831480)`(self)` | 
`public def `[`p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a4e4e4d5f10d1a7f1f687c7d0240d7f9c)`(self,value)` | 
`public def `[`p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac2740e46aa0c41c0bde3bd150325875a)`(self)` | 
`public def `[`spectrum_as_matrix`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a046899d470ed7aa672c4f771eec7f72f)`(self,str spectrum,str phase,str env,t. Union,int] rep)` | 

## Members

#### `public  `[`run_type`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1afe02987d092233bdc998d11300bb46ba) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1afe02987d092233bdc998d11300bb46ba}

#### `public  `[`phases`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a14d8f8cb7bc14c4d68de73a4319402ac) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a14d8f8cb7bc14c4d68de73a4319402ac}

#### `public  `[`estimated_duration`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1aad90956ef5d23b998a5bed68aaeaea67) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1aad90956ef5d23b998a5bed68aaeaea67}

#### `public  `[`spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a1aa5e79e476ea7606f44422dc3755918) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a1aa5e79e476ea7606f44422dc3755918}

#### `public  `[`p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a131a872d8118d9bde61febc121664a42) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a131a872d8118d9bde61febc121664a42}

#### `public def `[`__init__`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a5bafcab8827d0b421b37ee1cc9517679)`(self,* args,** kwargs)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a5bafcab8827d0b421b37ee1cc9517679}

Initialise an Experiment object

#### `public def `[`write`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac18ae4373ed333997463a306ee6a9b45)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac18ae4373ed333997463a306ee6a9b45}

Serialise the experiment

#### `public object `[`read`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a90aecb18598d4786ba3320b17d372544)`(cls,* args,** kwargs)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a90aecb18598d4786ba3320b17d372544}

#### `public def `[`validate`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a85c2377ee2b045881863c4d76b71947d)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a85c2377ee2b045881863c4d76b71947d}

Validate experiment configuration

#### `public def `[`generate`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1af33a5ae7cee20496fc7a5d8cbb2184a8)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1af33a5ae7cee20496fc7a5d8cbb2184a8}

Populate the experiment phases and instantiate Run's

Preconditions:
    - The experiment should be configured and bootstrapped.

#### `public None `[`generate_spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac1831a62f775e860ddf0c39c163d0157)`(self,*t.List phases,t.List envs,t.List reps,** kwargs)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac1831a62f775e860ddf0c39c163d0157}

This function generates following channel:
     * Shh ... Channel Spectrum
     * Sqq ... Noise Spectrum (if frequency=0 has been evaluated, otherwise 0)

#### `public def `[`spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1aaf11b6cc901b5c0829888e24525be37e)`(self,value)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1aaf11b6cc901b5c0829888e24525be37e}

#### `public def `[`spectra`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ad003dcfe4e6193a227045f9f78831480)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ad003dcfe4e6193a227045f9f78831480}

#### `public def `[`p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a4e4e4d5f10d1a7f1f687c7d0240d7f9c)`(self,value)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a4e4e4d5f10d1a7f1f687c7d0240d7f9c}

#### `public def `[`p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac2740e46aa0c41c0bde3bd150325875a)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1ac2740e46aa0c41c0bde3bd150325875a}

#### `public def `[`spectrum_as_matrix`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a046899d470ed7aa672c4f771eec7f72f)`(self,str spectrum,str phase,str env,t. Union,int] rep)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepExperiment_1a046899d470ed7aa672c4f771eec7f72f}

# class `exot::experiment::frequency_sweep::FrequencySweepRun` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun}

```
class exot::experiment::frequency_sweep::FrequencySweepRun
  : public exot.experiment._base.Run
  : public exot.experiment._mixins.StreamHandler
  : public exot.experiment._mixins.Ilnestream
  : public exot.experiment._mixins.Irdpstream
  : public exot.experiment._mixins.Irawstream
  : public exot.experiment._mixins.Olnestream
  : public exot.experiment._mixins.Ordpstream
  : public exot.experiment._mixins.Orawstream
  : public exot.experiment._mixins.Oschedules
  : public serialise_save
  : public serialise_ignore
  : public parent
  : public exot.experiment.frequency_sweep.FrequencySweepExperiment
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`o_lnestream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a3cfe035a4b03b414fee7a48508612ec9) | 
`public  `[`o_rdpstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a9b840410888c347e63f3bc5697d12c4f) | 
`public  `[`o_rawstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ad6892bd48843aa19b896523726fe5abf) | 
`public  `[`o_schedules`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a802bcb8369650cf84d7c411505f4de17) | 
`public  `[`i_rawstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1abc7479877f3034dec743bb5c4d05891b) | 
`public  `[`i_rdpstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a6c4d7125cc6f9c49402eca1e6d64a04e) | 
`public  `[`i_lnestream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a3cfed1dab767a7d63c45726d1e539e6a) | 
`public  `[`o_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1aa7b20f9bf904939d44a027ae63363c99) | 
`public  `[`o_p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ae6540c538187eb157fd5928cbcb7da44) | 
`public  `[`i_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a25e04ae95a37e2a17d5260133a5ea718) | 
`public def `[`identifier`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a072b7b14bd14a24bc0f8a6fd44fd74ea)`(self)` | Get the save path
`public object `[`read`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1aeb500f039576071259c84e55716414af)`(cls,Path path,t.Optional parent)` | Read a serialised Run and produce a Run instance
`public None `[`write`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ab6ef38691702cecf4a54734486c91894)`(self)` | Serialises the FrequencySweepRun
`public def `[`required_config_keys`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a29d2f20cf2a9ed8a69cd975afbfedcd5)`(self)` | Gets the required config keys
`public None `[`digest`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a9fae286d6ee1953e29b94bf862f920a6)`(self,*bool skip_checks,** kwargs)` | Perform all encoding operations, propagating the streams to subsequent layers
`public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a4062b2866d341c14ae14936ee91874a0)`(self)` | Write experiment schedules to files
`public None `[`ingest`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ade4c7b105bb2fdf179c0221f6b6df145)`(self,*bool skip_checks,** kwargs)` | Perform all decoding operations, propagating the streams to preceding Layers
`public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1abaf06dbacb53afe466f56eaa97b51079)`(self,env)` | Get the estimated duration of this Run's execution
`public def `[`i_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a6d3f3dab87db4e065413f227d4ae3e45)`(self,value)` | 
`public def `[`i_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a364e4792a9aba4ad16dabe9a40621dc9)`(self)` | 
`public def `[`o_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a0da665ff9e232b7d51b5f666aa720230)`(self,value)` | 
`public def `[`o_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a502fc462b3002f8ef51eb59762417cab)`(self)` | 
`public def `[`o_p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a59828a9e1b4e4ba10c0c228c11c20353)`(self,value)` | 
`public def `[`o_p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ac6c8cc499873028b77acbb0f367c9456)`(self)` | 

## Members

#### `public  `[`o_lnestream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a3cfe035a4b03b414fee7a48508612ec9) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a3cfe035a4b03b414fee7a48508612ec9}

#### `public  `[`o_rdpstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a9b840410888c347e63f3bc5697d12c4f) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a9b840410888c347e63f3bc5697d12c4f}

#### `public  `[`o_rawstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ad6892bd48843aa19b896523726fe5abf) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ad6892bd48843aa19b896523726fe5abf}

#### `public  `[`o_schedules`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a802bcb8369650cf84d7c411505f4de17) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a802bcb8369650cf84d7c411505f4de17}

#### `public  `[`i_rawstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1abc7479877f3034dec743bb5c4d05891b) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1abc7479877f3034dec743bb5c4d05891b}

#### `public  `[`i_rdpstream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a6c4d7125cc6f9c49402eca1e6d64a04e) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a6c4d7125cc6f9c49402eca1e6d64a04e}

#### `public  `[`i_lnestream`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a3cfed1dab767a7d63c45726d1e539e6a) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a3cfed1dab767a7d63c45726d1e539e6a}

#### `public  `[`o_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1aa7b20f9bf904939d44a027ae63363c99) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1aa7b20f9bf904939d44a027ae63363c99}

#### `public  `[`o_p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ae6540c538187eb157fd5928cbcb7da44) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ae6540c538187eb157fd5928cbcb7da44}

#### `public  `[`i_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a25e04ae95a37e2a17d5260133a5ea718) {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a25e04ae95a37e2a17d5260133a5ea718}

#### `public def `[`identifier`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a072b7b14bd14a24bc0f8a6fd44fd74ea)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a072b7b14bd14a24bc0f8a6fd44fd74ea}

Get the save path

#### `public object `[`read`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1aeb500f039576071259c84e55716414af)`(cls,Path path,t.Optional parent)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1aeb500f039576071259c84e55716414af}

Read a serialised Run and produce a Run instance

Args:
    path (Path): The path of the serialised instance
    parent (t.Optional[object], optional): The parent experiment to set

Returns:
    object: The deserialised instance

#### `public None `[`write`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ab6ef38691702cecf4a54734486c91894)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ab6ef38691702cecf4a54734486c91894}

Serialises the FrequencySweepRun

In addition to the base class'es `write`, the FrequencySweepRun also writes an
archive with output streams and writes the schedules to *.sched files.

#### `public def `[`required_config_keys`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a29d2f20cf2a9ed8a69cd975afbfedcd5)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a29d2f20cf2a9ed8a69cd975afbfedcd5}

Gets the required config keys

Returns:
    list: The required keys

#### `public None `[`digest`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a9fae286d6ee1953e29b94bf862f920a6)`(self,*bool skip_checks,** kwargs)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a9fae286d6ee1953e29b94bf862f920a6}

Perform all encoding operations, propagating the streams to subsequent layers

Caveats:
    Since `digest` accesses parent config in `_configure_layers_proxy`, the digest
    step cannot be performed concurrently.

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a4062b2866d341c14ae14936ee91874a0)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a4062b2866d341c14ae14936ee91874a0}

Write experiment schedules to files

Returns:
    t.List[Path]: a list of paths where schedules were written

#### `public None `[`ingest`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ade4c7b105bb2fdf179c0221f6b6df145)`(self,*bool skip_checks,** kwargs)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ade4c7b105bb2fdf179c0221f6b6df145}

Perform all decoding operations, propagating the streams to preceding Layers

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1abaf06dbacb53afe466f56eaa97b51079)`(self,env)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1abaf06dbacb53afe466f56eaa97b51079}

Get the estimated duration of this Run's execution

Returns:
    t.Optional[float]: the duration in seconds, or None if not digested

#### `public def `[`i_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a6d3f3dab87db4e065413f227d4ae3e45)`(self,value)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a6d3f3dab87db4e065413f227d4ae3e45}

#### `public def `[`i_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a364e4792a9aba4ad16dabe9a40621dc9)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a364e4792a9aba4ad16dabe9a40621dc9}

#### `public def `[`o_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a0da665ff9e232b7d51b5f666aa720230)`(self,value)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a0da665ff9e232b7d51b5f666aa720230}

#### `public def `[`o_fspectrum`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a502fc462b3002f8ef51eb59762417cab)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a502fc462b3002f8ef51eb59762417cab}

#### `public def `[`o_p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a59828a9e1b4e4ba10c0c228c11c20353)`(self,value)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1a59828a9e1b4e4ba10c0c228c11c20353}

#### `public def `[`o_p0`](#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ac6c8cc499873028b77acbb0f367c9456)`(self)` {#classexot_1_1experiment_1_1frequency__sweep_1_1FrequencySweepRun_1ac6c8cc499873028b77acbb0f367c9456}

# namespace `exot::experiment::performance` {#namespaceexot_1_1experiment_1_1performance}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::experiment::performance::PerformanceExperiment`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment) | 
`class `[`exot::experiment::performance::PerformanceRun`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun) | 

# class `exot::experiment::performance::PerformanceExperiment` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment}

```
class exot::experiment::performance::PerformanceExperiment
  : public exot.experiment._base.Experiment
  : public serialise_save
  : public type
  : public Performance
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`run_type`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a79a4e29b29ebea91e48079956af056aa) | 
`public  `[`phases`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1aed79c20a8ce02e2158e30d10c26aa377) | 
`public  `[`estimated_duration`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a2b43422a1bfcb141e88b2fa17aa5f30c) | 
`public  `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a23d4aeee544f0eaf412bf1bec8952def) | 
`public def `[`__init__`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a947b59e5984633278de74b81ecfaf0e5)`(self,* args,** kwargs)` | Initialise an Experiment object
`public def `[`validate`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a1b6a32cd100eee7a2bb3605b226cdaf4)`(self)` | Validate experiment configuration
`public def `[`generate`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1acddaf4fdab8bae94c0b18f581d774a38)`(self,** kwargs)` | 
`public def `[`write`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a6d3dc34418e9f05a6480efde27f21ab9)`(self)` | Serialise the experiment
`public object `[`read`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a5220ea2c8b3acac1b9b7150698d800c8)`(cls,* args,** kwargs)` | 
`public t.Tuple`[`pd.DataFrame, [Run](#classexot_1_1experiment_1_1__base_1_1Run), t.Optional[[Run`](#classexot_1_1experiment_1_1__base_1_1Run)`]] `[`analyse_run_pair`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a64e30b954e9ebc7cfc32896690b4393e)`(self,str train_phase,t.Optional eval_phase,t.Hashable idx,dict ingest_args,*bool standalone,bool use_levensthein,** kwargs)` | 
`public pd.DataFrame `[`calculate_performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a1162adc59ceee2e329bc470045b9b37c)`(self,*t.Dict phase_mapping,t.List envs,t.List reps,** kwargs)` | Calculates performance metrics for different environments, repetitions, and train->eval mappings
`public pd.DataFrame `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a580ac2b7778b48ee7ee0c521bbeb6046)`(self)` | 
`public def `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1af6c24d5a9d3c3fb1771615d3cd8feb8d)`(self,value)` | 
`public def `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1abe527b54e11cdcef9aa2626d295dda8b)`(self)` | 
`public pd.DataFrame `[`aggregate_performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a11008c0e386d8ef10ed524fbe2194ce1)`(self,t.Callable function)` | Aggregatas the performance metrics using a function

## Members

#### `public  `[`run_type`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a79a4e29b29ebea91e48079956af056aa) {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a79a4e29b29ebea91e48079956af056aa}

#### `public  `[`phases`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1aed79c20a8ce02e2158e30d10c26aa377) {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1aed79c20a8ce02e2158e30d10c26aa377}

#### `public  `[`estimated_duration`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a2b43422a1bfcb141e88b2fa17aa5f30c) {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a2b43422a1bfcb141e88b2fa17aa5f30c}

#### `public  `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a23d4aeee544f0eaf412bf1bec8952def) {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a23d4aeee544f0eaf412bf1bec8952def}

#### `public def `[`__init__`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a947b59e5984633278de74b81ecfaf0e5)`(self,* args,** kwargs)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a947b59e5984633278de74b81ecfaf0e5}

Initialise an Experiment object

#### `public def `[`validate`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a1b6a32cd100eee7a2bb3605b226cdaf4)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a1b6a32cd100eee7a2bb3605b226cdaf4}

Validate experiment configuration

#### `public def `[`generate`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1acddaf4fdab8bae94c0b18f581d774a38)`(self,** kwargs)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1acddaf4fdab8bae94c0b18f581d774a38}

#### `public def `[`write`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a6d3dc34418e9f05a6480efde27f21ab9)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a6d3dc34418e9f05a6480efde27f21ab9}

Serialise the experiment

#### `public object `[`read`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a5220ea2c8b3acac1b9b7150698d800c8)`(cls,* args,** kwargs)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a5220ea2c8b3acac1b9b7150698d800c8}

#### `public t.Tuple`[`pd.DataFrame, [Run](#classexot_1_1experiment_1_1__base_1_1Run), t.Optional[[Run`](#classexot_1_1experiment_1_1__base_1_1Run)`]] `[`analyse_run_pair`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a64e30b954e9ebc7cfc32896690b4393e)`(self,str train_phase,t.Optional eval_phase,t.Hashable idx,dict ingest_args,*bool standalone,bool use_levensthein,** kwargs)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a64e30b954e9ebc7cfc32896690b4393e}

#### `public pd.DataFrame `[`calculate_performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a1162adc59ceee2e329bc470045b9b37c)`(self,*t.Dict phase_mapping,t.List envs,t.List reps,** kwargs)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a1162adc59ceee2e329bc470045b9b37c}

Calculates performance metrics for different environments, repetitions, and train->eval mappings

Args:
    phase_mapping (t.Dict[str, str], optional): Phase mapping train -> eval
    envs (t.List[str], optional): List of environments
    reps (t.List[int], optional): List of repetitions
    **kwargs: Keyword arguments to ingest and (optionally) the matcher

#### `public pd.DataFrame `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a580ac2b7778b48ee7ee0c521bbeb6046)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a580ac2b7778b48ee7ee0c521bbeb6046}

#### `public def `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1af6c24d5a9d3c3fb1771615d3cd8feb8d)`(self,value)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1af6c24d5a9d3c3fb1771615d3cd8feb8d}

#### `public def `[`performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1abe527b54e11cdcef9aa2626d295dda8b)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1abe527b54e11cdcef9aa2626d295dda8b}

#### `public pd.DataFrame `[`aggregate_performance_metrics`](#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a11008c0e386d8ef10ed524fbe2194ce1)`(self,t.Callable function)` {#classexot_1_1experiment_1_1performance_1_1PerformanceExperiment_1a11008c0e386d8ef10ed524fbe2194ce1}

Aggregatas the performance metrics using a function

Args:
    function (t.Callable, optional): The aggregator function, takes a Series as an argument

Returns:
    pd.DataFrame: A DataFrame similar to performance_metrics, without repetitions

Raises:
    TypeError: Wrong type is provided for the function
    ValueError: Performance metrics not available

# class `exot::experiment::performance::PerformanceRun` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun}

```
class exot::experiment::performance::PerformanceRun
  : public exot.experiment._base.Run
  : public exot.experiment._mixins.StreamHandler
  : public exot.experiment._mixins.Ibitstream
  : public exot.experiment._mixins.Isymstream
  : public exot.experiment._mixins.Ilnestream
  : public exot.experiment._mixins.Irdpstream
  : public exot.experiment._mixins.Irawstream
  : public exot.experiment._mixins.Obitstream
  : public exot.experiment._mixins.Osymstream
  : public exot.experiment._mixins.Olnestream
  : public exot.experiment._mixins.Ordpstream
  : public exot.experiment._mixins.Orawstream
  : public exot.experiment._mixins.Oschedules
  : public serialise_save
  : public serialise_ignore
  : public parent
  : public exot.experiment.performance.PerformanceExperiment
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`o_bitstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a865370f8569b6bad92a1a19b25c1e79c) | 
`public  `[`o_symstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ab81c66cad034fc920758a7ff5c099af8) | 
`public  `[`o_lnestream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a9eb23f8d2a1a2844fb98752a23e5ee96) | 
`public  `[`o_rdpstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a9e34f2fcb782cfcac837f1e919c981c0) | 
`public  `[`o_rawstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aecbb71e5520ebcd09aee84f56549893e) | 
`public  `[`o_schedules`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a132c1eb6c8ab6b5e1bb54ed00a331a12) | 
`public  `[`i_rawstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aa872b2d879f8b5ac0a414bf97b0d201a) | 
`public  `[`i_rdpstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a93acb0ab2ab1125f2bc6fcf8302ab9b8) | 
`public  `[`i_lnestream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a8028d4b0eee02bc5f0a20a6870492f14) | 
`public  `[`i_symstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a07a51fd409aecca50d867ca7aa00514d) | 
`public  `[`i_bitstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a66ebaaea55d79c4ea07fe0e807663ba6) | 
`public def `[`identifier`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ae079edcae24c75572276163499c3f433)`(self)` | Get the save path
`public object `[`read`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ae09410f6abc9ce718f96270ef5968856)`(cls,Path path,t.Optional parent)` | Read a serialised Run and produce a Run instance
`public None `[`write`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a30a28c8be73911e86263e6ea9adb973a)`(self)` | Serialises the PerformanceRun
`public def `[`required_config_keys`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a78ccab91d46251f94c1975b428755556)`(self)` | Gets the required config keys
`public None `[`digest`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a0e673422717d396a01d6c048f83298b6)`(self,*bool skip_checks,** kwargs)` | Perform all encoding operations, propagating the streams to subsequent layers
`public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a18bf6bd5becdbee957f7b37f57163bd1)`(self)` | Write experiment schedules to files
`public None `[`ingest`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a3b914e3893c2e19d6e82112e0e03570a)`(self,*bool skip_checks,** kwargs)` | Perform all decoding operations, propagating the streams to preceding Layers
`public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aa02dc63e8f60a9fd7147d7b506255eda)`(self,env)` | Get the estimated duration of this Run's execution

## Members

#### `public  `[`o_bitstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a865370f8569b6bad92a1a19b25c1e79c) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a865370f8569b6bad92a1a19b25c1e79c}

#### `public  `[`o_symstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ab81c66cad034fc920758a7ff5c099af8) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ab81c66cad034fc920758a7ff5c099af8}

#### `public  `[`o_lnestream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a9eb23f8d2a1a2844fb98752a23e5ee96) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a9eb23f8d2a1a2844fb98752a23e5ee96}

#### `public  `[`o_rdpstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a9e34f2fcb782cfcac837f1e919c981c0) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a9e34f2fcb782cfcac837f1e919c981c0}

#### `public  `[`o_rawstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aecbb71e5520ebcd09aee84f56549893e) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aecbb71e5520ebcd09aee84f56549893e}

#### `public  `[`o_schedules`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a132c1eb6c8ab6b5e1bb54ed00a331a12) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a132c1eb6c8ab6b5e1bb54ed00a331a12}

#### `public  `[`i_rawstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aa872b2d879f8b5ac0a414bf97b0d201a) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aa872b2d879f8b5ac0a414bf97b0d201a}

#### `public  `[`i_rdpstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a93acb0ab2ab1125f2bc6fcf8302ab9b8) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a93acb0ab2ab1125f2bc6fcf8302ab9b8}

#### `public  `[`i_lnestream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a8028d4b0eee02bc5f0a20a6870492f14) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a8028d4b0eee02bc5f0a20a6870492f14}

#### `public  `[`i_symstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a07a51fd409aecca50d867ca7aa00514d) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a07a51fd409aecca50d867ca7aa00514d}

#### `public  `[`i_bitstream`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a66ebaaea55d79c4ea07fe0e807663ba6) {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a66ebaaea55d79c4ea07fe0e807663ba6}

#### `public def `[`identifier`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ae079edcae24c75572276163499c3f433)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ae079edcae24c75572276163499c3f433}

Get the save path

#### `public object `[`read`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ae09410f6abc9ce718f96270ef5968856)`(cls,Path path,t.Optional parent)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1ae09410f6abc9ce718f96270ef5968856}

Read a serialised Run and produce a Run instance

Args:
    path (Path): The path of the serialised instance
    parent (t.Optional[object], optional): The parent experiment to set

Returns:
    object: The deserialised instance

#### `public None `[`write`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a30a28c8be73911e86263e6ea9adb973a)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a30a28c8be73911e86263e6ea9adb973a}

Serialises the PerformanceRun

In addition to the base class'es `write`, the PerformanceRun also writes an
archive with output streams and writes the schedules to *.sched files.

#### `public def `[`required_config_keys`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a78ccab91d46251f94c1975b428755556)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a78ccab91d46251f94c1975b428755556}

Gets the required config keys

Returns:
    list: The required keys

#### `public None `[`digest`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a0e673422717d396a01d6c048f83298b6)`(self,*bool skip_checks,** kwargs)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a0e673422717d396a01d6c048f83298b6}

Perform all encoding operations, propagating the streams to subsequent layers

Caveats:
    Since `digest` accesses parent config in `_configure_layers_proxy`, the digest
    step cannot be performed concurrently.

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.List[Path] `[`write_schedules`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a18bf6bd5becdbee957f7b37f57163bd1)`(self)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a18bf6bd5becdbee957f7b37f57163bd1}

Write experiment schedules to files

Returns:
    t.List[Path]: a list of paths where schedules were written

#### `public None `[`ingest`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a3b914e3893c2e19d6e82112e0e03570a)`(self,*bool skip_checks,** kwargs)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1a3b914e3893c2e19d6e82112e0e03570a}

Perform all decoding operations, propagating the streams to preceding Layers

Args:
    **kwargs: Optional configuration for layers, can be supplied in the form of:
      layer=dict(a=..., b=...), or **{layer: {"a":...}}

#### `public t.Optional[float] `[`estimated_duration`](#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aa02dc63e8f60a9fd7147d7b506255eda)`(self,env)` {#classexot_1_1experiment_1_1performance_1_1PerformanceRun_1aa02dc63e8f60a9fd7147d7b506255eda}

Get the estimated duration of this Run's execution

Returns:
    t.Optional[float]: the duration in seconds, or None if not digested

# class `exot::experiment::_base::Experiment::Type` {#classexot_1_1experiment_1_1__base_1_1Experiment_1_1Type}

```
class exot::experiment::_base::Experiment::Type
  : public IntEnum
```  
