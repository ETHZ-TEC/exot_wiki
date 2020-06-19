[:back:](/home)
---

# Information flow
We base the information flow in an ExOT experiment on the information model depicted bellow, which is a layered model like the well known OSI model:

![Experiment flow diagram](../uploads/figures/communication_model.svg)

Layer 6 describes the generation of a random bit sequence of defined length, and layer 5 the conversion of the bit sequence to a symbol sequence.
The bit to symbol conversion can be seen as a form of data compression, which utilises the channel more effectively.
Layer 4 describes how the symbol sequence is converted into the desired trace, that needs to be input to the channel.
This trace can, for example, be a sequence of codes for cache operations necessary to send the symbol sequence through a cache channel.
The formatting of the trace to conform with the format needed by the source application is described in layer 3, and file writing in layer 2.
The actual applications are described by layer 1 and the covert channel by layer 0.
Moving from the bottom up, layer 2 describes file reading.
The measurements are then pre-processed as defined in layer 3 and the appropriate decoding schemes to recover the bit sequence are described in layers 4 and 5.
Last, layer 6 describes how the recovered bit sequence is compared with the generated one, to derive the error rate of the transmission.

Not all layers have to be implemented or used in every experiment.
Layers 3 to 6 can be omitted or bypassed.

## Layer example
Each layer can be used as a single entity for data processing, or as part of an experiment.
For further information, please have a look at the [example](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/notebooks/examples/layer_lne.ipynb) in the repository.

## Covert channel information flow
The diagram below shows the setup for a covert channel evaluation experiment. 

![Experiment Information flow diagram](../uploads/figures/flow.png)


# Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::layer::_base`](#namespaceexot_1_1layer_1_1__base) | 
`namespace `[`exot::layer::_factory`](#namespaceexot_1_1layer_1_1__factory) | 
`namespace `[`exot::layer::_mixins`](#namespaceexot_1_1layer_1_1__mixins) | 
`namespace `[`exot::layer::io::timevalue`](#namespaceexot_1_1layer_1_1io_1_1timevalue) | 
`namespace `[`exot::layer::lne::edge`](#namespaceexot_1_1layer_1_1lne_1_1edge) | 
`namespace `[`exot::layer::lne::frequency_governors`](#namespaceexot_1_1layer_1_1lne_1_1frequency__governors) | 
`namespace `[`exot::layer::lne::generic`](#namespaceexot_1_1layer_1_1lne_1_1generic) | 
`namespace `[`exot::layer::lne::label_refactoring`](#namespaceexot_1_1layer_1_1lne_1_1label__refactoring) | 
`namespace `[`exot::layer::lne::manchester`](#namespaceexot_1_1layer_1_1lne_1_1manchester) | 
`namespace `[`exot::layer::lne::median`](#namespaceexot_1_1layer_1_1lne_1_1median) | 
`namespace `[`exot::layer::lne::multi`](#namespaceexot_1_1layer_1_1lne_1_1multi) | 
`namespace `[`exot::layer::lne::passthrough`](#namespaceexot_1_1layer_1_1lne_1_1passthrough) | 
`namespace `[`exot::layer::lne::simple`](#namespaceexot_1_1layer_1_1lne_1_1simple) | 
`namespace `[`exot::layer::rdp::cacheactivation`](#namespaceexot_1_1layer_1_1rdp_1_1cacheactivation) | 
`namespace `[`exot::layer::rdp::coreactivation`](#namespaceexot_1_1layer_1_1rdp_1_1coreactivation) | 
`namespace `[`exot::layer::rdp::directactivation`](#namespaceexot_1_1layer_1_1rdp_1_1directactivation) | 
`namespace `[`exot::layer::rdp::quantisation`](#namespaceexot_1_1layer_1_1rdp_1_1quantisation) | 
`namespace `[`exot::layer::rdp::resampling`](#namespaceexot_1_1layer_1_1rdp_1_1resampling) | 
`namespace `[`exot::layer::src::_base`](#namespaceexot_1_1layer_1_1src_1_1__base) | 
`namespace `[`exot::layer::src::bitset`](#namespaceexot_1_1layer_1_1src_1_1bitset) | 
`namespace `[`exot::layer::src::huffman`](#namespaceexot_1_1layer_1_1src_1_1huffman) | 
`namespace `[`exot::layer::src::passthrough`](#namespaceexot_1_1layer_1_1src_1_1passthrough) | 
`class `[`exot::layer::_base::Layer::Type`](#classexot_1_1layer_1_1__base_1_1Layer_1_1Type) | Layer types

# namespace `exot::layer::_base` {#namespaceexot_1_1layer_1_1__base}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::_base::Layer`](#classexot_1_1layer_1_1__base_1_1Layer) | A base class for communication-oriented layers

# class `exot::layer::_base::Layer` {#classexot_1_1layer_1_1__base_1_1Layer}

```
class exot::layer::_base::Layer
  : public SubclassTracker
  : public IntermediatesHolder
  : public Configurable
  : public track
  : public metaclass
  : public ABCMeta
```  

A base class for communication-oriented layers

Layers that require runtime configuration are considered stateful and must be
configured before `encode` and `decode` can be called. To indicate whether a
layer is stateless or stateful, provide the correct boolean value in the property
`requires_runtime_config`.

If a layer is stateful and not configured, an exception will be thrown when
attempting to run the user-facing API `encode`, `decode`. Using raw `_encode` and
`_decode` might produce undefined behaviour due to the preconditions not being
satisfied.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.NoReturn `[`validate_encode_input`](#classexot_1_1layer_1_1__base_1_1Layer_1a08352a91e318f096872cc1fa6a1f4731)`(self,value)` | 
`public t.NoReturn `[`validate_encode_output`](#classexot_1_1layer_1_1__base_1_1Layer_1aa97aec14c879a58e3a6678a48c307cec)`(self,value)` | 
`public t.NoReturn `[`validate_decode_input`](#classexot_1_1layer_1_1__base_1_1Layer_1a9fc26ab8616c3eac7ab2dd85757951e2)`(self,value)` | 
`public t.NoReturn `[`validate_decode_output`](#classexot_1_1layer_1_1__base_1_1Layer_1a08f3fd92bb79533270446fdaa956dc46)`(self,value)` | 
`public str `[`name`](#classexot_1_1layer_1_1__base_1_1Layer_1adbc799c74ffcf81ab934a2c37488be11)`(self)` | 
`public str `[`__repr__`](#classexot_1_1layer_1_1__base_1_1Layer_1ad1af3dc7eebcb9e075c314845d695f09)`(self)` | Gets a string representation of the object
`public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1__base_1_1Layer_1ab40b8272be4d65873d5e38fc7e8c2f13)`(self)` | Does the layer's (encode, decode) require runtime configuration?
`public def `[`encode`](#classexot_1_1layer_1_1__base_1_1Layer_1a259d91ddb6fe3e5ccf37e8efbdcbafeb)`(self,encode_input,skip_checks)` | Encode a stream from a preceding layer
`public def `[`decode`](#classexot_1_1layer_1_1__base_1_1Layer_1aebe11dc2742b5ad280152089f642cf03)`(self,decode_input,skip_checks)` | Decode a stream from a succeeding layer

## Members

#### `public t.NoReturn `[`validate_encode_input`](#classexot_1_1layer_1_1__base_1_1Layer_1a08352a91e318f096872cc1fa6a1f4731)`(self,value)` {#classexot_1_1layer_1_1__base_1_1Layer_1a08352a91e318f096872cc1fa6a1f4731}

#### `public t.NoReturn `[`validate_encode_output`](#classexot_1_1layer_1_1__base_1_1Layer_1aa97aec14c879a58e3a6678a48c307cec)`(self,value)` {#classexot_1_1layer_1_1__base_1_1Layer_1aa97aec14c879a58e3a6678a48c307cec}

#### `public t.NoReturn `[`validate_decode_input`](#classexot_1_1layer_1_1__base_1_1Layer_1a9fc26ab8616c3eac7ab2dd85757951e2)`(self,value)` {#classexot_1_1layer_1_1__base_1_1Layer_1a9fc26ab8616c3eac7ab2dd85757951e2}

#### `public t.NoReturn `[`validate_decode_output`](#classexot_1_1layer_1_1__base_1_1Layer_1a08f3fd92bb79533270446fdaa956dc46)`(self,value)` {#classexot_1_1layer_1_1__base_1_1Layer_1a08f3fd92bb79533270446fdaa956dc46}

#### `public str `[`name`](#classexot_1_1layer_1_1__base_1_1Layer_1adbc799c74ffcf81ab934a2c37488be11)`(self)` {#classexot_1_1layer_1_1__base_1_1Layer_1adbc799c74ffcf81ab934a2c37488be11}

#### `public str `[`__repr__`](#classexot_1_1layer_1_1__base_1_1Layer_1ad1af3dc7eebcb9e075c314845d695f09)`(self)` {#classexot_1_1layer_1_1__base_1_1Layer_1ad1af3dc7eebcb9e075c314845d695f09}

Gets a string representation of the object

Returns:
    str: The info

#### `public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1__base_1_1Layer_1ab40b8272be4d65873d5e38fc7e8c2f13)`(self)` {#classexot_1_1layer_1_1__base_1_1Layer_1ab40b8272be4d65873d5e38fc7e8c2f13}

Does the layer's (encode, decode) require runtime configuration?

#### `public def `[`encode`](#classexot_1_1layer_1_1__base_1_1Layer_1a259d91ddb6fe3e5ccf37e8efbdcbafeb)`(self,encode_input,skip_checks)` {#classexot_1_1layer_1_1__base_1_1Layer_1a259d91ddb6fe3e5ccf37e8efbdcbafeb}

Encode a stream from a preceding layer

#### `public def `[`decode`](#classexot_1_1layer_1_1__base_1_1Layer_1aebe11dc2742b5ad280152089f642cf03)`(self,decode_input,skip_checks)` {#classexot_1_1layer_1_1__base_1_1Layer_1aebe11dc2742b5ad280152089f642cf03}

Decode a stream from a succeeding layer

# namespace `exot::layer::_factory` {#namespaceexot_1_1layer_1_1__factory}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::_factory::LayerFactory`](#classexot_1_1layer_1_1__factory_1_1LayerFactory) | 

# class `exot::layer::_factory::LayerFactory` {#classexot_1_1layer_1_1__factory_1_1LayerFactory}

```
class exot::layer::_factory::LayerFactory
  : public GenericFactory
  : public klass
  : public exot.layer._base.Layer
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::layer::_mixins` {#namespaceexot_1_1layer_1_1__mixins}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::_mixins::RDPmixins`](#classexot_1_1layer_1_1__mixins_1_1RDPmixins) | 

# class `exot::layer::_mixins::RDPmixins` {#classexot_1_1layer_1_1__mixins_1_1RDPmixins}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`cores_and_schedules`](#classexot_1_1layer_1_1__mixins_1_1RDPmixins_1a5bf32a1685d7a4b4818e932b3d54cfe2)`(self)` | Get the cores and schedules set of 2-tuples
`public def `[`cores_and_schedules`](#classexot_1_1layer_1_1__mixins_1_1RDPmixins_1a14728b4b48920a064c234408e246bb15)`(self,value)` | Set the cores and schedules set of 2-tuples

## Members

#### `public def `[`cores_and_schedules`](#classexot_1_1layer_1_1__mixins_1_1RDPmixins_1a5bf32a1685d7a4b4818e932b3d54cfe2)`(self)` {#classexot_1_1layer_1_1__mixins_1_1RDPmixins_1a5bf32a1685d7a4b4818e932b3d54cfe2}

Get the cores and schedules set of 2-tuples

#### `public def `[`cores_and_schedules`](#classexot_1_1layer_1_1__mixins_1_1RDPmixins_1a14728b4b48920a064c234408e246bb15)`(self,value)` {#classexot_1_1layer_1_1__mixins_1_1RDPmixins_1a14728b4b48920a064c234408e246bb15}

Set the cores and schedules set of 2-tuples

# namespace `exot::layer::io::timevalue` {#namespaceexot_1_1layer_1_1io_1_1timevalue}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::io::timevalue::TimeValue`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue) | 

# class `exot::layer::io::timevalue::TimeValue` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue}

```
class exot::layer::io::timevalue::TimeValue
  : public exot.layer._base.Layer
  : public LabelConversions
  : public layer
  : public InputOutput
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`timebase`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a87352e2fc6136ac91d18387f642fdb61) | 
`public  `[`synchronise`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a3a2834bebb5f66f416d142e780b41438) | 
`public  `[`schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a9b6e16063135728fbe93c285fa857869) | 
`public def `[`__init__`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1af9fe8017ce30c84bb69bee4c714195cd)`(self,*str timebase,bool synchronise,** kwargs)` | Initialise the TimeValue I/O layer
`public def `[`validate`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aec200c8307b3e9909788412e104e6220)`(self)` | Validate config
`public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a8550699e45b7bffb13f5378a3cb40873)`(self)` | Does encode/decode require runtime configuration?
`public t.Mapping[str, pd.DataFrame] `[`schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a9da9d70c27c26406d2fcbf12fa15a8f6)`(self)` | Get schedules
`public None `[`schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1af9d469105b2bd6a3d51ac1959049e4d2)`(self,t.Mapping value)` | Set schedules
`public int `[`timebase`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1ae99da3e06427506a048badd50dbacb99)`(self)` | Get the timebase as a number of divisions of a second
`public None `[`timebase`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a45edeadf6fd27245d96715bc26060ab4)`(self,str value)` | Set the timebase with a string representation
`public def `[`synchronise`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a24468bc53a2f9346e3ad820d66bb792a)`(self)` | 
`public def `[`synchronise`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aec218d8803aced582f74560fb3ac3649)`(self,value)` | 
`public t.List[Path] `[`write_schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a851711269ea74d036b9f6f629a3e4878)`(self,t.Mapping schedules)` | Write schedules to files
`public pd.DataFrame `[`get_measurements`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a6cfc4b56326823bfc8bfbeea8cf474c7)`(self,app)` | Get measurements for a specific environment, app and repetition
`public def `[`get_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a90d4326cdffa16f8da260d3c3af92b48)`(self,env,app,rep,* suffix,** kwargs)` | 
`public t.Mapping `[`describe_measurements`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a86b7edb6b9e09fb20a5bb97e3447b51d)`(self,pd.DataFrame data)` | Describe the values contained in a raw measurements DataFrame
`public t.List[str] `[`get_available_environments`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a0c88ccef3f90c3b52289586a71e8bbd7)`(self)` | Get the environments which have logs available
`public t.Mapping `[`get_available_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a077acc2f33f97efba8261aab4067d01a)`(self,glob)` | Get the available logs at the config path that match the chosen glob pattern
`public t.Mapping `[`get_available_app_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a931d983cd134beee1fb0751e09b54529)`(self)` | Get the available app logs at the config path
`public t.Mapping `[`get_available_debug_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aac7e68e80824faa71bb8db7a80fcf4e2)`(self)` | Get the available app logs at the config path

## Members

#### `public  `[`timebase`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a87352e2fc6136ac91d18387f642fdb61) {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a87352e2fc6136ac91d18387f642fdb61}

#### `public  `[`synchronise`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a3a2834bebb5f66f416d142e780b41438) {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a3a2834bebb5f66f416d142e780b41438}

#### `public  `[`schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a9b6e16063135728fbe93c285fa857869) {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a9b6e16063135728fbe93c285fa857869}

#### `public def `[`__init__`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1af9fe8017ce30c84bb69bee4c714195cd)`(self,*str timebase,bool synchronise,** kwargs)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1af9fe8017ce30c84bb69bee4c714195cd}

Initialise the TimeValue I/O layer

Args:
    timebase (str, optional): The timebase, either "s", "ms", "us" or "ns"

#### `public def `[`validate`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aec200c8307b3e9909788412e104e6220)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aec200c8307b3e9909788412e104e6220}

Validate config

Implementation of Configurable's `validate` method

#### `public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a8550699e45b7bffb13f5378a3cb40873)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a8550699e45b7bffb13f5378a3cb40873}

Does encode/decode require runtime configuration?

Encoding needs to be provided:
- "path": run path. (for writing schedules)

Decoding needs to be provided:
- "env": environment name,
- "rep": repetition number,
- "path": run path,
- "matcher": selection specifiers.

#### `public t.Mapping[str, pd.DataFrame] `[`schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a9da9d70c27c26406d2fcbf12fa15a8f6)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a9da9d70c27c26406d2fcbf12fa15a8f6}

Get schedules

#### `public None `[`schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1af9d469105b2bd6a3d51ac1959049e4d2)`(self,t.Mapping value)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1af9d469105b2bd6a3d51ac1959049e4d2}

Set schedules

#### `public int `[`timebase`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1ae99da3e06427506a048badd50dbacb99)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1ae99da3e06427506a048badd50dbacb99}

Get the timebase as a number of divisions of a second

#### `public None `[`timebase`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a45edeadf6fd27245d96715bc26060ab4)`(self,str value)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a45edeadf6fd27245d96715bc26060ab4}

Set the timebase with a string representation

#### `public def `[`synchronise`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a24468bc53a2f9346e3ad820d66bb792a)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a24468bc53a2f9346e3ad820d66bb792a}

#### `public def `[`synchronise`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aec218d8803aced582f74560fb3ac3649)`(self,value)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aec218d8803aced582f74560fb3ac3649}

#### `public t.List[Path] `[`write_schedules`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a851711269ea74d036b9f6f629a3e4878)`(self,t.Mapping schedules)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a851711269ea74d036b9f6f629a3e4878}

Write schedules to files

#### `public pd.DataFrame `[`get_measurements`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a6cfc4b56326823bfc8bfbeea8cf474c7)`(self,app)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a6cfc4b56326823bfc8bfbeea8cf474c7}

Get measurements for a specific environment, app and repetition

Returns:
    pd.DataFrame: a DataFrame constructed from a raw CSV app log

Raises:
    LayerRuntimeError: If an unexpected missing value is encountered
    LayerRuntimeMisconfigured: If a rep or env is not available

#### `public def `[`get_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a90d4326cdffa16f8da260d3c3af92b48)`(self,env,app,rep,* suffix,** kwargs)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a90d4326cdffa16f8da260d3c3af92b48}

#### `public t.Mapping `[`describe_measurements`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a86b7edb6b9e09fb20a5bb97e3447b51d)`(self,pd.DataFrame data)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a86b7edb6b9e09fb20a5bb97e3447b51d}

Describe the values contained in a raw measurements DataFrame

Args:
    data (pd.DataFrame): a measurements DataFrame

Returns:
    t.Mapping: a dict with available parameters

#### `public t.List[str] `[`get_available_environments`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a0c88ccef3f90c3b52289586a71e8bbd7)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a0c88ccef3f90c3b52289586a71e8bbd7}

Get the environments which have logs available

Returns:
    t.List[str]: A list of environment names

#### `public t.Mapping `[`get_available_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a077acc2f33f97efba8261aab4067d01a)`(self,glob)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a077acc2f33f97efba8261aab4067d01a}

Get the available logs at the config path that match the chosen glob pattern

Returns:
    t.Mapping: a mapping env: str -> app: str -> list of file Paths

#### `public t.Mapping `[`get_available_app_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a931d983cd134beee1fb0751e09b54529)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1a931d983cd134beee1fb0751e09b54529}

Get the available app logs at the config path

Returns:
    t.Mapping: a mapping env: str -> app: str -> list of file Paths

#### `public t.Mapping `[`get_available_debug_logs`](#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aac7e68e80824faa71bb8db7a80fcf4e2)`(self)` {#classexot_1_1layer_1_1io_1_1timevalue_1_1TimeValue_1aac7e68e80824faa71bb8db7a80fcf4e2}

Get the available app logs at the config path

Returns:
    t.Mapping: a mapping env: str -> app: str -> list of file Paths

# namespace `exot::layer::lne::edge` {#namespaceexot_1_1layer_1_1lne_1_1edge}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::edge::EdgeLineCoding`](#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding) | 

# class `exot::layer::lne::edge::EdgeLineCoding` {#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding}

```
class exot::layer::lne::edge::EdgeLineCoding
  : public exot.layer.lne.simple.SimpleN
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`threshold`](#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding_1a3fb94c978c446e4217875a71a8cc4270) | 
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding_1ab94f0c4468dd7d7cc27113573944cb14)`(self,* args,int threshold,** kwargs)` | 

## Members

#### `public  `[`threshold`](#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding_1a3fb94c978c446e4217875a71a8cc4270) {#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding_1a3fb94c978c446e4217875a71a8cc4270}

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding_1ab94f0c4468dd7d7cc27113573944cb14)`(self,* args,int threshold,** kwargs)` {#classexot_1_1layer_1_1lne_1_1edge_1_1EdgeLineCoding_1ab94f0c4468dd7d7cc27113573944cb14}

# namespace `exot::layer::lne::frequency_governors` {#namespaceexot_1_1layer_1_1lne_1_1frequency__governors}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::frequency_governors::ConservativeGovLineCoding`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding) | 
`class `[`exot::layer::lne::frequency_governors::FrequencyGovernorLineCoding`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding) | 

# class `exot::layer::lne::frequency_governors::ConservativeGovLineCoding` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding}

```
class exot::layer::lne::frequency_governors::ConservativeGovLineCoding
  : public exot.layer.lne.frequency_governors.FrequencyGovernorLineCoding
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`center`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a7664fb467475258c54dce48677a538ac) | 
`public  `[`step`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1ac4efd50c54cffee9df72a08ea922ff74) | 
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a56e1e7a4b487c59fd22a90fddf5a6dd7)`(self,*int center,int step,** kwargs)` | Initialise the Conservative Governor Line Coding layer
`public def `[`subsymbol_count`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a6205e29e7422cdc4ff52489a96f30415)`(self)` | 
`public def `[`codebook`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a30b00b78f970ca98fea9fa130797428a)`(self)` | 
`public def `[`preamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1adb8ccab94576cf5f0d25378a91b79018)`(self)` | 
`public def `[`postamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a6bdc30ec6c514b6f9fe98554fffa25ef)`(self)` | 

## Members

#### `public  `[`center`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a7664fb467475258c54dce48677a538ac) {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a7664fb467475258c54dce48677a538ac}

#### `public  `[`step`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1ac4efd50c54cffee9df72a08ea922ff74) {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1ac4efd50c54cffee9df72a08ea922ff74}

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a56e1e7a4b487c59fd22a90fddf5a6dd7)`(self,*int center,int step,** kwargs)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a56e1e7a4b487c59fd22a90fddf5a6dd7}

Initialise the Conservative Governor Line Coding layer

Args:

#### `public def `[`subsymbol_count`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a6205e29e7422cdc4ff52489a96f30415)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a6205e29e7422cdc4ff52489a96f30415}

#### `public def `[`codebook`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a30b00b78f970ca98fea9fa130797428a)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a30b00b78f970ca98fea9fa130797428a}

#### `public def `[`preamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1adb8ccab94576cf5f0d25378a91b79018)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1adb8ccab94576cf5f0d25378a91b79018}

#### `public def `[`postamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a6bdc30ec6c514b6f9fe98554fffa25ef)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1ConservativeGovLineCoding_1a6bdc30ec6c514b6f9fe98554fffa25ef}

# class `exot::layer::lne::frequency_governors::FrequencyGovernorLineCoding` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding}

```
class exot::layer::lne::frequency_governors::FrequencyGovernorLineCoding
  : public exot.layer._base.Layer
  : public layer
  : public Line
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a295fbdd451b40287c57100a521c9c614)`(self,* args,** kwargs)` | 
`public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1afdf11ac771d4461bfa41b3d9fea03cc9)`(self,t.T symrate)` | Convert a symbol rate to a subsymbol rate
`public def `[`subsymbol_count`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a057b0c8bf41e4b7669a16b2dd7be989d)`(self)` | 
`public def `[`codebook`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1aa04d3267da15dee863ae4e8f2712a73d)`(self)` | 
`public def `[`preamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a9eba0182c1a43347baaf1b0bf1c1c274)`(self)` | 
`public def `[`postamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1aad93cdd2bfec5ab753faf5e1c1a3a58a)`(self)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a295fbdd451b40287c57100a521c9c614)`(self,* args,** kwargs)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a295fbdd451b40287c57100a521c9c614}

#### `public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1afdf11ac771d4461bfa41b3d9fea03cc9)`(self,t.T symrate)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1afdf11ac771d4461bfa41b3d9fea03cc9}

Convert a symbol rate to a subsymbol rate

#### `public def `[`subsymbol_count`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a057b0c8bf41e4b7669a16b2dd7be989d)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a057b0c8bf41e4b7669a16b2dd7be989d}

#### `public def `[`codebook`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1aa04d3267da15dee863ae4e8f2712a73d)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1aa04d3267da15dee863ae4e8f2712a73d}

#### `public def `[`preamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a9eba0182c1a43347baaf1b0bf1c1c274)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1a9eba0182c1a43347baaf1b0bf1c1c274}

#### `public def `[`postamble`](#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1aad93cdd2bfec5ab753faf5e1c1a3a58a)`(self)` {#classexot_1_1layer_1_1lne_1_1frequency__governors_1_1FrequencyGovernorLineCoding_1aad93cdd2bfec5ab753faf5e1c1a3a58a}

# namespace `exot::layer::lne::generic` {#namespaceexot_1_1layer_1_1lne_1_1generic}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::generic::GenericLineCoding`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding) | 

# class `exot::layer::lne::generic::GenericLineCoding` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding}

```
class exot::layer::lne::generic::GenericLineCoding
  : public exot.layer._base.Layer
  : public layer
  : public Line
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`signal`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1abfab7fce46f72ee1e52466f67eb792d1) | 
`public  `[`samples_per_subsymbol`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0bd18aa3f858f0357e2f6ff19a6c3c9a) | 
`public  `[`demean`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a5bc514a4a44e25eb6b77783bbf0b47f0) | 
`public  `[`flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a929e60838e08f39deee3b4b8c09d9533) | 
`public  `[`saturated`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aa57024e9b78b54b2ba28a8458ca6ebc9) | 
`public  `[`saturate_mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a9d81134d87ddda328335641587594988) | 
`public  `[`decode_flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a829ce7415906e986e308314e46a9ec1c) | 
`public  `[`roll_divisions`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a1f260ac629e93f174b9d4b06f0ac1a43) | 
`public  `[`min_samples`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ab116e55a08ae138ad98ea37e1a7d0cfd) | 
`public  `[`symbol_space_op`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aacd5805a3ef54485c2fcd8a70d01e765) | 
`public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a204e48bd55023951944247143c3265f1) | 
`public t.List[str] `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a38100b967b866d9e8b2e5c82b32b7cee)`(self)` | 
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aca56cfb09e50be46be60c9047d15b909)`(self)` | Implements method `validate` from Configurable
`public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aea63a32f3874e09174905d772ad6d29b)`(self)` | Decoding needs access to 'ideal_symstream'
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0366af22a886352a80366844aba10509)`(self,* args,t.Mapping signal,int samples_per_subsymbol,bool demean,bool flattened,bool saturated,bool decode_flattened,int roll_divisions,int min_samples,t.Callable symbol_space_op,t.Mapping saturate_mapping,** kwargs)` | Initialise the GenericLineCoding object
`public def `[`decode_flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a3bb71206c94c7eecc31d0a8da07fe511)`(self)` | 
`public def `[`roll_divisions`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae77c428cee582444281e6c1df827aba6)`(self)` | 
`public def `[`min_samples`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a1d939f2c39d24dfd2cc20e647860f319)`(self)` | 
`public def `[`symbol_space_op`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a59717f905c593d22d8df1ae667f024fd)`(self)` | 
`public def `[`decode_flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a6cb9b0a1587bd8edd2166fd554926a0f)`(self,value)` | 
`public def `[`roll_divisions`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a03d8d73bb04566094d5020f01105b151)`(self,value)` | 
`public def `[`min_samples`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a82408cba9462b9d4dc06e3fae2c90378)`(self,value)` | 
`public def `[`symbol_space_op`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aec8e692ddbfcb409064987b53baabf4b)`(self,value)` | 
`public t.Mapping[int, int] `[`saturate_mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ace331e8398b57f11cb9c1c806fb046f2)`(self)` | 
`public None `[`saturate_mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a709a97f37edf7d783cd6df24605c9de5)`(self,t.Mapping value)` | 
`public t.Mapping `[`signal`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a9b8b85772dbad9a7fe8b8dddc2b6c201)`(self)` | Get the signal mapping
`public None `[`signal`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a3d3d0d367087db9d2e052945f5b98302)`(self,t.Mapping value)` | Set the signal mapping
`public t.Mapping `[`mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ac7c2e27d7bba2031641fcac3ce34f76a)`(self)` | Gets the symbol-only mapping (signal sans 'carrier')
`public def `[`demean`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1afeaa39bb007f554a9dfd1f790e723cfd)`(self)` | 
`public def `[`demean`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a25b07bd48482eaef3f0b5bcbef7d463e)`(self,value)` | 
`public t.List `[`carrier`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a8a7a8df1c116dab552ae73eb34eb9b64)`(self)` | Gets the carrier
`public bool `[`flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a29c4e45fea170cc52256f5ac16be2faf)`(self)` | Should the output be flattened?
`public None `[`flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ab33db2618316c7fa4c5b4db45cb1d21c)`(self,value)` | Sets the 'flattened' property
`public bool `[`saturated`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a289e7393d562b3482283085c57a9891e)`(self)` | Should the output be saturated?
`public None `[`saturated`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0b3e68a7e06bf3f63924f3a3c7233ea7)`(self,value)` | Sets the 'saturated' property
`public int `[`max_num_symbols`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a18c6e1b28d955be75b204da0f843501e)`(self)` | 
`public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aaf1be1862671169e187d5be2362223bc)`(self,t.T symrate)` | Convert a symbol rate to a subsymbol rate
`public int `[`subsymbol_count`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1af650ffa72ebe1a4275de39f5d1eb922f)`(self)` | Get the number of subsymbols
`public int `[`phase_count`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a5d964e39df22717354f9b4bad156c0ec)`(self)` | 
`public int `[`samples_per_subsymbol`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a93c810a06385a5c225322a0106b72fcb)`(self)` | 
`public t.Optional[object] `[`decision_device`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a53b1f6d336e60dd15274f7b2e3a1902d)`(self)` | 
`public None `[`decision_device`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae4833bdd6a4e8714ea7dce4393cd1691)`(self,value)` | 
`public None `[`samples_per_subsymbol`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a79853a9a2b850cb5772d3a4dd6642c8e)`(self,int value)` | 
`public bool `[`is_compatible`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a171e447fa154bdfb34880136ef63c129)`(self,int num_symbols)` | 
`public np.ndarray `[`create_mask`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ad2a0d32a2ecdb778685f20685abc61cb)`(self,*int samples,str kind)` | Create a mask for symbol space computation
`public np.ndarray `[`create_symbol_space`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1abe917cb3b077918caf495a48e813f133)`(self,np.ndarray data)` | Create a symbol space representation of input data
`public t.Optional[np.ndarray] `[`symbol_space`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae687cb5d417f5701bf83813cba815524)`(self)` | 

## Members

#### `public  `[`signal`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1abfab7fce46f72ee1e52466f67eb792d1) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1abfab7fce46f72ee1e52466f67eb792d1}

#### `public  `[`samples_per_subsymbol`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0bd18aa3f858f0357e2f6ff19a6c3c9a) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0bd18aa3f858f0357e2f6ff19a6c3c9a}

#### `public  `[`demean`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a5bc514a4a44e25eb6b77783bbf0b47f0) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a5bc514a4a44e25eb6b77783bbf0b47f0}

#### `public  `[`flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a929e60838e08f39deee3b4b8c09d9533) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a929e60838e08f39deee3b4b8c09d9533}

#### `public  `[`saturated`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aa57024e9b78b54b2ba28a8458ca6ebc9) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aa57024e9b78b54b2ba28a8458ca6ebc9}

#### `public  `[`saturate_mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a9d81134d87ddda328335641587594988) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a9d81134d87ddda328335641587594988}

#### `public  `[`decode_flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a829ce7415906e986e308314e46a9ec1c) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a829ce7415906e986e308314e46a9ec1c}

#### `public  `[`roll_divisions`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a1f260ac629e93f174b9d4b06f0ac1a43) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a1f260ac629e93f174b9d4b06f0ac1a43}

#### `public  `[`min_samples`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ab116e55a08ae138ad98ea37e1a7d0cfd) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ab116e55a08ae138ad98ea37e1a7d0cfd}

#### `public  `[`symbol_space_op`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aacd5805a3ef54485c2fcd8a70d01e765) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aacd5805a3ef54485c2fcd8a70d01e765}

#### `public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a204e48bd55023951944247143c3265f1) {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a204e48bd55023951944247143c3265f1}

#### `public t.List[str] `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a38100b967b866d9e8b2e5c82b32b7cee)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a38100b967b866d9e8b2e5c82b32b7cee}

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aca56cfb09e50be46be60c9047d15b909)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aca56cfb09e50be46be60c9047d15b909}

Implements method `validate` from Configurable

Raises:
    LayerMisconfigured: If wrong symstream was provided

#### `public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aea63a32f3874e09174905d772ad6d29b)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aea63a32f3874e09174905d772ad6d29b}

Decoding needs access to 'ideal_symstream'

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0366af22a886352a80366844aba10509)`(self,* args,t.Mapping signal,int samples_per_subsymbol,bool demean,bool flattened,bool saturated,bool decode_flattened,int roll_divisions,int min_samples,t.Callable symbol_space_op,t.Mapping saturate_mapping,** kwargs)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0366af22a886352a80366844aba10509}

Initialise the GenericLineCoding object

Args:
    *args: passthrough...
    signal (t.Mapping): a signal mapping
    samples_per_subsymbol (int, optional): default number of samples/subsymbol
    flattened (bool, optional): operates in flattened mode?
    saturated (bool, optional): saturate the output?
    symbol_to_saturate (int, optional): symbol to saturate, e.g. 1
    saturate_replacement_symbol (int, optional): replacement symbol, e.g. -1
    **kwargs: passthrough...

#### `public def `[`decode_flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a3bb71206c94c7eecc31d0a8da07fe511)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a3bb71206c94c7eecc31d0a8da07fe511}

#### `public def `[`roll_divisions`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae77c428cee582444281e6c1df827aba6)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae77c428cee582444281e6c1df827aba6}

#### `public def `[`min_samples`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a1d939f2c39d24dfd2cc20e647860f319)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a1d939f2c39d24dfd2cc20e647860f319}

#### `public def `[`symbol_space_op`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a59717f905c593d22d8df1ae667f024fd)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a59717f905c593d22d8df1ae667f024fd}

#### `public def `[`decode_flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a6cb9b0a1587bd8edd2166fd554926a0f)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a6cb9b0a1587bd8edd2166fd554926a0f}

#### `public def `[`roll_divisions`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a03d8d73bb04566094d5020f01105b151)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a03d8d73bb04566094d5020f01105b151}

#### `public def `[`min_samples`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a82408cba9462b9d4dc06e3fae2c90378)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a82408cba9462b9d4dc06e3fae2c90378}

#### `public def `[`symbol_space_op`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aec8e692ddbfcb409064987b53baabf4b)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aec8e692ddbfcb409064987b53baabf4b}

#### `public t.Mapping[int, int] `[`saturate_mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ace331e8398b57f11cb9c1c806fb046f2)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ace331e8398b57f11cb9c1c806fb046f2}

#### `public None `[`saturate_mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a709a97f37edf7d783cd6df24605c9de5)`(self,t.Mapping value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a709a97f37edf7d783cd6df24605c9de5}

#### `public t.Mapping `[`signal`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a9b8b85772dbad9a7fe8b8dddc2b6c201)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a9b8b85772dbad9a7fe8b8dddc2b6c201}

Get the signal mapping

Returns:
    t.Mapping: a mapping, same as Channel's signal

#### `public None `[`signal`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a3d3d0d367087db9d2e052945f5b98302)`(self,t.Mapping value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a3d3d0d367087db9d2e052945f5b98302}

Set the signal mapping

Args:
    value (t.Mapping): a mapping with symbols and a 'carrier'

Raises:
    LayerMisconfigured: If incompatible value is provided

#### `public t.Mapping `[`mapping`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ac7c2e27d7bba2031641fcac3ce34f76a)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ac7c2e27d7bba2031641fcac3ce34f76a}

Gets the symbol-only mapping (signal sans 'carrier')

#### `public def `[`demean`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1afeaa39bb007f554a9dfd1f790e723cfd)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1afeaa39bb007f554a9dfd1f790e723cfd}

#### `public def `[`demean`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a25b07bd48482eaef3f0b5bcbef7d463e)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a25b07bd48482eaef3f0b5bcbef7d463e}

#### `public t.List `[`carrier`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a8a7a8df1c116dab552ae73eb34eb9b64)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a8a7a8df1c116dab552ae73eb34eb9b64}

Gets the carrier

#### `public bool `[`flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a29c4e45fea170cc52256f5ac16be2faf)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a29c4e45fea170cc52256f5ac16be2faf}

Should the output be flattened?

#### `public None `[`flattened`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ab33db2618316c7fa4c5b4db45cb1d21c)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ab33db2618316c7fa4c5b4db45cb1d21c}

Sets the 'flattened' property

#### `public bool `[`saturated`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a289e7393d562b3482283085c57a9891e)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a289e7393d562b3482283085c57a9891e}

Should the output be saturated?

#### `public None `[`saturated`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0b3e68a7e06bf3f63924f3a3c7233ea7)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a0b3e68a7e06bf3f63924f3a3c7233ea7}

Sets the 'saturated' property

#### `public int `[`max_num_symbols`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a18c6e1b28d955be75b204da0f843501e)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a18c6e1b28d955be75b204da0f843501e}

#### `public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aaf1be1862671169e187d5be2362223bc)`(self,t.T symrate)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1aaf1be1862671169e187d5be2362223bc}

Convert a symbol rate to a subsymbol rate

#### `public int `[`subsymbol_count`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1af650ffa72ebe1a4275de39f5d1eb922f)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1af650ffa72ebe1a4275de39f5d1eb922f}

Get the number of subsymbols

#### `public int `[`phase_count`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a5d964e39df22717354f9b4bad156c0ec)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a5d964e39df22717354f9b4bad156c0ec}

#### `public int `[`samples_per_subsymbol`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a93c810a06385a5c225322a0106b72fcb)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a93c810a06385a5c225322a0106b72fcb}

#### `public t.Optional[object] `[`decision_device`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a53b1f6d336e60dd15274f7b2e3a1902d)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a53b1f6d336e60dd15274f7b2e3a1902d}

#### `public None `[`decision_device`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae4833bdd6a4e8714ea7dce4393cd1691)`(self,value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae4833bdd6a4e8714ea7dce4393cd1691}

#### `public None `[`samples_per_subsymbol`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a79853a9a2b850cb5772d3a4dd6642c8e)`(self,int value)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a79853a9a2b850cb5772d3a4dd6642c8e}

#### `public bool `[`is_compatible`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a171e447fa154bdfb34880136ef63c129)`(self,int num_symbols)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1a171e447fa154bdfb34880136ef63c129}

#### `public np.ndarray `[`create_mask`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ad2a0d32a2ecdb778685f20685abc61cb)`(self,*int samples,str kind)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ad2a0d32a2ecdb778685f20685abc61cb}

Create a mask for symbol space computation

Args:
    samples (int, optional): number of samples per subsymbol
    kind (str, optional): interpolation method

Returns:
    np.ndarray: a mask of shape: subsymbol_count * samples, phase_count

#### `public np.ndarray `[`create_symbol_space`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1abe917cb3b077918caf495a48e813f133)`(self,np.ndarray data)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1abe917cb3b077918caf495a48e813f133}

Create a symbol space representation of input data

Args:
    data (np.ndarray): a 2-d array

Returns:
    np.ndarray: a symbol space or shape: data.shape[0], phase_count

#### `public t.Optional[np.ndarray] `[`symbol_space`](#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae687cb5d417f5701bf83813cba815524)`(self)` {#classexot_1_1layer_1_1lne_1_1generic_1_1GenericLineCoding_1ae687cb5d417f5701bf83813cba815524}

# namespace `exot::layer::lne::label_refactoring` {#namespaceexot_1_1layer_1_1lne_1_1label__refactoring}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::label_refactoring::LabelRefactoring`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring) | 
`class `[`exot::layer::lne::label_refactoring::ThermalLabelRefactoring`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring) | 

# class `exot::layer::lne::label_refactoring::LabelRefactoring` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring}

```
class exot::layer::lne::label_refactoring::LabelRefactoring
  : public exot.layer._base.Layer
  : public layer
  : public Line
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a7a703ec8d4e8d6f0f28a56e704a284a4)`(self,** kwargs)` | 
`public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a6624e8b068ce40da4e1a049edc30a382)`(self)` | Does the layer's (encode, decode) require runtime configuration?
`public def `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1ae68ade2615601362ad0487b041da2b7e)`(self)` | The required config keys
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a2a695fd19e42398fbdaf3ee86b8cd2a1)`(self)` | Implementation of Configurable's `validate`
`public def `[`augment`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a72ba6c915a0e114138f3ef4f9931bf83)`(self,* args,** kwargs)` | This method defines how the transitions are treated if parts have been removed due to the option remove_unknown

## Members

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a7a703ec8d4e8d6f0f28a56e704a284a4)`(self,** kwargs)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a7a703ec8d4e8d6f0f28a56e704a284a4}

#### `public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a6624e8b068ce40da4e1a049edc30a382)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a6624e8b068ce40da4e1a049edc30a382}

Does the layer's (encode, decode) require runtime configuration?

#### `public def `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1ae68ade2615601362ad0487b041da2b7e)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1ae68ade2615601362ad0487b041da2b7e}

The required config keys

Implements the `required_config_keys` from Configurable base class

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a2a695fd19e42398fbdaf3ee86b8cd2a1)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a2a695fd19e42398fbdaf3ee86b8cd2a1}

Implementation of Configurable's `validate`

#### `public def `[`augment`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a72ba6c915a0e114138f3ef4f9931bf83)`(self,* args,** kwargs)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1LabelRefactoring_1a72ba6c915a0e114138f3ef4f9931bf83}

This method defines how the transitions are treated if parts have been removed due to the option remove_unknown

# class `exot::layer::lne::label_refactoring::ThermalLabelRefactoring` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring}

```
class exot::layer::lne::label_refactoring::ThermalLabelRefactoring
  : public exot.layer.lne.label_refactoring.LabelRefactoring
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`beta_z`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1ad3c6603893dce71ff9119ef2406b1390)`(self)` | 
`public def `[`beta_z_heat`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a09a92f5b64577fc2f0e2cdd62205cb67)`(self)` | 
`public def `[`beta_z_cool`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a9e17cbe1067cc421f11b472b891a1faa)`(self)` | 
`public def `[`T_idle`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a40f3e65342f1a0f0d53c2205d7978728)`(self)` | 
`public def `[`np_beta_z`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1aa62f9a99a443a4c32476d540d1c070ee)`(self)` | 
`public def `[`np_T_idle`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1af65ef51750d00cb533026272c7cd7981)`(self)` | 
`public def `[`augment`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1af6965a5ebf716127d5329d01a3792602)`(self,* args,** kwargs)` | This method defines how the transitions are treated if parts have been removed due to the option remove_unknown

## Members

#### `public def `[`beta_z`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1ad3c6603893dce71ff9119ef2406b1390)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1ad3c6603893dce71ff9119ef2406b1390}

#### `public def `[`beta_z_heat`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a09a92f5b64577fc2f0e2cdd62205cb67)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a09a92f5b64577fc2f0e2cdd62205cb67}

#### `public def `[`beta_z_cool`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a9e17cbe1067cc421f11b472b891a1faa)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a9e17cbe1067cc421f11b472b891a1faa}

#### `public def `[`T_idle`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a40f3e65342f1a0f0d53c2205d7978728)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1a40f3e65342f1a0f0d53c2205d7978728}

#### `public def `[`np_beta_z`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1aa62f9a99a443a4c32476d540d1c070ee)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1aa62f9a99a443a4c32476d540d1c070ee}

#### `public def `[`np_T_idle`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1af65ef51750d00cb533026272c7cd7981)`(self)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1af65ef51750d00cb533026272c7cd7981}

#### `public def `[`augment`](#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1af6965a5ebf716127d5329d01a3792602)`(self,* args,** kwargs)` {#classexot_1_1layer_1_1lne_1_1label__refactoring_1_1ThermalLabelRefactoring_1af6965a5ebf716127d5329d01a3792602}

This method defines how the transitions are treated if parts have been removed due to the option remove_unknown

# namespace `exot::layer::lne::manchester` {#namespaceexot_1_1layer_1_1lne_1_1manchester}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::manchester::ManchesterLineCoding`](#classexot_1_1layer_1_1lne_1_1manchester_1_1ManchesterLineCoding) | 

# class `exot::layer::lne::manchester::ManchesterLineCoding` {#classexot_1_1layer_1_1lne_1_1manchester_1_1ManchesterLineCoding}

```
class exot::layer::lne::manchester::ManchesterLineCoding
  : public exot.layer.lne.generic.GenericLineCoding
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1manchester_1_1ManchesterLineCoding_1a2a4d7d6fe2775e7d5fcd56027cf10d5f)`(self,* args,** kwargs)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1manchester_1_1ManchesterLineCoding_1a2a4d7d6fe2775e7d5fcd56027cf10d5f)`(self,* args,** kwargs)` {#classexot_1_1layer_1_1lne_1_1manchester_1_1ManchesterLineCoding_1a2a4d7d6fe2775e7d5fcd56027cf10d5f}

# namespace `exot::layer::lne::median` {#namespaceexot_1_1layer_1_1lne_1_1median}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::median::MedianLineCoding`](#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding) | 

# class `exot::layer::lne::median::MedianLineCoding` {#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding}

```
class exot::layer::lne::median::MedianLineCoding
  : public exot.layer.lne.simple.SimpleN
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1a68bc66ac5d11623324cc566d9a57dc08) | 
`public np.ndarray `[`create_symbol_space`](#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1a39ff39f3ea3e57d2d109583d0853b6dc)`(self,np.ndarray data)` | Create a symbol space representation of input data
`public t.Optional[np.ndarray] `[`symbol_space`](#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1aaf54dbb2eef46c9dba7b6828eefae39b)`(self)` | 

## Members

#### `public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1a68bc66ac5d11623324cc566d9a57dc08) {#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1a68bc66ac5d11623324cc566d9a57dc08}

#### `public np.ndarray `[`create_symbol_space`](#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1a39ff39f3ea3e57d2d109583d0853b6dc)`(self,np.ndarray data)` {#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1a39ff39f3ea3e57d2d109583d0853b6dc}

Create a symbol space representation of input data

Args:
    data (np.ndarray): a 2-d array

Returns:
    np.ndarray: a symbol space or shape: data.shape[0], phase_count

#### `public t.Optional[np.ndarray] `[`symbol_space`](#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1aaf54dbb2eef46c9dba7b6828eefae39b)`(self)` {#classexot_1_1layer_1_1lne_1_1median_1_1MedianLineCoding_1aaf54dbb2eef46c9dba7b6828eefae39b}

# namespace `exot::layer::lne::multi` {#namespaceexot_1_1layer_1_1lne_1_1multi}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::multi::MultiN`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN) | 

# class `exot::layer::lne::multi::MultiN` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN}

```
class exot::layer::lne::multi::MultiN
  : public exot.layer._base.Layer
  : public layer
  : public Line
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`N_factor`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1aef9a0f6bb66343b57a002f5d8736b8fd) | 
`public  `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a5653f3160717e65f822c6d0578108a27) | 
`public  `[`reducer`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a3c9b3947b0170df45f7b75fd36915651) | 
`public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a8a73c090c10c966e43934a808ec5357b) | 
`public t.List[str] `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ac0219dc483b9be519db3467a118698be)`(self)` | 
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1af511f7ada7cdd3c429357b0e9b3709ad)`(self)` | Implements method `validate` from Configurable
`public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a8f4702e06cd774b6bb18843067aca28f)`(self)` | Decoding needs access to 'ideal_symstream'
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a67e0ac3077a6ad172ecd1503d737ce12)`(self,* args,int N,decision_device,reducer,** kwargs)` | 
`public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a08440d11293afcba5067dad6d9278809)`(self)` | 
`public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a112a48c0971621a104a930ac67783139)`(self,value)` | 
`public int `[`max_num_symbols`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ad7dd3b30e8dea655b6deab72a7e8b12e)`(self)` | 
`public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a5f410db50362124b2dcc3d70361102e1)`(self,t.T symrate)` | 
`public t.Optional[object] `[`decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1af58224923525581fce4773f28c2405cd)`(self)` | 
`public None `[`decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ae9d51a737253c75066e36b8ca4d70be1)`(self,value)` | 
`public t.Optional[object] `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a2ee56a1368ae5e5fdc82d31448a29927)`(self)` | 
`public None `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a4b270d54ab555d0e174e9101d56f51f8)`(self,value)` | 
`public bool `[`is_compatible`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a32a368a064d70e549c8dffa27217d409)`(self,int num_symbols)` | 
`public def `[`reducer`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ac90e30596470e1bd134ab4f93a6bc033)`(self)` | 
`public def `[`reducer`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ad19e1d57fa3a71c6a2f10bb1c12f90b0)`(self,value)` | 

## Members

#### `public  `[`N_factor`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1aef9a0f6bb66343b57a002f5d8736b8fd) {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1aef9a0f6bb66343b57a002f5d8736b8fd}

#### `public  `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a5653f3160717e65f822c6d0578108a27) {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a5653f3160717e65f822c6d0578108a27}

#### `public  `[`reducer`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a3c9b3947b0170df45f7b75fd36915651) {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a3c9b3947b0170df45f7b75fd36915651}

#### `public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a8a73c090c10c966e43934a808ec5357b) {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a8a73c090c10c966e43934a808ec5357b}

#### `public t.List[str] `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ac0219dc483b9be519db3467a118698be)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ac0219dc483b9be519db3467a118698be}

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1af511f7ada7cdd3c429357b0e9b3709ad)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1af511f7ada7cdd3c429357b0e9b3709ad}

Implements method `validate` from Configurable

Raises:
    LayerMisconfigured: If wrong symstream was provided

#### `public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a8f4702e06cd774b6bb18843067aca28f)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a8f4702e06cd774b6bb18843067aca28f}

Decoding needs access to 'ideal_symstream'

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a67e0ac3077a6ad172ecd1503d737ce12)`(self,* args,int N,decision_device,reducer,** kwargs)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a67e0ac3077a6ad172ecd1503d737ce12}

#### `public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a08440d11293afcba5067dad6d9278809)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a08440d11293afcba5067dad6d9278809}

#### `public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a112a48c0971621a104a930ac67783139)`(self,value)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a112a48c0971621a104a930ac67783139}

#### `public int `[`max_num_symbols`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ad7dd3b30e8dea655b6deab72a7e8b12e)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ad7dd3b30e8dea655b6deab72a7e8b12e}

#### `public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a5f410db50362124b2dcc3d70361102e1)`(self,t.T symrate)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a5f410db50362124b2dcc3d70361102e1}

#### `public t.Optional[object] `[`decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1af58224923525581fce4773f28c2405cd)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1af58224923525581fce4773f28c2405cd}

#### `public None `[`decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ae9d51a737253c75066e36b8ca4d70be1)`(self,value)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ae9d51a737253c75066e36b8ca4d70be1}

#### `public t.Optional[object] `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a2ee56a1368ae5e5fdc82d31448a29927)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a2ee56a1368ae5e5fdc82d31448a29927}

#### `public None `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a4b270d54ab555d0e174e9101d56f51f8)`(self,value)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a4b270d54ab555d0e174e9101d56f51f8}

#### `public bool `[`is_compatible`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a32a368a064d70e549c8dffa27217d409)`(self,int num_symbols)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1a32a368a064d70e549c8dffa27217d409}

#### `public def `[`reducer`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ac90e30596470e1bd134ab4f93a6bc033)`(self)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ac90e30596470e1bd134ab4f93a6bc033}

#### `public def `[`reducer`](#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ad19e1d57fa3a71c6a2f10bb1c12f90b0)`(self,value)` {#classexot_1_1layer_1_1lne_1_1multi_1_1MultiN_1ad19e1d57fa3a71c6a2f10bb1c12f90b0}

# namespace `exot::layer::lne::passthrough` {#namespaceexot_1_1layer_1_1lne_1_1passthrough}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::passthrough::PassthroughLineCoding`](#classexot_1_1layer_1_1lne_1_1passthrough_1_1PassthroughLineCoding) | 

# class `exot::layer::lne::passthrough::PassthroughLineCoding` {#classexot_1_1layer_1_1lne_1_1passthrough_1_1PassthroughLineCoding}

```
class exot::layer::lne::passthrough::PassthroughLineCoding
  : public exot.layer._base.Layer
  : public layer
  : public Line
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1passthrough_1_1PassthroughLineCoding_1af381aeaf381a031700aa9be2336b537f)`(self,symrate)` | 

## Members

#### `public def `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1passthrough_1_1PassthroughLineCoding_1af381aeaf381a031700aa9be2336b537f)`(self,symrate)` {#classexot_1_1layer_1_1lne_1_1passthrough_1_1PassthroughLineCoding_1af381aeaf381a031700aa9be2336b537f}

# namespace `exot::layer::lne::simple` {#namespaceexot_1_1layer_1_1lne_1_1simple}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::lne::simple::SimpleN`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN) | 

# class `exot::layer::lne::simple::SimpleN` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN}

```
class exot::layer::lne::simple::SimpleN
  : public exot.layer._base.Layer
  : public layer
  : public Line
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`N_factor`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a92bb9b90210b02c2a9e105b52d8cd01a) | 
`public  `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1ad23afd6323422f2d634cfd8f7b315849) | 
`public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a78b65ea9efd0d5307c4fedfb4b48cdd9) | 
`public t.List[str] `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aa11af079c54b84ad9bcdd1fb41a7ee0b)`(self)` | 
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a4250d9a26e284fc2972a4e26d31a4f9f)`(self)` | Implements method `validate` from Configurable
`public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aaf8bd0abdb8c61b4425e514c55151c01)`(self)` | Decoding needs access to 'ideal_symstream'
`public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1abf425c40e7ef9a0ee247fc9879107594)`(self,* args,int N,t.Type decision_device,** kwargs)` | 
`public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a16d559ee6da1a23494d2a117079626ab)`(self)` | 
`public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a21e207e2594ac93174166ac3a60605f6)`(self,value)` | 
`public int `[`max_num_symbols`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a717e6324f10e1abbb8f0e38769de3255)`(self)` | 
`public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aca037843ce0ba8c5dacc1d558c87e6e1)`(self,t.T symrate)` | 
`public t.Optional[object] `[`decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a2cae6eefcd87c51c1e8305ae13047087)`(self)` | 
`public None `[`decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a6b5c89fb5ccbec0e9c9aee17676df9ce)`(self,value)` | 
`public t.Optional[object] `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a3fa63c3d2242d3456bd60ddbb747223e)`(self)` | 
`public None `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1ac8f32a4f554c76c3da8456384ff680bf)`(self,value)` | 
`public bool `[`is_compatible`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a9846821c2f467825dc097d9ce782d349)`(self,int num_symbols)` | 

## Members

#### `public  `[`N_factor`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a92bb9b90210b02c2a9e105b52d8cd01a) {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a92bb9b90210b02c2a9e105b52d8cd01a}

#### `public  `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1ad23afd6323422f2d634cfd8f7b315849) {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1ad23afd6323422f2d634cfd8f7b315849}

#### `public  `[`decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a78b65ea9efd0d5307c4fedfb4b48cdd9) {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a78b65ea9efd0d5307c4fedfb4b48cdd9}

#### `public t.List[str] `[`required_config_keys`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aa11af079c54b84ad9bcdd1fb41a7ee0b)`(self)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aa11af079c54b84ad9bcdd1fb41a7ee0b}

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a4250d9a26e284fc2972a4e26d31a4f9f)`(self)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a4250d9a26e284fc2972a4e26d31a4f9f}

Implements method `validate` from Configurable

Raises:
    LayerMisconfigured: If wrong symstream was provided

#### `public bool `[`requires_runtime_config`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aaf8bd0abdb8c61b4425e514c55151c01)`(self)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aaf8bd0abdb8c61b4425e514c55151c01}

Decoding needs access to 'ideal_symstream'

#### `public def `[`__init__`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1abf425c40e7ef9a0ee247fc9879107594)`(self,* args,int N,t.Type decision_device,** kwargs)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1abf425c40e7ef9a0ee247fc9879107594}

#### `public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a16d559ee6da1a23494d2a117079626ab)`(self)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a16d559ee6da1a23494d2a117079626ab}

#### `public def `[`N_factor`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a21e207e2594ac93174166ac3a60605f6)`(self,value)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a21e207e2594ac93174166ac3a60605f6}

#### `public int `[`max_num_symbols`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a717e6324f10e1abbb8f0e38769de3255)`(self)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a717e6324f10e1abbb8f0e38769de3255}

#### `public t.T `[`symrate_to_subsymrate`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aca037843ce0ba8c5dacc1d558c87e6e1)`(self,t.T symrate)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1aca037843ce0ba8c5dacc1d558c87e6e1}

#### `public t.Optional[object] `[`decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a2cae6eefcd87c51c1e8305ae13047087)`(self)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a2cae6eefcd87c51c1e8305ae13047087}

#### `public None `[`decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a6b5c89fb5ccbec0e9c9aee17676df9ce)`(self,value)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a6b5c89fb5ccbec0e9c9aee17676df9ce}

#### `public t.Optional[object] `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a3fa63c3d2242d3456bd60ddbb747223e)`(self)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a3fa63c3d2242d3456bd60ddbb747223e}

#### `public None `[`default_decision_device`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1ac8f32a4f554c76c3da8456384ff680bf)`(self,value)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1ac8f32a4f554c76c3da8456384ff680bf}

#### `public bool `[`is_compatible`](#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a9846821c2f467825dc097d9ce782d349)`(self,int num_symbols)` {#classexot_1_1layer_1_1lne_1_1simple_1_1SimpleN_1a9846821c2f467825dc097d9ce782d349}

# namespace `exot::layer::rdp::cacheactivation` {#namespaceexot_1_1layer_1_1rdp_1_1cacheactivation}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public set `[`get_cache_set_counts`](#cacheactivation_8py_1a8637419366291886ff37160439255b04)`(t.Mapping environments_apps_zones)`            | Extracts the set_count value from experiment app configurations
`public float `[`row_mean`](#cacheactivation_8py_1abf2e1066f4922f39a3f2c4bbd3318399)`(np.ndarray x)`            | 
`class `[`exot::layer::rdp::cacheactivation::CacheActivation`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation) | 

## Members

#### `public set `[`get_cache_set_counts`](#cacheactivation_8py_1a8637419366291886ff37160439255b04)`(t.Mapping environments_apps_zones)` {#cacheactivation_8py_1a8637419366291886ff37160439255b04}

Extracts the set_count value from experiment app configurations

Args:
    environments_apps_zones (t.Mapping): The mapping env -> app -> zone

Returns:
    set: A set with (set-count, schedule-tag) pairs

Raises:
    LayerMisconfigured: If field not found in the config.

#### `public float `[`row_mean`](#cacheactivation_8py_1abf2e1066f4922f39a3f2c4bbd3318399)`(np.ndarray x)` {#cacheactivation_8py_1abf2e1066f4922f39a3f2c4bbd3318399}

# class `exot::layer::rdp::cacheactivation::CacheActivation` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation}

```
class exot::layer::rdp::cacheactivation::CacheActivation
  : public exot.layer._base.Layer
  : public layer
  : public PrePost
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a0fa74c69e31d748741da2153b6526404) | 
`public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a1483168e842bcbbf9870e34a81b766f6) | 
`public  `[`saturating`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a208e229866832b7e537cf67b3b29dff5) | 
`public  `[`reducer`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a7f45c7ca0b414f9b954b1419eb249d1c) | 
`public  `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a50a7e2b3553d8026e51136c3c5fa1fcd) | 
`public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a0461fe1f3fc0199a06582b408678ab09)`(self,*float sampling_period,t.Mapping environments_apps_zones,bool saturating,t.Callable reducer,** kwargs)` | Initialise the CacheActivation RDP layer
`public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a2b7a84107d244588d3b2201d3563c6ed)`(self)` | Does the layer's (encode, decode) require runtime configuration?
`public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1ab1db24f683aaa9e5ad4d7ef9df0abc3e)`(self)` | The required config keys
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a1fbc1fcabb7ede84349a15a7aff44bc7)`(self)` | Implementation of Configurable's `validate`
`public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a3fb30cf98f4ce35b6a9730037d0f67f5)`(self)` | Get the sampling period
`public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a515b86861c309f7ac31cd40c673ea54d)`(self,value)` | Set the sampling period
`public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a93cd120316cd5be6e0848768ce8f3ec1)`(self)` | Get the cache set count and schedules set of 2-tuples
`public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a230667ec1c337eaa1a81f81b3e065683)`(self,value)` | Set the cache set count and schedules set of 2-tuples
`public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1ae79b3a6b1bf39b3ec4961f2091a59cc6)`(self)` | Is the layer operating in the saturating mode?
`public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a9903e60548822431aa24dc25a283e89f)`(self,value)` | Set the saturating property
`public t.Optional[t.Callable] `[`timing_interpolator`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1aeb7e825ad02c244cc328ab0196932637)`(self)` | Get the timing interpolator
`public t.Optional[t.Callable] `[`values_interpolator`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a90698c3e0556e9c502c3769a42448830)`(self)` | Get the values interpolator
`public np.ndarray `[`decode_timestamps`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a354a21ac8b982247dd92acfcc01d5729)`(self)` | Get the timestamps of the resampled and reshaped rdpstream

## Members

#### `public  `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a0fa74c69e31d748741da2153b6526404) {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a0fa74c69e31d748741da2153b6526404}

#### `public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a1483168e842bcbbf9870e34a81b766f6) {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a1483168e842bcbbf9870e34a81b766f6}

#### `public  `[`saturating`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a208e229866832b7e537cf67b3b29dff5) {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a208e229866832b7e537cf67b3b29dff5}

#### `public  `[`reducer`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a7f45c7ca0b414f9b954b1419eb249d1c) {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a7f45c7ca0b414f9b954b1419eb249d1c}

#### `public  `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a50a7e2b3553d8026e51136c3c5fa1fcd) {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a50a7e2b3553d8026e51136c3c5fa1fcd}

#### `public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a0461fe1f3fc0199a06582b408678ab09)`(self,*float sampling_period,t.Mapping environments_apps_zones,bool saturating,t.Callable reducer,** kwargs)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a0461fe1f3fc0199a06582b408678ab09}

Initialise the CacheActivation RDP layer

Args:
    sampling_period (float): the sink app's sampling period
    environments_apps_zones (t.Mapping): the env->app->zone mapping
    saturating (bool, optional): is configured as saturating?
    reducer (t.Callable, optional): function that reduces rows to single column
    **kwargs: unused

#### `public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a2b7a84107d244588d3b2201d3563c6ed)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a2b7a84107d244588d3b2201d3563c6ed}

Does the layer's (encode, decode) require runtime configuration?

#### `public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1ab1db24f683aaa9e5ad4d7ef9df0abc3e)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1ab1db24f683aaa9e5ad4d7ef9df0abc3e}

The required config keys

Implements the `required_config_keys` from Configurable base class

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a1fbc1fcabb7ede84349a15a7aff44bc7)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a1fbc1fcabb7ede84349a15a7aff44bc7}

Implementation of Configurable's `validate`

#### `public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a3fb30cf98f4ce35b6a9730037d0f67f5)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a3fb30cf98f4ce35b6a9730037d0f67f5}

Get the sampling period

#### `public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a515b86861c309f7ac31cd40c673ea54d)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a515b86861c309f7ac31cd40c673ea54d}

Set the sampling period

#### `public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a93cd120316cd5be6e0848768ce8f3ec1)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a93cd120316cd5be6e0848768ce8f3ec1}

Get the cache set count and schedules set of 2-tuples

#### `public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a230667ec1c337eaa1a81f81b3e065683)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a230667ec1c337eaa1a81f81b3e065683}

Set the cache set count and schedules set of 2-tuples

#### `public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1ae79b3a6b1bf39b3ec4961f2091a59cc6)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1ae79b3a6b1bf39b3ec4961f2091a59cc6}

Is the layer operating in the saturating mode?

#### `public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a9903e60548822431aa24dc25a283e89f)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a9903e60548822431aa24dc25a283e89f}

Set the saturating property

#### `public t.Optional[t.Callable] `[`timing_interpolator`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1aeb7e825ad02c244cc328ab0196932637)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1aeb7e825ad02c244cc328ab0196932637}

Get the timing interpolator

Returns:
    t.Optional[t.Callable]: the interpolator function, if available

#### `public t.Optional[t.Callable] `[`values_interpolator`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a90698c3e0556e9c502c3769a42448830)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a90698c3e0556e9c502c3769a42448830}

Get the values interpolator

Returns:
    t.Optional[t.Callable]: the interpolator function, if available

#### `public np.ndarray `[`decode_timestamps`](#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a354a21ac8b982247dd92acfcc01d5729)`(self)` {#classexot_1_1layer_1_1rdp_1_1cacheactivation_1_1CacheActivation_1a354a21ac8b982247dd92acfcc01d5729}

Get the timestamps of the resampled and reshaped rdpstream

Notes:
-   For plotting, one might want to access the 0-th index of the returned array.

Returns:
    np.ndarray: 2-d array of same size as the output of `decode`.

# namespace `exot::layer::rdp::coreactivation` {#namespaceexot_1_1layer_1_1rdp_1_1coreactivation}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::rdp::coreactivation::CoreActivation`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation) | 

# class `exot::layer::rdp::coreactivation::CoreActivation` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation}

```
class exot::layer::rdp::coreactivation::CoreActivation
  : public exot.layer._mixins.RDPmixins
  : public exot.layer._base.Layer
  : public layer
  : public PrePost
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`interpolation`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a9772bb99f4875a8a21ba6cb2cf362e2f) | 
`public  `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1af2a69fa5bcc5a306f7ca26ac49e63b6d) | 
`public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1ae4bb2963375bb1893c06b0e6e99080a1) | 
`public  `[`saturating`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a3043319c4184110f12d78b84ddd4d180) | 
`public  `[`cores_and_schedules`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a363529a5e1b26b56771e4d9fda22881f) | 
`public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1aab22dba8229fbca0b2abb342ab3dbb56)`(self,*float sampling_period,t.Mapping environments_apps_zones,bool saturating,str interpolation,** kwargs)` | Initialise the CoreActivation RDP layer
`public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a011615bbf50dc442fb3210287cb2288b)`(self)` | Does the layer's (encode, decode) require runtime configuration?
`public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a1949179d021a14026c128ada72e20a03)`(self)` | The required config keys
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a2c116a57f6180fb7c05ad21e925381eb)`(self)` | Implementation of Configurable's `validate`
`public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a2d17f4726e4a0faa9fc7df19e650603d)`(self)` | Get the sampling period
`public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a85bfb4490569e5e9997e902834ad1dfb)`(self,value)` | Set the sampling period
`public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a048793749baf0319814a62183209a448)`(self)` | Is the layer operating in the saturating mode?
`public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a23ac66761d4651bb2283dd5da199869d)`(self,value)` | Set the saturating property
`public t.Optional[t.Callable] `[`timing_interpolator`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a772c0237bf2729164f9ba84fd695c1c6)`(self)` | Get the timing interpolator
`public t.Optional[t.Callable] `[`values_interpolator`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a0d34fc08eebcec2ab1fff7e347aaef42)`(self)` | Get the values interpolator
`public np.ndarray `[`decode_timestamps`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1ae94831b0ba8830ff93cdfb76868ef4a0)`(self)` | Get the timestamps of the resampled and reshaped rdpstream

## Members

#### `public  `[`interpolation`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a9772bb99f4875a8a21ba6cb2cf362e2f) {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a9772bb99f4875a8a21ba6cb2cf362e2f}

#### `public  `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1af2a69fa5bcc5a306f7ca26ac49e63b6d) {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1af2a69fa5bcc5a306f7ca26ac49e63b6d}

#### `public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1ae4bb2963375bb1893c06b0e6e99080a1) {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1ae4bb2963375bb1893c06b0e6e99080a1}

#### `public  `[`saturating`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a3043319c4184110f12d78b84ddd4d180) {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a3043319c4184110f12d78b84ddd4d180}

#### `public  `[`cores_and_schedules`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a363529a5e1b26b56771e4d9fda22881f) {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a363529a5e1b26b56771e4d9fda22881f}

#### `public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1aab22dba8229fbca0b2abb342ab3dbb56)`(self,*float sampling_period,t.Mapping environments_apps_zones,bool saturating,str interpolation,** kwargs)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1aab22dba8229fbca0b2abb342ab3dbb56}

Initialise the CoreActivation RDP layer

Args:
    sampling_period (float): the sink app's sampling period
    environments_apps_zones (t.Mapping): the env->app->zone mapping
    saturating (bool, optional): is configured as saturating?

#### `public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a011615bbf50dc442fb3210287cb2288b)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a011615bbf50dc442fb3210287cb2288b}

Does the layer's (encode, decode) require runtime configuration?

#### `public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a1949179d021a14026c128ada72e20a03)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a1949179d021a14026c128ada72e20a03}

The required config keys

Implements the `required_config_keys` from Configurable base class

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a2c116a57f6180fb7c05ad21e925381eb)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a2c116a57f6180fb7c05ad21e925381eb}

Implementation of Configurable's `validate`

#### `public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a2d17f4726e4a0faa9fc7df19e650603d)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a2d17f4726e4a0faa9fc7df19e650603d}

Get the sampling period

#### `public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a85bfb4490569e5e9997e902834ad1dfb)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a85bfb4490569e5e9997e902834ad1dfb}

Set the sampling period

#### `public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a048793749baf0319814a62183209a448)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a048793749baf0319814a62183209a448}

Is the layer operating in the saturating mode?

#### `public def `[`saturating`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a23ac66761d4651bb2283dd5da199869d)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a23ac66761d4651bb2283dd5da199869d}

Set the saturating property

#### `public t.Optional[t.Callable] `[`timing_interpolator`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a772c0237bf2729164f9ba84fd695c1c6)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a772c0237bf2729164f9ba84fd695c1c6}

Get the timing interpolator

Returns:
    t.Optional[t.Callable]: the interpolator function, if available

#### `public t.Optional[t.Callable] `[`values_interpolator`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a0d34fc08eebcec2ab1fff7e347aaef42)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1a0d34fc08eebcec2ab1fff7e347aaef42}

Get the values interpolator

Returns:
    t.Optional[t.Callable]: the interpolator function, if available

#### `public np.ndarray `[`decode_timestamps`](#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1ae94831b0ba8830ff93cdfb76868ef4a0)`(self)` {#classexot_1_1layer_1_1rdp_1_1coreactivation_1_1CoreActivation_1ae94831b0ba8830ff93cdfb76868ef4a0}

Get the timestamps of the resampled and reshaped rdpstream

Notes:
-   For plotting, one might want to access the 0-th index of the returned array.

Returns:
    np.ndarray: 2-d array of same size as the output of `decode`.

# namespace `exot::layer::rdp::directactivation` {#namespaceexot_1_1layer_1_1rdp_1_1directactivation}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public set `[`get_cache_set_counts`](#directactivation_8py_1ac6dc16c6a895affa9668ac1b86f7a1d2)`(t.Mapping environments_apps_zones)`            | Extracts the set_count value from experiment app configurations
`class `[`exot::layer::rdp::directactivation::DirectActivation`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation) | 

## Members

#### `public set `[`get_cache_set_counts`](#directactivation_8py_1ac6dc16c6a895affa9668ac1b86f7a1d2)`(t.Mapping environments_apps_zones)` {#directactivation_8py_1ac6dc16c6a895affa9668ac1b86f7a1d2}

Extracts the set_count value from experiment app configurations

Args:
    environments_apps_zones (t.Mapping): The mapping env -> app -> zone

Returns:
    set: A set with (set-count, schedule-tag) pairs

Raises:
    LayerMisconfigured: If field not found in the config.

# class `exot::layer::rdp::directactivation::DirectActivation` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation}

```
class exot::layer::rdp::directactivation::DirectActivation
  : public exot.layer._base.Layer
  : public layer
  : public PrePost
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a4a63aa997a4b2f28da3d90564c334045) | 
`public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aece18d05316375b6f5223684af41cc5a) | 
`public  `[`sync_pulse_duration`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a47d76cb7ed8f14e20a04cc79fc7d9014) | 
`public  `[`sync_pulse_detection`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aaac24e30a1f155381c5ccdac0e4a4d27) | 
`public  `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aca133693339881696fa771f27ae8616f) | 
`public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a1d9286302d336448aeb31a40b5e8c8e9)`(self,*float sampling_period,t.Mapping environments_apps_zones,float sync_pulse_duration,str sync_pulse_detection,** kwargs)` | Initialise the DirectActivation RDP layer
`public def `[`sync_pulse_detection`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a845d01cd65abb179951549151700c987)`(self)` | 
`public def `[`sync_pulse_detection`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aef35766fabc9c8277f27a2f017acd9a5)`(self,value)` | 
`public def `[`sync_pulse_duration`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aa0d816b0092b32e4e1fc336b063795ba)`(self)` | 
`public def `[`sync_pulse_duration`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aef591a39c284cc0041f4f3c3f4514b0e)`(self,value)` | 
`public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a17da45990c5fbec7c8240a3d77d8cf63)`(self)` | Does the layer's (encode, decode) require runtime configuration?
`public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1af34ec5205267471884987d5e28af566a)`(self)` | The required config keys
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aee2fdf5f9abc510c28757dccdd0a0ccd)`(self)` | Implementation of Configurable's `validate`
`public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1abfc95baf49ff8bf72ec845066024ab0b)`(self)` | Get the sampling period
`public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1ab449f9614891cec3d52591db26422843)`(self,value)` | Set the sampling period
`public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a049f96c959ecf90d0f741640ede69113)`(self)` | Get the cache set count and schedules set of 2-tuples
`public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a8e541bdda03722776964eaf07cad114a)`(self,value)` | Set the cache set count and schedules set of 2-tuples
`public t.Optional[t.Callable] `[`values_interpolator`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1ab215809d2f9220c5f708f5b52b007241)`(self)` | Get the values interpolator
`public np.ndarray `[`decode_timestamps`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a396b0f5c1e0590e76a2a37fd6726a89b)`(self)` | Get the timestamps of the resampled and reshaped rdpstream

## Members

#### `public  `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a4a63aa997a4b2f28da3d90564c334045) {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a4a63aa997a4b2f28da3d90564c334045}

#### `public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aece18d05316375b6f5223684af41cc5a) {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aece18d05316375b6f5223684af41cc5a}

#### `public  `[`sync_pulse_duration`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a47d76cb7ed8f14e20a04cc79fc7d9014) {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a47d76cb7ed8f14e20a04cc79fc7d9014}

#### `public  `[`sync_pulse_detection`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aaac24e30a1f155381c5ccdac0e4a4d27) {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aaac24e30a1f155381c5ccdac0e4a4d27}

#### `public  `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aca133693339881696fa771f27ae8616f) {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aca133693339881696fa771f27ae8616f}

#### `public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a1d9286302d336448aeb31a40b5e8c8e9)`(self,*float sampling_period,t.Mapping environments_apps_zones,float sync_pulse_duration,str sync_pulse_detection,** kwargs)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a1d9286302d336448aeb31a40b5e8c8e9}

Initialise the DirectActivation RDP layer

Args:
    sampling_period (float): the sink app's sampling period
    environments_apps_zones (t.Mapping): the env->app->zone mapping
    sync_pulse_duration (float, optional): Duration of the sync pulse
    sync_pulse_detection (str, optional): Which edge to look first for?
    **kwargs: unused

#### `public def `[`sync_pulse_detection`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a845d01cd65abb179951549151700c987)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a845d01cd65abb179951549151700c987}

#### `public def `[`sync_pulse_detection`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aef35766fabc9c8277f27a2f017acd9a5)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aef35766fabc9c8277f27a2f017acd9a5}

#### `public def `[`sync_pulse_duration`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aa0d816b0092b32e4e1fc336b063795ba)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aa0d816b0092b32e4e1fc336b063795ba}

#### `public def `[`sync_pulse_duration`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aef591a39c284cc0041f4f3c3f4514b0e)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aef591a39c284cc0041f4f3c3f4514b0e}

#### `public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a17da45990c5fbec7c8240a3d77d8cf63)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a17da45990c5fbec7c8240a3d77d8cf63}

Does the layer's (encode, decode) require runtime configuration?

#### `public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1af34ec5205267471884987d5e28af566a)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1af34ec5205267471884987d5e28af566a}

The required config keys

Implements the `required_config_keys` from Configurable base class

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aee2fdf5f9abc510c28757dccdd0a0ccd)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1aee2fdf5f9abc510c28757dccdd0a0ccd}

Implementation of Configurable's `validate`

#### `public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1abfc95baf49ff8bf72ec845066024ab0b)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1abfc95baf49ff8bf72ec845066024ab0b}

Get the sampling period

#### `public def `[`sampling_period`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1ab449f9614891cec3d52591db26422843)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1ab449f9614891cec3d52591db26422843}

Set the sampling period

#### `public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a049f96c959ecf90d0f741640ede69113)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a049f96c959ecf90d0f741640ede69113}

Get the cache set count and schedules set of 2-tuples

#### `public def `[`cache_set_counts`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a8e541bdda03722776964eaf07cad114a)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a8e541bdda03722776964eaf07cad114a}

Set the cache set count and schedules set of 2-tuples

#### `public t.Optional[t.Callable] `[`values_interpolator`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1ab215809d2f9220c5f708f5b52b007241)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1ab215809d2f9220c5f708f5b52b007241}

Get the values interpolator

Returns:
    t.Optional[t.Callable]: the interpolator function, if available

#### `public np.ndarray `[`decode_timestamps`](#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a396b0f5c1e0590e76a2a37fd6726a89b)`(self)` {#classexot_1_1layer_1_1rdp_1_1directactivation_1_1DirectActivation_1a396b0f5c1e0590e76a2a37fd6726a89b}

Get the timestamps of the resampled and reshaped rdpstream

# namespace `exot::layer::rdp::quantisation` {#namespaceexot_1_1layer_1_1rdp_1_1quantisation}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::rdp::quantisation::FrequencyLevelQuantistion`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion) | 
`class `[`exot::layer::rdp::quantisation::QuantCoreActivation`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1QuantCoreActivation) | 

# class `exot::layer::rdp::quantisation::FrequencyLevelQuantistion` {#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion}

```
class exot::layer::rdp::quantisation::FrequencyLevelQuantistion
  : public exot.layer._mixins.RDPmixins
  : public exot.layer._base.Layer
  : public layer
  : public PrePost
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`timeout_s`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a7d47c781d8e62aa15664ecc15488984e) | 
`public  `[`cores_and_schedules`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a8134ac31461d5c104d793625a410c415) | 
`public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1ab6f68c4f3b3399ce7500077650884530)`(self,*int timeout_s,t.Mapping environments_apps_zones,** kwargs)` | Initialise the Conservative Governor Line Coding layer
`public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a44d816d87e2a31a267ec937453843b74)`(self)` | The required config keys

## Members

#### `public  `[`timeout_s`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a7d47c781d8e62aa15664ecc15488984e) {#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a7d47c781d8e62aa15664ecc15488984e}

#### `public  `[`cores_and_schedules`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a8134ac31461d5c104d793625a410c415) {#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a8134ac31461d5c104d793625a410c415}

#### `public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1ab6f68c4f3b3399ce7500077650884530)`(self,*int timeout_s,t.Mapping environments_apps_zones,** kwargs)` {#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1ab6f68c4f3b3399ce7500077650884530}

Initialise the Conservative Governor Line Coding layer

Args:

#### `public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a44d816d87e2a31a267ec937453843b74)`(self)` {#classexot_1_1layer_1_1rdp_1_1quantisation_1_1FrequencyLevelQuantistion_1a44d816d87e2a31a267ec937453843b74}

The required config keys

Implements the `required_config_keys` from Configurable base class

# class `exot::layer::rdp::quantisation::QuantCoreActivation` {#classexot_1_1layer_1_1rdp_1_1quantisation_1_1QuantCoreActivation}

```
class exot::layer::rdp::quantisation::QuantCoreActivation
  : public exot.layer.rdp.coreactivation.CoreActivation
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1QuantCoreActivation_1a750d6bfa3813af1b8f55abc71c81c0c4)`(self)` | The required config keys

## Members

#### `public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1quantisation_1_1QuantCoreActivation_1a750d6bfa3813af1b8f55abc71c81c0c4)`(self)` {#classexot_1_1layer_1_1rdp_1_1quantisation_1_1QuantCoreActivation_1a750d6bfa3813af1b8f55abc71c81c0c4}

The required config keys

Implements the `required_config_keys` from Configurable base class

# namespace `exot::layer::rdp::resampling` {#namespaceexot_1_1layer_1_1rdp_1_1resampling}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::rdp::resampling::Normalise`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise) | 

# class `exot::layer::rdp::resampling::Normalise` {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise}

```
class exot::layer::rdp::resampling::Normalise
  : public exot.layer._base.Layer
  : public layer
  : public PrePost
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`resampling_period_s`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1adb8985c2bd7d2bc8d9c605286eed7b9f) | 
`public  `[`offset`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a69e9bde3a97a52d9ee5c2a2d6e9c3e8c) | 
`public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ae021d6cf6e7bcfcc400f1613c40bbe0f) | 
`public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a384d2e7db61bdf0f910ea9a495ab35c3)`(self,*float resampling_period_s,float offset,t.Mapping environments_apps_zones,** kwargs)` | Initialise the Normalisation RDP layer
`public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a8042d1a80e686ce1e65741bf885ed816)`(self)` | Does the layer's (encode, decode) require runtime configuration?
`public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ae879619bc4a33baa417eb160a98e0c8b)`(self)` | The required config keys
`public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a3d110ba6faa623c5863b94fa86e98894)`(self)` | Validate config
`public def `[`resampling_period_s`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a7d9eaf9787af3923d00a591e7f38acbb)`(self)` | Get the sampling period
`public def `[`resampling_period_s`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ab415e63c01afbf72a5e8dffb8558b362)`(self,value)` | Set the sampling period

## Members

#### `public  `[`resampling_period_s`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1adb8985c2bd7d2bc8d9c605286eed7b9f) {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1adb8985c2bd7d2bc8d9c605286eed7b9f}

#### `public  `[`offset`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a69e9bde3a97a52d9ee5c2a2d6e9c3e8c) {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a69e9bde3a97a52d9ee5c2a2d6e9c3e8c}

#### `public  `[`environments_apps_zones`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ae021d6cf6e7bcfcc400f1613c40bbe0f) {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ae021d6cf6e7bcfcc400f1613c40bbe0f}

#### `public def `[`__init__`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a384d2e7db61bdf0f910ea9a495ab35c3)`(self,*float resampling_period_s,float offset,t.Mapping environments_apps_zones,** kwargs)` {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a384d2e7db61bdf0f910ea9a495ab35c3}

Initialise the Normalisation RDP layer

Args:
    resampling_period (float): the resampling period
    offset (float): the offset of the measured value which will be compensated
    environments_apps_zones (t.Mapping): the env->app->zone mapping

#### `public (bool, bool) `[`requires_runtime_config`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a8042d1a80e686ce1e65741bf885ed816)`(self)` {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a8042d1a80e686ce1e65741bf885ed816}

Does the layer's (encode, decode) require runtime configuration?

#### `public def `[`required_config_keys`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ae879619bc4a33baa417eb160a98e0c8b)`(self)` {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ae879619bc4a33baa417eb160a98e0c8b}

The required config keys

Implements the `required_config_keys` from Configurable base class

#### `public t.NoReturn `[`validate`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a3d110ba6faa623c5863b94fa86e98894)`(self)` {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a3d110ba6faa623c5863b94fa86e98894}

Validate config

Implementation of Configurable's `validate` method

#### `public def `[`resampling_period_s`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a7d9eaf9787af3923d00a591e7f38acbb)`(self)` {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1a7d9eaf9787af3923d00a591e7f38acbb}

Get the sampling period

#### `public def `[`resampling_period_s`](#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ab415e63c01afbf72a5e8dffb8558b362)`(self,value)` {#classexot_1_1layer_1_1rdp_1_1resampling_1_1Normalise_1ab415e63c01afbf72a5e8dffb8558b362}

Set the sampling period

# namespace `exot::layer::src::_base` {#namespaceexot_1_1layer_1_1src_1_1__base}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::src::_base::SourceCoding`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding) | 

# class `exot::layer::src::_base::SourceCoding` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding}

```
class exot::layer::src::_base::SourceCoding
  : public exot.layer._base.Layer
  : public layer
  : public Source
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`symrate_to_bitrate`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1adeb47f8b08b4b62a08f7cd45422f2cf6)`(self,t.Union symrate)` | 
`public def `[`bitrate_to_symrate`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a5ce97326b52ee38cd488c71357da0081)`(self,t.Union bitrate)` | 
`public def `[`num_syms_to_num_bits`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1aad66f9b2e44c2e6688d109d7175383da)`(self,t.Union num_syms)` | 
`public def `[`num_bits_to_num_syms`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a0cb4b1a0f866cda9830c1e07f6adc409)`(self,t.Union num_bits)` | 
`public float `[`compression_factor`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1adcafc06a3aa7f88ff311ea994f1624bb)`(self)` | 
`public bool `[`is_uniform`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1acf18b957198009a11a9989b30101efd0)`(self)` | 
`public bool `[`is_compatible`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a6e56994a161a79c3b81f9c49e7c7452a)`(self,int max_num_symbols)` | 
`public def `[`symbols`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a0182a33877e834b0f6d62f7ddc0f2914)`(self)` | 
`public dict `[`codebook`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a3a37faa41ecec26c576f2a82958bd34a)`(self)` | 

## Members

#### `public def `[`symrate_to_bitrate`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1adeb47f8b08b4b62a08f7cd45422f2cf6)`(self,t.Union symrate)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1adeb47f8b08b4b62a08f7cd45422f2cf6}

#### `public def `[`bitrate_to_symrate`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a5ce97326b52ee38cd488c71357da0081)`(self,t.Union bitrate)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a5ce97326b52ee38cd488c71357da0081}

#### `public def `[`num_syms_to_num_bits`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1aad66f9b2e44c2e6688d109d7175383da)`(self,t.Union num_syms)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1aad66f9b2e44c2e6688d109d7175383da}

#### `public def `[`num_bits_to_num_syms`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a0cb4b1a0f866cda9830c1e07f6adc409)`(self,t.Union num_bits)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a0cb4b1a0f866cda9830c1e07f6adc409}

#### `public float `[`compression_factor`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1adcafc06a3aa7f88ff311ea994f1624bb)`(self)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1adcafc06a3aa7f88ff311ea994f1624bb}

#### `public bool `[`is_uniform`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1acf18b957198009a11a9989b30101efd0)`(self)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1acf18b957198009a11a9989b30101efd0}

#### `public bool `[`is_compatible`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a6e56994a161a79c3b81f9c49e7c7452a)`(self,int max_num_symbols)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a6e56994a161a79c3b81f9c49e7c7452a}

#### `public def `[`symbols`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a0182a33877e834b0f6d62f7ddc0f2914)`(self)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a0182a33877e834b0f6d62f7ddc0f2914}

#### `public dict `[`codebook`](#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a3a37faa41ecec26c576f2a82958bd34a)`(self)` {#classexot_1_1layer_1_1src_1_1__base_1_1SourceCoding_1a3a37faa41ecec26c576f2a82958bd34a}

# namespace `exot::layer::src::bitset` {#namespaceexot_1_1layer_1_1src_1_1bitset}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::src::bitset::BitsetCoding`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding) | 

# class `exot::layer::src::bitset::BitsetCoding` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding}

```
class exot::layer::src::bitset::BitsetCoding
  : public exot.layer.src._base.SourceCoding
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`bitset_length`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1aa653939ab00455bb5016fbb0b225c6a3) | 
`public def `[`__init__`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a28855116e24e42c7b6f8aeba6c886823)`(self,* args,int bitset_length,** kwargs)` | 
`public def `[`bitset_length`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a2d6559385826a4108aa2b1920264ba8e)`(self)` | 
`public def `[`bitset_length`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1ab2e029452a84bfbb621054ce9fd3cfa4)`(self,int value)` | 
`public float `[`compression_factor`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a091b6d6c10797b1d9d1f08261db0dbe1)`(self)` | 
`public bool `[`is_uniform`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a6c17882e2bf4b4ce132df744d0ab4ae4)`(self)` | 
`public bool `[`is_compatible`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a5b3f2bb7f42071b316e7e0881dc6c48c)`(self,int max_num_symbols)` | 
`public def `[`symbols`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a1dcc10893113b84b4f18bf0e5e093b7f)`(self)` | 
`public dict `[`codebook`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1adda6b06cd838712b9cabdce6a02161b2)`(self)` | 

## Members

#### `public  `[`bitset_length`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1aa653939ab00455bb5016fbb0b225c6a3) {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1aa653939ab00455bb5016fbb0b225c6a3}

#### `public def `[`__init__`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a28855116e24e42c7b6f8aeba6c886823)`(self,* args,int bitset_length,** kwargs)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a28855116e24e42c7b6f8aeba6c886823}

#### `public def `[`bitset_length`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a2d6559385826a4108aa2b1920264ba8e)`(self)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a2d6559385826a4108aa2b1920264ba8e}

#### `public def `[`bitset_length`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1ab2e029452a84bfbb621054ce9fd3cfa4)`(self,int value)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1ab2e029452a84bfbb621054ce9fd3cfa4}

#### `public float `[`compression_factor`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a091b6d6c10797b1d9d1f08261db0dbe1)`(self)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a091b6d6c10797b1d9d1f08261db0dbe1}

#### `public bool `[`is_uniform`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a6c17882e2bf4b4ce132df744d0ab4ae4)`(self)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a6c17882e2bf4b4ce132df744d0ab4ae4}

#### `public bool `[`is_compatible`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a5b3f2bb7f42071b316e7e0881dc6c48c)`(self,int max_num_symbols)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a5b3f2bb7f42071b316e7e0881dc6c48c}

#### `public def `[`symbols`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a1dcc10893113b84b4f18bf0e5e093b7f)`(self)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1a1dcc10893113b84b4f18bf0e5e093b7f}

#### `public dict `[`codebook`](#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1adda6b06cd838712b9cabdce6a02161b2)`(self)` {#classexot_1_1layer_1_1src_1_1bitset_1_1BitsetCoding_1adda6b06cd838712b9cabdce6a02161b2}

# namespace `exot::layer::src::huffman` {#namespaceexot_1_1layer_1_1src_1_1huffman}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::src::huffman::Huffman`](#classexot_1_1layer_1_1src_1_1huffman_1_1Huffman) | 

# class `exot::layer::src::huffman::Huffman` {#classexot_1_1layer_1_1src_1_1huffman_1_1Huffman}

```
class exot::layer::src::huffman::Huffman
  : public exot.layer.src._base.SourceCoding
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1layer_1_1src_1_1huffman_1_1Huffman_1ad317f245f854a42708d3bb14ad1c76c7)`(self,* args,** kwargs)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1layer_1_1src_1_1huffman_1_1Huffman_1ad317f245f854a42708d3bb14ad1c76c7)`(self,* args,** kwargs)` {#classexot_1_1layer_1_1src_1_1huffman_1_1Huffman_1ad317f245f854a42708d3bb14ad1c76c7}

# namespace `exot::layer::src::passthrough` {#namespaceexot_1_1layer_1_1src_1_1passthrough}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::layer::src::passthrough::SourcePassthrough`](#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough) | 

# class `exot::layer::src::passthrough::SourcePassthrough` {#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough}

```
class exot::layer::src::passthrough::SourcePassthrough
  : public exot.layer.src._base.SourceCoding
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough_1a808b06a729813b3362f0b8575fc571d3)`(self,* args,** kwargs)` | 
`public def `[`codebook`](#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough_1a3aea13c2d6da39bbdea42c338b9e8a04)`(self)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough_1a808b06a729813b3362f0b8575fc571d3)`(self,* args,** kwargs)` {#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough_1a808b06a729813b3362f0b8575fc571d3}

#### `public def `[`codebook`](#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough_1a3aea13c2d6da39bbdea42c338b9e8a04)`(self)` {#classexot_1_1layer_1_1src_1_1passthrough_1_1SourcePassthrough_1a3aea13c2d6da39bbdea42c338b9e8a04}

# class `exot::layer::_base::Layer::Type` {#classexot_1_1layer_1_1__base_1_1Layer_1_1Type}

```
class exot::layer::_base::Layer::Type
  : public Enum
```  

Layer types

The values must be unique, strings, and correspond to keys in the config.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

Generated by [Moxygen](https://sourcey.com/moxygen)