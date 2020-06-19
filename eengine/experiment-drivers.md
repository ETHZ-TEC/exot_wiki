[:back:](/home)
---

# Drivers
The drivers allow the experiment engine to communicate with the experiment environment.
For now, ExOT offers two drivers:
1. UNIX with SSH interface
1. Android with ADB interface

The drivers are designed to allow the experiment engine to automate the experiment execution, but also to be used interactively.
Please refer to the examples for the [driver](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/notebooks/examples/driver.ipynb) and the [backend](https://gitlab.ethz.ch/tec/public/exot/eengine/-/blob/master/notebooks/examples/driver_backend.ipynb) and the [code](https://gitlab.ethz.ch/tec/public/exot/eengine/-/tree/master/exot/driver) for further information.


# Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::driver::_backend`](#namespaceexot_1_1driver_1_1__backend) | 
`namespace `[`exot::driver::_driver`](#namespaceexot_1_1driver_1_1__driver) | 
`namespace `[`exot::driver::_factory`](#namespaceexot_1_1driver_1_1__factory) | 
`namespace `[`exot::driver::_mixins`](#namespaceexot_1_1driver_1_1__mixins) | 
`namespace `[`exot::driver::_process`](#namespaceexot_1_1driver_1_1__process) | 
`namespace `[`exot::driver::backend_adb`](#namespaceexot_1_1driver_1_1backend__adb) | 
`namespace `[`exot::driver::backend_ssh`](#namespaceexot_1_1driver_1_1backend__ssh) | 
`namespace `[`exot::driver::driver_android`](#namespaceexot_1_1driver_1_1driver__android) | 
`namespace `[`exot::driver::driver_unix`](#namespaceexot_1_1driver_1_1driver__unix) | 
`namespace `[`exot::driver::extensions::android`](#namespaceexot_1_1driver_1_1extensions_1_1android) | 
`namespace `[`exot::driver::extensions::rsync`](#namespaceexot_1_1driver_1_1extensions_1_1rsync) | 
`namespace `[`exot::driver::extensions::sysfs`](#namespaceexot_1_1driver_1_1extensions_1_1sysfs) | 
`namespace `[`exot::driver::extensions::unix`](#namespaceexot_1_1driver_1_1extensions_1_1unix) | 

# namespace `exot::driver::_backend` {#namespaceexot_1_1driver_1_1__backend}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public dict `[`result_to_dict`](#__backend_8py_1a45ef58ec15b5f83f7e60074287bdae6b)`(ReturnT result)`            | Produces a dict from a ReturnT
`public dict `[`result_to_print_ready_dict`](#__backend_8py_1a8e66e984d3e2001dcc75becc6cd39a5f)`(ReturnT result)`            | Produce a dict from a ReturnT with some details omitted
`class `[`exot::driver::_backend::Backend`](#classexot_1_1driver_1_1__backend_1_1Backend) | The base class for driver backends

## Members

#### `public dict `[`result_to_dict`](#__backend_8py_1a45ef58ec15b5f83f7e60074287bdae6b)`(ReturnT result)` {#__backend_8py_1a45ef58ec15b5f83f7e60074287bdae6b}

Produces a dict from a ReturnT

#### `public dict `[`result_to_print_ready_dict`](#__backend_8py_1a8e66e984d3e2001dcc75becc6cd39a5f)`(ReturnT result)` {#__backend_8py_1a8e66e984d3e2001dcc75becc6cd39a5f}

Produce a dict from a ReturnT with some details omitted

# class `exot::driver::_backend::Backend` {#classexot_1_1driver_1_1__backend_1_1Backend}

```
class exot::driver::_backend::Backend
  : public Configurable
  : public AbstractContextManager
  : public configure
  : public metaclass
  : public ABCMeta
```  

The base class for driver backends

Attributes:
    CommandT (TYPE): The command type passed to the backend
    ReturnT (TYPE): The type returned by the backend when a command completes

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public None `[`__init__`](#classexot_1_1driver_1_1__backend_1_1Backend_1aed53a8cc07aef5f58fea1f87ee18c442)`(self,* args,** kwargs)` | Initialises the backend
`public object `[`__enter__`](#classexot_1_1driver_1_1__backend_1_1Backend_1aa40758d4f6bbeda00f21e8b63a6da7e5)`(self)` | Creates a backend object to be used as a context manager
`public None `[`__exit__`](#classexot_1_1driver_1_1__backend_1_1Backend_1aec57ab8e3697a83907505958b31b6055)`(self,* exc)` | Destroys the backend object after exiting a 'with' context
`public str `[`__repr__`](#classexot_1_1driver_1_1__backend_1_1Backend_1a571de8ae1a5c4d7285ac5d0cccdacf0e)`(self)` | Represents the backend instance as a string
`public object `[`instantiate`](#classexot_1_1driver_1_1__backend_1_1Backend_1a928b5abec24393a8d2e179539e2e4e0c)`(cls,* args,** kwargs)` | Get a connected Backend instance
`public bool `[`can_connect`](#classexot_1_1driver_1_1__backend_1_1Backend_1afb902529130f4a43e89cff464dfc0b06)`(self)` | Can the backend connect to its target?
`public bool `[`connected`](#classexot_1_1driver_1_1__backend_1_1Backend_1a180a4187468e71158412f6eddfcfe3ba)`(self)` | Is the backend connected?
`public object `[`connection`](#classexot_1_1driver_1_1__backend_1_1Backend_1a2036f6faac6cdaca017cdcf789a7d653)`(self)` | Gets the underlying implementation-specific connection object
`public None `[`connect`](#classexot_1_1driver_1_1__backend_1_1Backend_1a774c4d70a1b3e7523e226b6f479afae7)`(self)` | Connects the backend
`public None `[`disconnect`](#classexot_1_1driver_1_1__backend_1_1Backend_1aa6a684a05865bc62942de33f5a8a6b8a)`(self)` | Disconnects the backend
`public ReturnT `[`run`](#classexot_1_1driver_1_1__backend_1_1Backend_1a3e3d5a986e5dfa2980bfd89b71ffb755)`(self,CommandT cmd,** kwargs)` | Runs a command on the target using the backend
`public ReturnT `[`sudo`](#classexot_1_1driver_1_1__backend_1_1Backend_1a88ec5e0e90568767b133553a2265192d)`(self,CommandT cmd,** kwargs)` | Runs a command on the target using the backend with elevated privileges
`public t.List[ReturnT] `[`history`](#classexot_1_1driver_1_1__backend_1_1Backend_1afd1f9e4707d1d40a9f8632778f915735)`(self)` | Get the command/result history

## Members

#### `public None `[`__init__`](#classexot_1_1driver_1_1__backend_1_1Backend_1aed53a8cc07aef5f58fea1f87ee18c442)`(self,* args,** kwargs)` {#classexot_1_1driver_1_1__backend_1_1Backend_1aed53a8cc07aef5f58fea1f87ee18c442}

Initialises the backend

Args:
    *args: Positional arguments passed to the base class
    **kwargs: Keyword arguments passed to the base class

#### `public object `[`__enter__`](#classexot_1_1driver_1_1__backend_1_1Backend_1aa40758d4f6bbeda00f21e8b63a6da7e5)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1aa40758d4f6bbeda00f21e8b63a6da7e5}

Creates a backend object to be used as a context manager

Returns:
    object: The backend, connected if possible

#### `public None `[`__exit__`](#classexot_1_1driver_1_1__backend_1_1Backend_1aec57ab8e3697a83907505958b31b6055)`(self,* exc)` {#classexot_1_1driver_1_1__backend_1_1Backend_1aec57ab8e3697a83907505958b31b6055}

Destroys the backend object after exiting a 'with' context

Args:
    *exc: The exceptions array

#### `public str `[`__repr__`](#classexot_1_1driver_1_1__backend_1_1Backend_1a571de8ae1a5c4d7285ac5d0cccdacf0e)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1a571de8ae1a5c4d7285ac5d0cccdacf0e}

Represents the backend instance as a string

Returns:
    str: The string representation

#### `public object `[`instantiate`](#classexot_1_1driver_1_1__backend_1_1Backend_1a928b5abec24393a8d2e179539e2e4e0c)`(cls,* args,** kwargs)` {#classexot_1_1driver_1_1__backend_1_1Backend_1a928b5abec24393a8d2e179539e2e4e0c}

Get a connected Backend instance

#### `public bool `[`can_connect`](#classexot_1_1driver_1_1__backend_1_1Backend_1afb902529130f4a43e89cff464dfc0b06)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1afb902529130f4a43e89cff464dfc0b06}

Can the backend connect to its target?

Returns:
    bool: True if properly configured

#### `public bool `[`connected`](#classexot_1_1driver_1_1__backend_1_1Backend_1a180a4187468e71158412f6eddfcfe3ba)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1a180a4187468e71158412f6eddfcfe3ba}

Is the backend connected?

#### `public object `[`connection`](#classexot_1_1driver_1_1__backend_1_1Backend_1a2036f6faac6cdaca017cdcf789a7d653)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1a2036f6faac6cdaca017cdcf789a7d653}

Gets the underlying implementation-specific connection object

#### `public None `[`connect`](#classexot_1_1driver_1_1__backend_1_1Backend_1a774c4d70a1b3e7523e226b6f479afae7)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1a774c4d70a1b3e7523e226b6f479afae7}

Connects the backend

#### `public None `[`disconnect`](#classexot_1_1driver_1_1__backend_1_1Backend_1aa6a684a05865bc62942de33f5a8a6b8a)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1aa6a684a05865bc62942de33f5a8a6b8a}

Disconnects the backend

#### `public ReturnT `[`run`](#classexot_1_1driver_1_1__backend_1_1Backend_1a3e3d5a986e5dfa2980bfd89b71ffb755)`(self,CommandT cmd,** kwargs)` {#classexot_1_1driver_1_1__backend_1_1Backend_1a3e3d5a986e5dfa2980bfd89b71ffb755}

Runs a command on the target using the backend

Args:
    cmd (CommandT): The command
    **kwargs: Optional keyword arguments

#### `public ReturnT `[`sudo`](#classexot_1_1driver_1_1__backend_1_1Backend_1a88ec5e0e90568767b133553a2265192d)`(self,CommandT cmd,** kwargs)` {#classexot_1_1driver_1_1__backend_1_1Backend_1a88ec5e0e90568767b133553a2265192d}

Runs a command on the target using the backend with elevated privileges

Args:
    cmd (CommandT): The command
    **kwargs: Optional keyword arguments

#### `public t.List[ReturnT] `[`history`](#classexot_1_1driver_1_1__backend_1_1Backend_1afd1f9e4707d1d40a9f8632778f915735)`(self)` {#classexot_1_1driver_1_1__backend_1_1Backend_1afd1f9e4707d1d40a9f8632778f915735}

Get the command/result history

# namespace `exot::driver::_driver` {#namespaceexot_1_1driver_1_1__driver}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::_driver::Driver`](#classexot_1_1driver_1_1__driver_1_1Driver) | 

# class `exot::driver::_driver::Driver` {#classexot_1_1driver_1_1__driver_1_1Driver}

```
class exot::driver::_driver::Driver
  : public SubclassTracker
  : public exot.driver._mixins.TransferMethodsMixin
  : public exot.driver._mixins.ProcessMethodsMixin
  : public exot.driver._mixins.FileMethodsMixin
  : public exot.driver._mixins.LockingMethodsMixin
  : public AbstractContextManager
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public None `[`__init_subclass__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a0518efbc3dd034dd0c688bab87dab828)`(cls,`[`Backend`](#classexot_1_1driver_1_1__backend_1_1Backend)` backend,**t.Any kwargs)` | 
`public None `[`__init__`](#classexot_1_1driver_1_1__driver_1_1Driver_1acc3ad3204a2a39a9eb00b5fcd8069968)`(self,*t.Any args,**t.Any kwargs)` | 
`public `[`Driver`](#classexot_1_1driver_1_1__driver_1_1Driver)` `[`__enter__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a5d810696c314a568ef1f7d31fd4b72f9)`(self)` | 
`public None `[`__exit__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a688c77327b5013cc776f6bcdfaef072a)`(self,* exc)` | 
`public str `[`__repr__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a799ef3ac13649a013d14494168da07ca)`(self)` | 
`public `[`Driver`](#classexot_1_1driver_1_1__driver_1_1Driver)` `[`instantiate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a67fee7a88e0480995b6cd83bd6c28a54)`(cls,* args,** kwargs)` | Get a connected Driver instance
`public `[`Backend`](#classexot_1_1driver_1_1__backend_1_1Backend)` `[`backend`](#classexot_1_1driver_1_1__driver_1_1Driver_1a4d20abf3b723a157bcff581ed79f11ca)`(self)` | 
`public str `[`connection_id`](#classexot_1_1driver_1_1__driver_1_1Driver_1ab0f00a18fdb171775f9aa2cd426218c7)`(self)` | 
`public bool `[`connected`](#classexot_1_1driver_1_1__driver_1_1Driver_1a83f6629bd357e8ce9a8d6e96eaae5377)`(self)` | 
`public bool `[`can_connect`](#classexot_1_1driver_1_1__driver_1_1Driver_1a1bb7883712ed3c6fec32ae0eb848f847)`(self)` | 
`public None `[`connect`](#classexot_1_1driver_1_1__driver_1_1Driver_1af0a2f225fce86438c08198b1c62480c0)`(self,force)` | 
`public None `[`disconnect`](#classexot_1_1driver_1_1__driver_1_1Driver_1ab6f14f3e28bb5f0efb9cc5dc8e1284b4)`(self)` | 
`public Backend.ReturnT `[`command`](#classexot_1_1driver_1_1__driver_1_1Driver_1a163ee4222a0481dcb6c1da46c5f7bcce)`(self,Backend.CommandT cmd,bool sudo,**dict kwargs)` | 
`public t.List[str] `[`setable_states`](#classexot_1_1driver_1_1__driver_1_1Driver_1a0253fea505df30dd0927ff845a33a4f8)`(self)` | 
`public t.List[str] `[`getable_states`](#classexot_1_1driver_1_1__driver_1_1Driver_1a2fec30ccd7c6857afee1c85459189187)`(self)` | 
`public t.Dict `[`getstate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a0c0e40c9cae6b232c2305b20119b62b9)`(self)` | 
`public None `[`setstate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a985af4ae9be10376d7c5798dc8f96cee)`(self,** kwargs)` | 
`public None `[`initstate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a55c7b0a82a7483a66bd15116f948d3e4)`(self)` | 
`public t.Dict `[`original_state`](#classexot_1_1driver_1_1__driver_1_1Driver_1a604c1d448fc613f0121b9eef5a08c2d4)`(self)` | 
`public None `[`cleanup`](#classexot_1_1driver_1_1__driver_1_1Driver_1a5384092bd675fe26d8609c873870f896)`(self)` | 

## Members

#### `public None `[`__init_subclass__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a0518efbc3dd034dd0c688bab87dab828)`(cls,`[`Backend`](#classexot_1_1driver_1_1__backend_1_1Backend)` backend,**t.Any kwargs)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a0518efbc3dd034dd0c688bab87dab828}

#### `public None `[`__init__`](#classexot_1_1driver_1_1__driver_1_1Driver_1acc3ad3204a2a39a9eb00b5fcd8069968)`(self,*t.Any args,**t.Any kwargs)` {#classexot_1_1driver_1_1__driver_1_1Driver_1acc3ad3204a2a39a9eb00b5fcd8069968}

#### `public `[`Driver`](#classexot_1_1driver_1_1__driver_1_1Driver)` `[`__enter__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a5d810696c314a568ef1f7d31fd4b72f9)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a5d810696c314a568ef1f7d31fd4b72f9}

#### `public None `[`__exit__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a688c77327b5013cc776f6bcdfaef072a)`(self,* exc)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a688c77327b5013cc776f6bcdfaef072a}

#### `public str `[`__repr__`](#classexot_1_1driver_1_1__driver_1_1Driver_1a799ef3ac13649a013d14494168da07ca)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a799ef3ac13649a013d14494168da07ca}

#### `public `[`Driver`](#classexot_1_1driver_1_1__driver_1_1Driver)` `[`instantiate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a67fee7a88e0480995b6cd83bd6c28a54)`(cls,* args,** kwargs)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a67fee7a88e0480995b6cd83bd6c28a54}

Get a connected Driver instance

#### `public `[`Backend`](#classexot_1_1driver_1_1__backend_1_1Backend)` `[`backend`](#classexot_1_1driver_1_1__driver_1_1Driver_1a4d20abf3b723a157bcff581ed79f11ca)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a4d20abf3b723a157bcff581ed79f11ca}

#### `public str `[`connection_id`](#classexot_1_1driver_1_1__driver_1_1Driver_1ab0f00a18fdb171775f9aa2cd426218c7)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1ab0f00a18fdb171775f9aa2cd426218c7}

#### `public bool `[`connected`](#classexot_1_1driver_1_1__driver_1_1Driver_1a83f6629bd357e8ce9a8d6e96eaae5377)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a83f6629bd357e8ce9a8d6e96eaae5377}

#### `public bool `[`can_connect`](#classexot_1_1driver_1_1__driver_1_1Driver_1a1bb7883712ed3c6fec32ae0eb848f847)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a1bb7883712ed3c6fec32ae0eb848f847}

#### `public None `[`connect`](#classexot_1_1driver_1_1__driver_1_1Driver_1af0a2f225fce86438c08198b1c62480c0)`(self,force)` {#classexot_1_1driver_1_1__driver_1_1Driver_1af0a2f225fce86438c08198b1c62480c0}

#### `public None `[`disconnect`](#classexot_1_1driver_1_1__driver_1_1Driver_1ab6f14f3e28bb5f0efb9cc5dc8e1284b4)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1ab6f14f3e28bb5f0efb9cc5dc8e1284b4}

#### `public Backend.ReturnT `[`command`](#classexot_1_1driver_1_1__driver_1_1Driver_1a163ee4222a0481dcb6c1da46c5f7bcce)`(self,Backend.CommandT cmd,bool sudo,**dict kwargs)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a163ee4222a0481dcb6c1da46c5f7bcce}

#### `public t.List[str] `[`setable_states`](#classexot_1_1driver_1_1__driver_1_1Driver_1a0253fea505df30dd0927ff845a33a4f8)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a0253fea505df30dd0927ff845a33a4f8}

#### `public t.List[str] `[`getable_states`](#classexot_1_1driver_1_1__driver_1_1Driver_1a2fec30ccd7c6857afee1c85459189187)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a2fec30ccd7c6857afee1c85459189187}

#### `public t.Dict `[`getstate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a0c0e40c9cae6b232c2305b20119b62b9)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a0c0e40c9cae6b232c2305b20119b62b9}

#### `public None `[`setstate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a985af4ae9be10376d7c5798dc8f96cee)`(self,** kwargs)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a985af4ae9be10376d7c5798dc8f96cee}

#### `public None `[`initstate`](#classexot_1_1driver_1_1__driver_1_1Driver_1a55c7b0a82a7483a66bd15116f948d3e4)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a55c7b0a82a7483a66bd15116f948d3e4}

#### `public t.Dict `[`original_state`](#classexot_1_1driver_1_1__driver_1_1Driver_1a604c1d448fc613f0121b9eef5a08c2d4)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a604c1d448fc613f0121b9eef5a08c2d4}

#### `public None `[`cleanup`](#classexot_1_1driver_1_1__driver_1_1Driver_1a5384092bd675fe26d8609c873870f896)`(self)` {#classexot_1_1driver_1_1__driver_1_1Driver_1a5384092bd675fe26d8609c873870f896}

# namespace `exot::driver::_factory` {#namespaceexot_1_1driver_1_1__factory}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::_factory::DriverFactory`](#classexot_1_1driver_1_1__factory_1_1DriverFactory) | 

# class `exot::driver::_factory::DriverFactory` {#classexot_1_1driver_1_1__factory_1_1DriverFactory}

```
class exot::driver::_factory::DriverFactory
  : public GenericFactory
  : public klass
  : public exot.driver._driver.Driver
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::driver::_mixins` {#namespaceexot_1_1driver_1_1__mixins}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::_mixins::ExtraFileMethodsMixin`](#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin) | 
`class `[`exot::driver::_mixins::FileMethodsMixin`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin) | 
`class `[`exot::driver::_mixins::LockingMethodsMixin`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin) | 
`class `[`exot::driver::_mixins::PersistenceMethodsMixin`](#classexot_1_1driver_1_1__mixins_1_1PersistenceMethodsMixin) | 
`class `[`exot::driver::_mixins::ProcessMethodsMixin`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin) | 
`class `[`exot::driver::_mixins::TransferMethodsMixin`](#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin) | 

# class `exot::driver::_mixins::ExtraFileMethodsMixin` {#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin}

```
class exot::driver::_mixins::ExtraFileMethodsMixin
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Optional[t.List[str]] `[`find`](#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin_1a0114643045a045a548a1517152469b8a)`(self,str path,*bool recursive,bool hidden,bool no_path,str query)` | 
`public t.Optional[os.stat_result] `[`stat`](#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin_1af588e138f58a2c73db9adf7ac5bf1654)`(self,str path,*t.Optional dir_fd,bool follow_symlinks)` | 

## Members

#### `public t.Optional[t.List[str]] `[`find`](#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin_1a0114643045a045a548a1517152469b8a)`(self,str path,*bool recursive,bool hidden,bool no_path,str query)` {#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin_1a0114643045a045a548a1517152469b8a}

#### `public t.Optional[os.stat_result] `[`stat`](#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin_1af588e138f58a2c73db9adf7ac5bf1654)`(self,str path,*t.Optional dir_fd,bool follow_symlinks)` {#classexot_1_1driver_1_1__mixins_1_1ExtraFileMethodsMixin_1af588e138f58a2c73db9adf7ac5bf1654}

# class `exot::driver::_mixins::FileMethodsMixin` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin}

```
class exot::driver::_mixins::FileMethodsMixin
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public str `[`delete`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a56f79623c2b132342fd92dd95023f84f)`(self,str path,bool recursive)` | 
`public bool `[`executable_exists`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a8c63932da4accc260092ee3f9c7b653f)`(self,str executable)` | 
`public bool `[`exists`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a08df7dbf00de5c4d0b0b54c9071e2833)`(self,str path)` | 
`public bool `[`is_file`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a561af769a0081db15e2827487866b130)`(self,str path)` | 
`public bool `[`is_dir`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a842ed3923fec4acf8bf077bd4867e8dc)`(self,str path)` | 
`public bool `[`move`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a10b3e982fb66a612eb2aec7046e8102e)`(self,str path_from,str path_to,bool overwrite)` | 
`public bool `[`copy`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1ab04df0e30477a24b9cb2871fa9cdc7c7)`(self,str path_from,str path_to,bool recursive,bool overwrite)` | 
`public bool `[`mkdir`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a81b7880f92988e663c22b3c439adee43)`(self,str path,bool parents)` | 
`public bool `[`access`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1af65f22a4564cb95d28e068b7e919b29f)`(self,str path,str mode)` | 
`public str `[`working_directory`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a994c940507220f2db33fcd649e9ebe41)`(self)` | 

## Members

#### `public str `[`delete`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a56f79623c2b132342fd92dd95023f84f)`(self,str path,bool recursive)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a56f79623c2b132342fd92dd95023f84f}

#### `public bool `[`executable_exists`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a8c63932da4accc260092ee3f9c7b653f)`(self,str executable)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a8c63932da4accc260092ee3f9c7b653f}

#### `public bool `[`exists`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a08df7dbf00de5c4d0b0b54c9071e2833)`(self,str path)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a08df7dbf00de5c4d0b0b54c9071e2833}

#### `public bool `[`is_file`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a561af769a0081db15e2827487866b130)`(self,str path)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a561af769a0081db15e2827487866b130}

#### `public bool `[`is_dir`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a842ed3923fec4acf8bf077bd4867e8dc)`(self,str path)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a842ed3923fec4acf8bf077bd4867e8dc}

#### `public bool `[`move`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a10b3e982fb66a612eb2aec7046e8102e)`(self,str path_from,str path_to,bool overwrite)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a10b3e982fb66a612eb2aec7046e8102e}

#### `public bool `[`copy`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1ab04df0e30477a24b9cb2871fa9cdc7c7)`(self,str path_from,str path_to,bool recursive,bool overwrite)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1ab04df0e30477a24b9cb2871fa9cdc7c7}

#### `public bool `[`mkdir`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a81b7880f92988e663c22b3c439adee43)`(self,str path,bool parents)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a81b7880f92988e663c22b3c439adee43}

#### `public bool `[`access`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1af65f22a4564cb95d28e068b7e919b29f)`(self,str path,str mode)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1af65f22a4564cb95d28e068b7e919b29f}

#### `public str `[`working_directory`](#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a994c940507220f2db33fcd649e9ebe41)`(self)` {#classexot_1_1driver_1_1__mixins_1_1FileMethodsMixin_1a994c940507220f2db33fcd649e9ebe41}

# class `exot::driver::_mixins::LockingMethodsMixin` {#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin}

```
class exot::driver::_mixins::LockingMethodsMixin
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool `[`can_execute`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a11eb64b3ec049348213a48a8864a3b56)`(self)` | 
`public def `[`lock_file`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a4c10d6018ecf6a4a4d34baceff5f8ce7)`(self)` | 
`public bool `[`is_locked`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1acca62ce932352b81bba2daf5eebe2b34)`(self)` | 
`public None `[`lock`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a5cd84dc9e802d2869ee1fd9229d10ae1)`(self)` | 
`public bool `[`unlock`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a1aa71374d119b4173829428657693750)`(self)` | 

## Members

#### `public bool `[`can_execute`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a11eb64b3ec049348213a48a8864a3b56)`(self)` {#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a11eb64b3ec049348213a48a8864a3b56}

#### `public def `[`lock_file`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a4c10d6018ecf6a4a4d34baceff5f8ce7)`(self)` {#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a4c10d6018ecf6a4a4d34baceff5f8ce7}

#### `public bool `[`is_locked`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1acca62ce932352b81bba2daf5eebe2b34)`(self)` {#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1acca62ce932352b81bba2daf5eebe2b34}

#### `public None `[`lock`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a5cd84dc9e802d2869ee1fd9229d10ae1)`(self)` {#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a5cd84dc9e802d2869ee1fd9229d10ae1}

#### `public bool `[`unlock`](#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a1aa71374d119b4173829428657693750)`(self)` {#classexot_1_1driver_1_1__mixins_1_1LockingMethodsMixin_1a1aa71374d119b4173829428657693750}

# class `exot::driver::_mixins::PersistenceMethodsMixin` {#classexot_1_1driver_1_1__mixins_1_1PersistenceMethodsMixin}

```
class exot::driver::_mixins::PersistenceMethodsMixin
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public ReturnT `[`persistent`](#classexot_1_1driver_1_1__mixins_1_1PersistenceMethodsMixin_1a71c72ecbde230eb1acae4b8b737e97c2)`(self,CommandT cmd,t.Optional chain,bool sudo,**t.Any kwargs)` | 

## Members

#### `public ReturnT `[`persistent`](#classexot_1_1driver_1_1__mixins_1_1PersistenceMethodsMixin_1a71c72ecbde230eb1acae4b8b737e97c2)`(self,CommandT cmd,t.Optional chain,bool sudo,**t.Any kwargs)` {#classexot_1_1driver_1_1__mixins_1_1PersistenceMethodsMixin_1a71c72ecbde230eb1acae4b8b737e97c2}

# class `exot::driver::_mixins::ProcessMethodsMixin` {#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin}

```
class exot::driver::_mixins::ProcessMethodsMixin
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Tuple`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`, ReturnT] `[`spawn`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a023bb615168b234a5744d3a88dae14eb)`(self,str path,t. Union,t.Dict] args,t.List slaves,*t.Optional details)` | 
`public bool `[`start`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1aa056f0a64b6b2a0f7b7190b14b7796ef)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`stop`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a5c2c5ab42085f24bf7a9dd15e3eaf821)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`kill`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a0fd7c1318d2478d5408f6371591a447c)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`wait`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1aa38aedce8ef38d2b17fc0b051658dff1)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 

## Members

#### `public t.Tuple`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`, ReturnT] `[`spawn`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a023bb615168b234a5744d3a88dae14eb)`(self,str path,t. Union,t.Dict] args,t.List slaves,*t.Optional details)` {#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a023bb615168b234a5744d3a88dae14eb}

#### `public bool `[`start`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1aa056f0a64b6b2a0f7b7190b14b7796ef)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1aa056f0a64b6b2a0f7b7190b14b7796ef}

#### `public bool `[`stop`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a5c2c5ab42085f24bf7a9dd15e3eaf821)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a5c2c5ab42085f24bf7a9dd15e3eaf821}

#### `public bool `[`kill`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a0fd7c1318d2478d5408f6371591a447c)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1a0fd7c1318d2478d5408f6371591a447c}

#### `public bool `[`wait`](#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1aa38aedce8ef38d2b17fc0b051658dff1)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1__mixins_1_1ProcessMethodsMixin_1aa38aedce8ef38d2b17fc0b051658dff1}

# class `exot::driver::_mixins::TransferMethodsMixin` {#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin}

```
class exot::driver::_mixins::TransferMethodsMixin
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool `[`fetch`](#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin_1a31292c2b0f73bd34094a6ef8c7435993)`(t.Union path_from,t.Union path_to,t.List exclude)` | 
`public bool `[`send`](#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin_1af08b11a5da4ad836bf86e2e6daf2b3af)`(self,t.Union path_from,t.Union path_to,t.List exclude)` | 

## Members

#### `public bool `[`fetch`](#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin_1a31292c2b0f73bd34094a6ef8c7435993)`(t.Union path_from,t.Union path_to,t.List exclude)` {#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin_1a31292c2b0f73bd34094a6ef8c7435993}

#### `public bool `[`send`](#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin_1af08b11a5da4ad836bf86e2e6daf2b3af)`(self,t.Union path_from,t.Union path_to,t.List exclude)` {#classexot_1_1driver_1_1__mixins_1_1TransferMethodsMixin_1af08b11a5da4ad836bf86e2e6daf2b3af}

# namespace `exot::driver::_process` {#namespaceexot_1_1driver_1_1__process}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::_process::Process`](#classexot_1_1driver_1_1__process_1_1Process) | 

# class `exot::driver::_process::Process` {#classexot_1_1driver_1_1__process_1_1Process}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`driver`](#classexot_1_1driver_1_1__process_1_1Process_1af4c615dd407260b7fd6e4b8a088c01c2) | 
`public  `[`invocation`](#classexot_1_1driver_1_1__process_1_1Process_1a4005946dce375d692157016991aea6de) | 
`public  `[`identity`](#classexot_1_1driver_1_1__process_1_1Process_1a2ee3a54a895fb1a11998122acb8fca3b) | 
`public  `[`slaves`](#classexot_1_1driver_1_1__process_1_1Process_1a4c89b1b0de874581a6860dd50b827bb7) | 
`public  `[`duration`](#classexot_1_1driver_1_1__process_1_1Process_1adc14fc8627efdb80d1a3fd559d0f3053) | 
`public def `[`__init__`](#classexot_1_1driver_1_1__process_1_1Process_1a2695ae2e5f592eebbdc82a5a687ac99c)`(self,object driver,object invocation,t.Union identity,t.List slaves,t.Optional duration)` | Creates a Process instance
`public str `[`__repr__`](#classexot_1_1driver_1_1__process_1_1Process_1a7e12a3d2c9c5d42674166cb6322a9fbf)`(self)` | 
`public int `[`__hash__`](#classexot_1_1driver_1_1__process_1_1Process_1aaf7166fb8a0e9d8d3efd862982055a9e)`(self)` | 
`public t.Optional[int] `[`exited`](#classexot_1_1driver_1_1__process_1_1Process_1a8b0e04f5395f34e5b42c861f0fc27296)`(self)` | Gets the exit code of the process
`public t.Optional[str] `[`stderr`](#classexot_1_1driver_1_1__process_1_1Process_1ace75871e26fd0804949625548080778a)`(self)` | Gets the invocation's standard error
`public t.Optional[str] `[`stdout`](#classexot_1_1driver_1_1__process_1_1Process_1ae7564c7598d84747097cf7341318259b)`(self)` | Gets the invocation's standard output
`public t.List[t.Union[int, str]] `[`children`](#classexot_1_1driver_1_1__process_1_1Process_1ad33240283612bc019372c8bfa6dc8ffe)`(self)` | Gets the identities of child properties
`public t.List`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`] `[`slaves`](#classexot_1_1driver_1_1__process_1_1Process_1ac222935325f047a4ae85241ac924e9a6)`(self)` | Gets the slave processes
`public None `[`slaves`](#classexot_1_1driver_1_1__process_1_1Process_1a3b284eb472f1eb9404ebe2bf177c2067)`(self,t.List value)` | Sets the slave processes
`public def `[`update`](#classexot_1_1driver_1_1__process_1_1Process_1a5bdf0591026db79102df2476209a680c)`(self)` | Updates the process status

## Members

#### `public  `[`driver`](#classexot_1_1driver_1_1__process_1_1Process_1af4c615dd407260b7fd6e4b8a088c01c2) {#classexot_1_1driver_1_1__process_1_1Process_1af4c615dd407260b7fd6e4b8a088c01c2}

#### `public  `[`invocation`](#classexot_1_1driver_1_1__process_1_1Process_1a4005946dce375d692157016991aea6de) {#classexot_1_1driver_1_1__process_1_1Process_1a4005946dce375d692157016991aea6de}

#### `public  `[`identity`](#classexot_1_1driver_1_1__process_1_1Process_1a2ee3a54a895fb1a11998122acb8fca3b) {#classexot_1_1driver_1_1__process_1_1Process_1a2ee3a54a895fb1a11998122acb8fca3b}

#### `public  `[`slaves`](#classexot_1_1driver_1_1__process_1_1Process_1a4c89b1b0de874581a6860dd50b827bb7) {#classexot_1_1driver_1_1__process_1_1Process_1a4c89b1b0de874581a6860dd50b827bb7}

#### `public  `[`duration`](#classexot_1_1driver_1_1__process_1_1Process_1adc14fc8627efdb80d1a3fd559d0f3053) {#classexot_1_1driver_1_1__process_1_1Process_1adc14fc8627efdb80d1a3fd559d0f3053}

#### `public def `[`__init__`](#classexot_1_1driver_1_1__process_1_1Process_1a2695ae2e5f592eebbdc82a5a687ac99c)`(self,object driver,object invocation,t.Union identity,t.List slaves,t.Optional duration)` {#classexot_1_1driver_1_1__process_1_1Process_1a2695ae2e5f592eebbdc82a5a687ac99c}

Creates a Process instance

Args:
    driver (object): The driver
    invocation (object): The command invocation (invoke_result)
    identity (t.Union[int, str]): The identity, for example the PID or Component name
    slaves (t.List[Process], optional): The slave processes

#### `public str `[`__repr__`](#classexot_1_1driver_1_1__process_1_1Process_1a7e12a3d2c9c5d42674166cb6322a9fbf)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1a7e12a3d2c9c5d42674166cb6322a9fbf}

#### `public int `[`__hash__`](#classexot_1_1driver_1_1__process_1_1Process_1aaf7166fb8a0e9d8d3efd862982055a9e)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1aaf7166fb8a0e9d8d3efd862982055a9e}

#### `public t.Optional[int] `[`exited`](#classexot_1_1driver_1_1__process_1_1Process_1a8b0e04f5395f34e5b42c861f0fc27296)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1a8b0e04f5395f34e5b42c861f0fc27296}

Gets the exit code of the process

Returns:
    t.Optional[int]: The exit code or None if failed or running

#### `public t.Optional[str] `[`stderr`](#classexot_1_1driver_1_1__process_1_1Process_1ace75871e26fd0804949625548080778a)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1ace75871e26fd0804949625548080778a}

Gets the invocation's standard error

Returns:
    t.Optional[str]: The standard error

#### `public t.Optional[str] `[`stdout`](#classexot_1_1driver_1_1__process_1_1Process_1ae7564c7598d84747097cf7341318259b)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1ae7564c7598d84747097cf7341318259b}

Gets the invocation's standard output

Returns:
    t.Optional[str]: The standard output

#### `public t.List[t.Union[int, str]] `[`children`](#classexot_1_1driver_1_1__process_1_1Process_1ad33240283612bc019372c8bfa6dc8ffe)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1ad33240283612bc019372c8bfa6dc8ffe}

Gets the identities of child properties

Returns:
    t.List[t.Union[int, str]]: The children identities

#### `public t.List`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`] `[`slaves`](#classexot_1_1driver_1_1__process_1_1Process_1ac222935325f047a4ae85241ac924e9a6)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1ac222935325f047a4ae85241ac924e9a6}

Gets the slave processes

Returns:
    t.List[Process]: The slave processes

#### `public None `[`slaves`](#classexot_1_1driver_1_1__process_1_1Process_1a3b284eb472f1eb9404ebe2bf177c2067)`(self,t.List value)` {#classexot_1_1driver_1_1__process_1_1Process_1a3b284eb472f1eb9404ebe2bf177c2067}

Sets the slave processes

Args:
    value (t.List[Process]): The list of slave processes

Raises:
    TypeError: Wrong type(s) supplied

#### `public def `[`update`](#classexot_1_1driver_1_1__process_1_1Process_1a5bdf0591026db79102df2476209a680c)`(self)` {#classexot_1_1driver_1_1__process_1_1Process_1a5bdf0591026db79102df2476209a680c}

Updates the process status

# namespace `exot::driver::backend_adb` {#namespaceexot_1_1driver_1_1backend__adb}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::backend_adb::ADBBackend`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend) | 

# class `exot::driver::backend_adb::ADBBackend` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend}

```
class exot::driver::backend_adb::ADBBackend
  : public exot.driver._backend.Backend
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`keyfile`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a0c711c842c5b61203ea651749941aa51) | 
`public  `[`adb_port`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a550f139876ab0ddd3bc8061cce0b7e0f) | 
`public  `[`adb_ip`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a17215a60d1db567c06b0f3edd767a4bc) | 
`public t.List[str] `[`required_config_keys`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a97a0b99e0313e93be7ab27feddc19e4f)`(self)` | 
`public t.NoReturn `[`validate`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a08431aaf9150ddf609dc5d098c785c15)`(self)` | Implements `validate` from the Configurable base class
`public def `[`__init__`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a02d85c4498bab91bddef6fc07f7f64d7)`(self,* args,** kwargs)` | Initialises the backend
`public str `[`adb_port`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a23187fe13a21914e46e02367f6be0e60)`(self)` | 
`public None `[`adb_port`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aff53d695c6ad8ee241a1afe64f8c8c21)`(self,str value)` | 
`public str `[`adb_ip`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af362887487d51009be1679c6e5334f67)`(self)` | 
`public None `[`adb_ip`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a1de4d5999e8addcf1a2c2b000611954f)`(self,str value)` | 
`public str `[`adb_stdout`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a8209cd622d6df402f425aa2644e104f4)`(self)` | 
`public str `[`adb_stderr`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a776674c272c0ab40a0d2e02b747e0dcf)`(self)` | 
`public str `[`adb_key`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aa0be90a8c0ab27a10e0375bc05041465)`(self)` | 
`public dict `[`adb_params`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a4955028abcb2365d1c817319da3c6aa4)`(self)` | 
`public def `[`keyfile`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1acfb62cc8207d4e11069db20d8eeb0957)`(self)` | 
`public def `[`keyfile`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1add6055575fd19e47a71af87fbd5ea877)`(self,value)` | 
`public def `[`__getstate__`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aef1d8add13239501addea219631d799a)`(self)` | 
`public def `[`__setstate__`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a57b601b61e545289431e8e48126c67ba)`(self,value)` | 
`public t.Optional[fabric.Connection] `[`gateway`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a9f2df18c90e5aa549c365f2686c63148)`(self)` | 
`public bool `[`can_connect`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a5ea9f282c9bff941e34ebcfe5b2f09a8)`(self)` | Can the backend connect to its target?
`public bool `[`connected`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1abe393c31c153fc369a50064b8133712f)`(self)` | Is the backend connected?
`public t.Optional[invoke.Context] `[`connection`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a1404bab9cb4cc909c0b724560ef3fc1e)`(self)` | Gets the underlying implementation-specific connection object
`public def `[`is_server_spawned`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a0da2151b8ee1b4f0cd507c816550f69e)`(self)` | 
`public def `[`is_usb`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af42cdc6623589bbe5b7701387b2c9dfe)`(self)` | 
`public None `[`connect`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1ac48b8b1d217a702d5e24504d450b37e3)`(self)` | Connects the backend
`public t.List[str] `[`devices`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af10d5313a9824f17fd589d1a2b9a8e4f)`(self)` | 
`public None `[`disconnect`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aa719d7f2cdd8aee0607b9852752dddfa)`(self)` | Disconnects the backend
`public Backend.ReturnT `[`run`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a6693a4fdfec36b61b3e9498a2ca91683)`(self,Backend.CommandT cmd,** kwargs)` | As ADB often does not properly forward the return values of commands, we
`public Backend.ReturnT `[`sudo`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1ad734257c2be5138fec04e7f4f4c98df1)`(self,Backend.CommandT cmd,** kwargs)` | 
`public Backend.ReturnT `[`send_intent`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a7f00e2a04e600c7b66a6a154f5adecaa)`(self,Intent intent,str kind)` | 

## Members

#### `public  `[`keyfile`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a0c711c842c5b61203ea651749941aa51) {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a0c711c842c5b61203ea651749941aa51}

#### `public  `[`adb_port`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a550f139876ab0ddd3bc8061cce0b7e0f) {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a550f139876ab0ddd3bc8061cce0b7e0f}

#### `public  `[`adb_ip`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a17215a60d1db567c06b0f3edd767a4bc) {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a17215a60d1db567c06b0f3edd767a4bc}

#### `public t.List[str] `[`required_config_keys`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a97a0b99e0313e93be7ab27feddc19e4f)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a97a0b99e0313e93be7ab27feddc19e4f}

#### `public t.NoReturn `[`validate`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a08431aaf9150ddf609dc5d098c785c15)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a08431aaf9150ddf609dc5d098c785c15}

Implements `validate` from the Configurable base class

#### `public def `[`__init__`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a02d85c4498bab91bddef6fc07f7f64d7)`(self,* args,** kwargs)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a02d85c4498bab91bddef6fc07f7f64d7}

Initialises the backend

Args:
    *args: Positional arguments passed to the base class
    **kwargs: Keyword arguments passed to the base class

#### `public str `[`adb_port`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a23187fe13a21914e46e02367f6be0e60)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a23187fe13a21914e46e02367f6be0e60}

#### `public None `[`adb_port`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aff53d695c6ad8ee241a1afe64f8c8c21)`(self,str value)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aff53d695c6ad8ee241a1afe64f8c8c21}

#### `public str `[`adb_ip`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af362887487d51009be1679c6e5334f67)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af362887487d51009be1679c6e5334f67}

#### `public None `[`adb_ip`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a1de4d5999e8addcf1a2c2b000611954f)`(self,str value)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a1de4d5999e8addcf1a2c2b000611954f}

#### `public str `[`adb_stdout`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a8209cd622d6df402f425aa2644e104f4)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a8209cd622d6df402f425aa2644e104f4}

#### `public str `[`adb_stderr`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a776674c272c0ab40a0d2e02b747e0dcf)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a776674c272c0ab40a0d2e02b747e0dcf}

#### `public str `[`adb_key`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aa0be90a8c0ab27a10e0375bc05041465)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aa0be90a8c0ab27a10e0375bc05041465}

#### `public dict `[`adb_params`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a4955028abcb2365d1c817319da3c6aa4)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a4955028abcb2365d1c817319da3c6aa4}

#### `public def `[`keyfile`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1acfb62cc8207d4e11069db20d8eeb0957)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1acfb62cc8207d4e11069db20d8eeb0957}

#### `public def `[`keyfile`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1add6055575fd19e47a71af87fbd5ea877)`(self,value)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1add6055575fd19e47a71af87fbd5ea877}

#### `public def `[`__getstate__`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aef1d8add13239501addea219631d799a)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aef1d8add13239501addea219631d799a}

#### `public def `[`__setstate__`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a57b601b61e545289431e8e48126c67ba)`(self,value)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a57b601b61e545289431e8e48126c67ba}

#### `public t.Optional[fabric.Connection] `[`gateway`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a9f2df18c90e5aa549c365f2686c63148)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a9f2df18c90e5aa549c365f2686c63148}

#### `public bool `[`can_connect`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a5ea9f282c9bff941e34ebcfe5b2f09a8)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a5ea9f282c9bff941e34ebcfe5b2f09a8}

Can the backend connect to its target?

Returns:
    bool: True if properly configured

#### `public bool `[`connected`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1abe393c31c153fc369a50064b8133712f)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1abe393c31c153fc369a50064b8133712f}

Is the backend connected?

#### `public t.Optional[invoke.Context] `[`connection`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a1404bab9cb4cc909c0b724560ef3fc1e)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a1404bab9cb4cc909c0b724560ef3fc1e}

Gets the underlying implementation-specific connection object

#### `public def `[`is_server_spawned`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a0da2151b8ee1b4f0cd507c816550f69e)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a0da2151b8ee1b4f0cd507c816550f69e}

#### `public def `[`is_usb`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af42cdc6623589bbe5b7701387b2c9dfe)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af42cdc6623589bbe5b7701387b2c9dfe}

#### `public None `[`connect`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1ac48b8b1d217a702d5e24504d450b37e3)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1ac48b8b1d217a702d5e24504d450b37e3}

Connects the backend

#### `public t.List[str] `[`devices`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af10d5313a9824f17fd589d1a2b9a8e4f)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1af10d5313a9824f17fd589d1a2b9a8e4f}

#### `public None `[`disconnect`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aa719d7f2cdd8aee0607b9852752dddfa)`(self)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1aa719d7f2cdd8aee0607b9852752dddfa}

Disconnects the backend

#### `public Backend.ReturnT `[`run`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a6693a4fdfec36b61b3e9498a2ca91683)`(self,Backend.CommandT cmd,** kwargs)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a6693a4fdfec36b61b3e9498a2ca91683}

As ADB often does not properly forward the return values of commands, we
append the return value to the stdout stream. This function also parses
the return value from stdout to ensure compatibiliy. We do this for all commands
except the activity manager (am), as quoting creates issues with the extras.

#### `public Backend.ReturnT `[`sudo`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1ad734257c2be5138fec04e7f4f4c98df1)`(self,Backend.CommandT cmd,** kwargs)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1ad734257c2be5138fec04e7f4f4c98df1}

#### `public Backend.ReturnT `[`send_intent`](#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a7f00e2a04e600c7b66a6a154f5adecaa)`(self,Intent intent,str kind)` {#classexot_1_1driver_1_1backend__adb_1_1ADBBackend_1a7f00e2a04e600c7b66a6a154f5adecaa}

# namespace `exot::driver::backend_ssh` {#namespaceexot_1_1driver_1_1backend__ssh}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::backend_ssh::SSHBackend`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend) | 

# class `exot::driver::backend_ssh::SSHBackend` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend}

```
class exot::driver::backend_ssh::SSHBackend
  : public exot.driver._backend.Backend
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`keyfile`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8c474d2d621b3ec593bff22bd12803cd) | 
`public t.List[str] `[`required_config_keys`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a69a8c659b97d50ae3ec779bba79a191f)`(self)` | 
`public t.NoReturn `[`validate`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a9123fc667a1e140f4d9362fff842371b)`(self)` | Implements `validate` from the Configurable base class
`public bool `[`can_connect`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a6dc6a0a20500852a213f2229b1a5140a)`(self)` | Can the backend connect to its target?
`public def `[`keyfile`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a32004afe0a31514abb0c27c3e1e3012e)`(self)` | 
`public def `[`keyfile`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ae49ebcdd176b14ac442b6b67ee759b9a)`(self,value)` | 
`public def `[`__getstate__`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8f60e25c6ccdcecfa46f40ca576ea558)`(self)` | 
`public def `[`__setstate__`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1af7ade1960999c3f7e2ff5d8d7ad6756b)`(self,value)` | 
`public t.Optional[fabric.Connection] `[`gateway`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8e431e400d5bb85bf1bb2e9c5221b8f9)`(self)` | 
`public bool `[`connected`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ae62acc4d70bb1339c268ec39fb2da354)`(self)` | Is the backend connected?
`public None `[`connect`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a7a0b65e27bf62f08325a1062cf752a84)`(self)` | Connects the backend
`public None `[`disconnect`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ac833841a2f6eb3a9a13d4c9b87e03c79)`(self)` | Disconnects the backend
`public t.Optional[fabric.Connection] `[`connection`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a4b6204f4173dee5cbc87cff340269c49)`(self)` | Gets the underlying implementation-specific connection object
`public Backend.ReturnT `[`run`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a44de8a400146c66d9fc822870c9bca99)`(self,Backend.CommandT cmd,**t.Any kwargs)` | 
`public Backend.ReturnT `[`sudo`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ac590e9710e24ff7a8647014059c09a1e)`(self,Backend.CommandT cmd,**t.Any kwargs)` | 

## Members

#### `public  `[`keyfile`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8c474d2d621b3ec593bff22bd12803cd) {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8c474d2d621b3ec593bff22bd12803cd}

#### `public t.List[str] `[`required_config_keys`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a69a8c659b97d50ae3ec779bba79a191f)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a69a8c659b97d50ae3ec779bba79a191f}

#### `public t.NoReturn `[`validate`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a9123fc667a1e140f4d9362fff842371b)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a9123fc667a1e140f4d9362fff842371b}

Implements `validate` from the Configurable base class

#### `public bool `[`can_connect`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a6dc6a0a20500852a213f2229b1a5140a)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a6dc6a0a20500852a213f2229b1a5140a}

Can the backend connect to its target?

Returns:
    bool: True if properly configured

#### `public def `[`keyfile`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a32004afe0a31514abb0c27c3e1e3012e)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a32004afe0a31514abb0c27c3e1e3012e}

#### `public def `[`keyfile`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ae49ebcdd176b14ac442b6b67ee759b9a)`(self,value)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ae49ebcdd176b14ac442b6b67ee759b9a}

#### `public def `[`__getstate__`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8f60e25c6ccdcecfa46f40ca576ea558)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8f60e25c6ccdcecfa46f40ca576ea558}

#### `public def `[`__setstate__`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1af7ade1960999c3f7e2ff5d8d7ad6756b)`(self,value)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1af7ade1960999c3f7e2ff5d8d7ad6756b}

#### `public t.Optional[fabric.Connection] `[`gateway`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8e431e400d5bb85bf1bb2e9c5221b8f9)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a8e431e400d5bb85bf1bb2e9c5221b8f9}

#### `public bool `[`connected`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ae62acc4d70bb1339c268ec39fb2da354)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ae62acc4d70bb1339c268ec39fb2da354}

Is the backend connected?

#### `public None `[`connect`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a7a0b65e27bf62f08325a1062cf752a84)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a7a0b65e27bf62f08325a1062cf752a84}

Connects the backend

#### `public None `[`disconnect`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ac833841a2f6eb3a9a13d4c9b87e03c79)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ac833841a2f6eb3a9a13d4c9b87e03c79}

Disconnects the backend

#### `public t.Optional[fabric.Connection] `[`connection`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a4b6204f4173dee5cbc87cff340269c49)`(self)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a4b6204f4173dee5cbc87cff340269c49}

Gets the underlying implementation-specific connection object

#### `public Backend.ReturnT `[`run`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a44de8a400146c66d9fc822870c9bca99)`(self,Backend.CommandT cmd,**t.Any kwargs)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1a44de8a400146c66d9fc822870c9bca99}

#### `public Backend.ReturnT `[`sudo`](#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ac590e9710e24ff7a8647014059c09a1e)`(self,Backend.CommandT cmd,**t.Any kwargs)` {#classexot_1_1driver_1_1backend__ssh_1_1SSHBackend_1ac590e9710e24ff7a8647014059c09a1e}

# namespace `exot::driver::driver_android` {#namespaceexot_1_1driver_1_1driver__android}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::driver_android::ADBAndroidDriver`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver) | 
`class `[`exot::driver::driver_android::EXOT_APP_STATE`](#classexot_1_1driver_1_1driver__android_1_1EXOT__APP__STATE) | 
`class `[`exot::driver::driver_android::Invocation`](#classexot_1_1driver_1_1driver__android_1_1Invocation) | 
`class `[`exot::driver::driver_android::STANDALONE_APP_STATE`](#classexot_1_1driver_1_1driver__android_1_1STANDALONE__APP__STATE) | 

# class `exot::driver::driver_android::ADBAndroidDriver` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver}

```
class exot::driver::driver_android::ADBAndroidDriver
  : public exot.driver.extensions.android.AndroidMethods
  : public exot.driver.extensions.sysfs.StateMethods
  : public exot.driver.extensions.unix.LatencyMethods
  : public exot.driver.extensions.unix.LockingMethods
  : public exot.driver.extensions.unix.ExtraFileMethods
  : public exot.driver.extensions.unix.FileMethods
  : public exot.driver._driver.Driver
  : public backend
  : public exot.driver.backend_adb.ADBBackend
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`reboot_count`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a20aae18a1ce61cc227502eb5ac48f849) | 
`public def `[`lock_file`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aa1e2e56cc04af70d241deafdbef7b353)`(self)` | 
`public def `[`getable_states`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ac7f15db919b72cd83e2efe2d01408311)`(self)` | 
`public def `[`setable_states`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aed63dda0b99c934c2c32480c25752062)`(self)` | 
`public def `[`latency`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ae08f0ecc42a39296095e9d4ac0996eb5)`(self)` | Get the CPU DMA latency from devfs
`public def `[`latency`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a594e213878d14b6c1388b89692b68656)`(self,t.Any value)` | No way of running a persistent background process so far, setter is disabled
`public bool `[`executable_exists`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a22b7157e5e2c34ec1cc56843c8e55630)`(self,str executable)` | Checks if an executable exists locally or on the system
`public t.Tuple`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`, ADBBackend.ReturnT] `[`spawn`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a8c8bc53231add082c4fdbddad14d2ad8)`(self,str path,t.List args,t.List slaves,t.Optional details)` | 
`public bool `[`start`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a245e13a6232f6fa4d3068dd6e540e22c)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`stop`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a229e4ffa13fcffd7a38891de20642b1b)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`kill`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a126144d047ec4b2abe3c62953e9843ca)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`wait`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a3194dabe20a20e2d628d554e4ce7603c)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public int `[`reboot_count`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a7590ceee70f539492676233ceac02ba2)`(self)` | 
`public def `[`reboot_count`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a90f3a14669ee299afa6b15a173e77580)`(self,int value)` | 
`public def `[`reboot_device`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1adaa6013f52e61402e44a202901836c1f)`(self)` | 
`public None `[`initstate`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ad6f3772ef5984dfbad7ac3fab81824b2)`(self)` | 
`public def `[`cleanup`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aee463c7929e3508bbf9abd8eff634530)`(self)` | 
`public ADBBackend.ReturnT `[`fetch`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a169830474011b2e06b54876cf1c3e55f)`(self,t.Union path_from,t.Union path_to,t.List exclude)` | Fetches data from the device
`public ADBBackend.ReturnT `[`send`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a671d06ed497fb932d1e4b7d3f1aad1f3)`(self,t.Union path_from,t.Union path_to,t.List exclude)` | Sends data to the device

## Members

#### `public  `[`reboot_count`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a20aae18a1ce61cc227502eb5ac48f849) {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a20aae18a1ce61cc227502eb5ac48f849}

#### `public def `[`lock_file`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aa1e2e56cc04af70d241deafdbef7b353)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aa1e2e56cc04af70d241deafdbef7b353}

#### `public def `[`getable_states`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ac7f15db919b72cd83e2efe2d01408311)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ac7f15db919b72cd83e2efe2d01408311}

#### `public def `[`setable_states`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aed63dda0b99c934c2c32480c25752062)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aed63dda0b99c934c2c32480c25752062}

#### `public def `[`latency`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ae08f0ecc42a39296095e9d4ac0996eb5)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ae08f0ecc42a39296095e9d4ac0996eb5}

Get the CPU DMA latency from devfs

Returns:
    t.Optional[int]: an integer value or None if unsuccessful

#### `public def `[`latency`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a594e213878d14b6c1388b89692b68656)`(self,t.Any value)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a594e213878d14b6c1388b89692b68656}

No way of running a persistent background process so far, setter is disabled

#### `public bool `[`executable_exists`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a22b7157e5e2c34ec1cc56843c8e55630)`(self,str executable)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a22b7157e5e2c34ec1cc56843c8e55630}

Checks if an executable exists locally or on the system

Args:
    executable (str): The executable, either a path or an app name

Returns:
    bool: True if exists and is an executable

#### `public t.Tuple`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`, ADBBackend.ReturnT] `[`spawn`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a8c8bc53231add082c4fdbddad14d2ad8)`(self,str path,t.List args,t.List slaves,t.Optional details)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a8c8bc53231add082c4fdbddad14d2ad8}

#### `public bool `[`start`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a245e13a6232f6fa4d3068dd6e540e22c)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a245e13a6232f6fa4d3068dd6e540e22c}

#### `public bool `[`stop`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a229e4ffa13fcffd7a38891de20642b1b)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a229e4ffa13fcffd7a38891de20642b1b}

#### `public bool `[`kill`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a126144d047ec4b2abe3c62953e9843ca)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a126144d047ec4b2abe3c62953e9843ca}

#### `public bool `[`wait`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a3194dabe20a20e2d628d554e4ce7603c)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a3194dabe20a20e2d628d554e4ce7603c}

#### `public int `[`reboot_count`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a7590ceee70f539492676233ceac02ba2)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a7590ceee70f539492676233ceac02ba2}

#### `public def `[`reboot_count`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a90f3a14669ee299afa6b15a173e77580)`(self,int value)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a90f3a14669ee299afa6b15a173e77580}

#### `public def `[`reboot_device`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1adaa6013f52e61402e44a202901836c1f)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1adaa6013f52e61402e44a202901836c1f}

#### `public None `[`initstate`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ad6f3772ef5984dfbad7ac3fab81824b2)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1ad6f3772ef5984dfbad7ac3fab81824b2}

#### `public def `[`cleanup`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aee463c7929e3508bbf9abd8eff634530)`(self)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1aee463c7929e3508bbf9abd8eff634530}

#### `public ADBBackend.ReturnT `[`fetch`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a169830474011b2e06b54876cf1c3e55f)`(self,t.Union path_from,t.Union path_to,t.List exclude)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a169830474011b2e06b54876cf1c3e55f}

Fetches data from the device

Due to how ADB file transfer with 'push' and 'pull' works, if the source path is a
directory, we first make a temporary local directory (with `tempfile.mkdtemp`), then
transfer the entire directory from the source there, and then use rsync locally
to allow filtering out and synchronising directories.

Args:
    path_from (t.Union[Path, str]): The path to a file/folder on the device
    path_to (t.Union[Path, str]): The path to the destination file/folder
    exclude (t.List[str], optional): The exclusion list

#### `public ADBBackend.ReturnT `[`send`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a671d06ed497fb932d1e4b7d3f1aad1f3)`(self,t.Union path_from,t.Union path_to,t.List exclude)` {#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver_1a671d06ed497fb932d1e4b7d3f1aad1f3}

Sends data to the device

Due to how ADB file transfer with 'push' and 'pull' works, if the local path is a
directory, we first make a temporary local directory (with `tempfile.mkdtemp`), then
use rsync locally to apply exclusion list and  synchronise with the source directory,
and then transfer the temporary directory to the device.

Args:
    path_from (t.Union[Path, str]): The local file/folder
    path_to (t.Union[Path, str]): The path to the destination file/folder
    exclude (t.List[str], optional): The exclusion list

# class `exot::driver::driver_android::EXOT_APP_STATE` {#classexot_1_1driver_1_1driver__android_1_1EXOT__APP__STATE}

```
class exot::driver::driver_android::EXOT_APP_STATE
  : public Enum
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::driver::driver_android::Invocation` {#classexot_1_1driver_1_1driver__android_1_1Invocation}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`driver`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a3cae84a6e47fdb99222577bdeeafa8ef) | 
`public  `[`component`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a41ffc6da21c2a9304c9ad23d72de3b6d) | 
`public  `[`is_framework_app`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a61d9af4633a06b7c6e1f3d63e6b7106c) | 
`public  `[`details`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a5f7933b15d29a054fa57d967948220d9) | 
`public  `[`spawned_at`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a030e5ce4d3008bfd6be49195080aae11) | 
`public  `[`duration`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ada8646d11d075a1acc79bf1abe518526) | 
`public def `[`__init__`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ae2fbde6b0798852e8c3e993fe26dd5d1)`(self,`[`ADBAndroidDriver`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver)` driver,str component,bool is_framework_app,t.Dict details,datetime spawned_at,t.Optional duration,bool exit_on_expiration)` | Creates the invocation object
`public str `[`__repr__`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ab01b9bf7510068b31b77ee298f813121)`(self)` | 
`public timedelta `[`active_time`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a066a18ba4024866ca5b3e341d02b13d3)`(self)` | Gets the active time (since spawning)
`public t.Optional[timedelta] `[`running_time`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1af6a4523410a160e72ab66fe9ffd37789)`(self)` | Gets the running time (since started)
`public t.Optional[timedelta] `[`remaining_time`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ae88ebc6f50ff0c17e14aad8bae3db5fd)`(self)` | Gets the remaining time
`public datetime `[`started_at`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a2691fb771ba9bd20e865bd8080db3fc7)`(self)` | 
`public None `[`started_at`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ac075e83e2c404ae4b083092836de20ed)`(self,value)` | 
`public bool `[`ok`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a5c58bb15e59e52bcbbbd6c4910075b87)`(self)` | Exited correctly?
`public t.Optional[int] `[`exited`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a03a2fb4331286295fe6ef857cc3bba04)`(self)` | Gets the exit code of the process
`public str `[`stderr`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a11bd1c8b99f625ea679f4c2af0f2ae4a)`(self)` | Gets the "standard error"
`public str `[`stdout`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a7b5cfe912582f24c9b51f8d4cb82dd00)`(self)` | 
`public t.Union`[`[EXOT_APP_STATE](#classexot_1_1driver_1_1driver__android_1_1EXOT__APP__STATE), [STANDALONE_APP_STATE`](#classexot_1_1driver_1_1driver__android_1_1STANDALONE__APP__STATE)`] `[`query_state`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a309b0d944ef2dfbbfd781b5e5f55e859)`(self)` | Queries the state
`public def `[`update`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a804b6953644b854187e224decc65e7a7)`(self)` | Updates the state

## Members

#### `public  `[`driver`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a3cae84a6e47fdb99222577bdeeafa8ef) {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a3cae84a6e47fdb99222577bdeeafa8ef}

#### `public  `[`component`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a41ffc6da21c2a9304c9ad23d72de3b6d) {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a41ffc6da21c2a9304c9ad23d72de3b6d}

#### `public  `[`is_framework_app`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a61d9af4633a06b7c6e1f3d63e6b7106c) {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a61d9af4633a06b7c6e1f3d63e6b7106c}

#### `public  `[`details`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a5f7933b15d29a054fa57d967948220d9) {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a5f7933b15d29a054fa57d967948220d9}

#### `public  `[`spawned_at`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a030e5ce4d3008bfd6be49195080aae11) {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a030e5ce4d3008bfd6be49195080aae11}

#### `public  `[`duration`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ada8646d11d075a1acc79bf1abe518526) {#classexot_1_1driver_1_1driver__android_1_1Invocation_1ada8646d11d075a1acc79bf1abe518526}

#### `public def `[`__init__`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ae2fbde6b0798852e8c3e993fe26dd5d1)`(self,`[`ADBAndroidDriver`](#classexot_1_1driver_1_1driver__android_1_1ADBAndroidDriver)` driver,str component,bool is_framework_app,t.Dict details,datetime spawned_at,t.Optional duration,bool exit_on_expiration)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1ae2fbde6b0798852e8c3e993fe26dd5d1}

Creates the invocation object

Args:
    driver (ADBAndroidDriver): The driver
    component (str): The component/identity
    is_framework_app (bool): Is this a framework app?
    spawned_at (datetime, optional): Spawning time point
    duration (t.Optional[float], optional): Estimated duration?
    exit_on_expiration (bool, optional): Should report as exited once estimated duration is reached?

#### `public str `[`__repr__`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ab01b9bf7510068b31b77ee298f813121)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1ab01b9bf7510068b31b77ee298f813121}

#### `public timedelta `[`active_time`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a066a18ba4024866ca5b3e341d02b13d3)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a066a18ba4024866ca5b3e341d02b13d3}

Gets the active time (since spawning)

Returns:
    timedelta: The active time

#### `public t.Optional[timedelta] `[`running_time`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1af6a4523410a160e72ab66fe9ffd37789)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1af6a4523410a160e72ab66fe9ffd37789}

Gets the running time (since started)

Returns:
    t.Optional[timedelta]: The running time

#### `public t.Optional[timedelta] `[`remaining_time`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ae88ebc6f50ff0c17e14aad8bae3db5fd)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1ae88ebc6f50ff0c17e14aad8bae3db5fd}

Gets the remaining time

Returns:
    t.Optional[timedelta]: Remaining time if expiration time is set

#### `public datetime `[`started_at`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a2691fb771ba9bd20e865bd8080db3fc7)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a2691fb771ba9bd20e865bd8080db3fc7}

#### `public None `[`started_at`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1ac075e83e2c404ae4b083092836de20ed)`(self,value)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1ac075e83e2c404ae4b083092836de20ed}

#### `public bool `[`ok`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a5c58bb15e59e52bcbbbd6c4910075b87)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a5c58bb15e59e52bcbbbd6c4910075b87}

Exited correctly?

Returns:
    bool: True if exited with zero exit code

#### `public t.Optional[int] `[`exited`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a03a2fb4331286295fe6ef857cc3bba04)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a03a2fb4331286295fe6ef857cc3bba04}

Gets the exit code of the process

Returns:
    t.Optional[int]: The exit code or None if not exited

#### `public str `[`stderr`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a11bd1c8b99f625ea679f4c2af0f2ae4a)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a11bd1c8b99f625ea679f4c2af0f2ae4a}

Gets the "standard error"

Returns:
    str: The "standard error" output, i.e. the log lines that match the self._search_str

#### `public str `[`stdout`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a7b5cfe912582f24c9b51f8d4cb82dd00)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a7b5cfe912582f24c9b51f8d4cb82dd00}

#### `public t.Union`[`[EXOT_APP_STATE](#classexot_1_1driver_1_1driver__android_1_1EXOT__APP__STATE), [STANDALONE_APP_STATE`](#classexot_1_1driver_1_1driver__android_1_1STANDALONE__APP__STATE)`] `[`query_state`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a309b0d944ef2dfbbfd781b5e5f55e859)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a309b0d944ef2dfbbfd781b5e5f55e859}

Queries the state

Returns:
    t.Union[EXOT_APP_STATE, STANDALONE_APP_STATE]: The state

#### `public def `[`update`](#classexot_1_1driver_1_1driver__android_1_1Invocation_1a804b6953644b854187e224decc65e7a7)`(self)` {#classexot_1_1driver_1_1driver__android_1_1Invocation_1a804b6953644b854187e224decc65e7a7}

Updates the state

# class `exot::driver::driver_android::STANDALONE_APP_STATE` {#classexot_1_1driver_1_1driver__android_1_1STANDALONE__APP__STATE}

```
class exot::driver::driver_android::STANDALONE_APP_STATE
  : public Enum
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::driver::driver_unix` {#namespaceexot_1_1driver_1_1driver__unix}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::driver_unix::SSHUnixDriver`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver) | 

# class `exot::driver::driver_unix::SSHUnixDriver` {#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver}

```
class exot::driver::driver_unix::SSHUnixDriver
  : public exot.driver.extensions.rsync.TransferMethods
  : public exot.driver.extensions.sysfs.StateMethods
  : public exot.driver.extensions.unix.FanMethods
  : public exot.driver.extensions.unix.LatencyMethods
  : public exot.driver.extensions.unix.LockingMethods
  : public exot.driver.extensions.unix.ProcessMethods
  : public exot.driver.extensions.unix.PersistenceMethods
  : public exot.driver.extensions.unix.ExtraFileMethods
  : public exot.driver.extensions.unix.FileMethods
  : public exot.driver._driver.Driver
  : public backend
  : public exot.driver.backend_ssh.SSHBackend
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`lock_file`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a4125b64f1b3315aeb5092f89e1fcc9b4)`(self)` | 
`public def `[`setable_states`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a6e43372800aae07eaf242146b0600144)`(self)` | 
`public def `[`getable_states`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a2da7ca209477f444294777c12cf62e84)`(self)` | 
`public t.Tuple`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`, Backend.ReturnT] `[`spawn`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1ab0a0196ebb218f56cc1c316fdd0a1cab)`(self,str path,t.List args,t.List slaves,*t.Optional details)` | 
`public None `[`cleanup`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a6415dfdcff50c421773dd01c6449ea26)`(self)` | 

## Members

#### `public def `[`lock_file`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a4125b64f1b3315aeb5092f89e1fcc9b4)`(self)` {#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a4125b64f1b3315aeb5092f89e1fcc9b4}

#### `public def `[`setable_states`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a6e43372800aae07eaf242146b0600144)`(self)` {#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a6e43372800aae07eaf242146b0600144}

#### `public def `[`getable_states`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a2da7ca209477f444294777c12cf62e84)`(self)` {#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a2da7ca209477f444294777c12cf62e84}

#### `public t.Tuple`[`[Process`](#classexot_1_1driver_1_1__process_1_1Process)`, Backend.ReturnT] `[`spawn`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1ab0a0196ebb218f56cc1c316fdd0a1cab)`(self,str path,t.List args,t.List slaves,*t.Optional details)` {#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1ab0a0196ebb218f56cc1c316fdd0a1cab}

#### `public None `[`cleanup`](#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a6415dfdcff50c421773dd01c6449ea26)`(self)` {#classexot_1_1driver_1_1driver__unix_1_1SSHUnixDriver_1a6415dfdcff50c421773dd01c6449ea26}

# namespace `exot::driver::extensions::android` {#namespaceexot_1_1driver_1_1extensions_1_1android}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::extensions::android::AndroidMethods`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods) | 

# class `exot::driver::extensions::android::AndroidMethods` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods}

```
class exot::driver::extensions::android::AndroidMethods
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.List[str] `[`list_packages`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f117ab3b8203272107799f4b6906963)`(self,t.Optional with_filter)` | Lists packages available on the platform
`public t.List[str] `[`list_dumpsys_services`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a25bc91b735f953ac6801239bf5c9ffc8)`(self)` | Lists services available via platform's dumpsys
`public t.List[TaskRecord] `[`list_tasks`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac53d1263dbc98b28579c7d0673aca209)`(self,** kwargs)` | 
`public t.List[ActivityRecord] `[`list_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af01f48b1919b72c8bbd58664be879803)`(self,** kwargs)` | 
`public t.List[ServiceRecord] `[`list_services`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a34b2e4525329105963f0b45810472d3c)`(self,** kwargs)` | 
`public t.List[TaskRecord] `[`list_recent_tasks`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a263eaf851e9c2737470af25801226490)`(self,** kwargs)` | 
`public t.List[ActivityRecord] `[`list_recent_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ae99e5f4a1fa430b655bbb02d82cb8def)`(self,** kwargs)` | 
`public t.List[WindowRecord] `[`list_windows`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f67efbabd8b08947354688c85ad2fe9)`(self,** kwargs)` | 
`public def `[`installed_packages`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ab585caa4deffc03f24a8e60832affb22)`(self)` | 
`public def `[`running_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1add31daadf75c98a9a42c9df633758dcc)`(self)` | 
`public def `[`running_services`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a56d17faae6ef46260ab3b1181b105646)`(self)` | 
`public def `[`recent_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5b0afdcd74bccdc9ba93d718a5f5db4f)`(self)` | 
`public def `[`active_windows`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a756d7e36fb5e32f176f9b7b22064808b)`(self)` | 
`public t.Optional[WindowRecord] `[`focused_window`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ad014d7b1e83bcb068053056184daac63)`(self)` | Gets the currently focused window
`public t.Optional[ActivityRecord] `[`focused_activity`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abe1092afbb04c9eb85854f2712dd9bf9)`(self)` | Gets the currently focused activity
`public def `[`get_time`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abe02062ae4f537de7d2db8886ce20835)`(self)` | Gets the current time from the device
`public bool `[`send_tap`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a093b66c68dc0e8dc1637dd13ecd26ebe)`(self,int x,int y)` | Sends a tap to the platform
`public bool `[`send_swipe`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a04285c79079fce9d460550765da7f836)`(self,list start,list end,int duration)` | Sends a keycode/keyevent to the platform
`public bool `[`send_keyevent`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a2dbfa980d4277b416b6db7ab49545acf)`(self,t.Union keycode)` | Sends a keycode/keyevent to the platform
`public bool `[`open_home_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3e8033ebc0e319490fcb99f0fac8dddf)`(self)` | Opens the home screen
`public bool `[`open_app_switcher`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f23d8011ec8b9c91261dd064212201f)`(self)` | Opens the app switcher
`public bool `[`is_app_switcher_opened`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ae8ee5790a5f99b60f4f4ecd261598a5f)`(self)` | It the topmost window the app switcher?
`public None `[`clear_app_switcher`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3994b809ccc55a7eb922541e5ef9589f)`(self)` | Clears the activities in the app switcher
`public bool `[`is_home_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5777647a59d7e6206b9e950d40b1ed20)`(self)` | Is focused on the home screen?
`public dict `[`power_state`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3419fb976f573b1120a103925296dd60)`(self)` | Gets the power state
`public None `[`turn_screen_on`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ad601077b29a09536c5f472dcf4201053)`(self)` | Turns the screen on
`public None `[`turn_screen_off`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5fe4f2415b5c3906734c83e58a26af02)`(self)` | Turns the screen off
`public bool `[`is_screen_on`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af4ae5178d1a35274f9028cb7a8c1c56f)`(self)` | Is the screen on?
`public bool `[`is_screen_off`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a12f7d44e517cbc13cf94fdb128df0dc0)`(self)` | Is screen off?
`public bool `[`is_screen_locked`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a8e858d23cc37a157cd94ab53a9202a9d)`(self)` | Is screen locked?
`public None `[`lock_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ada1a691db133e43a9ac138efb8a5b185)`(self)` | Locks the screen
`public None `[`unlock_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abf1feb9ddd57239f82f669989210b171)`(self)` | Unlocks the screen
`public bool `[`clear_chrome_tabs`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1aae0038f8ce68ed3088898536bfbce250)`(self)` | Removes the temporary data that saves open tabs.
`public bool `[`force_stop_package`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a12c6be5f5bee900929ac480af903f39e)`(self,str package)` | Forces all activities and tasks of a package to stop
`public bool `[`kill_activity`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5a18dc1e6b1cb1d9bb1d56415beac148)`(self,t.Union activity)` | Killsan activity
`public None `[`kill_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af4b438bab459b7b641e9760675a97ae4)`(self,*t.Union activities)` | Kills multiple activities
`public ReturnT `[`send_intent`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5e4db9c218c4ebc46d16e76a4bc5fadf)`(self,Intent value,* args,** kwargs)` | Sends an intent
`public ReturnT `[`send_intent_via_proxy`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a57167f8f72a9fad0329260b261534553)`(self,Intent value,kind,** kwargs)` | Sends an intent via the IntentProxy
`public bool `[`start_proxy_service`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac8dcd280882784005bb14c78cbc10b8f)`(self)` | Starts the intent proxy service
`public bool `[`stop_proxy_service`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac348434029c787c3db404bb7dfacd1b2)`(self)` | Stops the intent proxy service
`public bool `[`is_proxy_service_active`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3d05e007ea8a383be776b9229b612daf)`(self)` | Is the intent proxy service active?
`public None `[`clear_logs`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a6f0be492be3723c11d1412d0528ba3b5)`(self)` | Clears logs on the device
`public t.List[str] `[`get_logs`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ade83759874f374fe127b8fd30964d660)`(self,t.Optional grep,t.Optional] since,t.Optional] till,t.Optional count)` | Gets the logs, optionally since a timepoint and with regex matching.

## Members

#### `public t.List[str] `[`list_packages`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f117ab3b8203272107799f4b6906963)`(self,t.Optional with_filter)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f117ab3b8203272107799f4b6906963}

Lists packages available on the platform

Args:
    with_filter (t.Optional[t.Callable], optional): Filtering callable, (str) -> bool

Returns:
    t.List[str]: A list of packages

#### `public t.List[str] `[`list_dumpsys_services`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a25bc91b735f953ac6801239bf5c9ffc8)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a25bc91b735f953ac6801239bf5c9ffc8}

Lists services available via platform's dumpsys

Returns:
    t.List[str]: A list of services/commands

#### `public t.List[TaskRecord] `[`list_tasks`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac53d1263dbc98b28579c7d0673aca209)`(self,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac53d1263dbc98b28579c7d0673aca209}

#### `public t.List[ActivityRecord] `[`list_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af01f48b1919b72c8bbd58664be879803)`(self,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af01f48b1919b72c8bbd58664be879803}

#### `public t.List[ServiceRecord] `[`list_services`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a34b2e4525329105963f0b45810472d3c)`(self,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a34b2e4525329105963f0b45810472d3c}

#### `public t.List[TaskRecord] `[`list_recent_tasks`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a263eaf851e9c2737470af25801226490)`(self,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a263eaf851e9c2737470af25801226490}

#### `public t.List[ActivityRecord] `[`list_recent_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ae99e5f4a1fa430b655bbb02d82cb8def)`(self,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ae99e5f4a1fa430b655bbb02d82cb8def}

#### `public t.List[WindowRecord] `[`list_windows`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f67efbabd8b08947354688c85ad2fe9)`(self,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f67efbabd8b08947354688c85ad2fe9}

#### `public def `[`installed_packages`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ab585caa4deffc03f24a8e60832affb22)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ab585caa4deffc03f24a8e60832affb22}

#### `public def `[`running_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1add31daadf75c98a9a42c9df633758dcc)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1add31daadf75c98a9a42c9df633758dcc}

#### `public def `[`running_services`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a56d17faae6ef46260ab3b1181b105646)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a56d17faae6ef46260ab3b1181b105646}

#### `public def `[`recent_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5b0afdcd74bccdc9ba93d718a5f5db4f)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5b0afdcd74bccdc9ba93d718a5f5db4f}

#### `public def `[`active_windows`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a756d7e36fb5e32f176f9b7b22064808b)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a756d7e36fb5e32f176f9b7b22064808b}

#### `public t.Optional[WindowRecord] `[`focused_window`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ad014d7b1e83bcb068053056184daac63)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ad014d7b1e83bcb068053056184daac63}

Gets the currently focused window

Returns:
    t.Optional[WindowRecord]: The WindowRecord of the topmost window

#### `public t.Optional[ActivityRecord] `[`focused_activity`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abe1092afbb04c9eb85854f2712dd9bf9)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abe1092afbb04c9eb85854f2712dd9bf9}

Gets the currently focused activity

Returns:
    t.Optional[ActivityRecord]: The ActivityRecord of the topmost activity, None if
no activity is focused, for example when the screen is locked.

#### `public def `[`get_time`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abe02062ae4f537de7d2db8886ce20835)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abe02062ae4f537de7d2db8886ce20835}

Gets the current time from the device

Returns:
    datetime: now

#### `public bool `[`send_tap`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a093b66c68dc0e8dc1637dd13ecd26ebe)`(self,int x,int y)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a093b66c68dc0e8dc1637dd13ecd26ebe}

Sends a tap to the platform

Args:
    x (int): x-coordinate
    y (int): y-coordinate

Returns:
    bool: Command status

Raises:
    TypeError: Wrong type supplied

#### `public bool `[`send_swipe`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a04285c79079fce9d460550765da7f836)`(self,list start,list end,int duration)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a04285c79079fce9d460550765da7f836}

Sends a keycode/keyevent to the platform

Args:
    start (list[int]): Start coordinates
    end   (list[int]): End coordinates
    duration (int):    Lenght of the swipe in ms

Returns:
    bool: Command status

Raises:
    TypeError: Wrong type supplied

#### `public bool `[`send_keyevent`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a2dbfa980d4277b416b6db7ab49545acf)`(self,t.Union keycode)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a2dbfa980d4277b416b6db7ab49545acf}

Sends a keycode/keyevent to the platform

Args:
    keycode (t.Union[str, int]): The keycode

Returns:
    bool: Command status

Raises:
    TypeError: Wrong type supplied
    ValueError: Whitespace in keycode

#### `public bool `[`open_home_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3e8033ebc0e319490fcb99f0fac8dddf)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3e8033ebc0e319490fcb99f0fac8dddf}

Opens the home screen

Returns:
    bool: Is at home screen?

#### `public bool `[`open_app_switcher`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f23d8011ec8b9c91261dd064212201f)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a4f23d8011ec8b9c91261dd064212201f}

Opens the app switcher

Returns:
    bool: Is app switcher opened?

#### `public bool `[`is_app_switcher_opened`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ae8ee5790a5f99b60f4f4ecd261598a5f)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ae8ee5790a5f99b60f4f4ecd261598a5f}

It the topmost window the app switcher?

Returns:
    bool: True if focused on the app switcher, False otherwise

#### `public None `[`clear_app_switcher`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3994b809ccc55a7eb922541e5ef9589f)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3994b809ccc55a7eb922541e5ef9589f}

Clears the activities in the app switcher

Raises:
    RuntimeError: App switcher was not opened

Returns:
    None: Returns early if only two recent activities exist

#### `public bool `[`is_home_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5777647a59d7e6206b9e950d40b1ed20)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5777647a59d7e6206b9e950d40b1ed20}

Is focused on the home screen?

Returns:
    bool: True if on the home screen, False otherwise.

#### `public dict `[`power_state`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3419fb976f573b1120a103925296dd60)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3419fb976f573b1120a103925296dd60}

Gets the power state

Returns:
    dict: The power state

#### `public None `[`turn_screen_on`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ad601077b29a09536c5f472dcf4201053)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ad601077b29a09536c5f472dcf4201053}

Turns the screen on

#### `public None `[`turn_screen_off`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5fe4f2415b5c3906734c83e58a26af02)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5fe4f2415b5c3906734c83e58a26af02}

Turns the screen off

#### `public bool `[`is_screen_on`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af4ae5178d1a35274f9028cb7a8c1c56f)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af4ae5178d1a35274f9028cb7a8c1c56f}

Is the screen on?

Returns:
    bool: True if on, False otherwise.

#### `public bool `[`is_screen_off`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a12f7d44e517cbc13cf94fdb128df0dc0)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a12f7d44e517cbc13cf94fdb128df0dc0}

Is screen off?

Returns:
    bool: True if off, False otherwise.

#### `public bool `[`is_screen_locked`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a8e858d23cc37a157cd94ab53a9202a9d)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a8e858d23cc37a157cd94ab53a9202a9d}

Is screen locked?

Returns:
    bool: True if locked, False otherwise.

#### `public None `[`lock_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ada1a691db133e43a9ac138efb8a5b185)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ada1a691db133e43a9ac138efb8a5b185}

Locks the screen

#### `public None `[`unlock_screen`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abf1feb9ddd57239f82f669989210b171)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1abf1feb9ddd57239f82f669989210b171}

Unlocks the screen

#### `public bool `[`clear_chrome_tabs`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1aae0038f8ce68ed3088898536bfbce250)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1aae0038f8ce68ed3088898536bfbce250}

Removes the temporary data that saves open tabs.

Returns:
   bool: Command status

#### `public bool `[`force_stop_package`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a12c6be5f5bee900929ac480af903f39e)`(self,str package)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a12c6be5f5bee900929ac480af903f39e}

Forces all activities and tasks of a package to stop

Args:
    package (str): The package

Returns:
    bool: Command status

Raises:
    TypeError: Wrong type supplied for package

#### `public bool `[`kill_activity`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5a18dc1e6b1cb1d9bb1d56415beac148)`(self,t.Union activity)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5a18dc1e6b1cb1d9bb1d56415beac148}

Killsan activity

Args:
    activity (t.Union[str, ActivityRecord]): ActivityRecord or activity's component

Returns:
    bool: Command status

Raises:
    TypeError: Wrong type supplied for activity

#### `public None `[`kill_activities`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af4b438bab459b7b641e9760675a97ae4)`(self,*t.Union activities)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1af4b438bab459b7b641e9760675a97ae4}

Kills multiple activities

Args:
    *activities (t.Union[str, ActivityRecord]): The records or components

#### `public ReturnT `[`send_intent`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5e4db9c218c4ebc46d16e76a4bc5fadf)`(self,Intent value,* args,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a5e4db9c218c4ebc46d16e76a4bc5fadf}

Sends an intent

Args:
    value (Intent): The intent
    *args: Positional arguments to send_intent
    **kwargs: Keyword arguments to send_intent

Returns:
    ReturnT: The command result

Raises:
    RuntimeError: Failed to send the intent

#### `public ReturnT `[`send_intent_via_proxy`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a57167f8f72a9fad0329260b261534553)`(self,Intent value,kind,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a57167f8f72a9fad0329260b261534553}

Sends an intent via the IntentProxy

Args:
    value (Intent): The intent
    kind (str, optional): Kind ("service", "broadcast", or proxy-specific actions)
    **kwargs: Keyword arguments to send_intent

Returns:
    ReturnT: The command result

Raises:
    RuntimeError: Failed to send the intent

#### `public bool `[`start_proxy_service`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac8dcd280882784005bb14c78cbc10b8f)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac8dcd280882784005bb14c78cbc10b8f}

Starts the intent proxy service

Returns:
    bool: True if active, False otherwise.

#### `public bool `[`stop_proxy_service`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac348434029c787c3db404bb7dfacd1b2)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ac348434029c787c3db404bb7dfacd1b2}

Stops the intent proxy service

Returns:
    bool: Command status

#### `public bool `[`is_proxy_service_active`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3d05e007ea8a383be776b9229b612daf)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a3d05e007ea8a383be776b9229b612daf}

Is the intent proxy service active?

Returns:
    bool: True if active, False otherwise.

#### `public None `[`clear_logs`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a6f0be492be3723c11d1412d0528ba3b5)`(self)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1a6f0be492be3723c11d1412d0528ba3b5}

Clears logs on the device

Returns:
    bool: Operation was successful?

#### `public t.List[str] `[`get_logs`](#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ade83759874f374fe127b8fd30964d660)`(self,t.Optional grep,t.Optional] since,t.Optional] till,t.Optional count)` {#classexot_1_1driver_1_1extensions_1_1android_1_1AndroidMethods_1ade83759874f374fe127b8fd30964d660}

Gets the logs, optionally since a timepoint and with regex matching.
As the -t option of logcat does not properly work for all android flavors (e.g. Samsung),
we need to use a workaround to get the log from a certain time on.

The till option does only work on a second granularity.

Args:
    grep (t.Optional[str], optional): The regular expression to match
    since (t.Optional[t.Union[datetime, str, int]], optional): The starting timepoint or line count
    till (t.Optional[t.Union[datetime, str]], optional): The end timepoint

Returns:
    t.List[str]: List of log lines

Raises:
    TypeError: Wrong type supplied to either argument

# namespace `exot::driver::extensions::rsync` {#namespaceexot_1_1driver_1_1extensions_1_1rsync}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::extensions::rsync::TransferMethods`](#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods) | 

# class `exot::driver::extensions::rsync::TransferMethods` {#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods}

```
class exot::driver::extensions::rsync::TransferMethods
  : public exot.driver._mixins.TransferMethodsMixin
  : public exot.driver._mixins.FileMethodsMixin
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public None `[`fetch`](#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods_1a5326cf2fc8f47b8b50200d7e6857669a)`(self,t.Union path_from,t.Union path_to,t.List exclude)` | 
`public None `[`send`](#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods_1ad42906619bb5be6616bffc63c6044564)`(self,t.Union path_from,t.Union path_to,t.List exclude)` | 

## Members

#### `public None `[`fetch`](#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods_1a5326cf2fc8f47b8b50200d7e6857669a)`(self,t.Union path_from,t.Union path_to,t.List exclude)` {#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods_1a5326cf2fc8f47b8b50200d7e6857669a}

#### `public None `[`send`](#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods_1ad42906619bb5be6616bffc63c6044564)`(self,t.Union path_from,t.Union path_to,t.List exclude)` {#classexot_1_1driver_1_1extensions_1_1rsync_1_1TransferMethods_1ad42906619bb5be6616bffc63c6044564}

# namespace `exot::driver::extensions::sysfs` {#namespaceexot_1_1driver_1_1extensions_1_1sysfs}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::extensions::sysfs::StateMethods`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods) | 

# class `exot::driver::extensions::sysfs::StateMethods` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods}

```
class exot::driver::extensions::sysfs::StateMethods
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public dict `[`cpuinfo`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1ae2eeb0622963e82e8af72df9e63ac112)`(self)` | 
`public t.List[str] `[`available_governors`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a05ea3f390a19789978cdc78976a9daff)`(self)` | 
`public t.List[int] `[`available_frequencies`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1aff268f14d7ad97f87cc3e41fa52bc6f7)`(self)` | 
`public t.List[bool] `[`online_cores`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a0bff28e85e78f92d31f704792c61a895)`(self)` | 
`public None `[`online_cores`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8350735631485a3c0304db503e49a856)`(self,t.List] value)` | 
`public t.List[str] `[`governors`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8cb88ed8985a8544d28ed0eb0b778cbf)`(self)` | 
`public None `[`governors`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a7e59723bc40e9181b4f94099665c7a99)`(self,t. Union,str] value)` | 
`public t.List `[`frequencies`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1af07cc5ee4a4514a6cbd9be583603b323)`(self)` | Read current CPU scaling frequencies for all cores
`public def `[`frequencies`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8929ff7d9ae48e87f5dd4f84be84f06e)`(self,t.Optional] value)` | Set CPU scaling frequencies for all or specific cores
`public t.Optional[t.Dict] `[`cpuidle`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1aba430d31d60105c36b64c637ab10b925)`(self)` | Get state-latency pairs for cpuidle

## Members

#### `public dict `[`cpuinfo`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1ae2eeb0622963e82e8af72df9e63ac112)`(self)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1ae2eeb0622963e82e8af72df9e63ac112}

#### `public t.List[str] `[`available_governors`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a05ea3f390a19789978cdc78976a9daff)`(self)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a05ea3f390a19789978cdc78976a9daff}

#### `public t.List[int] `[`available_frequencies`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1aff268f14d7ad97f87cc3e41fa52bc6f7)`(self)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1aff268f14d7ad97f87cc3e41fa52bc6f7}

#### `public t.List[bool] `[`online_cores`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a0bff28e85e78f92d31f704792c61a895)`(self)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a0bff28e85e78f92d31f704792c61a895}

#### `public None `[`online_cores`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8350735631485a3c0304db503e49a856)`(self,t.List] value)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8350735631485a3c0304db503e49a856}

#### `public t.List[str] `[`governors`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8cb88ed8985a8544d28ed0eb0b778cbf)`(self)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8cb88ed8985a8544d28ed0eb0b778cbf}

#### `public None `[`governors`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a7e59723bc40e9181b4f94099665c7a99)`(self,t. Union,str] value)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a7e59723bc40e9181b4f94099665c7a99}

#### `public t.List `[`frequencies`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1af07cc5ee4a4514a6cbd9be583603b323)`(self)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1af07cc5ee4a4514a6cbd9be583603b323}

Read current CPU scaling frequencies for all cores

#### `public def `[`frequencies`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8929ff7d9ae48e87f5dd4f84be84f06e)`(self,t.Optional] value)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1a8929ff7d9ae48e87f5dd4f84be84f06e}

Set CPU scaling frequencies for all or specific cores

#### `public t.Optional[t.Dict] `[`cpuidle`](#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1aba430d31d60105c36b64c637ab10b925)`(self)` {#classexot_1_1driver_1_1extensions_1_1sysfs_1_1StateMethods_1aba430d31d60105c36b64c637ab10b925}

Get state-latency pairs for cpuidle

The values returned by this command

# namespace `exot::driver::extensions::unix` {#namespaceexot_1_1driver_1_1extensions_1_1unix}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::driver::extensions::unix::ExtraFileMethods`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods) | 
`class `[`exot::driver::extensions::unix::FanMethods`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods) | 
`class `[`exot::driver::extensions::unix::FileMethods`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods) | 
`class `[`exot::driver::extensions::unix::LatencyMethods`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods) | 
`class `[`exot::driver::extensions::unix::LockingMethods`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods) | 
`class `[`exot::driver::extensions::unix::PersistenceMethods`](#classexot_1_1driver_1_1extensions_1_1unix_1_1PersistenceMethods) | 
`class `[`exot::driver::extensions::unix::ProcessMethods`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods) | 

# class `exot::driver::extensions::unix::ExtraFileMethods` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods}

```
class exot::driver::extensions::unix::ExtraFileMethods
  : public exot.driver._mixins.ExtraFileMethodsMixin
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Optional[os.stat_result] `[`stat`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods_1ae5715e8f23c303ba6213bbbc9f9cf644)`(self,str path,*t.Optional dir_fd,bool follow_symlinks)` | 
`public t.Optional[t.List[str]] `[`find`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods_1a72be8ad86ac7d03bf99a4bf9bb784cde)`(self,str path,*bool recursive,bool hidden,bool no_path,str query)` | 

## Members

#### `public t.Optional[os.stat_result] `[`stat`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods_1ae5715e8f23c303ba6213bbbc9f9cf644)`(self,str path,*t.Optional dir_fd,bool follow_symlinks)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods_1ae5715e8f23c303ba6213bbbc9f9cf644}

#### `public t.Optional[t.List[str]] `[`find`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods_1a72be8ad86ac7d03bf99a4bf9bb784cde)`(self,str path,*bool recursive,bool hidden,bool no_path,str query)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ExtraFileMethods_1a72be8ad86ac7d03bf99a4bf9bb784cde}

# class `exot::driver::extensions::unix::FanMethods` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Optional[t.Dict] `[`fan_path`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1ac4db3adbf677dfd646e14d618cdf9f51)`(self)` | Gets the path to fan settings on the device
`public t.Optional[t.Union[str, tuple]] `[`fan`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1a49d52b3db3c3a1eb3b1345c1b540c34d)`(self)` | Gets fan settings
`public None `[`fan`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1a9b1c9284d847fd79088ec1569685e3db)`(self,t.Union value)` | Sets fan settings

## Members

#### `public t.Optional[t.Dict] `[`fan_path`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1ac4db3adbf677dfd646e14d618cdf9f51)`(self)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1ac4db3adbf677dfd646e14d618cdf9f51}

Gets the path to fan settings on the device

Returns:
    t.Optional[t.Dict]: The {key, path, exists} of an existing fan path,
                   None if no path has been found.

#### `public t.Optional[t.Union[str, tuple]] `[`fan`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1a49d52b3db3c3a1eb3b1345c1b540c34d)`(self)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1a49d52b3db3c3a1eb3b1345c1b540c34d}

Gets fan settings

Returns:
    t.Optional[t.Union[str, tuple]]: The fan settings

#### `public None `[`fan`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1a9b1c9284d847fd79088ec1569685e3db)`(self,t.Union value)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FanMethods_1a9b1c9284d847fd79088ec1569685e3db}

Sets fan settings

Args:
    value (t.Union[str, int, tuple]): Value appropriate for the specific fan endpoints

Returns:
    None: Returns early if no fan path is available

Raises:
    DriverTypeError: Wrong type supplied to the specific fan endpoint
    DriverValueError: Wrong value supplied to the specific fan endpoint

# class `exot::driver::extensions::unix::FileMethods` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods}

```
class exot::driver::extensions::unix::FileMethods
  : public exot.driver._mixins.FileMethodsMixin
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public str `[`delete`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a2c604a1d1e679b498f8cede9678059e8)`(self,str path,bool recursive)` | 
`public bool `[`exists`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a6851c4dd53441a3461f5275a14e96fef)`(self,str path)` | 
`public bool `[`is_file`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1ae907d46bc2d56c1b9d8b18f843485dfd)`(self,str path)` | 
`public bool `[`is_dir`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a0722f8b1100940f6caa3e35c9c8d2dce)`(self,str path)` | 
`public bool `[`move`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a8ebf75ae1c5f6d4d294504fdf7049d48)`(self,str path_from,str path_to,bool overwrite)` | 
`public bool `[`copy`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a54ac53ede0a1e68e1870f7f5b3f2e518)`(self,str path_from,str path_to,bool recursive,bool overwrite)` | 
`public bool `[`mkdir`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a805d0cb06a5ec3dbd88acafdf6b9bd28)`(self,str path,bool parents)` | 
`public bool `[`access`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a3cef359dfaa74546f9552f4634816299)`(self,str path,str mode)` | 
`public bool `[`executable_exists`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a99aad798d1f5d6d0422ac412832967ab)`(self,str executable)` | Checks if an executable exists locally or on the system
`public str `[`working_directory`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1af49317077393573e4cf82e5e3831e4e6)`(self)` | 

## Members

#### `public str `[`delete`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a2c604a1d1e679b498f8cede9678059e8)`(self,str path,bool recursive)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a2c604a1d1e679b498f8cede9678059e8}

#### `public bool `[`exists`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a6851c4dd53441a3461f5275a14e96fef)`(self,str path)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a6851c4dd53441a3461f5275a14e96fef}

#### `public bool `[`is_file`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1ae907d46bc2d56c1b9d8b18f843485dfd)`(self,str path)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1ae907d46bc2d56c1b9d8b18f843485dfd}

#### `public bool `[`is_dir`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a0722f8b1100940f6caa3e35c9c8d2dce)`(self,str path)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a0722f8b1100940f6caa3e35c9c8d2dce}

#### `public bool `[`move`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a8ebf75ae1c5f6d4d294504fdf7049d48)`(self,str path_from,str path_to,bool overwrite)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a8ebf75ae1c5f6d4d294504fdf7049d48}

#### `public bool `[`copy`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a54ac53ede0a1e68e1870f7f5b3f2e518)`(self,str path_from,str path_to,bool recursive,bool overwrite)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a54ac53ede0a1e68e1870f7f5b3f2e518}

#### `public bool `[`mkdir`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a805d0cb06a5ec3dbd88acafdf6b9bd28)`(self,str path,bool parents)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a805d0cb06a5ec3dbd88acafdf6b9bd28}

#### `public bool `[`access`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a3cef359dfaa74546f9552f4634816299)`(self,str path,str mode)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a3cef359dfaa74546f9552f4634816299}

#### `public bool `[`executable_exists`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a99aad798d1f5d6d0422ac412832967ab)`(self,str executable)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1a99aad798d1f5d6d0422ac412832967ab}

Checks if an executable exists locally or on the system

Args:
    executable (str): The executable, either a path or an app name

Returns:
    bool: True if exists and is an executable

#### `public str `[`working_directory`](#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1af49317077393573e4cf82e5e3831e4e6)`(self)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1FileMethods_1af49317077393573e4cf82e5e3831e4e6}

# class `exot::driver::extensions::unix::LatencyMethods` {#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Optional[int] `[`latency`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods_1a4b44bc5af5671d4316b84009056a8f97)`(self)` | Get the CPU DMA latency from devfs
`public None `[`latency`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods_1a66d9ba106bc50a1b698a7a0dfc797386)`(self,t.Optional value)` | 

## Members

#### `public t.Optional[int] `[`latency`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods_1a4b44bc5af5671d4316b84009056a8f97)`(self)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods_1a4b44bc5af5671d4316b84009056a8f97}

Get the CPU DMA latency from devfs

Returns:
    t.Optional[int]: an integer value or None if unsuccessful

#### `public None `[`latency`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods_1a66d9ba106bc50a1b698a7a0dfc797386)`(self,t.Optional value)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1LatencyMethods_1a66d9ba106bc50a1b698a7a0dfc797386}

# class `exot::driver::extensions::unix::LockingMethods` {#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods}

```
class exot::driver::extensions::unix::LockingMethods
  : public exot.driver._mixins.FileMethodsMixin
  : public exot.driver._mixins.LockingMethodsMixin
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool `[`is_locked`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1ab87cf68468157d5fa6b215ed9254b03e)`(self)` | 
`public None `[`lock`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1a37ac5621f265707d803d00fbea93fbc1)`(self)` | 
`public bool `[`unlock`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1a3a89f74d48f7a85cbffef21f3077c996)`(self)` | 

## Members

#### `public bool `[`is_locked`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1ab87cf68468157d5fa6b215ed9254b03e)`(self)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1ab87cf68468157d5fa6b215ed9254b03e}

#### `public None `[`lock`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1a37ac5621f265707d803d00fbea93fbc1)`(self)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1a37ac5621f265707d803d00fbea93fbc1}

#### `public bool `[`unlock`](#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1a3a89f74d48f7a85cbffef21f3077c996)`(self)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1LockingMethods_1a3a89f74d48f7a85cbffef21f3077c996}

# class `exot::driver::extensions::unix::PersistenceMethods` {#classexot_1_1driver_1_1extensions_1_1unix_1_1PersistenceMethods}

```
class exot::driver::extensions::unix::PersistenceMethods
  : public exot.driver._mixins.PersistenceMethodsMixin
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public ReturnT `[`persistent`](#classexot_1_1driver_1_1extensions_1_1unix_1_1PersistenceMethods_1adda4c6ab632dc3e65443b40a92b53331)`(self,CommandT cmd,t.Optional chain,bool sudo,**t.Any kwargs)` | Run a persistent command that is detached from the calling process

## Members

#### `public ReturnT `[`persistent`](#classexot_1_1driver_1_1extensions_1_1unix_1_1PersistenceMethods_1adda4c6ab632dc3e65443b40a92b53331)`(self,CommandT cmd,t.Optional chain,bool sudo,**t.Any kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1PersistenceMethods_1adda4c6ab632dc3e65443b40a92b53331}

Run a persistent command that is detached from the calling process

In addition to the base ReturnT, the output contains attributes:
-   pid: the pid of the detached process
-   pgid: the process group id of the detached process
-   children: child processes spawned by the shell

Args:
    cmd (CommandT): the command to run persistently
    chain (t.Optional[CommandT], optional):
a command to run once the primary command finishes
    sudo (bool): run commands with elevated privileges
    **kwargs (t.Any): optional keyword arguments: "history", "command_only"

# class `exot::driver::extensions::unix::ProcessMethods` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods}

```
class exot::driver::extensions::unix::ProcessMethods
  : public exot.driver._mixins.ProcessMethodsMixin
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool `[`unix_signal`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a66a71b956c2946eea19f8a29a5e2642a)`(self,*int pids,t.Union sig)` | 
`public bool `[`unix_pkill`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a757155929c8ddf3f3e9c55d4f75fe9fd)`(self,*str pids,str flag,t.Union sig,** kwargs)` | 
`public bool `[`unix_kill`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1aff7d71806a2223d483d3477db0e0496f)`(self,*int pids,** kwargs)` | 
`public bool `[`unix_stop`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a4ef0862e47dd2d00c8b8456be773eed4)`(self,*int pids,** kwargs)` | 
`public bool `[`unix_start`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1acc4a529df90aaf9ebf7a48b99165c5fb)`(self,*int pids,** kwargs)` | 
`public bool `[`unix_wait`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a1dc238bb0096bffeaadc4eece48e49e9)`(self,*t.Union pids,float refresh_period)` | 
`public bool `[`start`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a08669a1ec38f8389eb454d2606d0651d)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`stop`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1afa2e4ffdbf65de122e5619105b80dcc7)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`kill`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1ae576bb0f7d6e352963fe4b0fe7857758)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 
`public bool `[`wait`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1aeb40e749b656eceb6ce8d0857cd5fc7d)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` | 

## Members

#### `public bool `[`unix_signal`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a66a71b956c2946eea19f8a29a5e2642a)`(self,*int pids,t.Union sig)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a66a71b956c2946eea19f8a29a5e2642a}

#### `public bool `[`unix_pkill`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a757155929c8ddf3f3e9c55d4f75fe9fd)`(self,*str pids,str flag,t.Union sig,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a757155929c8ddf3f3e9c55d4f75fe9fd}

#### `public bool `[`unix_kill`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1aff7d71806a2223d483d3477db0e0496f)`(self,*int pids,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1aff7d71806a2223d483d3477db0e0496f}

#### `public bool `[`unix_stop`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a4ef0862e47dd2d00c8b8456be773eed4)`(self,*int pids,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a4ef0862e47dd2d00c8b8456be773eed4}

#### `public bool `[`unix_start`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1acc4a529df90aaf9ebf7a48b99165c5fb)`(self,*int pids,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1acc4a529df90aaf9ebf7a48b99165c5fb}

#### `public bool `[`unix_wait`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a1dc238bb0096bffeaadc4eece48e49e9)`(self,*t.Union pids,float refresh_period)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a1dc238bb0096bffeaadc4eece48e49e9}

#### `public bool `[`start`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a08669a1ec38f8389eb454d2606d0651d)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1a08669a1ec38f8389eb454d2606d0651d}

#### `public bool `[`stop`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1afa2e4ffdbf65de122e5619105b80dcc7)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1afa2e4ffdbf65de122e5619105b80dcc7}

#### `public bool `[`kill`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1ae576bb0f7d6e352963fe4b0fe7857758)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1ae576bb0f7d6e352963fe4b0fe7857758}

#### `public bool `[`wait`](#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1aeb40e749b656eceb6ce8d0857cd5fc7d)`(self,*`[`Process`](#classexot_1_1driver_1_1__process_1_1Process)` processes,** kwargs)` {#classexot_1_1driver_1_1extensions_1_1unix_1_1ProcessMethods_1aeb40e749b656eceb6ce8d0857cd5fc7d}

Generated by [Moxygen](https://sourcey.com/moxygen)