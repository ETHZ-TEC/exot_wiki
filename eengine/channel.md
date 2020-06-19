[:back:](/home)
---

# Channel analysis
The name `channel` stems from the initial use of ExOT, and is a bit misleading. 
Actually, the `channel` module can contain any analysis that might be done on an experiment executed with ExOT.
If the analysis of a data leak, application characterization, etc. is finished, it can be pushed to this module to integrate it into ExOT and allow other researchers to easily reproduce your experiments and analyses.
An example is the thermal side channel analysis published as part of [Mie20](https://gitlab.ethz.ch/tec/research/exot/eengine/-/blob/pub_Mie20/notebooks/thermal-sc_execute_analysis.py).

# Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::channel::_base`](#namespaceexot_1_1channel_1_1__base) | 
`namespace `[`exot::channel::covertchannels`](#namespaceexot_1_1channel_1_1covertchannels) | 
`namespace `[`exot::channel::mixins::covertchannel`](#namespaceexot_1_1channel_1_1mixins_1_1covertchannel) | 
`namespace `[`exot::channel::mixins::mldataset`](#namespaceexot_1_1channel_1_1mixins_1_1mldataset) | 
`namespace `[`exot::channel::rnndecoder::_base`](#namespaceexot_1_1channel_1_1rnndecoder_1_1__base) | 
`namespace `[`exot::channel::rnndecoder::_mixins`](#namespaceexot_1_1channel_1_1rnndecoder_1_1__mixins) | 
`namespace `[`exot::channel::rnndecoder::evaluate`](#namespaceexot_1_1channel_1_1rnndecoder_1_1evaluate) | 
`namespace `[`exot::channel::rnndecoder::train`](#namespaceexot_1_1channel_1_1rnndecoder_1_1train) | 
`namespace `[`exot::channel::sidechannels`](#namespaceexot_1_1channel_1_1sidechannels) | 
`namespace `[`exot::channel::thermalsc::_mixins`](#namespaceexot_1_1channel_1_1thermalsc_1_1__mixins) | 
`namespace `[`exot::channel::thermalsc::appdetection`](#namespaceexot_1_1channel_1_1thermalsc_1_1appdetection) | 
`namespace `[`exot::channel::thermalsc::dataaugmentation`](#namespaceexot_1_1channel_1_1thermalsc_1_1dataaugmentation) | 

# namespace `exot::channel::_base` {#namespaceexot_1_1channel_1_1__base}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::_base::Analysis`](#classexot_1_1channel_1_1__base_1_1Analysis) | 
`class `[`exot::channel::_base::Channel`](#classexot_1_1channel_1_1__base_1_1Channel) | 
`class `[`exot::channel::_base::ChannelFactory`](#classexot_1_1channel_1_1__base_1_1ChannelFactory) | 

# class `exot::channel::_base::Analysis` {#classexot_1_1channel_1_1__base_1_1Analysis}

```
class exot::channel::_base::Analysis
  : public SubclassTracker
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`config`](#classexot_1_1channel_1_1__base_1_1Analysis_1a1f8f9ede7d33c9dd719ea23e27ae0aa5) | 
`public  `[`experiment`](#classexot_1_1channel_1_1__base_1_1Analysis_1a4cf697c03ba26a5e79d8a31abd8ca0c2) | 
`public def `[`__init__`](#classexot_1_1channel_1_1__base_1_1Analysis_1af751a57e4ebb9241d83c6d03e3f19dbe)`(self,* args,** kwargs)` | 
`public def `[`execute`](#classexot_1_1channel_1_1__base_1_1Analysis_1a9bb85ea8743cd1730b96d23690f15f18)`(self,* args,** kwargs)` | 
`public def `[`name`](#classexot_1_1channel_1_1__base_1_1Analysis_1a6ede8a79fd9cf9bd10d15da4ce798f5f)`(self)` | 
`public def `[`path`](#classexot_1_1channel_1_1__base_1_1Analysis_1af304ed737162c9fd37bcd103383bb934)`(self)` | 
`public def `[`log_path`](#classexot_1_1channel_1_1__base_1_1Analysis_1a2fd833a94907f35dd2de06aa727e1278)`(self)` | 

## Members

#### `public  `[`config`](#classexot_1_1channel_1_1__base_1_1Analysis_1a1f8f9ede7d33c9dd719ea23e27ae0aa5) {#classexot_1_1channel_1_1__base_1_1Analysis_1a1f8f9ede7d33c9dd719ea23e27ae0aa5}

#### `public  `[`experiment`](#classexot_1_1channel_1_1__base_1_1Analysis_1a4cf697c03ba26a5e79d8a31abd8ca0c2) {#classexot_1_1channel_1_1__base_1_1Analysis_1a4cf697c03ba26a5e79d8a31abd8ca0c2}

#### `public def `[`__init__`](#classexot_1_1channel_1_1__base_1_1Analysis_1af751a57e4ebb9241d83c6d03e3f19dbe)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1__base_1_1Analysis_1af751a57e4ebb9241d83c6d03e3f19dbe}

#### `public def `[`execute`](#classexot_1_1channel_1_1__base_1_1Analysis_1a9bb85ea8743cd1730b96d23690f15f18)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1__base_1_1Analysis_1a9bb85ea8743cd1730b96d23690f15f18}

#### `public def `[`name`](#classexot_1_1channel_1_1__base_1_1Analysis_1a6ede8a79fd9cf9bd10d15da4ce798f5f)`(self)` {#classexot_1_1channel_1_1__base_1_1Analysis_1a6ede8a79fd9cf9bd10d15da4ce798f5f}

#### `public def `[`path`](#classexot_1_1channel_1_1__base_1_1Analysis_1af304ed737162c9fd37bcd103383bb934)`(self)` {#classexot_1_1channel_1_1__base_1_1Analysis_1af304ed737162c9fd37bcd103383bb934}

#### `public def `[`log_path`](#classexot_1_1channel_1_1__base_1_1Analysis_1a2fd833a94907f35dd2de06aa727e1278)`(self)` {#classexot_1_1channel_1_1__base_1_1Analysis_1a2fd833a94907f35dd2de06aa727e1278}

# class `exot::channel::_base::Channel` {#classexot_1_1channel_1_1__base_1_1Channel}

```
class exot::channel::_base::Channel
  : public SubclassTracker
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public object `[`parent`](#classexot_1_1channel_1_1__base_1_1Channel_1a06d7ab65738edda85fca65071b256753)`(self)` | 
`public def `[`parent`](#classexot_1_1channel_1_1__base_1_1Channel_1a5ffbb982641123323bca88eb064edb96)`(self,value)` | 
`public def `[`hasparent`](#classexot_1_1channel_1_1__base_1_1Channel_1a3417f4b317b467d97dae156aecca5df2)`(self)` | 
`public def `[`analyses`](#classexot_1_1channel_1_1__base_1_1Channel_1a91881294cad3d863eacee0ca89cce007)`(self)` | 
`public def `[`analyses_classes`](#classexot_1_1channel_1_1__base_1_1Channel_1af782e78dd482fb7acf71e4ab1767aa30)`(self)` | 
`public def `[`bootstrap_analyses`](#classexot_1_1channel_1_1__base_1_1Channel_1acf42b94228e5ac0548a7244245dff1ab)`(self)` | 
`public def `[`bootstrap_analysis`](#classexot_1_1channel_1_1__base_1_1Channel_1a2e54abf773666ba4918432dd32c5375f)`(self,str analysis_name)` | 

## Members

#### `public object `[`parent`](#classexot_1_1channel_1_1__base_1_1Channel_1a06d7ab65738edda85fca65071b256753)`(self)` {#classexot_1_1channel_1_1__base_1_1Channel_1a06d7ab65738edda85fca65071b256753}

#### `public def `[`parent`](#classexot_1_1channel_1_1__base_1_1Channel_1a5ffbb982641123323bca88eb064edb96)`(self,value)` {#classexot_1_1channel_1_1__base_1_1Channel_1a5ffbb982641123323bca88eb064edb96}

#### `public def `[`hasparent`](#classexot_1_1channel_1_1__base_1_1Channel_1a3417f4b317b467d97dae156aecca5df2)`(self)` {#classexot_1_1channel_1_1__base_1_1Channel_1a3417f4b317b467d97dae156aecca5df2}

#### `public def `[`analyses`](#classexot_1_1channel_1_1__base_1_1Channel_1a91881294cad3d863eacee0ca89cce007)`(self)` {#classexot_1_1channel_1_1__base_1_1Channel_1a91881294cad3d863eacee0ca89cce007}

#### `public def `[`analyses_classes`](#classexot_1_1channel_1_1__base_1_1Channel_1af782e78dd482fb7acf71e4ab1767aa30)`(self)` {#classexot_1_1channel_1_1__base_1_1Channel_1af782e78dd482fb7acf71e4ab1767aa30}

#### `public def `[`bootstrap_analyses`](#classexot_1_1channel_1_1__base_1_1Channel_1acf42b94228e5ac0548a7244245dff1ab)`(self)` {#classexot_1_1channel_1_1__base_1_1Channel_1acf42b94228e5ac0548a7244245dff1ab}

#### `public def `[`bootstrap_analysis`](#classexot_1_1channel_1_1__base_1_1Channel_1a2e54abf773666ba4918432dd32c5375f)`(self,str analysis_name)` {#classexot_1_1channel_1_1__base_1_1Channel_1a2e54abf773666ba4918432dd32c5375f}

# class `exot::channel::_base::ChannelFactory` {#classexot_1_1channel_1_1__base_1_1ChannelFactory}

```
class exot::channel::_base::ChannelFactory
  : public GenericFactory
  : public klass
  : public exot.channel._base.Channel
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::channel::covertchannels` {#namespaceexot_1_1channel_1_1covertchannels}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::covertchannels::CacheCC`](#classexot_1_1channel_1_1covertchannels_1_1CacheCC) | 
`class `[`exot::channel::covertchannels::ConservativeGovernorCC`](#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC) | 
`class `[`exot::channel::covertchannels::CovertChannel`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel) | 
`class `[`exot::channel::covertchannels::FlushFlushCC`](#classexot_1_1channel_1_1covertchannels_1_1FlushFlushCC) | 
`class `[`exot::channel::covertchannels::FlushPrefetchCC`](#classexot_1_1channel_1_1covertchannels_1_1FlushPrefetchCC) | 
`class `[`exot::channel::covertchannels::FlushReloadCC`](#classexot_1_1channel_1_1covertchannels_1_1FlushReloadCC) | 
`class `[`exot::channel::covertchannels::FrequencyCC`](#classexot_1_1channel_1_1covertchannels_1_1FrequencyCC) | 
`class `[`exot::channel::covertchannels::PowerCC`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC) | 
`class `[`exot::channel::covertchannels::ThermalCC`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC) | 

# class `exot::channel::covertchannels::CacheCC` {#classexot_1_1channel_1_1covertchannels_1_1CacheCC}

```
class exot::channel::covertchannels::CacheCC
  : public exot.channel.covertchannels.CovertChannel
  : public exot.channel.mixins.covertchannel.PerformanceSweep
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1a75031929769c9b53b69925c59943c83c)`(self)` | 0 -> Keep data in cache (low access time)
`public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1a7fc1ceb3abe47ea17fed507196065799)`(self)` | 
`public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1aedf1b8ce8bcdadfa1046bddea92dc689)`(self)` | 

## Members

#### `public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1a75031929769c9b53b69925c59943c83c)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1a75031929769c9b53b69925c59943c83c}

0 -> Keep data in cache (low access time)
1 -> Remove data from cache (high access time)

#### `public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1a7fc1ceb3abe47ea17fed507196065799)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1a7fc1ceb3abe47ea17fed507196065799}

#### `public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1aedf1b8ce8bcdadfa1046bddea92dc689)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CacheCC_1aedf1b8ce8bcdadfa1046bddea92dc689}

# class `exot::channel::covertchannels::ConservativeGovernorCC` {#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC}

```
class exot::channel::covertchannels::ConservativeGovernorCC
  : public exot.channel.covertchannels.FrequencyCC
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a80fc34dbf637d531c6f7dc01c0fb89a2)`(self)` | -X -> Decrease frequency by X levels (if possible)
`public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a8ba811b7d1406f5aad6c4d8b9215f76a)`(self)` | 
`public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a1fe848eba1f94800884e32c82e955b9a)`(self)` | 

## Members

#### `public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a80fc34dbf637d531c6f7dc01c0fb89a2)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a80fc34dbf637d531c6f7dc01c0fb89a2}

-X -> Decrease frequency by X levels (if possible)
 X -> Increase frequency by X levels (if possible)

#### `public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a8ba811b7d1406f5aad6c4d8b9215f76a)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a8ba811b7d1406f5aad6c4d8b9215f76a}

#### `public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a1fe848eba1f94800884e32c82e955b9a)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1ConservativeGovernorCC_1a1fe848eba1f94800884e32c82e955b9a}

# class `exot::channel::covertchannels::CovertChannel` {#classexot_1_1channel_1_1covertchannels_1_1CovertChannel}

```
class exot::channel::covertchannels::CovertChannel
  : public exot.channel._base.Channel
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1a0a214bee954543c6314c75c20f90b96e)`(self)` | 
`public int `[`max_num_symbols`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1a4d859910d62b7a77bcb2a4bfaa2b5d48)`(self)` | 
`public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afa31ff03d5070f7a07b16aefdcb8187d)`(self)` | 
`public t.List `[`symbols`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afaa7d892a9f3db0bd284900f65d05028)`(self)` | 
`public str `[`__repr__`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afb843d86435e66e7b5ce2cb75f06898e)`(self)` | 

## Members

#### `public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1a0a214bee954543c6314c75c20f90b96e)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1a0a214bee954543c6314c75c20f90b96e}

#### `public int `[`max_num_symbols`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1a4d859910d62b7a77bcb2a4bfaa2b5d48)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1a4d859910d62b7a77bcb2a4bfaa2b5d48}

#### `public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afa31ff03d5070f7a07b16aefdcb8187d)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afa31ff03d5070f7a07b16aefdcb8187d}

#### `public t.List `[`symbols`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afaa7d892a9f3db0bd284900f65d05028)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afaa7d892a9f3db0bd284900f65d05028}

#### `public str `[`__repr__`](#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afb843d86435e66e7b5ce2cb75f06898e)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1CovertChannel_1afb843d86435e66e7b5ce2cb75f06898e}

# class `exot::channel::covertchannels::FlushFlushCC` {#classexot_1_1channel_1_1covertchannels_1_1FlushFlushCC}

```
class exot::channel::covertchannels::FlushFlushCC
  : public exot.channel.covertchannels.CacheCC
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::covertchannels::FlushPrefetchCC` {#classexot_1_1channel_1_1covertchannels_1_1FlushPrefetchCC}

```
class exot::channel::covertchannels::FlushPrefetchCC
  : public exot.channel.covertchannels.CacheCC
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::covertchannels::FlushReloadCC` {#classexot_1_1channel_1_1covertchannels_1_1FlushReloadCC}

```
class exot::channel::covertchannels::FlushReloadCC
  : public exot.channel.covertchannels.CacheCC
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::covertchannels::FrequencyCC` {#classexot_1_1channel_1_1covertchannels_1_1FrequencyCC}

```
class exot::channel::covertchannels::FrequencyCC
  : public exot.channel.covertchannels.CovertChannel
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::covertchannels::PowerCC` {#classexot_1_1channel_1_1covertchannels_1_1PowerCC}

```
class exot::channel::covertchannels::PowerCC
  : public exot.channel.covertchannels.CovertChannel
  : public exot.channel.mixins.covertchannel.CapacityContinuous
  : public exot.channel.mixins.covertchannel.PerformanceSweep
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public np.array `[`inputs`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1af033b5691f47c9dba76a1ec851c999f2)`(self)` | 0  -> Do not utilise core (cool down)
`public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1a6548297b9b1941e554c2e894cccf16b1)`(self)` | 0 -> Do not utilise core (low power consumption)
`public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1abf4c88418a9a3ca9b29ba347fed79552)`(self)` | 
`public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1aec7af97e77c4a977592e5a2d7d4a6c3e)`(self)` | 

## Members

#### `public np.array `[`inputs`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1af033b5691f47c9dba76a1ec851c999f2)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1af033b5691f47c9dba76a1ec851c999f2}

0  -> Do not utilise core (cool down)
n  -> Utilise n cores

#### `public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1a6548297b9b1941e554c2e894cccf16b1)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1a6548297b9b1941e554c2e894cccf16b1}

0 -> Do not utilise core (low power consumption)
1 -> Utilise core (high power consumption)

#### `public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1abf4c88418a9a3ca9b29ba347fed79552)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1abf4c88418a9a3ca9b29ba347fed79552}

#### `public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1aec7af97e77c4a977592e5a2d7d4a6c3e)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1PowerCC_1aec7af97e77c4a977592e5a2d7d4a6c3e}

# class `exot::channel::covertchannels::ThermalCC` {#classexot_1_1channel_1_1covertchannels_1_1ThermalCC}

```
class exot::channel::covertchannels::ThermalCC
  : public exot.channel.covertchannels.CovertChannel
  : public exot.channel.mixins.covertchannel.PerformanceSweep
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public np.array `[`inputs`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1a7ef1884d59d9194380af413d2e9d0a40)`(self)` | 0  -> Do not utilise core (cool down)
`public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1aaf04651add271fc306164c73732a9396)`(self)` | 
`public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1a845af2890907c0c6d6d951f68b03d743)`(self)` | 
`public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1ab403fca9f4de829d6b299a856130667e)`(self)` | 

## Members

#### `public np.array `[`inputs`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1a7ef1884d59d9194380af413d2e9d0a40)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1a7ef1884d59d9194380af413d2e9d0a40}

0  -> Do not utilise core (cool down)
-1 -> Fully utilise all cores (heat up)

#### `public t.Mapping `[`signal`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1aaf04651add271fc306164c73732a9396)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1aaf04651add271fc306164c73732a9396}

#### `public bool `[`fixed_length_symbols`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1a845af2890907c0c6d6d951f68b03d743)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1a845af2890907c0c6d6d951f68b03d743}

#### `public def `[`analyses_classes`](#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1ab403fca9f4de829d6b299a856130667e)`(self)` {#classexot_1_1channel_1_1covertchannels_1_1ThermalCC_1ab403fca9f4de829d6b299a856130667e}

# namespace `exot::channel::mixins::covertchannel` {#namespaceexot_1_1channel_1_1mixins_1_1covertchannel}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::mixins::covertchannel::CapacityContinuous`](#classexot_1_1channel_1_1mixins_1_1covertchannel_1_1CapacityContinuous) | Handler to perform the capacity calculation for a continuous (covert) channel.
`class `[`exot::channel::mixins::covertchannel::PerformanceSweep`](#classexot_1_1channel_1_1mixins_1_1covertchannel_1_1PerformanceSweep) | 

# class `exot::channel::mixins::covertchannel::CapacityContinuous` {#classexot_1_1channel_1_1mixins_1_1covertchannel_1_1CapacityContinuous}

```
class exot::channel::mixins::covertchannel::CapacityContinuous
  : public metaclass
  : public ABCMeta
```  

Handler to perform the capacity calculation for a continuous (covert) channel.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::mixins::covertchannel::PerformanceSweep` {#classexot_1_1channel_1_1mixins_1_1covertchannel_1_1PerformanceSweep}

```
class exot::channel::mixins::covertchannel::PerformanceSweep
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::channel::mixins::mldataset` {#namespaceexot_1_1channel_1_1mixins_1_1mldataset}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::mixins::mldataset::DatasetType`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1DatasetType) | Stream types
`class `[`exot::channel::mixins::mldataset::GenericDataSetHandler`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler) | 
`class `[`exot::channel::mixins::mldataset::TestSampleLen`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen) | 
`class `[`exot::channel::mixins::mldataset::TestWeights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights) | 
`class `[`exot::channel::mixins::mldataset::TestX`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX) | 
`class `[`exot::channel::mixins::mldataset::TestY`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY) | 
`class `[`exot::channel::mixins::mldataset::TrainSampleLen`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen) | 
`class `[`exot::channel::mixins::mldataset::TrainWeights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights) | 
`class `[`exot::channel::mixins::mldataset::TrainX`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX) | 
`class `[`exot::channel::mixins::mldataset::TrainY`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY) | 
`class `[`exot::channel::mixins::mldataset::VerifSampleLen`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen) | 
`class `[`exot::channel::mixins::mldataset::VerifX`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX) | 
`class `[`exot::channel::mixins::mldataset::VerifY`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY) | 

# class `exot::channel::mixins::mldataset::DatasetType` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1DatasetType}

```
class exot::channel::mixins::mldataset::DatasetType
  : public IntEnum
```  

Stream types

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::mixins::mldataset::GenericDataSetHandler` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler}

```
class exot::channel::mixins::mldataset::GenericDataSetHandler
  : public Pickleable
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`train_set`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afa33878cd515b81d283af9047a8c326a)`(self)` | 
`public def `[`test_set`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a29e32ce061afadc4d13918d85ec3926c)`(self)` | 
`public def `[`verification_set`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ada8d35397c0b82d782042c12647859cb)`(self)` | 
`public None `[`remove_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ac53c5f8e1f0dfe0ebe439caf7c799d77)`(self)` | Serialise a Dataset
`public None `[`write_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a062bc697b1c481792e9f6e5d884bebb0)`(self)` | Serialise a Dataset
`public None `[`read_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a82bad0486996d9d2bf23d6e0c802f8d0)`(self)` | Deserialise a Dataset
`public Path `[`path_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ab30634d580d62a19e93dffb39a9ab532)`(self)` | 
`public def `[`batch_size`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afcbe1f21dba6a7ebc5fd82d1ffc17712)`(self)` | 
`public def `[`batch_size`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a17278577a074efef2efa6672a9e6e710)`(self,value)` | 
`public def `[`num_feature_dims`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afed3fde89b0447e5d310d29572ed2d00)`(self)` | 
`public def `[`num_feature_dims`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a4831c8dde5be89694ededa44dcb55550)`(self,value)` | 
`public def `[`num_train_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a287407cc63b924b7b2d0c2140d314f4b)`(self)` | 
`public def `[`num_train_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ae1318ca156892383e7fecf4dd831c67c)`(self,int value)` | 
`public def `[`num_test_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1aecbd60442444ad20f5ef134a292dad08)`(self)` | 
`public def `[`num_test_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a219725fec3d4f3a66788d24714221e5d)`(self,int value)` | 
`public def `[`num_verif_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a274fbf2aac9f25e8efc15a591ae2dab5)`(self)` | 
`public def `[`num_verif_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a5c8890bd0b91948460c9cb7c57fd2f8c)`(self,int value)` | 
`public dict `[`dataset_parameters_to_dict`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1aa73504049fa6c9eb42ecc75ed04c954c)`(self)` | 
`public None `[`dataset_parameters_from_dict`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ae8ff5ab8c2a3c659ad4a02b9388eee16)`(self,dict param_dict)` | 

## Members

#### `public def `[`train_set`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afa33878cd515b81d283af9047a8c326a)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afa33878cd515b81d283af9047a8c326a}

#### `public def `[`test_set`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a29e32ce061afadc4d13918d85ec3926c)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a29e32ce061afadc4d13918d85ec3926c}

#### `public def `[`verification_set`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ada8d35397c0b82d782042c12647859cb)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ada8d35397c0b82d782042c12647859cb}

#### `public None `[`remove_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ac53c5f8e1f0dfe0ebe439caf7c799d77)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ac53c5f8e1f0dfe0ebe439caf7c799d77}

Serialise a Dataset

#### `public None `[`write_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a062bc697b1c481792e9f6e5d884bebb0)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a062bc697b1c481792e9f6e5d884bebb0}

Serialise a Dataset

#### `public None `[`read_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a82bad0486996d9d2bf23d6e0c802f8d0)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a82bad0486996d9d2bf23d6e0c802f8d0}

Deserialise a Dataset

#### `public Path `[`path_dataset`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ab30634d580d62a19e93dffb39a9ab532)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ab30634d580d62a19e93dffb39a9ab532}

#### `public def `[`batch_size`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afcbe1f21dba6a7ebc5fd82d1ffc17712)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afcbe1f21dba6a7ebc5fd82d1ffc17712}

#### `public def `[`batch_size`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a17278577a074efef2efa6672a9e6e710)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a17278577a074efef2efa6672a9e6e710}

#### `public def `[`num_feature_dims`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afed3fde89b0447e5d310d29572ed2d00)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1afed3fde89b0447e5d310d29572ed2d00}

#### `public def `[`num_feature_dims`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a4831c8dde5be89694ededa44dcb55550)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a4831c8dde5be89694ededa44dcb55550}

#### `public def `[`num_train_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a287407cc63b924b7b2d0c2140d314f4b)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a287407cc63b924b7b2d0c2140d314f4b}

#### `public def `[`num_train_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ae1318ca156892383e7fecf4dd831c67c)`(self,int value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ae1318ca156892383e7fecf4dd831c67c}

#### `public def `[`num_test_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1aecbd60442444ad20f5ef134a292dad08)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1aecbd60442444ad20f5ef134a292dad08}

#### `public def `[`num_test_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a219725fec3d4f3a66788d24714221e5d)`(self,int value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a219725fec3d4f3a66788d24714221e5d}

#### `public def `[`num_verif_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a274fbf2aac9f25e8efc15a591ae2dab5)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a274fbf2aac9f25e8efc15a591ae2dab5}

#### `public def `[`num_verif_batches`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a5c8890bd0b91948460c9cb7c57fd2f8c)`(self,int value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1a5c8890bd0b91948460c9cb7c57fd2f8c}

#### `public dict `[`dataset_parameters_to_dict`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1aa73504049fa6c9eb42ecc75ed04c954c)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1aa73504049fa6c9eb42ecc75ed04c954c}

#### `public None `[`dataset_parameters_from_dict`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ae8ff5ab8c2a3c659ad4a02b9388eee16)`(self,dict param_dict)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1GenericDataSetHandler_1ae8ff5ab8c2a3c659ad4a02b9388eee16}

# class `exot::channel::mixins::mldataset::TestSampleLen` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen}

```
class exot::channel::mixins::mldataset::TestSampleLen
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`test_actual_batch_len_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a1df9890c1e904f2e8a4b9e7c3ffca944)`(self)` | 
`public def `[`test_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a795eb145b648cadea65477aa94525a5e)`(self)` | 
`public def `[`test_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a715fe5622ab4fc473fed13602a9b437b)`(self,value)` | 

## Members

#### `public def `[`test_actual_batch_len_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a1df9890c1e904f2e8a4b9e7c3ffca944)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a1df9890c1e904f2e8a4b9e7c3ffca944}

#### `public def `[`test_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a795eb145b648cadea65477aa94525a5e)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a795eb145b648cadea65477aa94525a5e}

#### `public def `[`test_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a715fe5622ab4fc473fed13602a9b437b)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestSampleLen_1a715fe5622ab4fc473fed13602a9b437b}

# class `exot::channel::mixins::mldataset::TestWeights` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights}

```
class exot::channel::mixins::mldataset::TestWeights
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`test_weights_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1af74f515e725432a0a0debab4d545128f)`(self)` | 
`public def `[`test_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1a9a8187b1385dafd13cae9134791171fc)`(self)` | 
`public def `[`test_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1a73a8c57fdc9496262c22b230b5c984f7)`(self,value)` | 

## Members

#### `public def `[`test_weights_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1af74f515e725432a0a0debab4d545128f)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1af74f515e725432a0a0debab4d545128f}

#### `public def `[`test_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1a9a8187b1385dafd13cae9134791171fc)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1a9a8187b1385dafd13cae9134791171fc}

#### `public def `[`test_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1a73a8c57fdc9496262c22b230b5c984f7)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestWeights_1a73a8c57fdc9496262c22b230b5c984f7}

# class `exot::channel::mixins::mldataset::TestX` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX}

```
class exot::channel::mixins::mldataset::TestX
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`test_X_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1af83f4c034fc84583a1f626eb95f244e2)`(self)` | 
`public def `[`test_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1ad1e59962b74fb06717dce241511eef93)`(self)` | 
`public def `[`test_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1af4a791dcd554f3bee02d2538b676eb45)`(self,value)` | 

## Members

#### `public def `[`test_X_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1af83f4c034fc84583a1f626eb95f244e2)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1af83f4c034fc84583a1f626eb95f244e2}

#### `public def `[`test_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1ad1e59962b74fb06717dce241511eef93)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1ad1e59962b74fb06717dce241511eef93}

#### `public def `[`test_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1af4a791dcd554f3bee02d2538b676eb45)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestX_1af4a791dcd554f3bee02d2538b676eb45}

# class `exot::channel::mixins::mldataset::TestY` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY}

```
class exot::channel::mixins::mldataset::TestY
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`test_Y_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1a464c6fae49774c80b84bca68db0d0aa1)`(self)` | 
`public def `[`test_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1a8173f010944195523d343f9dfc502b80)`(self)` | 
`public def `[`test_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1ac8b39d210df5b0044d71401c1c664554)`(self,value)` | 

## Members

#### `public def `[`test_Y_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1a464c6fae49774c80b84bca68db0d0aa1)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1a464c6fae49774c80b84bca68db0d0aa1}

#### `public def `[`test_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1a8173f010944195523d343f9dfc502b80)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1a8173f010944195523d343f9dfc502b80}

#### `public def `[`test_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1ac8b39d210df5b0044d71401c1c664554)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TestY_1ac8b39d210df5b0044d71401c1c664554}

# class `exot::channel::mixins::mldataset::TrainSampleLen` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen}

```
class exot::channel::mixins::mldataset::TrainSampleLen
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`train_actual_batch_len_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1a5538d881d97f22b5b496c7b831a724da)`(self)` | 
`public def `[`train_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1aec7ca858ec54ab6a18d3e462919fadd6)`(self)` | 
`public def `[`train_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1aab1cb4a22bc49646bd16f1f012a9515e)`(self,value)` | 

## Members

#### `public def `[`train_actual_batch_len_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1a5538d881d97f22b5b496c7b831a724da)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1a5538d881d97f22b5b496c7b831a724da}

#### `public def `[`train_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1aec7ca858ec54ab6a18d3e462919fadd6)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1aec7ca858ec54ab6a18d3e462919fadd6}

#### `public def `[`train_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1aab1cb4a22bc49646bd16f1f012a9515e)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainSampleLen_1aab1cb4a22bc49646bd16f1f012a9515e}

# class `exot::channel::mixins::mldataset::TrainWeights` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights}

```
class exot::channel::mixins::mldataset::TrainWeights
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`train_weights_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a3e4eb34d3c9128079e77ff9fd1656de9)`(self)` | 
`public def `[`train_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a8f0d547235e28929c685fe6dc99258cb)`(self)` | 
`public def `[`train_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a5c4ddc72d030b5fa859dc2e663947e7e)`(self,value)` | 

## Members

#### `public def `[`train_weights_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a3e4eb34d3c9128079e77ff9fd1656de9)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a3e4eb34d3c9128079e77ff9fd1656de9}

#### `public def `[`train_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a8f0d547235e28929c685fe6dc99258cb)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a8f0d547235e28929c685fe6dc99258cb}

#### `public def `[`train_weights`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a5c4ddc72d030b5fa859dc2e663947e7e)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainWeights_1a5c4ddc72d030b5fa859dc2e663947e7e}

# class `exot::channel::mixins::mldataset::TrainX` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX}

```
class exot::channel::mixins::mldataset::TrainX
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`train_X_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1a7c601cf6074fd51416a0caf66efc42a2)`(self)` | 
`public def `[`train_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1aceec9283198d76538675691e907c2310)`(self)` | 
`public def `[`train_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1a276ca24ac78a9280c97af28059533c72)`(self,value)` | 

## Members

#### `public def `[`train_X_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1a7c601cf6074fd51416a0caf66efc42a2)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1a7c601cf6074fd51416a0caf66efc42a2}

#### `public def `[`train_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1aceec9283198d76538675691e907c2310)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1aceec9283198d76538675691e907c2310}

#### `public def `[`train_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1a276ca24ac78a9280c97af28059533c72)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainX_1a276ca24ac78a9280c97af28059533c72}

# class `exot::channel::mixins::mldataset::TrainY` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY}

```
class exot::channel::mixins::mldataset::TrainY
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`train_Y_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1a013238475e6d414fded62d0a62e731e1)`(self)` | 
`public def `[`train_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1a993cec7ceef16662fc0a4d583371251d)`(self)` | 
`public def `[`train_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1aad028ebd8ecc4a3462deadd1b1bace52)`(self,value)` | 

## Members

#### `public def `[`train_Y_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1a013238475e6d414fded62d0a62e731e1)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1a013238475e6d414fded62d0a62e731e1}

#### `public def `[`train_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1a993cec7ceef16662fc0a4d583371251d)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1a993cec7ceef16662fc0a4d583371251d}

#### `public def `[`train_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1aad028ebd8ecc4a3462deadd1b1bace52)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1TrainY_1aad028ebd8ecc4a3462deadd1b1bace52}

# class `exot::channel::mixins::mldataset::VerifSampleLen` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen}

```
class exot::channel::mixins::mldataset::VerifSampleLen
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`verif_actual_batch_len_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1ab5343059cd55e63682480b668e91fd74)`(self)` | 
`public def `[`verif_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1ad475642d43dac2c64bc2f8de9b5676dd)`(self)` | 
`public def `[`verif_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1a0514b1da34dafbf84db90ea1f7befe6c)`(self,value)` | 

## Members

#### `public def `[`verif_actual_batch_len_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1ab5343059cd55e63682480b668e91fd74)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1ab5343059cd55e63682480b668e91fd74}

#### `public def `[`verif_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1ad475642d43dac2c64bc2f8de9b5676dd)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1ad475642d43dac2c64bc2f8de9b5676dd}

#### `public def `[`verif_actual_batch_len`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1a0514b1da34dafbf84db90ea1f7befe6c)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifSampleLen_1a0514b1da34dafbf84db90ea1f7befe6c}

# class `exot::channel::mixins::mldataset::VerifX` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX}

```
class exot::channel::mixins::mldataset::VerifX
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`verif_X_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1a598b9328da4cf38c216c81b14cfe8a0f)`(self)` | 
`public def `[`verif_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1a210f9ba7768c42f90ac74e78d501b795)`(self)` | 
`public def `[`verif_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1ab5a8a0208f35373c8f00fddea49c5526)`(self,value)` | 

## Members

#### `public def `[`verif_X_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1a598b9328da4cf38c216c81b14cfe8a0f)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1a598b9328da4cf38c216c81b14cfe8a0f}

#### `public def `[`verif_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1a210f9ba7768c42f90ac74e78d501b795)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1a210f9ba7768c42f90ac74e78d501b795}

#### `public def `[`verif_X`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1ab5a8a0208f35373c8f00fddea49c5526)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifX_1ab5a8a0208f35373c8f00fddea49c5526}

# class `exot::channel::mixins::mldataset::VerifY` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY}

```
class exot::channel::mixins::mldataset::VerifY
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`verif_Y_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1a0d177024930af53c27642355890a04f6)`(self)` | 
`public def `[`verif_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1ac0c74d6873b1acb11328ecc41589b540)`(self)` | 
`public def `[`verif_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1a2de8a3abd2d59c474866595f445139fe)`(self,value)` | 

## Members

#### `public def `[`verif_Y_shape`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1a0d177024930af53c27642355890a04f6)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1a0d177024930af53c27642355890a04f6}

#### `public def `[`verif_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1ac0c74d6873b1acb11328ecc41589b540)`(self)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1ac0c74d6873b1acb11328ecc41589b540}

#### `public def `[`verif_Y`](#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1a2de8a3abd2d59c474866595f445139fe)`(self,value)` {#classexot_1_1channel_1_1mixins_1_1mldataset_1_1VerifY_1a2de8a3abd2d59c474866595f445139fe}

# namespace `exot::channel::rnndecoder::_base` {#namespaceexot_1_1channel_1_1rnndecoder_1_1__base}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::rnndecoder::_base::RNNdecoder`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder) | 

# class `exot::channel::rnndecoder::_base::RNNdecoder` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder}

```
class exot::channel::rnndecoder::_base::RNNdecoder
  : public exot.channel._base.Analysis
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`label_length`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a78df2976d351607f7381640b4266c927) | 
`public def `[`__init__`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a07d00bc90dbc599a7194b193bf9790cd)`(self,* args,** kwargs)` | 
`public def `[`model_files`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a9e86d32d513aaa9b55625bdb7507e062)`(self)` | 
`public None `[`model_files`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a90f70ea97b7a1c404bbbaf403f30cdcf)`(self,str value)` | 
`public def `[`batch_size`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1abe774138d12cab17a63783404b2692c7)`(self)` | 
`public def `[`phases`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a39cf938b599d8b23720ce2f45f813755)`(self)` | 
`public def `[`env`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1ac0e7dcb9e5238f518c21f17979940f98)`(self)` | 
`public def `[`max_len_samples`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a5f6339c5305e5b4b100911a3a405511d)`(self)` | 
`public Path `[`path`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1aad7eda76ee5815e8f921ae69297562e4)`(self)` | 
`public def `[`ctc_cost_tensorflow`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a8b2dcd29c0a5fddfdd798571e2ca9160)`(y_true,y_pred)` | 
`public def `[`read_data`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a837d3c9e8b1dd47ce0bd36394b881767)`()` | 
`public def `[`read`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a356261e732582550633c530d7d927301)`(self)` | 
`public def `[`write`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a87fcc828ea05494acd2daed484e73237)`(self)` | 

## Members

#### `public  `[`label_length`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a78df2976d351607f7381640b4266c927) {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a78df2976d351607f7381640b4266c927}

#### `public def `[`__init__`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a07d00bc90dbc599a7194b193bf9790cd)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a07d00bc90dbc599a7194b193bf9790cd}

#### `public def `[`model_files`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a9e86d32d513aaa9b55625bdb7507e062)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a9e86d32d513aaa9b55625bdb7507e062}

#### `public None `[`model_files`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a90f70ea97b7a1c404bbbaf403f30cdcf)`(self,str value)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a90f70ea97b7a1c404bbbaf403f30cdcf}

#### `public def `[`batch_size`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1abe774138d12cab17a63783404b2692c7)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1abe774138d12cab17a63783404b2692c7}

#### `public def `[`phases`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a39cf938b599d8b23720ce2f45f813755)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a39cf938b599d8b23720ce2f45f813755}

#### `public def `[`env`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1ac0e7dcb9e5238f518c21f17979940f98)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1ac0e7dcb9e5238f518c21f17979940f98}

#### `public def `[`max_len_samples`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a5f6339c5305e5b4b100911a3a405511d)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a5f6339c5305e5b4b100911a3a405511d}

#### `public Path `[`path`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1aad7eda76ee5815e8f921ae69297562e4)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1aad7eda76ee5815e8f921ae69297562e4}

#### `public def `[`ctc_cost_tensorflow`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a8b2dcd29c0a5fddfdd798571e2ca9160)`(y_true,y_pred)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a8b2dcd29c0a5fddfdd798571e2ca9160}

#### `public def `[`read_data`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a837d3c9e8b1dd47ce0bd36394b881767)`()` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a837d3c9e8b1dd47ce0bd36394b881767}

#### `public def `[`read`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a356261e732582550633c530d7d927301)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a356261e732582550633c530d7d927301}

#### `public def `[`write`](#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a87fcc828ea05494acd2daed484e73237)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1__base_1_1RNNdecoder_1a87fcc828ea05494acd2daed484e73237}

# namespace `exot::channel::rnndecoder::_mixins` {#namespaceexot_1_1channel_1_1rnndecoder_1_1__mixins}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`cut_minibatch`](#rnndecoder_2__mixins_8py_1a54daae2cfd8c1495311b5c18cc09a920)`(label,freqv,minibatch_length)`            | Cut minibatches to equal length.
`public def `[`tf_count`](#rnndecoder_2__mixins_8py_1afa5a438c26c47244fb320589d2fbf94d)`(t,val)`            | Count how many values in a tensor a equal to a value val.
`public def `[`stdr`](#rnndecoder_2__mixins_8py_1a3bfed8779dfb458057b877eff1f5ab46)`(dataseq)`            | Make data zero mean and with unit standard deviation.
`public def `[`stdr_val`](#rnndecoder_2__mixins_8py_1af843d0a0dd9dd3c9b51ec7895afb3491)`(val_freqv,mean,std)`            | Make data zero mean and with unit variance with given mean and standard deviation.
`public def `[`separate_val`](#rnndecoder_2__mixins_8py_1a306e9010cc7226f28a666dec12d1fdc6)`(freqv,label)`            | Separate the training and the validation dataset

## Members

#### `public def `[`cut_minibatch`](#rnndecoder_2__mixins_8py_1a54daae2cfd8c1495311b5c18cc09a920)`(label,freqv,minibatch_length)` {#rnndecoder_2__mixins_8py_1a54daae2cfd8c1495311b5c18cc09a920}

Cut minibatches to equal length.

#### `public def `[`tf_count`](#rnndecoder_2__mixins_8py_1afa5a438c26c47244fb320589d2fbf94d)`(t,val)` {#rnndecoder_2__mixins_8py_1afa5a438c26c47244fb320589d2fbf94d}

Count how many values in a tensor a equal to a value val.

#### `public def `[`stdr`](#rnndecoder_2__mixins_8py_1a3bfed8779dfb458057b877eff1f5ab46)`(dataseq)` {#rnndecoder_2__mixins_8py_1a3bfed8779dfb458057b877eff1f5ab46}

Make data zero mean and with unit standard deviation.

#### `public def `[`stdr_val`](#rnndecoder_2__mixins_8py_1af843d0a0dd9dd3c9b51ec7895afb3491)`(val_freqv,mean,std)` {#rnndecoder_2__mixins_8py_1af843d0a0dd9dd3c9b51ec7895afb3491}

Make data zero mean and with unit variance with given mean and standard deviation.

#### `public def `[`separate_val`](#rnndecoder_2__mixins_8py_1a306e9010cc7226f28a666dec12d1fdc6)`(freqv,label)` {#rnndecoder_2__mixins_8py_1a306e9010cc7226f28a666dec12d1fdc6}

Separate the training and the validation dataset

# namespace `exot::channel::rnndecoder::evaluate` {#namespaceexot_1_1channel_1_1rnndecoder_1_1evaluate}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::rnndecoder::evaluate::RNNdecoderEval`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval) | 

# class `exot::channel::rnndecoder::evaluate::RNNdecoderEval` {#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval}

```
class exot::channel::rnndecoder::evaluate::RNNdecoderEval
  : public RNNdecoder
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`label_len`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1af66148bd188a80d719adba944b8deda3) | 
`public def `[`__init__`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1ad6acf131768e5270fb78fae77d9d4e51)`(self,* args,** kwargs)` | 
`public Path `[`path`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1abcb8ede3bd9c94775b425b75cc4ab45b)`(self)` | 
`public def `[`read`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1a3eda8da149ffe424e53e5a2dd07d8582)`(self)` | 
`public def `[`write`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1a7fc80263217a0f50456d998c2bda871b)`(self)` | 

## Members

#### `public  `[`label_len`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1af66148bd188a80d719adba944b8deda3) {#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1af66148bd188a80d719adba944b8deda3}

#### `public def `[`__init__`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1ad6acf131768e5270fb78fae77d9d4e51)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1ad6acf131768e5270fb78fae77d9d4e51}

#### `public Path `[`path`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1abcb8ede3bd9c94775b425b75cc4ab45b)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1abcb8ede3bd9c94775b425b75cc4ab45b}

#### `public def `[`read`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1a3eda8da149ffe424e53e5a2dd07d8582)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1a3eda8da149ffe424e53e5a2dd07d8582}

#### `public def `[`write`](#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1a7fc80263217a0f50456d998c2bda871b)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1evaluate_1_1RNNdecoderEval_1a7fc80263217a0f50456d998c2bda871b}

# namespace `exot::channel::rnndecoder::train` {#namespaceexot_1_1channel_1_1rnndecoder_1_1train}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::rnndecoder::train::RNNdecoderTrain`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain) | 

# class `exot::channel::rnndecoder::train::RNNdecoderTrain` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain}

```
class exot::channel::rnndecoder::train::RNNdecoderTrain
  : public RNNdecoder
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`label_len`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a6dc2c0aa22eb6aaed041f1515b79d6f2) | Continue model training
`public def `[`__init__`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a1edab56c03c157a53b6d2c17f6f18889)`(self,* args,** kwargs)` | 
`public def `[`n_epochs_0`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a2af928df93650304f81f172eba8984bd)`(self)` | 
`public def `[`n_epochs_1`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a91dc4f89f4024de451122d640474bf41)`(self)` | 
`public def `[`start_epoch`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aaac1507852bb3aaa485b9cb6a28b5872)`(self)` | 
`public None `[`start_epoch`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1af822d2b668677e5dd6429fb6f245e168)`(self,int value)` | 
`public def `[`debug_step`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1accce10c050cea56146ccb472271a1002)`(self)` | 
`public def `[`early_stopping_threshold`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a788f7fc9bde8c565be5d7dc1893d5ea7)`(self)` | 
`public def `[`max_grad_norm`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a67fbce63aecee871a9f38e0c9df0cc43)`(self)` | 
`public def `[`p_dropout`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a76b8813174751971f4be48a9b16f70ef)`(self)` | 
`public def `[`p_keep`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a6f62eaebaddb1afe84fa39dab253cfc9)`(self)` | 
`public def `[`num_layers`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1adcd7a47a7c9ce0ccf5580354250c1627)`(self)` | 
`public def `[`num_hidden`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aa4d9a247aaf07241327182919c2f1409)`(self)` | 
`public def `[`learning_rate_0`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a34f6d283dbd1465d0bb78fe86e9f5221)`(self)` | 
`public def `[`learning_rate_1`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aa1c64f20e03bc7d44a5a14e01bc07d51)`(self)` | 
`public def `[`decay`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1ab6f382b59d96f74e6c54e4b2715fb5bf)`(self)` | 
`public def `[`max_timesteps`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1ae42e44efdc25583d19df1f47dfa9eaab)`(self)` | 
`public Path `[`path`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a08e0392b82929758284b238166394791)`(self)` | 
`public def `[`read`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1af26cc02f591d7c8516357479c56e550c)`(self)` | 
`public def `[`write`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a0e9ce8fb6ab0e1beed24616ce53108f5)`(self)` | 

## Members

#### `public  `[`label_len`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a6dc2c0aa22eb6aaed041f1515b79d6f2) {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a6dc2c0aa22eb6aaed041f1515b79d6f2}

Continue model training

#### `public def `[`__init__`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a1edab56c03c157a53b6d2c17f6f18889)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a1edab56c03c157a53b6d2c17f6f18889}

#### `public def `[`n_epochs_0`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a2af928df93650304f81f172eba8984bd)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a2af928df93650304f81f172eba8984bd}

#### `public def `[`n_epochs_1`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a91dc4f89f4024de451122d640474bf41)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a91dc4f89f4024de451122d640474bf41}

#### `public def `[`start_epoch`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aaac1507852bb3aaa485b9cb6a28b5872)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aaac1507852bb3aaa485b9cb6a28b5872}

#### `public None `[`start_epoch`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1af822d2b668677e5dd6429fb6f245e168)`(self,int value)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1af822d2b668677e5dd6429fb6f245e168}

#### `public def `[`debug_step`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1accce10c050cea56146ccb472271a1002)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1accce10c050cea56146ccb472271a1002}

#### `public def `[`early_stopping_threshold`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a788f7fc9bde8c565be5d7dc1893d5ea7)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a788f7fc9bde8c565be5d7dc1893d5ea7}

#### `public def `[`max_grad_norm`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a67fbce63aecee871a9f38e0c9df0cc43)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a67fbce63aecee871a9f38e0c9df0cc43}

#### `public def `[`p_dropout`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a76b8813174751971f4be48a9b16f70ef)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a76b8813174751971f4be48a9b16f70ef}

#### `public def `[`p_keep`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a6f62eaebaddb1afe84fa39dab253cfc9)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a6f62eaebaddb1afe84fa39dab253cfc9}

#### `public def `[`num_layers`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1adcd7a47a7c9ce0ccf5580354250c1627)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1adcd7a47a7c9ce0ccf5580354250c1627}

#### `public def `[`num_hidden`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aa4d9a247aaf07241327182919c2f1409)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aa4d9a247aaf07241327182919c2f1409}

#### `public def `[`learning_rate_0`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a34f6d283dbd1465d0bb78fe86e9f5221)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a34f6d283dbd1465d0bb78fe86e9f5221}

#### `public def `[`learning_rate_1`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aa1c64f20e03bc7d44a5a14e01bc07d51)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1aa1c64f20e03bc7d44a5a14e01bc07d51}

#### `public def `[`decay`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1ab6f382b59d96f74e6c54e4b2715fb5bf)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1ab6f382b59d96f74e6c54e4b2715fb5bf}

#### `public def `[`max_timesteps`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1ae42e44efdc25583d19df1f47dfa9eaab)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1ae42e44efdc25583d19df1f47dfa9eaab}

#### `public Path `[`path`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a08e0392b82929758284b238166394791)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a08e0392b82929758284b238166394791}

#### `public def `[`read`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1af26cc02f591d7c8516357479c56e550c)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1af26cc02f591d7c8516357479c56e550c}

#### `public def `[`write`](#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a0e9ce8fb6ab0e1beed24616ce53108f5)`(self)` {#classexot_1_1channel_1_1rnndecoder_1_1train_1_1RNNdecoderTrain_1a0e9ce8fb6ab0e1beed24616ce53108f5}

# namespace `exot::channel::sidechannels` {#namespaceexot_1_1channel_1_1sidechannels}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::sidechannels::SideChannel`](#classexot_1_1channel_1_1sidechannels_1_1SideChannel) | 
`class `[`exot::channel::sidechannels::ThermalSC`](#classexot_1_1channel_1_1sidechannels_1_1ThermalSC) | 

# class `exot::channel::sidechannels::SideChannel` {#classexot_1_1channel_1_1sidechannels_1_1SideChannel}

```
class exot::channel::sidechannels::SideChannel
  : public exot.channel._base.Channel
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::sidechannels::ThermalSC` {#classexot_1_1channel_1_1sidechannels_1_1ThermalSC}

```
class exot::channel::sidechannels::ThermalSC
  : public exot.channel.sidechannels.SideChannel
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`analyses_classes`](#classexot_1_1channel_1_1sidechannels_1_1ThermalSC_1a6e33290fa96c616508df0d9d820fc7ad)`(self)` | 

## Members

#### `public def `[`analyses_classes`](#classexot_1_1channel_1_1sidechannels_1_1ThermalSC_1a6e33290fa96c616508df0d9d820fc7ad)`(self)` {#classexot_1_1channel_1_1sidechannels_1_1ThermalSC_1a6e33290fa96c616508df0d9d820fc7ad}

# namespace `exot::channel::thermalsc::_mixins` {#namespaceexot_1_1channel_1_1thermalsc_1_1__mixins}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::thermalsc::_mixins::ThermalAppDecectionDataSetHandler`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler) | 

# class `exot::channel::thermalsc::_mixins::ThermalAppDecectionDataSetHandler` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler}

```
class exot::channel::thermalsc::_mixins::ThermalAppDecectionDataSetHandler
  : public exot.channel.mixins.mldataset.GenericDataSetHandler
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public dict `[`dataset_parameters_to_dict`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a6f161a8cf909cd25871b07e10e0f89d1)`(self)` | 
`public def `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a4de33b1bc55b3bf57096c8501323f664)`(self)` | 
`public None `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ac174c6373f609e97a1b43da5f0b55df9)`(self,bool value)` | 
`public def `[`num_feature_dims`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a8ecb76f1e6da53b3c44f24837792f321)`(self)` | 
`public def `[`num_feature_dims`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a2b4d5bdf447b2ba225653a4b4382b985)`(self,value)` | 
`public def `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a0d28493702b1c29bc2652fa1cd798279)`(self)` | 
`public def `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ac9962db0425a04d0c70475c4ce46a506)`(self,value)` | 
`public def `[`batch_size_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a99bb5be8c022bf8bd7e14b84f5a74af6)`(self)` | 
`public def `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ad1520f7def4b4058c13aa84fd3c745fb)`(self)` | 
`public None `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a3ec221a2266400e6798493ea411a1e8d)`(self,int value)` | 

## Members

#### `public dict `[`dataset_parameters_to_dict`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a6f161a8cf909cd25871b07e10e0f89d1)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a6f161a8cf909cd25871b07e10e0f89d1}

#### `public def `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a4de33b1bc55b3bf57096c8501323f664)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a4de33b1bc55b3bf57096c8501323f664}

#### `public None `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ac174c6373f609e97a1b43da5f0b55df9)`(self,bool value)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ac174c6373f609e97a1b43da5f0b55df9}

#### `public def `[`num_feature_dims`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a8ecb76f1e6da53b3c44f24837792f321)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a8ecb76f1e6da53b3c44f24837792f321}

#### `public def `[`num_feature_dims`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a2b4d5bdf447b2ba225653a4b4382b985)`(self,value)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a2b4d5bdf447b2ba225653a4b4382b985}

#### `public def `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a0d28493702b1c29bc2652fa1cd798279)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a0d28493702b1c29bc2652fa1cd798279}

#### `public def `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ac9962db0425a04d0c70475c4ce46a506)`(self,value)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ac9962db0425a04d0c70475c4ce46a506}

#### `public def `[`batch_size_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a99bb5be8c022bf8bd7e14b84f5a74af6)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a99bb5be8c022bf8bd7e14b84f5a74af6}

#### `public def `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ad1520f7def4b4058c13aa84fd3c745fb)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1ad1520f7def4b4058c13aa84fd3c745fb}

#### `public None `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a3ec221a2266400e6798493ea411a1e8d)`(self,int value)` {#classexot_1_1channel_1_1thermalsc_1_1__mixins_1_1ThermalAppDecectionDataSetHandler_1a3ec221a2266400e6798493ea411a1e8d}

# namespace `exot::channel::thermalsc::appdetection` {#namespaceexot_1_1channel_1_1thermalsc_1_1appdetection}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::thermalsc::appdetection::ADBiDiLSTM`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADBiDiLSTM) | 
`class `[`exot::channel::thermalsc::appdetection::ADCNNLSTM`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM) | 
`class `[`exot::channel::thermalsc::appdetection::ADConvLSTM`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADConvLSTM) | 
`class `[`exot::channel::thermalsc::appdetection::ADLSTM`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM) | 
`class `[`exot::channel::thermalsc::appdetection::AppDetection`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection) | 
`class `[`exot::channel::thermalsc::appdetection::AppDetector`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector) | 

# class `exot::channel::thermalsc::appdetection::ADBiDiLSTM` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADBiDiLSTM}

```
class exot::channel::thermalsc::appdetection::ADBiDiLSTM
  : public exot.channel.thermalsc.appdetection.AppDetector
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::thermalsc::appdetection::ADCNNLSTM` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM}

```
class exot::channel::thermalsc::appdetection::ADCNNLSTM
  : public exot.channel.thermalsc.appdetection.AppDetector
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`batch_sz`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a34b4378dfe3ca74585e96908fb6ea71a) | 
`public  `[`enc_units`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a1b286c54bc734465362da94d7d279e66) | 
`public  `[`num_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a0fab0aa8c95c7d7d94eef84d8c4cbafb) | 
`public  `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a875c3ebce7e2de200daf4e715c1f43d5) | 
`public  `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1aeeacc38bd86c4268705951c110d240fe) | 
`public  `[`num_cnn_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ab0de489349c46c49e4558ce8756c0963) | 
`public  `[`kernel_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ac7539bae61ce64958d5b63961f8508c8) | 
`public  `[`cnn`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a41473860e0b9e2259eb9c904a26bf149) | 
`public  `[`pooling`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a6ab7c1c98d88eda482b1ddcc308406bd) | 
`public  `[`lstm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1adb3f278b270c319724a46609b014951b) | 
`public  `[`dense`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a8e197599b1335971a2b9a0b0de4ee7b1) | 
`public def `[`oversampling_rate`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ae61a92b8fc408c7ac69ff810183fd0b8)`(self)` | 
`public def `[`call`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a4ebe3042ea07fc123427d6f9a57d2d6f)`(self,x,state)` | 

## Members

#### `public  `[`batch_sz`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a34b4378dfe3ca74585e96908fb6ea71a) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a34b4378dfe3ca74585e96908fb6ea71a}

#### `public  `[`enc_units`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a1b286c54bc734465362da94d7d279e66) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a1b286c54bc734465362da94d7d279e66}

#### `public  `[`num_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a0fab0aa8c95c7d7d94eef84d8c4cbafb) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a0fab0aa8c95c7d7d94eef84d8c4cbafb}

#### `public  `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a875c3ebce7e2de200daf4e715c1f43d5) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a875c3ebce7e2de200daf4e715c1f43d5}

#### `public  `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1aeeacc38bd86c4268705951c110d240fe) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1aeeacc38bd86c4268705951c110d240fe}

#### `public  `[`num_cnn_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ab0de489349c46c49e4558ce8756c0963) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ab0de489349c46c49e4558ce8756c0963}

#### `public  `[`kernel_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ac7539bae61ce64958d5b63961f8508c8) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ac7539bae61ce64958d5b63961f8508c8}

#### `public  `[`cnn`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a41473860e0b9e2259eb9c904a26bf149) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a41473860e0b9e2259eb9c904a26bf149}

#### `public  `[`pooling`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a6ab7c1c98d88eda482b1ddcc308406bd) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a6ab7c1c98d88eda482b1ddcc308406bd}

#### `public  `[`lstm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1adb3f278b270c319724a46609b014951b) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1adb3f278b270c319724a46609b014951b}

#### `public  `[`dense`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a8e197599b1335971a2b9a0b0de4ee7b1) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a8e197599b1335971a2b9a0b0de4ee7b1}

#### `public def `[`oversampling_rate`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ae61a92b8fc408c7ac69ff810183fd0b8)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1ae61a92b8fc408c7ac69ff810183fd0b8}

#### `public def `[`call`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a4ebe3042ea07fc123427d6f9a57d2d6f)`(self,x,state)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADCNNLSTM_1a4ebe3042ea07fc123427d6f9a57d2d6f}

# class `exot::channel::thermalsc::appdetection::ADConvLSTM` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADConvLSTM}

```
class exot::channel::thermalsc::appdetection::ADConvLSTM
  : public exot.channel.thermalsc.appdetection.AppDetector
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::thermalsc::appdetection::ADLSTM` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM}

```
class exot::channel::thermalsc::appdetection::ADLSTM
  : public exot.channel.thermalsc.appdetection.AppDetector
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`batch_sz`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ac1e87844f869b6917af3a33479177d56) | 
`public  `[`enc_units`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a1a5f5b3ae5daec115cedbe84ed74d8f6) | 
`public  `[`num_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a3237f70a074dd8c93c43b9e44573b9fb) | 
`public  `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a5e1e6fcf88411066f9cc8fd969be50ca) | 
`public  `[`lstm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ad218141ac97ccacf258dff43b308b4d8) | 
`public  `[`dense`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ac09d9b0d1a7039af33f41e6c76e3f300) | 
`public def `[`call`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a75ebe6e311c1bb1443c1d3f3855a7760)`(self,x,state)` | 

## Members

#### `public  `[`batch_sz`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ac1e87844f869b6917af3a33479177d56) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ac1e87844f869b6917af3a33479177d56}

#### `public  `[`enc_units`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a1a5f5b3ae5daec115cedbe84ed74d8f6) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a1a5f5b3ae5daec115cedbe84ed74d8f6}

#### `public  `[`num_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a3237f70a074dd8c93c43b9e44573b9fb) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a3237f70a074dd8c93c43b9e44573b9fb}

#### `public  `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a5e1e6fcf88411066f9cc8fd969be50ca) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a5e1e6fcf88411066f9cc8fd969be50ca}

#### `public  `[`lstm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ad218141ac97ccacf258dff43b308b4d8) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ad218141ac97ccacf258dff43b308b4d8}

#### `public  `[`dense`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ac09d9b0d1a7039af33f41e6c76e3f300) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1ac09d9b0d1a7039af33f41e6c76e3f300}

#### `public def `[`call`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a75ebe6e311c1bb1443c1d3f3855a7760)`(self,x,state)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1ADLSTM_1a75ebe6e311c1bb1443c1d3f3855a7760}

# class `exot::channel::thermalsc::appdetection::AppDetection` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection}

```
class exot::channel::thermalsc::appdetection::AppDetection
  : public exot.channel._base.Analysis
  : public exot.channel.thermalsc._mixins.ThermalAppDecectionDataSetHandler
  : public exot.channel.mixins.mldataset.TrainX
  : public exot.channel.mixins.mldataset.TrainY
  : public exot.channel.mixins.mldataset.TrainSampleLen
  : public exot.channel.mixins.mldataset.TrainWeights
  : public exot.channel.mixins.mldataset.TestX
  : public exot.channel.mixins.mldataset.TestY
  : public exot.channel.mixins.mldataset.TestSampleLen
  : public exot.channel.mixins.mldataset.TestWeights
  : public exot.channel.mixins.mldataset.VerifX
  : public exot.channel.mixins.mldataset.VerifY
  : public exot.channel.mixins.mldataset.VerifSampleLen
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`model_type`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0e8aec5fb59acd781b011fbbdde4226f) | 
`public  `[`appdetector`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0d655d7d413282070b5a88e4d3d65611) | 
`public  `[`optimizer`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad8615847a9764d20fc5d3e5d652c1652) | 
`public  `[`checkpoint`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a922429082fa6272800173938c39f0c39) | 
`public  `[`best_lev_norm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a69e53883d465bd9c0196cb2e4966a0c1) | 
`public  `[`best_loss`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa0f9b385ac4f96233cfa46d9d82eda28) | 
`public def `[`__init__`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1afab74f0997ec326d50d251955048f666)`(self,* args,** kwargs)` | 
`public def `[`n_epochs`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2241f40991f5c3a7a3f82de413a32fcd)`(self)` | 
`public def `[`n_epochs`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae787632ac642e5fcd273cddf5c9d36bc)`(self,value)` | 
`public def `[`start_epoch`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a57dbcf0378ee9886e077b9eb70efd94a)`(self)` | 
`public None `[`start_epoch`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a311d46a416f7230fbe6f817e7bd87656)`(self,int value)` | 
`public def `[`debug_step`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad21c162c21454c70206bb9556336dc90)`(self)` | 
`public def `[`early_stopping_threshold`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac4b3b28bcf9c08d72e089a13f7ef1386)`(self)` | 
`public def `[`model_type`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2cf81d0e24d3145aa285e862a1a0a413)`(self)` | 
`public def `[`max_grad_norm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a05ffa6b9e10c51366c5e2837aaa3aa1b)`(self)` | 
`public def `[`p_dropout`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a7bffbbfb42a49eb0fdda8ffad36cf7c2)`(self)` | 
`public def `[`p_keep`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad6c4b012b1f202041d59e2550342f1b4)`(self)` | 
`public def `[`num_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac78d649ceb64cf58c2a1f1da07c207eb)`(self)` | 
`public def `[`num_hidden`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a126ed35c255dec7ef4e7b9eb856e3719)`(self)` | 
`public def `[`learning_rate`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a90e7c031c2a3d565d209362e5a76f45d)`(self)` | 
`public def `[`model_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aae81c9ee0b2f1738dacff75a88fd8594)`(self)` | 
`public None `[`model_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab9097831117911bb1efc98ba43a1bb9a)`(self,str value)` | 
`public def `[`filtering_window_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae1704fa1567b7f46c7b26c1cdd3c9e06)`(self)` | 
`public def `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a03c431e2409fa6a584076adfc7c1d08c)`(self)` | 
`public None `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a80bcb5b74bffcab1953f7bbbfbd446dc)`(self,bool value)` | 
`public def `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a7df8f0621d912eeb78cfb6718af7fbaa)`(self)` | 
`public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae91193b7a7d7153d6b22186be41154ba)`(self)` | 
`public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2130a3dda2d5f18519c14b077dc75ad1)`(self,value)` | 
`public None `[`reshuffle_data`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a65844b448936d08d72a5078427fe9c6f)`(self,str phase,int epoch)` | 
`public def `[`train_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abfdbba5c1648d4f69371a64fe5544b7e)`(self)` | 
`public def `[`train_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a788413235a67b01dbcd7bc4da979bef0)`(self)` | 
`public def `[`train_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac98a18cbba21ecc9c852df829004532e)`(self)` | 
`public def `[`train_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a458dba532be5694dacd7bacb5f2a48f9)`(self)` | 
`public def `[`test_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a72d9dba57daaefa2e7d381cb70b0bb3e)`(self)` | 
`public def `[`test_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aac9ac55962be60a59ab23518279a0c2a)`(self)` | 
`public def `[`test_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1afb3a8ae98aae8405fb7184f36488a1cb)`(self)` | 
`public def `[`test_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a06668d2e66a16079be2c887167483c5a)`(self)` | 
`public def `[`verif_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abdb22c1b847c9a00c88b592ce85bf357)`(self)` | 
`public def `[`verif_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abb3e3c30e3a37a7b27375a5dbaba8923)`(self)` | 
`public def `[`verif_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0601bf1e00ba2a36755a5edd8a442309)`(self)` | 
`public tuple `[`get_data`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac631eeef3182a740d293ec9c079ee523)`(self,str phase,int batch)` | 
`public Path `[`path`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae81537b94b7ed98961102f018b496426)`(self)` | 
`public Path `[`path_dataset`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0ebb7ec975b2d8f09a1e0ab4589ef2d1)`(self)` | Get the save path
`public def `[`read`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aeef1258c59790cac147df1a13394bdb0)`(self)` | 
`public def `[`write`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a6aa6c32d5fb11a9b135867554f556d95)`(self)` | 
`public def `[`write_debug_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1acd2cade61e909dc5710e5d0f2c75926f)`(self,str phase,outputs,prefix,as_txt)` | Serialise a checkpoint
`public def `[`read_debug_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab26436ad95ffde98b406ee26e168a8ad)`(self,str phase,prefix)` | Load a checkpoint
`public def `[`init_app_detector`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa221d9c4123bd5fcd3ed2b75d8553f8c)`(self)` | 
`public def `[`train`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab95de066ece159f8dfe12d28424695e6)`(self)` | 
`public def `[`debug_restore_checkpoint`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a001e73e7534db95c8f7452b42b99761f)`(self,str phase)` | 
`public def `[`verify`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac2197a152653ca952979e9cdf2137c76)`(self,best_model)` | 
`public def `[`inference`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa9a2e22d9880d13554d541e84b14df9e)`(self,int epoch,bool train,bool debug)` | 
`public def `[`process`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1adce280e97936a7a81b5444e0eb79ce4a)`(self,inp,targ,weights,appdetector_state,train)` | 
`public def `[`filter_batch`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a3eea2126bde462ddaa9af0025d004fdc)`(self,data,window_size)` | Sliding window over the data. Majority voting is performed to replace outliers and reduce noise.
`public def `[`majority_voting`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a9ae65269bfebe49b7eae4e0eb3f1134e)`(self,data,window_size)` | 
`public def `[`get_sequences`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abee67fc8fa27188a5f91d60d0015a5a2)`(self,labels,weights)` | 
`public def `[`tf_collapse_labels`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a5214c0d54a292122e9e62864322e7b42)`(self,labels,weights)` | 
`public def `[`batch_accuracy`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a8ad45de755b9084cac9e30a69552c158)`(self,predictions,target,weights)` | 
`public def `[`tf_accuracy`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1af77fa5e3b4bffeb7b820a7af01a79403)`(self,predictions,target)` | 
`public def `[`batch_levensthein_distance`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a59d55198cbd8449162d4848da53af254)`(self,predictions,target)` | 
`public def `[`batch_timing_accuracy`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a5b86d5482369098dd535ccc580752c88)`(self,predictions,target)` | 

## Members

#### `public  `[`model_type`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0e8aec5fb59acd781b011fbbdde4226f) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0e8aec5fb59acd781b011fbbdde4226f}

#### `public  `[`appdetector`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0d655d7d413282070b5a88e4d3d65611) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0d655d7d413282070b5a88e4d3d65611}

#### `public  `[`optimizer`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad8615847a9764d20fc5d3e5d652c1652) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad8615847a9764d20fc5d3e5d652c1652}

#### `public  `[`checkpoint`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a922429082fa6272800173938c39f0c39) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a922429082fa6272800173938c39f0c39}

#### `public  `[`best_lev_norm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a69e53883d465bd9c0196cb2e4966a0c1) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a69e53883d465bd9c0196cb2e4966a0c1}

#### `public  `[`best_loss`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa0f9b385ac4f96233cfa46d9d82eda28) {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa0f9b385ac4f96233cfa46d9d82eda28}

#### `public def `[`__init__`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1afab74f0997ec326d50d251955048f666)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1afab74f0997ec326d50d251955048f666}

#### `public def `[`n_epochs`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2241f40991f5c3a7a3f82de413a32fcd)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2241f40991f5c3a7a3f82de413a32fcd}

#### `public def `[`n_epochs`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae787632ac642e5fcd273cddf5c9d36bc)`(self,value)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae787632ac642e5fcd273cddf5c9d36bc}

#### `public def `[`start_epoch`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a57dbcf0378ee9886e077b9eb70efd94a)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a57dbcf0378ee9886e077b9eb70efd94a}

#### `public None `[`start_epoch`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a311d46a416f7230fbe6f817e7bd87656)`(self,int value)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a311d46a416f7230fbe6f817e7bd87656}

#### `public def `[`debug_step`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad21c162c21454c70206bb9556336dc90)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad21c162c21454c70206bb9556336dc90}

#### `public def `[`early_stopping_threshold`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac4b3b28bcf9c08d72e089a13f7ef1386)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac4b3b28bcf9c08d72e089a13f7ef1386}

#### `public def `[`model_type`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2cf81d0e24d3145aa285e862a1a0a413)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2cf81d0e24d3145aa285e862a1a0a413}

#### `public def `[`max_grad_norm`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a05ffa6b9e10c51366c5e2837aaa3aa1b)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a05ffa6b9e10c51366c5e2837aaa3aa1b}

#### `public def `[`p_dropout`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a7bffbbfb42a49eb0fdda8ffad36cf7c2)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a7bffbbfb42a49eb0fdda8ffad36cf7c2}

#### `public def `[`p_keep`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad6c4b012b1f202041d59e2550342f1b4)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ad6c4b012b1f202041d59e2550342f1b4}

#### `public def `[`num_layers`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac78d649ceb64cf58c2a1f1da07c207eb)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac78d649ceb64cf58c2a1f1da07c207eb}

#### `public def `[`num_hidden`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a126ed35c255dec7ef4e7b9eb856e3719)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a126ed35c255dec7ef4e7b9eb856e3719}

#### `public def `[`learning_rate`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a90e7c031c2a3d565d209362e5a76f45d)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a90e7c031c2a3d565d209362e5a76f45d}

#### `public def `[`model_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aae81c9ee0b2f1738dacff75a88fd8594)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aae81c9ee0b2f1738dacff75a88fd8594}

#### `public None `[`model_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab9097831117911bb1efc98ba43a1bb9a)`(self,str value)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab9097831117911bb1efc98ba43a1bb9a}

#### `public def `[`filtering_window_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae1704fa1567b7f46c7b26c1cdd3c9e06)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae1704fa1567b7f46c7b26c1cdd3c9e06}

#### `public def `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a03c431e2409fa6a584076adfc7c1d08c)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a03c431e2409fa6a584076adfc7c1d08c}

#### `public None `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a80bcb5b74bffcab1953f7bbbfbd446dc)`(self,bool value)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a80bcb5b74bffcab1953f7bbbfbd446dc}

#### `public def `[`max_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a7df8f0621d912eeb78cfb6718af7fbaa)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a7df8f0621d912eeb78cfb6718af7fbaa}

#### `public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae91193b7a7d7153d6b22186be41154ba)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae91193b7a7d7153d6b22186be41154ba}

#### `public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2130a3dda2d5f18519c14b077dc75ad1)`(self,value)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a2130a3dda2d5f18519c14b077dc75ad1}

#### `public None `[`reshuffle_data`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a65844b448936d08d72a5078427fe9c6f)`(self,str phase,int epoch)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a65844b448936d08d72a5078427fe9c6f}

#### `public def `[`train_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abfdbba5c1648d4f69371a64fe5544b7e)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abfdbba5c1648d4f69371a64fe5544b7e}

#### `public def `[`train_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a788413235a67b01dbcd7bc4da979bef0)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a788413235a67b01dbcd7bc4da979bef0}

#### `public def `[`train_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac98a18cbba21ecc9c852df829004532e)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac98a18cbba21ecc9c852df829004532e}

#### `public def `[`train_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a458dba532be5694dacd7bacb5f2a48f9)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a458dba532be5694dacd7bacb5f2a48f9}

#### `public def `[`test_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a72d9dba57daaefa2e7d381cb70b0bb3e)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a72d9dba57daaefa2e7d381cb70b0bb3e}

#### `public def `[`test_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aac9ac55962be60a59ab23518279a0c2a)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aac9ac55962be60a59ab23518279a0c2a}

#### `public def `[`test_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1afb3a8ae98aae8405fb7184f36488a1cb)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1afb3a8ae98aae8405fb7184f36488a1cb}

#### `public def `[`test_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a06668d2e66a16079be2c887167483c5a)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a06668d2e66a16079be2c887167483c5a}

#### `public def `[`verif_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abdb22c1b847c9a00c88b592ce85bf357)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abdb22c1b847c9a00c88b592ce85bf357}

#### `public def `[`verif_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abb3e3c30e3a37a7b27375a5dbaba8923)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abb3e3c30e3a37a7b27375a5dbaba8923}

#### `public def `[`verif_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0601bf1e00ba2a36755a5edd8a442309)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0601bf1e00ba2a36755a5edd8a442309}

#### `public tuple `[`get_data`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac631eeef3182a740d293ec9c079ee523)`(self,str phase,int batch)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac631eeef3182a740d293ec9c079ee523}

#### `public Path `[`path`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae81537b94b7ed98961102f018b496426)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ae81537b94b7ed98961102f018b496426}

#### `public Path `[`path_dataset`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0ebb7ec975b2d8f09a1e0ab4589ef2d1)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a0ebb7ec975b2d8f09a1e0ab4589ef2d1}

Get the save path

#### `public def `[`read`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aeef1258c59790cac147df1a13394bdb0)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aeef1258c59790cac147df1a13394bdb0}

#### `public def `[`write`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a6aa6c32d5fb11a9b135867554f556d95)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a6aa6c32d5fb11a9b135867554f556d95}

#### `public def `[`write_debug_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1acd2cade61e909dc5710e5d0f2c75926f)`(self,str phase,outputs,prefix,as_txt)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1acd2cade61e909dc5710e5d0f2c75926f}

Serialise a checkpoint

#### `public def `[`read_debug_files`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab26436ad95ffde98b406ee26e168a8ad)`(self,str phase,prefix)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab26436ad95ffde98b406ee26e168a8ad}

Load a checkpoint

#### `public def `[`init_app_detector`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa221d9c4123bd5fcd3ed2b75d8553f8c)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa221d9c4123bd5fcd3ed2b75d8553f8c}

#### `public def `[`train`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab95de066ece159f8dfe12d28424695e6)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ab95de066ece159f8dfe12d28424695e6}

#### `public def `[`debug_restore_checkpoint`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a001e73e7534db95c8f7452b42b99761f)`(self,str phase)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a001e73e7534db95c8f7452b42b99761f}

#### `public def `[`verify`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac2197a152653ca952979e9cdf2137c76)`(self,best_model)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1ac2197a152653ca952979e9cdf2137c76}

#### `public def `[`inference`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa9a2e22d9880d13554d541e84b14df9e)`(self,int epoch,bool train,bool debug)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1aa9a2e22d9880d13554d541e84b14df9e}

#### `public def `[`process`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1adce280e97936a7a81b5444e0eb79ce4a)`(self,inp,targ,weights,appdetector_state,train)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1adce280e97936a7a81b5444e0eb79ce4a}

#### `public def `[`filter_batch`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a3eea2126bde462ddaa9af0025d004fdc)`(self,data,window_size)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a3eea2126bde462ddaa9af0025d004fdc}

Sliding window over the data. Majority voting is performed to replace outliers and reduce noise.

#### `public def `[`majority_voting`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a9ae65269bfebe49b7eae4e0eb3f1134e)`(self,data,window_size)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a9ae65269bfebe49b7eae4e0eb3f1134e}

#### `public def `[`get_sequences`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abee67fc8fa27188a5f91d60d0015a5a2)`(self,labels,weights)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1abee67fc8fa27188a5f91d60d0015a5a2}

#### `public def `[`tf_collapse_labels`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a5214c0d54a292122e9e62864322e7b42)`(self,labels,weights)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a5214c0d54a292122e9e62864322e7b42}

#### `public def `[`batch_accuracy`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a8ad45de755b9084cac9e30a69552c158)`(self,predictions,target,weights)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a8ad45de755b9084cac9e30a69552c158}

#### `public def `[`tf_accuracy`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1af77fa5e3b4bffeb7b820a7af01a79403)`(self,predictions,target)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1af77fa5e3b4bffeb7b820a7af01a79403}

#### `public def `[`batch_levensthein_distance`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a59d55198cbd8449162d4848da53af254)`(self,predictions,target)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a59d55198cbd8449162d4848da53af254}

#### `public def `[`batch_timing_accuracy`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a5b86d5482369098dd535ccc580752c88)`(self,predictions,target)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetection_1a5b86d5482369098dd535ccc580752c88}

# class `exot::channel::thermalsc::appdetection::AppDetector` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector}

```
class exot::channel::thermalsc::appdetection::AppDetector
  : public Model
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1ab38b075b174c740f655d4094da4c4fc4)`(self,* args,** kwargs)` | 
`public def `[`oversampling_rate`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a3fbddfcd292768a3b50c8fb117948b14)`(self)` | 
`public def `[`call`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a75f2b26d93d5709eefa94ed773da7b46)`(self,x,state)` | 
`public def `[`initial_hidden_state`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a830fac4455523b8018bc73617e6770eb)`(self)` | 
`public def `[`state_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1afb6cb8b3f94f4c29c29b1fcbddfd33bf)`(self)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1ab38b075b174c740f655d4094da4c4fc4)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1ab38b075b174c740f655d4094da4c4fc4}

#### `public def `[`oversampling_rate`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a3fbddfcd292768a3b50c8fb117948b14)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a3fbddfcd292768a3b50c8fb117948b14}

#### `public def `[`call`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a75f2b26d93d5709eefa94ed773da7b46)`(self,x,state)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a75f2b26d93d5709eefa94ed773da7b46}

#### `public def `[`initial_hidden_state`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a830fac4455523b8018bc73617e6770eb)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1a830fac4455523b8018bc73617e6770eb}

#### `public def `[`state_size`](#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1afb6cb8b3f94f4c29c29b1fcbddfd33bf)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1appdetection_1_1AppDetector_1afb6cb8b3f94f4c29c29b1fcbddfd33bf}

# namespace `exot::channel::thermalsc::dataaugmentation` {#namespaceexot_1_1channel_1_1thermalsc_1_1dataaugmentation}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::channel::thermalsc::dataaugmentation::DataAugmentation`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation) | 
`class `[`exot::channel::thermalsc::dataaugmentation::SampleSelectionMode`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1SampleSelectionMode) | Layer types
`class `[`exot::channel::thermalsc::dataaugmentation::WeightCalculationMode`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1WeightCalculationMode) | Layer types

# class `exot::channel::thermalsc::dataaugmentation::DataAugmentation` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation}

```
class exot::channel::thermalsc::dataaugmentation::DataAugmentation
  : public exot.channel._base.Analysis
  : public exot.channel.thermalsc._mixins.ThermalAppDecectionDataSetHandler
  : public exot.channel.mixins.mldataset.TrainX
  : public exot.channel.mixins.mldataset.TrainY
  : public exot.channel.mixins.mldataset.TrainSampleLen
  : public exot.channel.mixins.mldataset.TrainWeights
  : public exot.channel.mixins.mldataset.TestX
  : public exot.channel.mixins.mldataset.TestY
  : public exot.channel.mixins.mldataset.TestSampleLen
  : public exot.channel.mixins.mldataset.TestWeights
  : public exot.channel.mixins.mldataset.VerifX
  : public exot.channel.mixins.mldataset.VerifY
  : public exot.channel.mixins.mldataset.VerifSampleLen
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`sample_selection_mode`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aed9ec4f47beb3c8d60ca6d064755b345) | 
`public  `[`num_verif_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac63c7b388f93cc9b58614f57527b9288) | 
`public def `[`__init__`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1addcd798c74cf80b9fcff555e0e8cd8c5)`(self,* args,** kwargs)` | 
`public def `[`train_runs`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa42fe77f6c3d8d979e3ca9502903114b)`(self)` | 
`public def `[`test_runs`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2777cf502811138c45c2b28e4789effc)`(self)` | 
`public def `[`verif_runs`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6b44fa1fb416bf65660d5eb4c2c2edf6)`(self)` | 
`public def `[`train_phases`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a3d5a03063764b0f957466d580db54469)`(self)` | 
`public def `[`test_phases`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6f48d85488192c9ba27f61d260a84414)`(self)` | 
`public def `[`verif_phases`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a0200452af4d2e55b345100d05aa11ae3)`(self)` | 
`public def `[`ambient`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac62dcf58691b16779ddabf5bedeebb0f)`(self)` | 
`public def `[`dynamic_start`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8baeb3b3fc6131b0296bfbfc63240af9)`(self)` | 
`public def `[`thermal_throttling`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa2e21bdaa82361fe64240dfd4bbf2abe)`(self)` | 
`public def `[`min_len_profile`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a4922e497328dc1fb4a973eddd5a3e720)`(self)` | 
`public def `[`duration_context_change`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a4406b5ac43847834019f9c7412543868)`(self)` | 
`public def `[`beta_z_names`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac31f9dd45ca57420e8d83b040937b4d4)`(self)` | 
`public def `[`data_columns_idxes`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a7bda258f3f3dd70dfcd42c99278b650e)`(self)` | 
`public def `[`label_columns_idxes`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a82d7634e146ba32147c9e6cb7587f549)`(self)` | 
`public def `[`resampling_period_s`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aeafcec5843b0a37303630a6c3febe7ca)`(self)` | 
`public def `[`env`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a7ba6c6bd51b463f971306b696aacdb0d)`(self)` | 
`public def `[`matcher_data`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2b6461bcc02cd7e0f1208ade02c3de24)`(self)` | 
`public def `[`matcher_labels`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad876b7e8d0b55c7425b911d5c9450e4c)`(self)` | 
`public def `[`num_train_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aff6371ad5f6fa0c47829e739246c0830)`(self)` | 
`public None `[`num_train_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6d044a5a93023eb61e41e802bfacdc35)`(self,int value)` | 
`public def `[`num_test_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6b522771f15327193c6357a22f39e448)`(self)` | 
`public None `[`num_test_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1acc0c02de9623f48872fe64f9e6ef05b9)`(self,int value)` | 
`public def `[`num_verif_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a58337dfe319125df48d77a6f48af90b0)`(self)` | 
`public None `[`num_verif_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a0d55ef3653a65047dcfe43b2154d3b4c)`(self,int value)` | 
`public def `[`augmentation_verif`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa5f5063cc4d1caf60d6e6d219cafc867)`(self)` | 
`public def `[`augmentation_test`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a29ac468b14f41d161341436e9e722881)`(self)` | 
`public def `[`augmentation_train`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a5d615403caea4cbea190fbb9e3118355)`(self)` | 
`public def `[`label_mapping`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad60b881875afa6a971997a6dff3925cd)`(self)` | 
`public def `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8804aebafc63984e3f0f658775dee3c7)`(self)` | 
`public def `[`label_refactoring_rule`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ab38e0a0900524adba55f3148c50a20c5)`(self,str analysis_phase)` | 
`public dict `[`ingest_args`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad9ed501c1c47431382293bbfefe6e992)`(self,int rep,str analysis_phase)` | 
`public bool `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa658a7d0727fd9f53021b73f55140dd3)`(self)` | 
`public None `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2a4937e0caadd7a9d52b393da96952b5)`(self,bool value)` | 
`public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8c425b959eb7611847d17a648c73b52d)`(self)` | 
`public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a76fc9c9704cead51fd63d64658abd10a)`(self,value)` | 
`public def `[`batch_size_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af0870a2fa8e9051a5cea9856524b62b7)`(self)` | 
`public def `[`train_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac2d9050ef062664ab08c2d97c25cccdd)`(self)` | 
`public def `[`train_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a96f304d2598f60fd36bfe93290d96ed9)`(self)` | 
`public def `[`train_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac0c1c592452716997e18b5c319adf923)`(self)` | 
`public def `[`train_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1ddc08fa5fb2eea3497f01be61dcbaf7)`(self)` | 
`public def `[`test_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af675beb5c50d03ff2230cddb602b9475)`(self)` | 
`public def `[`test_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8561d272f91552c150608f8a3beb79bd)`(self)` | 
`public def `[`test_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a74c64ae278eb1b8e66baa85057b40bc8)`(self)` | 
`public def `[`test_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aea845403fa1923ddbdd32c71b2ffb1c4)`(self)` | 
`public def `[`verif_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa2a67d8676b2bf9759a4e6a17fddb34b)`(self)` | 
`public def `[`verif_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af32aabe04bd764cc46b2bc776abf7194)`(self)` | 
`public def `[`verif_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a24f4b31016f75ec4b251c2535881fd32)`(self)` | 
`public def `[`T_meas_ambient`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1ab2428b387ade34d875e691859cbed2)`(self)` | 
`public def `[`cleanup`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2772778213c75b40a5968043288fe9dc)`(self)` | 
`public def `[`write`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6fb19b790a27ce70759e34de98a55de6)`(self)` | 
`public def `[`read`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1abdd36b0286bf1ea2835cba14c34c3908)`(self)` | 
`public Path `[`path`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac3e0287e308b4f896644b4802373faae)`(self)` | 
`public Path `[`path_dataset`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1a61a2e265ac9924fee45189b8b6f984)`(self)` | Get the save path
`public def `[`num_sensors`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a3bb2d848ab7f7e63aaed6a7787386443)`(self)` | 
`public def `[`num_feature_dims`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a29e8715b6084f75f657679d19a82434f)`(self)` | 
`public def `[`sample_selection_mode`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a128685112cef0c1f386caf4e205efbc7)`(self)` | 
`public def `[`compute_weights`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6c2911d6a39960c3960e3f19fc3c0314)`(self,histlabels,mode)` | Compute the weights for the labels and return as a dict

## Members

#### `public  `[`sample_selection_mode`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aed9ec4f47beb3c8d60ca6d064755b345) {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aed9ec4f47beb3c8d60ca6d064755b345}

#### `public  `[`num_verif_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac63c7b388f93cc9b58614f57527b9288) {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac63c7b388f93cc9b58614f57527b9288}

#### `public def `[`__init__`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1addcd798c74cf80b9fcff555e0e8cd8c5)`(self,* args,** kwargs)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1addcd798c74cf80b9fcff555e0e8cd8c5}

#### `public def `[`train_runs`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa42fe77f6c3d8d979e3ca9502903114b)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa42fe77f6c3d8d979e3ca9502903114b}

#### `public def `[`test_runs`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2777cf502811138c45c2b28e4789effc)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2777cf502811138c45c2b28e4789effc}

#### `public def `[`verif_runs`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6b44fa1fb416bf65660d5eb4c2c2edf6)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6b44fa1fb416bf65660d5eb4c2c2edf6}

#### `public def `[`train_phases`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a3d5a03063764b0f957466d580db54469)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a3d5a03063764b0f957466d580db54469}

#### `public def `[`test_phases`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6f48d85488192c9ba27f61d260a84414)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6f48d85488192c9ba27f61d260a84414}

#### `public def `[`verif_phases`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a0200452af4d2e55b345100d05aa11ae3)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a0200452af4d2e55b345100d05aa11ae3}

#### `public def `[`ambient`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac62dcf58691b16779ddabf5bedeebb0f)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac62dcf58691b16779ddabf5bedeebb0f}

#### `public def `[`dynamic_start`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8baeb3b3fc6131b0296bfbfc63240af9)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8baeb3b3fc6131b0296bfbfc63240af9}

#### `public def `[`thermal_throttling`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa2e21bdaa82361fe64240dfd4bbf2abe)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa2e21bdaa82361fe64240dfd4bbf2abe}

#### `public def `[`min_len_profile`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a4922e497328dc1fb4a973eddd5a3e720)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a4922e497328dc1fb4a973eddd5a3e720}

#### `public def `[`duration_context_change`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a4406b5ac43847834019f9c7412543868)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a4406b5ac43847834019f9c7412543868}

#### `public def `[`beta_z_names`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac31f9dd45ca57420e8d83b040937b4d4)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac31f9dd45ca57420e8d83b040937b4d4}

#### `public def `[`data_columns_idxes`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a7bda258f3f3dd70dfcd42c99278b650e)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a7bda258f3f3dd70dfcd42c99278b650e}

#### `public def `[`label_columns_idxes`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a82d7634e146ba32147c9e6cb7587f549)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a82d7634e146ba32147c9e6cb7587f549}

#### `public def `[`resampling_period_s`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aeafcec5843b0a37303630a6c3febe7ca)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aeafcec5843b0a37303630a6c3febe7ca}

#### `public def `[`env`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a7ba6c6bd51b463f971306b696aacdb0d)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a7ba6c6bd51b463f971306b696aacdb0d}

#### `public def `[`matcher_data`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2b6461bcc02cd7e0f1208ade02c3de24)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2b6461bcc02cd7e0f1208ade02c3de24}

#### `public def `[`matcher_labels`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad876b7e8d0b55c7425b911d5c9450e4c)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad876b7e8d0b55c7425b911d5c9450e4c}

#### `public def `[`num_train_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aff6371ad5f6fa0c47829e739246c0830)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aff6371ad5f6fa0c47829e739246c0830}

#### `public None `[`num_train_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6d044a5a93023eb61e41e802bfacdc35)`(self,int value)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6d044a5a93023eb61e41e802bfacdc35}

#### `public def `[`num_test_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6b522771f15327193c6357a22f39e448)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6b522771f15327193c6357a22f39e448}

#### `public None `[`num_test_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1acc0c02de9623f48872fe64f9e6ef05b9)`(self,int value)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1acc0c02de9623f48872fe64f9e6ef05b9}

#### `public def `[`num_verif_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a58337dfe319125df48d77a6f48af90b0)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a58337dfe319125df48d77a6f48af90b0}

#### `public None `[`num_verif_batches`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a0d55ef3653a65047dcfe43b2154d3b4c)`(self,int value)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a0d55ef3653a65047dcfe43b2154d3b4c}

#### `public def `[`augmentation_verif`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa5f5063cc4d1caf60d6e6d219cafc867)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa5f5063cc4d1caf60d6e6d219cafc867}

#### `public def `[`augmentation_test`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a29ac468b14f41d161341436e9e722881)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a29ac468b14f41d161341436e9e722881}

#### `public def `[`augmentation_train`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a5d615403caea4cbea190fbb9e3118355)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a5d615403caea4cbea190fbb9e3118355}

#### `public def `[`label_mapping`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad60b881875afa6a971997a6dff3925cd)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad60b881875afa6a971997a6dff3925cd}

#### `public def `[`num_labels`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8804aebafc63984e3f0f658775dee3c7)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8804aebafc63984e3f0f658775dee3c7}

#### `public def `[`label_refactoring_rule`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ab38e0a0900524adba55f3148c50a20c5)`(self,str analysis_phase)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ab38e0a0900524adba55f3148c50a20c5}

#### `public dict `[`ingest_args`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad9ed501c1c47431382293bbfefe6e992)`(self,int rep,str analysis_phase)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ad9ed501c1c47431382293bbfefe6e992}

#### `public bool `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa658a7d0727fd9f53021b73f55140dd3)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa658a7d0727fd9f53021b73f55140dd3}

#### `public None `[`unknown_label`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2a4937e0caadd7a9d52b393da96952b5)`(self,bool value)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2a4937e0caadd7a9d52b393da96952b5}

#### `public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8c425b959eb7611847d17a648c73b52d)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8c425b959eb7611847d17a648c73b52d}

#### `public def `[`batch_size`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a76fc9c9704cead51fd63d64658abd10a)`(self,value)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a76fc9c9704cead51fd63d64658abd10a}

#### `public def `[`batch_size_timesteps`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af0870a2fa8e9051a5cea9856524b62b7)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af0870a2fa8e9051a5cea9856524b62b7}

#### `public def `[`train_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac2d9050ef062664ab08c2d97c25cccdd)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac2d9050ef062664ab08c2d97c25cccdd}

#### `public def `[`train_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a96f304d2598f60fd36bfe93290d96ed9)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a96f304d2598f60fd36bfe93290d96ed9}

#### `public def `[`train_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac0c1c592452716997e18b5c319adf923)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac0c1c592452716997e18b5c319adf923}

#### `public def `[`train_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1ddc08fa5fb2eea3497f01be61dcbaf7)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1ddc08fa5fb2eea3497f01be61dcbaf7}

#### `public def `[`test_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af675beb5c50d03ff2230cddb602b9475)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af675beb5c50d03ff2230cddb602b9475}

#### `public def `[`test_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8561d272f91552c150608f8a3beb79bd)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a8561d272f91552c150608f8a3beb79bd}

#### `public def `[`test_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a74c64ae278eb1b8e66baa85057b40bc8)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a74c64ae278eb1b8e66baa85057b40bc8}

#### `public def `[`test_weights_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aea845403fa1923ddbdd32c71b2ffb1c4)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aea845403fa1923ddbdd32c71b2ffb1c4}

#### `public def `[`verif_X_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa2a67d8676b2bf9759a4e6a17fddb34b)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1aa2a67d8676b2bf9759a4e6a17fddb34b}

#### `public def `[`verif_Y_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af32aabe04bd764cc46b2bc776abf7194)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1af32aabe04bd764cc46b2bc776abf7194}

#### `public def `[`verif_actual_batch_len_shape`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a24f4b31016f75ec4b251c2535881fd32)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a24f4b31016f75ec4b251c2535881fd32}

#### `public def `[`T_meas_ambient`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1ab2428b387ade34d875e691859cbed2)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1ab2428b387ade34d875e691859cbed2}

#### `public def `[`cleanup`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2772778213c75b40a5968043288fe9dc)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a2772778213c75b40a5968043288fe9dc}

#### `public def `[`write`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6fb19b790a27ce70759e34de98a55de6)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6fb19b790a27ce70759e34de98a55de6}

#### `public def `[`read`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1abdd36b0286bf1ea2835cba14c34c3908)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1abdd36b0286bf1ea2835cba14c34c3908}

#### `public Path `[`path`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac3e0287e308b4f896644b4802373faae)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1ac3e0287e308b4f896644b4802373faae}

#### `public Path `[`path_dataset`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1a61a2e265ac9924fee45189b8b6f984)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a1a61a2e265ac9924fee45189b8b6f984}

Get the save path

#### `public def `[`num_sensors`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a3bb2d848ab7f7e63aaed6a7787386443)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a3bb2d848ab7f7e63aaed6a7787386443}

#### `public def `[`num_feature_dims`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a29e8715b6084f75f657679d19a82434f)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a29e8715b6084f75f657679d19a82434f}

#### `public def `[`sample_selection_mode`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a128685112cef0c1f386caf4e205efbc7)`(self)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a128685112cef0c1f386caf4e205efbc7}

#### `public def `[`compute_weights`](#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6c2911d6a39960c3960e3f19fc3c0314)`(self,histlabels,mode)` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1DataAugmentation_1a6c2911d6a39960c3960e3f19fc3c0314}

Compute the weights for the labels and return as a dict

# class `exot::channel::thermalsc::dataaugmentation::SampleSelectionMode` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1SampleSelectionMode}

```
class exot::channel::thermalsc::dataaugmentation::SampleSelectionMode
  : public Enum
```  

Layer types

The values must be unique, strings, and correspond to keys in the config.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::channel::thermalsc::dataaugmentation::WeightCalculationMode` {#classexot_1_1channel_1_1thermalsc_1_1dataaugmentation_1_1WeightCalculationMode}

```
class exot::channel::thermalsc::dataaugmentation::WeightCalculationMode
  : public Enum
```  

Layer types

The values must be unique, strings, and correspond to keys in the config.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

Generated by [Moxygen](https://sourcey.com/moxygen)