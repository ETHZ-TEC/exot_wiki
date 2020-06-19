[:back:](/home)
---

# Utilities
ExOT offers a wide range of different utilities which makes developing with, and handlign of, ExOT easier.
This page contains a (non-exhaustive) list of ExOT utilities, sorted per file in the [utilities module](https://gitlab.ethz.ch/tec/public/exot/eengine/-/tree/master/exot/util). 
For more details, please check the comments in the code.

# Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::util::analysers`](#namespaceexot_1_1util_1_1analysers) | 
`namespace `[`exot::util::android`](#namespaceexot_1_1util_1_1android) | 
`namespace `[`exot::util::attributedict`](#namespaceexot_1_1util_1_1attributedict) | 
`namespace `[`exot::util::capacity`](#namespaceexot_1_1util_1_1capacity) | 
`namespace `[`exot::util::debug`](#namespaceexot_1_1util_1_1debug) | 
`namespace `[`exot::util::decorators`](#namespaceexot_1_1util_1_1decorators) | 
`namespace `[`exot::util::factory`](#namespaceexot_1_1util_1_1factory) | 
`namespace `[`exot::util::file`](#namespaceexot_1_1util_1_1file) | 
`namespace `[`exot::util::git`](#namespaceexot_1_1util_1_1git) | 
`namespace `[`exot::util::logging`](#namespaceexot_1_1util_1_1logging) | 
`namespace `[`exot::util::misc`](#namespaceexot_1_1util_1_1misc) | 
`namespace `[`exot::util::mixins`](#namespaceexot_1_1util_1_1mixins) | 
`namespace `[`exot::util::plotting`](#namespaceexot_1_1util_1_1plotting) | 
`namespace `[`exot::util::prompts`](#namespaceexot_1_1util_1_1prompts) | 
`namespace `[`exot::util::scinum`](#namespaceexot_1_1util_1_1scinum) | 
`namespace `[`exot::util::timeout`](#namespaceexot_1_1util_1_1timeout) | 
`namespace `[`exot::util::wrangle`](#namespaceexot_1_1util_1_1wrangle) | 

# namespace `exot::util::analysers` {#namespaceexot_1_1util_1_1analysers}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`all_labels_in_dataset`](#analysers_8py_1a468dfd98debe2fdb40fe144526332df9)`(experiment,sort_str,** kwargs)`            | 
`public def `[`sort_str_labels`](#analysers_8py_1a3b40dcf677d48e9350bf134ea0f7873c)`(labels)`            | 
`public def `[`generate_unique_labels_mapping`](#analysers_8py_1a4e6dd2c2d20a3fc15c343406d921e046)`(labels_keys,labels_str)`            | 

## Members

#### `public def `[`all_labels_in_dataset`](#analysers_8py_1a468dfd98debe2fdb40fe144526332df9)`(experiment,sort_str,** kwargs)` {#analysers_8py_1a468dfd98debe2fdb40fe144526332df9}

#### `public def `[`sort_str_labels`](#analysers_8py_1a3b40dcf677d48e9350bf134ea0f7873c)`(labels)` {#analysers_8py_1a3b40dcf677d48e9350bf134ea0f7873c}

#### `public def `[`generate_unique_labels_mapping`](#analysers_8py_1a4e6dd2c2d20a3fc15c343406d921e046)`(labels_keys,labels_str)` {#analysers_8py_1a4e6dd2c2d20a3fc15c343406d921e046}

# namespace `exot::util::android` {#namespaceexot_1_1util_1_1android}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::util::android::Intent`](#classexot_1_1util_1_1android_1_1Intent) | Class for creating Android Intents
`class `[`exot::util::android::RecordParser`](#classexot_1_1util_1_1android_1_1RecordParser) | 

# class `exot::util::android::Intent` {#classexot_1_1util_1_1android_1_1Intent}

Class for creating Android Intents

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public str `[`__str__`](#classexot_1_1util_1_1android_1_1Intent_1a2ff2ed7e4a748855ce335550509c6321)`(self)` | 
`public t.List[str] `[`assemble`](#classexot_1_1util_1_1android_1_1Intent_1aee5795340314fbc02a12ae374f8aa348)`(self)` | Assembles the Intent into a command-line argument sequence for the ActivityManager
`public bool `[`__bool__`](#classexot_1_1util_1_1android_1_1Intent_1ae413723594ddfbf5c9ee0d1c4c7ba843)`(self)` | Checks if the Intent has any field specified
`public str `[`to_uri`](#classexot_1_1util_1_1android_1_1Intent_1ac9c86298268705de9b2b8cf0c007838d)`(self,t. Callable,ReturnT] runner)` | Converts the intent to an URI
`public str `[`to_intent_uri`](#classexot_1_1util_1_1android_1_1Intent_1acc13f75968831939e7360ad06adec73a)`(self,t. Callable,ReturnT] runner)` | Converts the intent to an Intent URI
`public str `[`to_app_uri`](#classexot_1_1util_1_1android_1_1Intent_1a3b6cf5208cc4bfd7dc1c2db632f8a101)`(self,t. Callable,ReturnT] runner)` | Converts the intent to an app URI

## Members

#### `public str `[`__str__`](#classexot_1_1util_1_1android_1_1Intent_1a2ff2ed7e4a748855ce335550509c6321)`(self)` {#classexot_1_1util_1_1android_1_1Intent_1a2ff2ed7e4a748855ce335550509c6321}

#### `public t.List[str] `[`assemble`](#classexot_1_1util_1_1android_1_1Intent_1aee5795340314fbc02a12ae374f8aa348)`(self)` {#classexot_1_1util_1_1android_1_1Intent_1aee5795340314fbc02a12ae374f8aa348}

Assembles the Intent into a command-line argument sequence for the ActivityManager

Raises:
    ValueError: If more than one of [URI, PACKAGE, COMPONENT] is provided
    TypeError: If an incompatible type is encountered during annotation-backed parsing

Returns:
    t.List[str]: A sequence of command-line arguments

#### `public bool `[`__bool__`](#classexot_1_1util_1_1android_1_1Intent_1ae413723594ddfbf5c9ee0d1c4c7ba843)`(self)` {#classexot_1_1util_1_1android_1_1Intent_1ae413723594ddfbf5c9ee0d1c4c7ba843}

Checks if the Intent has any field specified

Returns:
    bool: True if at least one field is specified

#### `public str `[`to_uri`](#classexot_1_1util_1_1android_1_1Intent_1ac9c86298268705de9b2b8cf0c007838d)`(self,t. Callable,ReturnT] runner)` {#classexot_1_1util_1_1android_1_1Intent_1ac9c86298268705de9b2b8cf0c007838d}

Converts the intent to an URI

Args:
    runner (t.Callable[[t.List[str]], Backend.ReturnT]):
A callable that runs shell commands on the target

Returns:
    str: The URI

Raises:
    RuntimeError: If the command failed

#### `public str `[`to_intent_uri`](#classexot_1_1util_1_1android_1_1Intent_1acc13f75968831939e7360ad06adec73a)`(self,t. Callable,ReturnT] runner)` {#classexot_1_1util_1_1android_1_1Intent_1acc13f75968831939e7360ad06adec73a}

Converts the intent to an Intent URI

Args:
    runner (t.Callable[[t.List[str]], Backend.ReturnT]):
A callable that runs shell commands on the target

Returns:
    str: The Intent URI

Raises:
    RuntimeError: If the command failed

#### `public str `[`to_app_uri`](#classexot_1_1util_1_1android_1_1Intent_1a3b6cf5208cc4bfd7dc1c2db632f8a101)`(self,t. Callable,ReturnT] runner)` {#classexot_1_1util_1_1android_1_1Intent_1a3b6cf5208cc4bfd7dc1c2db632f8a101}

Converts the intent to an app URI

Args:
    runner (t.Callable[[t.List[str]], Backend.ReturnT]):
A callable that runs shell commands on the target

Returns:
    str: The App URI

Raises:
    RuntimeError: If the command failed

# class `exot::util::android::RecordParser` {#classexot_1_1util_1_1android_1_1RecordParser}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::util::attributedict` {#namespaceexot_1_1util_1_1attributedict}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`warn`](#attributedict_8py_1a5a76b867eced0e0968d43b869b7f805a)`(* args,** kwargs)`            | 
`class `[`exot::util::attributedict::AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict) | A dict with attribute access
`class `[`exot::util::attributedict::LabelMapping`](#classexot_1_1util_1_1attributedict_1_1LabelMapping) | 

## Members

#### `public def `[`warn`](#attributedict_8py_1a5a76b867eced0e0968d43b869b7f805a)`(* args,** kwargs)` {#attributedict_8py_1a5a76b867eced0e0968d43b869b7f805a}

# class `exot::util::attributedict::AttributeDict` {#classexot_1_1util_1_1attributedict_1_1AttributeDict}

```
class exot::util::attributedict::AttributeDict
  : public MutableMapping
```  

A dict with attribute access

In addition to functions defined in the abstract base classes of Mapping and
MutableMapping, provides the {__getattr__}, {__setattr__}, and {__delattr__}
functions, for the 'dotted' attribute access.

AttributeDict methods perform 'forwarding' to an internal dict object which holds
the data. Attempting to set a key of type 'dict' will cast it to this type, to
ensure consistent access 'recursively'.

Extends MutableMapping.

Attributes:
    _locals (List[str]): local member variables
    _warn_list (List[str]): list of keys which might be tricky to set/access
    _mutate_on_init (bool): flag to recursively mutate contained data

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1aa2e9944c3915bfb22102027b8cedd2a5)`(self,*Dict args,**Any kwargs)` | Initialise an instance
`public def `[`__len__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a85d931c61c2248a393311730281d66f2)`(self)` | Get number of entries in the dict
`public def `[`__getitem__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a19228b59ff3bdae1ac4211afbabb066f)`(self,Hashable key)` | Get an item from the dict
`public def `[`__setitem__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a36e1a34a12bb0a6bf670ff96b9203a9c)`(self,Hashable key,Any value)` | Set/add an item in the dict
`public def `[`__delitem__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a2b1018b1bc83383b5d6c1199964d16c3)`(self,Hashable key)` | Delete an item in the dict
`public def `[`__iter__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ab5298bfc5c5c566da9b99889f6b45861)`(self)` | Get an iterator for the dict
`public def `[`__contains__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1af76d220869295846e30038e57faab43e)`(self,Hashable key)` | Check if an item is contained in the dict
`public def `[`__repr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1abfdcfd70d1c5a3cf044f635534b7c837)`(self)` | Get a representation of the dict
`public def `[`__getattr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a853c67a839b6982140e15f7e37845242)`(self,Hashable key)` | Get an attribute from the internal dict or elsewhere in the instance
`public def `[`__setattr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1afa63cc793a2bc6c7ae490c6c2d632221)`(self,Hashable key,Any value)` | Set an attribute in the instance or set/add an item in the contained dict
`public None `[`__delattr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a689faaffcc24749c0aebbb81c79626ac)`(self,Hashable key)` | Delete an attribute in the instance or an item in the contained dict
`public def `[`__getstate__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ab398adc48eab11b40862d2a4b9f5e771)`(self)` | Get state for serialisation
`public def `[`__setstate__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a9d5841f79a251c8c1a53c81cb2904670)`(self,value)` | Set state from a serialised representation
`public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`copy`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a56d7a4cce5718a166b05a894d30475f4)`(self)` | Make a copy of the AttributeDict instance
`public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`fromkeys`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a833d64c621e498bfc4b61cab6be57eed)`(cls,Iterable iterable,Any value)` | Produce an AttributeDict using an iterable type as keys
`public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`from_dict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ae159783ad85ec5233e159c3e365f022b)`(cls,Any o)` | Produce an AttributeDict from a built-in dict
`public Dict `[`to_dict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a2b82e05bb5df775f632bf92b67119b33)`(cls,Any o)` | Convert an AttributeDict to a built-in dict recursively
`public dict `[`as_dict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a9dccb7d2374e4890899eca8e7c7a3083)`(self)` | Get a copy of the instance converted to the built-in dict
`public None `[`mutate`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a5617f7aa7d25eaa64c727f1992f39623)`(self,Union,Type] to)` | Mutate the internal data to AttributeDict or dict, recursively

## Members

#### `public def `[`__init__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1aa2e9944c3915bfb22102027b8cedd2a5)`(self,*Dict args,**Any kwargs)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1aa2e9944c3915bfb22102027b8cedd2a5}

Initialise an instance

#### `public def `[`__len__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a85d931c61c2248a393311730281d66f2)`(self)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a85d931c61c2248a393311730281d66f2}

Get number of entries in the dict

Implements an abstract method from MutableMapping.

#### `public def `[`__getitem__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a19228b59ff3bdae1ac4211afbabb066f)`(self,Hashable key)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a19228b59ff3bdae1ac4211afbabb066f}

Get an item from the dict

Implements an abstract method from MutableMapping.

#### `public def `[`__setitem__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a36e1a34a12bb0a6bf670ff96b9203a9c)`(self,Hashable key,Any value)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a36e1a34a12bb0a6bf670ff96b9203a9c}

Set/add an item in the dict

Implements an abstract method from MutableMapping.

#### `public def `[`__delitem__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a2b1018b1bc83383b5d6c1199964d16c3)`(self,Hashable key)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a2b1018b1bc83383b5d6c1199964d16c3}

Delete an item in the dict

Implements an abstract method from MutableMapping.

#### `public def `[`__iter__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ab5298bfc5c5c566da9b99889f6b45861)`(self)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ab5298bfc5c5c566da9b99889f6b45861}

Get an iterator for the dict

Implements an abstract method from MutableMapping.

#### `public def `[`__contains__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1af76d220869295846e30038e57faab43e)`(self,Hashable key)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1af76d220869295846e30038e57faab43e}

Check if an item is contained in the dict

Implements an abstract method from MutableMapping.

#### `public def `[`__repr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1abfdcfd70d1c5a3cf044f635534b7c837)`(self)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1abfdcfd70d1c5a3cf044f635534b7c837}

Get a representation of the dict

Implements an abstract method from MutableMapping.

#### `public def `[`__getattr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a853c67a839b6982140e15f7e37845242)`(self,Hashable key)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a853c67a839b6982140e15f7e37845242}

Get an attribute from the internal dict or elsewhere in the instance

#### `public def `[`__setattr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1afa63cc793a2bc6c7ae490c6c2d632221)`(self,Hashable key,Any value)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1afa63cc793a2bc6c7ae490c6c2d632221}

Set an attribute in the instance or set/add an item in the contained dict

#### `public None `[`__delattr__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a689faaffcc24749c0aebbb81c79626ac)`(self,Hashable key)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a689faaffcc24749c0aebbb81c79626ac}

Delete an attribute in the instance or an item in the contained dict

#### `public def `[`__getstate__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ab398adc48eab11b40862d2a4b9f5e771)`(self)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ab398adc48eab11b40862d2a4b9f5e771}

Get state for serialisation

`_data` is the only 'state' that the AttributeDict is holding. Without this
method a recursion error may arise during serialisation (e.g. to YAML).

#### `public def `[`__setstate__`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a9d5841f79a251c8c1a53c81cb2904670)`(self,value)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a9d5841f79a251c8c1a53c81cb2904670}

Set state from a serialised representation

#### `public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`copy`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a56d7a4cce5718a166b05a894d30475f4)`(self)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a56d7a4cce5718a166b05a894d30475f4}

Make a copy of the AttributeDict instance

Implementation of an analogous method of the built-in dict.

#### `public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`fromkeys`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a833d64c621e498bfc4b61cab6be57eed)`(cls,Iterable iterable,Any value)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a833d64c621e498bfc4b61cab6be57eed}

Produce an AttributeDict using an iterable type as keys

Implementation of an analogous method of the built-in dict.

Args:
    iterable (Iterable): The iterable
    value (Any): Value to which the new keys are set, defaults to None

Returns:
    AttributeDict: The dict created from the iterable

#### `public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`from_dict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ae159783ad85ec5233e159c3e365f022b)`(cls,Any o)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1ae159783ad85ec5233e159c3e365f022b}

Produce an AttributeDict from a built-in dict

Args:
    o (Any): A Dict when called, other types when called recursively.

Returns:
    AttributeDict: The converted dict

#### `public Dict `[`to_dict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a2b82e05bb5df775f632bf92b67119b33)`(cls,Any o)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a2b82e05bb5df775f632bf92b67119b33}

Convert an AttributeDict to a built-in dict recursively

Args:
    o (Any): An AttributeDict when called, other types when called

Returns:
    Dict: A plain built-in dict

#### `public dict `[`as_dict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a9dccb7d2374e4890899eca8e7c7a3083)`(self)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a9dccb7d2374e4890899eca8e7c7a3083}

Get a copy of the instance converted to the built-in dict

#### `public None `[`mutate`](#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a5617f7aa7d25eaa64c727f1992f39623)`(self,Union,Type] to)` {#classexot_1_1util_1_1attributedict_1_1AttributeDict_1a5617f7aa7d25eaa64c727f1992f39623}

Mutate the internal data to AttributeDict or dict, recursively

Args:
    to (Union[AttributeDict, Dict, Type[AttributeDict], Type[Dict]]): The type
to which the internal data is to be mutated

# class `exot::util::attributedict::LabelMapping` {#classexot_1_1util_1_1attributedict_1_1LabelMapping}

```
class exot::util::attributedict::LabelMapping
  : public exot.util.attributedict.AttributeDict
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`UNKNOWN`](#classexot_1_1util_1_1attributedict_1_1LabelMapping_1ae98226484f52c3fe0dccf18e3cf59bf4) | 
`public def `[`__init__`](#classexot_1_1util_1_1attributedict_1_1LabelMapping_1a6b7f7f215ccde58f5f53d8bb174f71c1)`(self,*Dict args,**Any kwargs)` | Initialise an instance
`public def `[`__missing__`](#classexot_1_1util_1_1attributedict_1_1LabelMapping_1a6b0475e9f05b8740869d04c9c0e223c1)`(self,Hashable key)` | 

## Members

#### `public  `[`UNKNOWN`](#classexot_1_1util_1_1attributedict_1_1LabelMapping_1ae98226484f52c3fe0dccf18e3cf59bf4) {#classexot_1_1util_1_1attributedict_1_1LabelMapping_1ae98226484f52c3fe0dccf18e3cf59bf4}

#### `public def `[`__init__`](#classexot_1_1util_1_1attributedict_1_1LabelMapping_1a6b7f7f215ccde58f5f53d8bb174f71c1)`(self,*Dict args,**Any kwargs)` {#classexot_1_1util_1_1attributedict_1_1LabelMapping_1a6b7f7f215ccde58f5f53d8bb174f71c1}

Initialise an instance

#### `public def `[`__missing__`](#classexot_1_1util_1_1attributedict_1_1LabelMapping_1a6b0475e9f05b8740869d04c9c0e223c1)`(self,Hashable key)` {#classexot_1_1util_1_1attributedict_1_1LabelMapping_1a6b0475e9f05b8740869d04c9c0e223c1}

# namespace `exot::util::capacity` {#namespaceexot_1_1util_1_1capacity}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`classic_waterfilling`](#capacity_8py_1ac0ba6b67076c2f623d38f8083f9c53e4)`(p0,Sqq,Shh)`            | Returns the capacity bound of a given channel determined using classic waterfiling
`public def `[`constrained_waterfilling`](#capacity_8py_1ae5aafc123a82c3645547843db6e59514)`(p0,Sqq,Shh)`            | Returns the capacity bound of a given channel determined using constrained waterfiling
`public def `[`capacity_from_connection_matrix`](#capacity_8py_1a32d0437d9ce245bdb2088f86916d4db8)`(A,T_min)`            | Returns the capacity bound of a given channel determined for noise free channel based on

## Members

#### `public def `[`classic_waterfilling`](#capacity_8py_1ac0ba6b67076c2f623d38f8083f9c53e4)`(p0,Sqq,Shh)` {#capacity_8py_1ac0ba6b67076c2f623d38f8083f9c53e4}

Returns the capacity bound of a given channel determined using classic waterfiling

Args:
    p0: Power cap for the waterfilling algorithm as float
    Sqq: Noise power spectrum as np.darray shape(N,2) where N is the number of frequency
        bins, column 0 holds the frequencies and column 1 the power spectral density.
    Shh: Channel power spectrum as np.darray shape(N,2) where N is the number of frequency
        bins, column 0 holds the frequencies and column 1 the power spectral density.

Returns:
    Channel Capaicty: in bits per seconds

#### `public def `[`constrained_waterfilling`](#capacity_8py_1ae5aafc123a82c3645547843db6e59514)`(p0,Sqq,Shh)` {#capacity_8py_1ae5aafc123a82c3645547843db6e59514}

Returns the capacity bound of a given channel determined using constrained waterfiling

Parameters:
    p0: Power cap for the waterfilling algorithm as float
    Sqq: Noise power spectrum as np.darray shape(N,2) where N is the number of frequency
        bins, column 0 holds the frequencies and column 1 the power spectral density.
    Shh: Channel power spectrum as np.darray shape(N,2) where N is the number of frequency
        bins, column 0 holds the frequencies and column 1 the power spectral density.
Returns:
    Channel Capacity: in bits per seconds

#### `public def `[`capacity_from_connection_matrix`](#capacity_8py_1a32d0437d9ce245bdb2088f86916d4db8)`(A,T_min)` {#capacity_8py_1a32d0437d9ce245bdb2088f86916d4db8}

Returns the capacity bound of a given channel determined for noise free channel based on
the connection matrix.

Parameters:
    A: Transition matrix of the channel model
    T_min: Minimal channel access time in seconds
Returns:
    Channel Capacity in bits per seconds
    Channel Capacity in bits per channel use

# namespace `exot::util::debug` {#namespaceexot_1_1util_1_1debug}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public bool `[`running_in_ipython`](#debug_8py_1a056ca7c5a0d146056f818e69c94e9427)`()`            | Am I running inside an IPython session?
`public Callable `[`set_trace`](#debug_8py_1a3187fa16b6a2dda83e4f3526cdd5ea65)`()`            | Sets a tracepoint in IPython or a breakpoint elsewhere
`public List[str] `[`get_signatures`](#debug_8py_1a6c21155b7d439e704e4bbc2c1175cd48)`(*Any args,str sep,bool _print)`            | Gets signatures of all functions/classes in a module or class

## Members

#### `public bool `[`running_in_ipython`](#debug_8py_1a056ca7c5a0d146056f818e69c94e9427)`()` {#debug_8py_1a056ca7c5a0d146056f818e69c94e9427}

Am I running inside an IPython session?

Returns:
    bool: True if run within IPython session.

#### `public Callable `[`set_trace`](#debug_8py_1a3187fa16b6a2dda83e4f3526cdd5ea65)`()` {#debug_8py_1a3187fa16b6a2dda83e4f3526cdd5ea65}

Sets a tracepoint in IPython or a breakpoint elsewhere

Returns:
    Callable: The set_trace/breakpoint

#### `public List[str] `[`get_signatures`](#debug_8py_1a6c21155b7d439e704e4bbc2c1175cd48)`(*Any args,str sep,bool _print)` {#debug_8py_1a6c21155b7d439e704e4bbc2c1175cd48}

Gets signatures of all functions/classes in a module or class

Args:
    sep (str, optional): The separator to use in signature descriptions. Defaults to " $$$ ".
    _print (bool, optional): Print instead of returning?. Defaults to False.

Returns:
    List[str]: A list of strings with signatures, if not printing.

# namespace `exot::util::decorators` {#namespaceexot_1_1util_1_1decorators}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Callable[..., t.T] `[`only_once`](#decorators_8py_1ae72acff81c634d4497ffa77d589aaf30)`(t.Callable f)`            | Decorator for running a function only once
`public t.Callable `[`dummy`](#decorators_8py_1afe4f2efd63b418c8128b0ea4caa4ccae)`(t.Callable f)`            | Dummy forwarding decorator
`public t.Callable `[`verbose`](#decorators_8py_1a85c5ed5c4ac4c781ce7c4e5da2046f29)`(t.Callable f)`            | Decorator for printing function arguments before a call
`public t.Callable `[`noexcept`](#decorators_8py_1a6334a374bc4324ba84e660451256229c)`(t.Callable f)`            | Decorator for ignoring exceptions
`public t.Callable `[`decorate_methods`](#decorators_8py_1a9fa22e9bb2924a63e8b6585a7b87d24e)`(t.Callable] decorator,t.Optional] methods)`            | Class/object decorator that decorates its methods
`public t.Callable `[`make_read_only`](#decorators_8py_1a4a4b5a73d06254f33bd0d5a8038e30d0)`(*str attributes)`            | A class decorator that makes certain attributes read-only
`class `[`exot::util::decorators::read_only`](#classexot_1_1util_1_1decorators_1_1read__only) | Read only property using the descriptor protocol

## Members

#### `public t.Callable[..., t.T] `[`only_once`](#decorators_8py_1ae72acff81c634d4497ffa77d589aaf30)`(t.Callable f)` {#decorators_8py_1ae72acff81c634d4497ffa77d589aaf30}

Decorator for running a function only once

Args:
    f (t.Callable[..., t.T]): The function to be decorated

Returns:
    t.Callable[..., t.T]: A decorated function

#### `public t.Callable `[`dummy`](#decorators_8py_1afe4f2efd63b418c8128b0ea4caa4ccae)`(t.Callable f)` {#decorators_8py_1afe4f2efd63b418c8128b0ea4caa4ccae}

Dummy forwarding decorator

Args:
    f (t.Callable): The function to be decorated

Returns:
    t.Callable: a decorated function

#### `public t.Callable `[`verbose`](#decorators_8py_1a85c5ed5c4ac4c781ce7c4e5da2046f29)`(t.Callable f)` {#decorators_8py_1a85c5ed5c4ac4c781ce7c4e5da2046f29}

Decorator for printing function arguments before a call

Args:
    f (t.Callable): The function to be decorated

Returns:
    t.Callable: A decorated function

#### `public t.Callable `[`noexcept`](#decorators_8py_1a6334a374bc4324ba84e660451256229c)`(t.Callable f)` {#decorators_8py_1a6334a374bc4324ba84e660451256229c}

Decorator for ignoring exceptions

Args:
    f (t.Callable): The function to be decorated

Returns:
    t.Callable: A decorated function

#### `public t.Callable `[`decorate_methods`](#decorators_8py_1a9fa22e9bb2924a63e8b6585a7b87d24e)`(t.Callable] decorator,t.Optional] methods)` {#decorators_8py_1a9fa22e9bb2924a63e8b6585a7b87d24e}

Class/object decorator that decorates its methods

Args:
    decorator (t.Callable[..., t.Callable[..., t.Callable]]): The decorator function.
        Optional. Defaults to 'dummy'.
    methods (t.Optional[t.List[str]]): The list of methods to decorate. Defaults to None.

Returns:
    t.Callable: A decorator

Raises:
    TypeError: Wrong type provided to 'decorator'

The function can also be used to produce partially-evaluated versions of itself,
e.g. to create a `make_methods_verbose` decorator.

To produce partially-evaluated decorator helpers call this function on an
empty (None) argument. For example:

>>> decorate_methods(decorator=None, methods=['print'])()

will return a functools.partial object that is partially evaluated w.r.t.
'methods'. Similarly:

>>> decorate_methods(decorator=verbose)()

will return a functools.partial object that will apply the {verbose} decorator
to function methods. It can later be used as:
::

    # Make a new decorator
    make_methods_verbose = decorate_methods(decorator=verbose)()
    # Apply the decorator to a class definition
    @make_methods_verbose(methods=["__setitem__", "__getitem__"])
    class MyClass(dict): pass
    class SomeClass(dict): pass
    # Decorate an existing class
    ModifiedClass = make_methods_verbose(methods=[ "__getitem__"])(SomeClass)
    # Decorate an object
    make_methods_verbose(methods=[ "__setitem__"])(SomeClass()).__setitem__(1, 1)

#### `public t.Callable `[`make_read_only`](#decorators_8py_1a4a4b5a73d06254f33bd0d5a8038e30d0)`(*str attributes)` {#decorators_8py_1a4a4b5a73d06254f33bd0d5a8038e30d0}

A class decorator that makes certain attributes read-only

Args:
    *attributes (str): A list of attributes to make read-only

Returns:
    t.Callable: A wrapper function

Raises:
    ValueError: If any of  *attributes is not a `str`

# class `exot::util::decorators::read_only` {#classexot_1_1util_1_1decorators_1_1read__only}

Read only property using the descriptor protocol

..note::
    The read_only properties/attributes work only on instances, and will not
    work on standalone values. Attempting:

    >>> x = read_only(123.45)
    >>> x = "Something else"

    will simply reassing 'x'. However, it works when used as follows:

    >>> class X:
            x = read_only(123.45)
    >>> Instance = X()
    >>> print(Instance.x) # accesses correctly
    >>> Instance.x = "Something else" # fails!

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`value`](#classexot_1_1util_1_1decorators_1_1read__only_1a935b7e99fd46a0baa6d3adb9227f054f) | 
`public def `[`__init__`](#classexot_1_1util_1_1decorators_1_1read__only_1a087bfe73cc38f09afbeb922b6ea5de70)`(self,value)` | 
`public def `[`__get__`](#classexot_1_1util_1_1decorators_1_1read__only_1afcdfb4519ac023bffd9cb8e07c25cf90)`(self,instance,owner)` | 
`public def `[`__set__`](#classexot_1_1util_1_1decorators_1_1read__only_1ac2c69debb2f5f2eb306bae8ce1e7b9d2)`(self,instance,value)` | 

## Members

#### `public  `[`value`](#classexot_1_1util_1_1decorators_1_1read__only_1a935b7e99fd46a0baa6d3adb9227f054f) {#classexot_1_1util_1_1decorators_1_1read__only_1a935b7e99fd46a0baa6d3adb9227f054f}

#### `public def `[`__init__`](#classexot_1_1util_1_1decorators_1_1read__only_1a087bfe73cc38f09afbeb922b6ea5de70)`(self,value)` {#classexot_1_1util_1_1decorators_1_1read__only_1a087bfe73cc38f09afbeb922b6ea5de70}

#### `public def `[`__get__`](#classexot_1_1util_1_1decorators_1_1read__only_1afcdfb4519ac023bffd9cb8e07c25cf90)`(self,instance,owner)` {#classexot_1_1util_1_1decorators_1_1read__only_1afcdfb4519ac023bffd9cb8e07c25cf90}

#### `public def `[`__set__`](#classexot_1_1util_1_1decorators_1_1read__only_1ac2c69debb2f5f2eb306bae8ce1e7b9d2)`(self,instance,value)` {#classexot_1_1util_1_1decorators_1_1read__only_1ac2c69debb2f5f2eb306bae8ce1e7b9d2}

# namespace `exot::util::factory` {#namespaceexot_1_1util_1_1factory}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::util::factory::GenericFactory`](#classexot_1_1util_1_1factory_1_1GenericFactory) | Generic object factory

# class `exot::util::factory::GenericFactory` {#classexot_1_1util_1_1factory_1_1GenericFactory}

Generic object factory

..note::
    The type of objects to be used needs to be provided as a 'klass'
    argument, for example:

    >>> class MyFactory(GenericFactory, klass=MyType): pass

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a2ee1e33173113a9b2ee1309ddc215dcd)`(self,float similarity)` | Initialise the factory
`public def `[`__init_subclass__`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a50055d6c11a6ce7ca4f5b09db3b7172b)`(cls,type klass,** kwargs)` | 
`public type `[`klass`](#classexot_1_1util_1_1factory_1_1GenericFactory_1acfebf8c3279398d3947b4a5140a6d5b5)`(self)` | Gets the base class "produced" by the factory
`public t.Set[type] `[`available`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a671ac5a9d41c6913f8124ee33bc368bb)`(self)` | Gets the available classes that can be created
`public type `[`default`](#classexot_1_1util_1_1factory_1_1GenericFactory_1ab83f210e18aeee7eb414408595cdaf41)`(self)` | Gets the default production class
`public t.Set[type] `[`unavailable`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a1ac6373398cdb56257425b93ebbe295e)`(self)` | Gets the unavailable classes that cannot be created (e.g. abstract classes)
`public t.Optional[t.List] `[`available_types`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a573febc7412ca29b5edec90fb4e15cd2)`(self)` | Gets the available specialised "types"
`public def `[`update_registry`](#classexot_1_1util_1_1factory_1_1GenericFactory_1ae1a942bd26545f1e495eb8c7170a06c9)`(self)` | Updates the factory's registry (available and unavailable production classes)
`public t.List[t.Dict] `[`match`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a23da9c469ddc1af632c63737a78a1962)`(self,str name,str variant)` | Matches the name to an available production class
`public type `[`produce_type`](#classexot_1_1util_1_1factory_1_1GenericFactory_1ae1dd1350096c6b98bf8e7dae22027087)`(self,str name,** kwargs)` | Produces a type that matches the given name
`public None `[`verify_type`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a73cceb160b6b99edb7044ec0bd4fc8de)`(self,type klass,** kwargs)` | Verify if a type matches the desired type
`public object `[`__call__`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a72038c7235b611c5785bbdc63ffb6bd4)`(self,str name,* args,** kwargs)` | Produces an object, main factory method
`public object `[`make_default`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a6d1b64e6d2b2126916df0c7cf9b18a29)`(self,* args,** kwargs)` | Produces an instance of the default class

## Members

#### `public def `[`__init__`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a2ee1e33173113a9b2ee1309ddc215dcd)`(self,float similarity)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a2ee1e33173113a9b2ee1309ddc215dcd}

Initialise the factory

:param similarity: minimum match similarity, (0.0, 1.0],
defaults to 0.9
:type similarity: float, optional

#### `public def `[`__init_subclass__`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a50055d6c11a6ce7ca4f5b09db3b7172b)`(cls,type klass,** kwargs)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a50055d6c11a6ce7ca4f5b09db3b7172b}

#### `public type `[`klass`](#classexot_1_1util_1_1factory_1_1GenericFactory_1acfebf8c3279398d3947b4a5140a6d5b5)`(self)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1acfebf8c3279398d3947b4a5140a6d5b5}

Gets the base class "produced" by the factory

Returns:
    type: The factory's base class

#### `public t.Set[type] `[`available`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a671ac5a9d41c6913f8124ee33bc368bb)`(self)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a671ac5a9d41c6913f8124ee33bc368bb}

Gets the available classes that can be created

Returns:
    t.Set[type]: The set of available classes

#### `public type `[`default`](#classexot_1_1util_1_1factory_1_1GenericFactory_1ab83f210e18aeee7eb414408595cdaf41)`(self)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1ab83f210e18aeee7eb414408595cdaf41}

Gets the default production class

Returns:
    type: The default production class

#### `public t.Set[type] `[`unavailable`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a1ac6373398cdb56257425b93ebbe295e)`(self)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a1ac6373398cdb56257425b93ebbe295e}

Gets the unavailable classes that cannot be created (e.g. abstract classes)

Returns:
    t.Set[type]: The set of unavaialble classes

#### `public t.Optional[t.List] `[`available_types`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a573febc7412ca29b5edec90fb4e15cd2)`(self)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a573febc7412ca29b5edec90fb4e15cd2}

Gets the available specialised "types"

Returns:
    t.Optional[t.List]: The available specialised "types"

#### `public def `[`update_registry`](#classexot_1_1util_1_1factory_1_1GenericFactory_1ae1a942bd26545f1e495eb8c7170a06c9)`(self)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1ae1a942bd26545f1e495eb8c7170a06c9}

Updates the factory's registry (available and unavailable production classes)

#### `public t.List[t.Dict] `[`match`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a23da9c469ddc1af632c63737a78a1962)`(self,str name,str variant)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a23da9c469ddc1af632c63737a78a1962}

Matches the name to an available production class

Args:
    name (str): The name to search
    variant (str, optional): The variant (concrete or abstract). Defaults to "concrete".

Raises:
    TypeError: Wrong type supplied for 'variant'
    ValueError: Wrong value supplied for 'variant'
    AmbiguousMatchError: Ambiguous match among available production classes

Returns:
    t.List[t.Dict]: A list of dicts with keys: class, name, similarity

#### `public type `[`produce_type`](#classexot_1_1util_1_1factory_1_1GenericFactory_1ae1dd1350096c6b98bf8e7dae22027087)`(self,str name,** kwargs)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1ae1dd1350096c6b98bf8e7dae22027087}

Produces a type that matches the given name

Args:
    name (str): The name

Raises:
    NothingMatchedError: Nothing has matched
    AbstractMatchError: The matched type is abstract
    ValueError: Matched with insufficient similarity due to 'name'

Returns:
    type: The type that matches the name.

#### `public None `[`verify_type`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a73cceb160b6b99edb7044ec0bd4fc8de)`(self,type klass,** kwargs)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a73cceb160b6b99edb7044ec0bd4fc8de}

Verify if a type matches the desired type

Args:
    klass (type): Type to check

#### `public object `[`__call__`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a72038c7235b611c5785bbdc63ffb6bd4)`(self,str name,* args,** kwargs)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a72038c7235b611c5785bbdc63ffb6bd4}

Produces an object, main factory method

Args:
    name (str): The name of the class to create
    *args: Positional arguments passed to the constructor of the class
    **kwargs: Keyword arguments passed to the constructor of the class

Returns:
    object: The class instance

#### `public object `[`make_default`](#classexot_1_1util_1_1factory_1_1GenericFactory_1a6d1b64e6d2b2126916df0c7cf9b18a29)`(self,* args,** kwargs)` {#classexot_1_1util_1_1factory_1_1GenericFactory_1a6d1b64e6d2b2126916df0c7cf9b18a29}

Produces an instance of the default class

Args:
    *args: Positional arguments passed to the constructor of the default class
    **kwargs: Keyword arguments passed to the constructor of the default class

Returns:
    object: The default class instance

# namespace `exot::util::file` {#namespaceexot_1_1util_1_1file}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`private Path `[`_path_type_check`](#file_8py_1a41dcbc5ee48859436657c5ecf5312f88)`(t.Union path,str desc)`            | Normalise a path to a Path type
`public bool `[`check_access`](#file_8py_1ae520c45f8de287197e7d65bb532dc769)`(t.Union path,str mode)`            | Check access permissions on a path
`public bool `[`validate_root_path`](#file_8py_1a90047f343fca8a377099b1e287af800b)`(t.Union path,bool throw)`            | Check if a root path is a valid exot root path
`public Path `[`add_random`](#file_8py_1a60c976aa84ef3307e08e799c79ebc657)`(t.Union path,int length)`            | Add a random suffix to the stem of a path
`public Path `[`add_timestamp`](#file_8py_1a3137bb35fb8f5ebda3170536813f4272)`(t.Union path,t.Optional time)`            | Add a timestamp to a path
`public Path `[`move`](#file_8py_1a9619c3236f680098e32db058dcf4e4ae)`(t.Union path,t.Union to)`            | Move a file or a directory
`public str `[`move_action`](#file_8py_1aa359625857c90bdd6c91c23008468baa)`(Path path)`            | 
`public Path `[`copy`](#file_8py_1a75fde4f36ff2ca39d73d20d5378f486e)`(t.Union path,t.Union to,bool replace)`            | Copy a file or a directory
`public None `[`delete`](#file_8py_1a2beeffe2876ea312577a1b50898d9bab)`(t.Union path)`            | Delete a file or a directory
`public invoke.runners.Result `[`backup`](#file_8py_1a67c4c2603a795cc198ae5adde910be46)`(t.Union path,t.Mapping config)`            | Backups a path using SCP

## Members

#### `private Path `[`_path_type_check`](#file_8py_1a41dcbc5ee48859436657c5ecf5312f88)`(t.Union path,str desc)` {#file_8py_1a41dcbc5ee48859436657c5ecf5312f88}

Normalise a path to a Path type

Args:
    path (t.Union[Path, str]): The path or path string
    desc (str): The "category" of the error message. Defaults to "path".

Returns:
    Path: The path as a pathlib.Path.

#### `public bool `[`check_access`](#file_8py_1ae520c45f8de287197e7d65bb532dc769)`(t.Union path,str mode)` {#file_8py_1ae520c45f8de287197e7d65bb532dc769}

Check access permissions on a path

Args:
    path (t.Union[Path, str]): The path
    mode (str): The access mode (one of 'w', 'r', 'x'). Defaults to "r".

Returns:
    bool: True if can be accessed with the given mode.

#### `public bool `[`validate_root_path`](#file_8py_1a90047f343fca8a377099b1e287af800b)`(t.Union path,bool throw)` {#file_8py_1a90047f343fca8a377099b1e287af800b}

Check if a root path is a valid exot root path

Args:
    path (t.Union[Path, str]): The path
    throw (bool): Should throw if failed? Defaults to True.

Returns:
    bool: True if a valid root path.

#### `public Path `[`add_random`](#file_8py_1a60c976aa84ef3307e08e799c79ebc657)`(t.Union path,int length)` {#file_8py_1a60c976aa84ef3307e08e799c79ebc657}

Add a random suffix to the stem of a path

Args:
    path (t.Union[Path, str]): The path
    length (int): Length of the random string to append. Defaults to 5.

Returns:
    Path: The amended path.

#### `public Path `[`add_timestamp`](#file_8py_1a3137bb35fb8f5ebda3170536813f4272)`(t.Union path,t.Optional time)` {#file_8py_1a3137bb35fb8f5ebda3170536813f4272}

Add a timestamp to a path

Args:
    path (t.Union[Path, str]): The path
    time (t.Optional[str]): The optional time. Will use current time if None.

Returns:
    Path: The amended path.

#### `public Path `[`move`](#file_8py_1a9619c3236f680098e32db058dcf4e4ae)`(t.Union path,t.Union to)` {#file_8py_1a9619c3236f680098e32db058dcf4e4ae}

Move a file or a directory

Args:
    path (t.Union[Path, str]): The path to move
    to (t.Union[Path, str]): The destination path

Returns:
    Path: The destination path

Raises:
    FileNotFoundError: 'path' does not exist or inaccessible.
    FileExistsError: destination path exists.

#### `public str `[`move_action`](#file_8py_1aa359625857c90bdd6c91c23008468baa)`(Path path)` {#file_8py_1aa359625857c90bdd6c91c23008468baa}

#### `public Path `[`copy`](#file_8py_1a75fde4f36ff2ca39d73d20d5378f486e)`(t.Union path,t.Union to,bool replace)` {#file_8py_1a75fde4f36ff2ca39d73d20d5378f486e}

Copy a file or a directory

Args:
    path (t.Union[Path, str]): The path to copy
    to (t.Union[Path, str]): The destination path
    replace (bool): Should replace if destination path exists? Defaults to False.

Returns:
    Path: The destination path

Raises:
    FileNotFoundError: 'path' does not exist or inaccessible.
    FileExistsError: destination path exists and 'replace' not set.

#### `public None `[`delete`](#file_8py_1a2beeffe2876ea312577a1b50898d9bab)`(t.Union path)` {#file_8py_1a2beeffe2876ea312577a1b50898d9bab}

Delete a file or a directory

Args:
    path (t.Union[Path, str]): The path to delete

Raises:
    FileNotFoundError: 'path' does not exist.

#### `public invoke.runners.Result `[`backup`](#file_8py_1a67c4c2603a795cc198ae5adde910be46)`(t.Union path,t.Mapping config)` {#file_8py_1a67c4c2603a795cc198ae5adde910be46}

Backups a path using SCP

Args:
    path (t.Union[Path, str]): The path to backup
    config (t.Mapping): The config with keys: user, host, key, port, path.

Raises:
    FileNotFoundError: The path does not exist
    ValueError: Directory provided instead of a file
    ValueError: Misconfigured backup

Returns:
    invoke.runners.Result: The result of the SCP invocation

# namespace `exot::util::git` {#namespaceexot_1_1util_1_1git}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::util::git::GitRepository`](#classexot_1_1util_1_1git_1_1GitRepository) | Accessor to certain information about a git repository

# class `exot::util::git::GitRepository` {#classexot_1_1util_1_1git_1_1GitRepository}

Accessor to certain information about a git repository

Synopsis:
    Static methods:
        git_available        is_git_directory
    Properties:
        _permutations        staged              renamed
        _git                 unstaged            copied
        commit               tracked             unmerged
        digest               untracked           ignored
        status               added               modified
        dirty                deleted
    Methods:
        parse_status         _parse_status

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public None `[`__init__`](#classexot_1_1util_1_1git_1_1GitRepository_1a2d0ac41e66d73b4138e0b1b6a2640200)`(self,Path directory)` | Args:
`public str `[`commit`](#classexot_1_1util_1_1git_1_1GitRepository_1a59a1d9dcd183fc40598cf97da747ecf2)`(self)` | Get current git commit
`public str `[`digest`](#classexot_1_1util_1_1git_1_1GitRepository_1ac2df8069815d4094c456c869f729e519)`(self)` | Get current git commit's short digest
`public List[Dict[str, str]] `[`status`](#classexot_1_1util_1_1git_1_1GitRepository_1aee7a10dacb79764bc8c0749bb8878296)`(self)` | Get formatted output of `git status -s`
`public List[Dict[str, str]] `[`parse_status`](#classexot_1_1util_1_1git_1_1GitRepository_1a3d17fe49854aad5feffff806c5007068)`(self,Union statuses,AnyStr file)` | Wrapper for :meth:`_parse_status`
`public def `[`staged`](#classexot_1_1util_1_1git_1_1GitRepository_1aca3296a30f638645f4d132abf5173d8b)`(self)` | 
`public def `[`unstaged`](#classexot_1_1util_1_1git_1_1GitRepository_1a97ccfaeda17ea2edd038eee277e90894)`(self)` | 
`public def `[`tracked`](#classexot_1_1util_1_1git_1_1GitRepository_1aaefcfe703f7f9617c7f6cbeddba112ac)`(self)` | 
`public def `[`untracked`](#classexot_1_1util_1_1git_1_1GitRepository_1a2bc41f6b71ae58b61f500c4f35c8f07b)`(self)` | 
`public def `[`added`](#classexot_1_1util_1_1git_1_1GitRepository_1a3a7c126b1e3bd5040c9fd97505a09a4b)`(self)` | 
`public def `[`deleted`](#classexot_1_1util_1_1git_1_1GitRepository_1a742eb6e3fcc7cfd321e26dfd5deff718)`(self)` | 
`public def `[`renamed`](#classexot_1_1util_1_1git_1_1GitRepository_1a03c398360c2068de4bab3a909e292fe0)`(self)` | 
`public def `[`copied`](#classexot_1_1util_1_1git_1_1GitRepository_1a95fdd98906cc92736ed32512fcec887b)`(self)` | 
`public def `[`unmerged`](#classexot_1_1util_1_1git_1_1GitRepository_1ab84dd129cb6bb2e328f1a3b47c730d13)`(self)` | 
`public def `[`ignored`](#classexot_1_1util_1_1git_1_1GitRepository_1afb2204966dd726bdd978b341e6f08722)`(self)` | 
`public def `[`modified`](#classexot_1_1util_1_1git_1_1GitRepository_1a21039c14b05fa7a293d0d7edcc86be4b)`(self)` | 
`public def `[`dirty`](#classexot_1_1util_1_1git_1_1GitRepository_1a854a1e7dc3be9626cdb19d0443c9a971)`(self)` | Does the git directory contain modified or untracked python files?

## Members

#### `public None `[`__init__`](#classexot_1_1util_1_1git_1_1GitRepository_1a2d0ac41e66d73b4138e0b1b6a2640200)`(self,Path directory)` {#classexot_1_1util_1_1git_1_1GitRepository_1a2d0ac41e66d73b4138e0b1b6a2640200}

Args:
    directory (Path, optional): a path to the working directory

Raises:
    RuntimeError: if git binary is not available
    TypeError: if working directory is not valid

#### `public str `[`commit`](#classexot_1_1util_1_1git_1_1GitRepository_1a59a1d9dcd183fc40598cf97da747ecf2)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a59a1d9dcd183fc40598cf97da747ecf2}

Get current git commit

#### `public str `[`digest`](#classexot_1_1util_1_1git_1_1GitRepository_1ac2df8069815d4094c456c869f729e519)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1ac2df8069815d4094c456c869f729e519}

Get current git commit's short digest

#### `public List[Dict[str, str]] `[`status`](#classexot_1_1util_1_1git_1_1GitRepository_1aee7a10dacb79764bc8c0749bb8878296)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1aee7a10dacb79764bc8c0749bb8878296}

Get formatted output of `git status -s`

#### `public List[Dict[str, str]] `[`parse_status`](#classexot_1_1util_1_1git_1_1GitRepository_1a3d17fe49854aad5feffff806c5007068)`(self,Union statuses,AnyStr file)` {#classexot_1_1util_1_1git_1_1GitRepository_1a3d17fe49854aad5feffff806c5007068}

Wrapper for :meth:`_parse_status`

#### `public def `[`staged`](#classexot_1_1util_1_1git_1_1GitRepository_1aca3296a30f638645f4d132abf5173d8b)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1aca3296a30f638645f4d132abf5173d8b}

#### `public def `[`unstaged`](#classexot_1_1util_1_1git_1_1GitRepository_1a97ccfaeda17ea2edd038eee277e90894)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a97ccfaeda17ea2edd038eee277e90894}

#### `public def `[`tracked`](#classexot_1_1util_1_1git_1_1GitRepository_1aaefcfe703f7f9617c7f6cbeddba112ac)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1aaefcfe703f7f9617c7f6cbeddba112ac}

#### `public def `[`untracked`](#classexot_1_1util_1_1git_1_1GitRepository_1a2bc41f6b71ae58b61f500c4f35c8f07b)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a2bc41f6b71ae58b61f500c4f35c8f07b}

#### `public def `[`added`](#classexot_1_1util_1_1git_1_1GitRepository_1a3a7c126b1e3bd5040c9fd97505a09a4b)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a3a7c126b1e3bd5040c9fd97505a09a4b}

#### `public def `[`deleted`](#classexot_1_1util_1_1git_1_1GitRepository_1a742eb6e3fcc7cfd321e26dfd5deff718)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a742eb6e3fcc7cfd321e26dfd5deff718}

#### `public def `[`renamed`](#classexot_1_1util_1_1git_1_1GitRepository_1a03c398360c2068de4bab3a909e292fe0)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a03c398360c2068de4bab3a909e292fe0}

#### `public def `[`copied`](#classexot_1_1util_1_1git_1_1GitRepository_1a95fdd98906cc92736ed32512fcec887b)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a95fdd98906cc92736ed32512fcec887b}

#### `public def `[`unmerged`](#classexot_1_1util_1_1git_1_1GitRepository_1ab84dd129cb6bb2e328f1a3b47c730d13)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1ab84dd129cb6bb2e328f1a3b47c730d13}

#### `public def `[`ignored`](#classexot_1_1util_1_1git_1_1GitRepository_1afb2204966dd726bdd978b341e6f08722)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1afb2204966dd726bdd978b341e6f08722}

#### `public def `[`modified`](#classexot_1_1util_1_1git_1_1GitRepository_1a21039c14b05fa7a293d0d7edcc86be4b)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a21039c14b05fa7a293d0d7edcc86be4b}

#### `public def `[`dirty`](#classexot_1_1util_1_1git_1_1GitRepository_1a854a1e7dc3be9626cdb19d0443c9a971)`(self)` {#classexot_1_1util_1_1git_1_1GitRepository_1a854a1e7dc3be9626cdb19d0443c9a971}

Does the git directory contain modified or untracked python files?

# namespace `exot::util::logging` {#namespaceexot_1_1util_1_1logging}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public logging.Formatter `[`long_log_formatter`](#logging_8py_1abd3dd271bd75d1b323210b5c9425ee1d)`()`            | Get default logging string format
`public logging.Formatter `[`short_log_formatter`](#logging_8py_1a60cb186e79bc600aa76e2697ee53a7c2)`()`            | Get a more concise logging string format
`public str `[`abbreviate`](#logging_8py_1aff0e88817fdb76f50148449ac1904b34)`(str s,int threshold,int limit)`            | Abbreviate a string, taking accound of camel case to preserve some legibility
`public None `[`configure_root_logger`](#logging_8py_1a51370ec75ea596230b011ecada0c2319)`(t.Optional path,t.Optional name)`            | Configure the root logger
`public def `[`get_root_logger`](#logging_8py_1aba1959ca0d54db2bf03f493b25a83813)`(** kwargs)`            | Get the root logger
`public def `[`get_logger`](#logging_8py_1aec8444090b1f520f34cf60685b9d0eb5)`(t.Union obj,* args,** kwargs)`            | Get a logger instance for a type or an object
`class `[`exot::util::logging::Loggable`](#classexot_1_1util_1_1logging_1_1Loggable) | A mixin class for adding a logger

## Members

#### `public logging.Formatter `[`long_log_formatter`](#logging_8py_1abd3dd271bd75d1b323210b5c9425ee1d)`()` {#logging_8py_1abd3dd271bd75d1b323210b5c9425ee1d}

Get default logging string format

#### `public logging.Formatter `[`short_log_formatter`](#logging_8py_1a60cb186e79bc600aa76e2697ee53a7c2)`()` {#logging_8py_1a60cb186e79bc600aa76e2697ee53a7c2}

Get a more concise logging string format

#### `public str `[`abbreviate`](#logging_8py_1aff0e88817fdb76f50148449ac1904b34)`(str s,int threshold,int limit)` {#logging_8py_1aff0e88817fdb76f50148449ac1904b34}

Abbreviate a string, taking accound of camel case to preserve some legibility

#### `public None `[`configure_root_logger`](#logging_8py_1a51370ec75ea596230b011ecada0c2319)`(t.Optional path,t.Optional name)` {#logging_8py_1a51370ec75ea596230b011ecada0c2319}

Configure the root logger

#### `public def `[`get_root_logger`](#logging_8py_1aba1959ca0d54db2bf03f493b25a83813)`(** kwargs)` {#logging_8py_1aba1959ca0d54db2bf03f493b25a83813}

Get the root logger

#### `public def `[`get_logger`](#logging_8py_1aec8444090b1f520f34cf60685b9d0eb5)`(t.Union obj,* args,** kwargs)` {#logging_8py_1aec8444090b1f520f34cf60685b9d0eb5}

Get a logger instance for a type or an object

# class `exot::util::logging::Loggable` {#classexot_1_1util_1_1logging_1_1Loggable}

```
class exot::util::logging::Loggable
  : public metaclass
  : public ABCMeta
```  

A mixin class for adding a logger

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`logger`](#classexot_1_1util_1_1logging_1_1Loggable_1a39d3f4cd9d43adafaaaaf0671d5af9d8)`(self)` | 
`public def `[`__getstate__`](#classexot_1_1util_1_1logging_1_1Loggable_1ad96f2a680dc7fa96380cf6690a8c78d9)`(self)` | 
`public def `[`__setstate__`](#classexot_1_1util_1_1logging_1_1Loggable_1ae9427ab58c9864540249019da9807ac8)`(self,value)` | 
`public def `[`set_logging_level`](#classexot_1_1util_1_1logging_1_1Loggable_1ab64fb2083701d30681c23b6568bfbe6e)`(self,int value)` | 
`public def `[`__init__`](#classexot_1_1util_1_1logging_1_1Loggable_1a523da4c6ce275a7911a2fb510f13bdf1)`(self,* args,** kwargs)` | Inits the class logger

## Members

#### `public def `[`logger`](#classexot_1_1util_1_1logging_1_1Loggable_1a39d3f4cd9d43adafaaaaf0671d5af9d8)`(self)` {#classexot_1_1util_1_1logging_1_1Loggable_1a39d3f4cd9d43adafaaaaf0671d5af9d8}

#### `public def `[`__getstate__`](#classexot_1_1util_1_1logging_1_1Loggable_1ad96f2a680dc7fa96380cf6690a8c78d9)`(self)` {#classexot_1_1util_1_1logging_1_1Loggable_1ad96f2a680dc7fa96380cf6690a8c78d9}

#### `public def `[`__setstate__`](#classexot_1_1util_1_1logging_1_1Loggable_1ae9427ab58c9864540249019da9807ac8)`(self,value)` {#classexot_1_1util_1_1logging_1_1Loggable_1ae9427ab58c9864540249019da9807ac8}

#### `public def `[`set_logging_level`](#classexot_1_1util_1_1logging_1_1Loggable_1ab64fb2083701d30681c23b6568bfbe6e)`(self,int value)` {#classexot_1_1util_1_1logging_1_1Loggable_1ab64fb2083701d30681c23b6568bfbe6e}

#### `public def `[`__init__`](#classexot_1_1util_1_1logging_1_1Loggable_1a523da4c6ce275a7911a2fb510f13bdf1)`(self,* args,** kwargs)` {#classexot_1_1util_1_1logging_1_1Loggable_1a523da4c6ce275a7911a2fb510f13bdf1}

Inits the class logger

# namespace `exot::util::misc` {#namespaceexot_1_1util_1_1misc}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public None `[`call_with_leaves`](#misc_8py_1a7aa8d6ea768ae87c5d75599ea5f03126)`(t. Callable,t.Any] function,t.T obj,bool _seq)`            | Calls a function on leaves of an object
`public int `[`dict_depth`](#misc_8py_1a0475250f63dd9a1ac37078635fee099a)`(t.Any obj,int level)`            | Get maximum depth of a dict-like object
`public t.List[t.Dict] `[`dict_diff`](#misc_8py_1a836ce2c9b60f365c376d24744c3b799a)`(Map left,Map right)`            | Get the difference between 2 dict-like objects
`public t.List `[`find_attributes`](#misc_8py_1ae3e97e658597c6872a4da7e2712eed02)`(t.Any klass,str attr)`            | Find attributes in any of a class'es bases
`public Map `[`flatten_dict`](#misc_8py_1acbf3bd7152785d0f626c6acd759c43c5)`(Map obj,str sep)`            | Flatten a dict to a 1-level dict combining keys with a separator
`public Map `[`expand_dict`](#misc_8py_1ab9e7f6e56cbbf30a88aa256459d529c7)`(Map obj,str sep)`            | Expands a flattened mapping by splitting keys with the given separator
`public t.List `[`get_concrete_subclasses`](#misc_8py_1a2bfaa8777edb3c151ff39d5a0c65d695)`(klass,bool recursive,bool derived)`            | Get a list of non-abstract subclasses of a type
`public t.List `[`get_subclasses`](#misc_8py_1a9008a7f348df19b179f665e778f1dae1)`(klass,bool recursive,bool derived)`            | Get a list of subclasses of a type
`public t.Generator[t.Tuple, None, None] `[`get_valid_access_paths`](#misc_8py_1a932e3a1ec47254d145ffffcd8a7f2912)`(Map obj,int _limit,bool _leaf_only,bool _use_lists,bool _fallthrough_empty)`            | Generate valid key sequences in a dict, optionally including lists
`public t.Any `[`getitem`](#misc_8py_1a51a8975f9f3f57b1951db518339497cf)`(Map obj,t.Union query,*t.Any args,str sep)`            | Get a value from a dict-like object using an XPath-like query, or a tuple-path
`public bool `[`has_method`](#misc_8py_1ab722a815d11c3fc55d5a97aa75918fde)`(t.Union klass,str name)`            | Check if a method exists in any of a klass'es bases
`public bool `[`has_property`](#misc_8py_1a243da1b38efa65d04ca61ed1e18c9298)`(t.Union klass,str name)`            | Check if a variable exists in any of a klass'es bases
`public bool `[`has_type`](#misc_8py_1a58fca7818b573ebc7da843617d7a4e8b)`(t.Union klass)`            | Check if a type or instance has a Type member type that derives from Enum
`public bool `[`has_variable`](#misc_8py_1aa063fcc433fbbc95472f9304aa97f929)`(t.Union klass,str name)`            | Check if a variable exists in any of a klass'es bases
`public bool `[`is_abstract`](#misc_8py_1a1e4e4ff78ac9dec4c5e41849737add28)`(t.Union klass)`            | Check if a type or instance is abstract
`public bool `[`is_scalar_numeric`](#misc_8py_1a033fe99acf23334baf360af423a84e1c)`(t.Any value)`            | Check if is an int, a float, or a NumPy variant thereof
`public t.Generator `[`leaves`](#misc_8py_1a89e026b1bdb33104b980f4306fc06638)`(Map obj)`            | Get leaves of a mapping
`public str `[`list2cmdline`](#misc_8py_1a934259f47b5a35b2c94caab2e3d10deb)`(t.Iterable seq)`            | Translates a sequence of arguments into a command line string with "None" removal
`public t.Any `[`map_to_leaves`](#misc_8py_1a45875fcadea48165be382d622b3c383e)`(t. Callable,t.Any] function,t.T obj,bool _seq)`            | Map a function to leaves of an object
`public t.Any `[`mro_getattr`](#misc_8py_1ab7f773e3f66c7c86f88bae4a2eef98b2)`(type cls,str attr,*t.Any args)`            | Get an attribute from a type's class hierarchy
`public bool `[`mro_hasattr`](#misc_8py_1a8850c64faab4c0ad042f96355b0766d8)`(type cls,str attr)`            | Check if an attribute exists in a type's class hierarchy
`public str `[`random_string`](#misc_8py_1a8bf37e7e32626bf678689c362bc0cee9)`(int length)`            | Make a random string of specified length
`public str `[`timestamp`](#misc_8py_1ac8bf87ee573ec44a85e23a9432c3a9ed)`()`            | Make a timestamp with current time
`public object `[`safe_eval`](#misc_8py_1aae90984ba59a0368f5312f4c549d40c6)`(str to_eval,*t.Tuple expect,int timeout)`            | Evaluate a restricted subset of Python (and numpy) from a string
`public t.Union[t.List[str], str] `[`sanitise_ansi`](#misc_8py_1af1796bb80cb65f7127259425774a620b)`(t. Union,str] value)`            | Remove all ANSI escape characters from a str or a list of str
`public None `[`setgetattr`](#misc_8py_1a767e2d817c64dc15ba2410a121dcce32)`(t.Union klass,str attr,t.Any default)`            | Combines `setattr` and `getattr` to set attributes
`public None `[`setitem`](#misc_8py_1a76f63903de81af056b01e4f3f5c735b5)`(t.MutableMapping obj,t.Tuple query,t.Any value,bool force)`            | Set a value in a dict-like object using a tuple-path query
`public t.Optional[t.T] `[`stub_recursively`](#misc_8py_1ac9d4add756e74c532f0519d9b3cde578)`(t.T obj,t.Any stub,bool _stub_list_elements)`            | Produce a copy with all leaf values recursively set to a 'stub' value
`public t.Tuple[str] `[`unpack__all__`](#misc_8py_1a1233692c405706d10e11410371ae5c4d)`(*t.Collection imports)`            | Upacks a list of lists/tuples into a 1-dimensional list
`public t.NoReturn `[`validate_helper`](#misc_8py_1aec259ca62bfb0e077871e44a26e3dc37)`(t.Mapping what,t.Any key,*type types,str msg)`            | Validate types of key in a mapping using key-paths
`public set `[`get_cores_and_schedules`](#misc_8py_1aacee0d6a05bed3db631164d2de49c3f2)`(t.Mapping environments_apps_zones)`            | 

## Members

#### `public None `[`call_with_leaves`](#misc_8py_1a7aa8d6ea768ae87c5d75599ea5f03126)`(t. Callable,t.Any] function,t.T obj,bool _seq)` {#misc_8py_1a7aa8d6ea768ae87c5d75599ea5f03126}

Calls a function on leaves of an object

A leaf is considered to be an object that is not a Mapping (or, when _seq is set,
also not a Sequence except a string, which is also a Sequence).

Args:
    function (t.Callable[[t.Any], t.Any]): The callable
    obj (t.T): The tree-like or sequence-like object
    _seq (bool, optional): Should sequences be considered?. Defaults to True.

#### `public int `[`dict_depth`](#misc_8py_1a0475250f63dd9a1ac37078635fee099a)`(t.Any obj,int level)` {#misc_8py_1a0475250f63dd9a1ac37078635fee099a}

Get maximum depth of a dict-like object

Args:
    obj (t.Any): The dict-like object
    level (int): For internal use only. Defaults to 0.

.. note::
    The depth of a non-dict-like object is considered to be 0.
    An empty dict increases the depth if `_empty_increments` is True.

    Examples:

    >>> dict_depth(1)                         # returns 0
    >>> dict_depth([1,2,3])                   # returns 0
    >>> dict_depth({1: 1, 2: 2})              # returns 1
    >>> dict_depth({1: {2: {3: 3}}})          # returns 3
    >>> dict_depth({1: {2: {3: {}}}})         # returns 4

#### `public t.List[t.Dict] `[`dict_diff`](#misc_8py_1a836ce2c9b60f365c376d24744c3b799a)`(Map left,Map right)` {#misc_8py_1a836ce2c9b60f365c376d24744c3b799a}

Get the difference between 2 dict-like objects

Args:
    left (Map): The left dict-like object
    right (Map): The right dict-like object

The value returned is a list of dictionaries with keys ["path", "left", "right"]
which contain the query path and the differences between the left and right mapping.
If a key is missing in either mapping, it will be indicated as a "None".

`math.nan` (not-a-number) is used for default values in the comparison because of
the property: `math.nan != math.nan`. Simple None cannot be used, since it would
not handle keys that both have a value of None. In general, this function might
report false-positives for keys that contain the math.nan (or np.nan) value simply
due to this property. There is no workaround available.

#### `public t.List `[`find_attributes`](#misc_8py_1ae3e97e658597c6872a4da7e2712eed02)`(t.Any klass,str attr)` {#misc_8py_1ae3e97e658597c6872a4da7e2712eed02}

Find attributes in any of a class'es bases

Args:
    klass (t.Any): The type object
    attr (str): The attribute

Returns:
    t.List: List of found instances of the attribute in the class hierarchy

#### `public Map `[`flatten_dict`](#misc_8py_1acbf3bd7152785d0f626c6acd759c43c5)`(Map obj,str sep)` {#misc_8py_1acbf3bd7152785d0f626c6acd759c43c5}

Flatten a dict to a 1-level dict combining keys with a separator

Args:
    obj (Map): The dict-like object
    sep (str): The separator used when combining keys. Defaults to ".".

Returns:
    Map: A flattened object of same type as 'obj'.

.. warning::
    Flattening will enforce all keys to be string-types!

`reducer` is a function accepted by the functools.reduce function, which is of
form: f(a, b) where _a_ is the accumulated value, and _b_ is the updated value
from the iterable.

The .items() function produces key-value tuple-pairs. These can be expanded
with *, e.g. `*("a", "b")` will expand to `"a", "b"`. This property is used
to expand the `kv_pair` below.

Example walkthrough on `flatten_dict({'a': 1, 'b': {'c': {'d': 2}}})`: ::

    `outer` <- obj: {'a': 1, 'b': {'c': {'d': 2}}}, prefix: ''
        `reducer` <- key: 'a', value: 1
            `inner` <- acc: {}, key: 'a', value: 1, prefix: ''
            `inner` -> {'a': 1}
        `reducer` -> {'a': 1}
        `reducer` <- key: 'b', value: {'c': {'d': 2}}
            `inner` <- acc: {'a': 1}, key: 'b', value: {'c': {'d': 2}}, prefix: ''
    `outer` <- obj: {'c': {'d': 2}}, prefix: 'b.'
        `reducer` <- key: 'c', value: {'d': 2}
            `inner` <- acc: {}, key: 'c', value: {'d': 2}, prefix: 'b.'
    `outer` <- obj: {'d': 2}, prefix: 'b.c.'
        `reducer` <- key: 'd', value: 2
            `inner` <- acc: {}, key: 'd', value: 2, prefix: 'b.c.'
            `inner` -> {'b.c.d': 2}
        `reducer` -> {'b.c.d': 2}
    `outer` -> {'b.c.d': 2}
            `inner` -> {'b.c.d': 2}
        `reducer` -> {'b.c.d': 2}
    `outer` -> {'b.c.d': 2}
            `inner` -> {'a': 1, 'b.c.d': 2}
        `reducer` -> {'a': 1, 'b.c.d': 2}
    `outer` -> {'a': 1, 'b.c.d': 2}

#### `public Map `[`expand_dict`](#misc_8py_1ab9e7f6e56cbbf30a88aa256459d529c7)`(Map obj,str sep)` {#misc_8py_1ab9e7f6e56cbbf30a88aa256459d529c7}

Expands a flattened mapping by splitting keys with the given separator

Args:
    obj (Map): The flattened dict-like object to unflatten
    sep (str, optional): The key separator

Raises:
    TypeError: If wrong type is supplied
    ValueError: If a non-flat dict is supplied

Returns:
    Map: The expanded mapping object of same type as 'obj'.

Example:
    >>> d = {'a': 1, 'b': 2, 'c.ca': 1, 'c.cb': 2}
    >>> expand_dict(d)
    {'a': 1, 'b': 2, 'c': {'ca': 1, 'cb': 2}}

#### `public t.List `[`get_concrete_subclasses`](#misc_8py_1a2bfaa8777edb3c151ff39d5a0c65d695)`(klass,bool recursive,bool derived)` {#misc_8py_1a2bfaa8777edb3c151ff39d5a0c65d695}

Get a list of non-abstract subclasses of a type

Args:
    klass (t.Type): The type object
    recursive (bool): Should the classes be extracted recursively? Defaults to True.
    derived (bool): Use the 'derived' property of SubclassTracker-enhanced types? [True]

Returns:
    t.List: A list of concrete subclasses of the type

#### `public t.List `[`get_subclasses`](#misc_8py_1a9008a7f348df19b179f665e778f1dae1)`(klass,bool recursive,bool derived)` {#misc_8py_1a9008a7f348df19b179f665e778f1dae1}

Get a list of subclasses of a type

Args:
    klass (t.Type): The type object
    recursive (bool): Should the classes be extracted recursively? Defaults to True.
    derived (bool): Use the 'derived' property of SubclassTracker-enhanced types? [True]

Returns:
    t.List: A list of concrete subclasses of the type

#### `public t.Generator[t.Tuple, None, None] `[`get_valid_access_paths`](#misc_8py_1a932e3a1ec47254d145ffffcd8a7f2912)`(Map obj,int _limit,bool _leaf_only,bool _use_lists,bool _fallthrough_empty)` {#misc_8py_1a932e3a1ec47254d145ffffcd8a7f2912}

Generate valid key sequences in a dict, optionally including lists

Args:
    obj (Map): The dict-like object
    _limit (int): Maximum number of paths that can be created with list-like elements.
    _leaf_only (bool): Provide paths for only the leaves of the mapping. Defaults to True.
    _use_lists (bool): Provide paths for list-like elements in the mapping. Defaults to True.
    _fallthrough_empty (bool): Discard empty list- or dict-like elements? Defaults to True.

Details:
    If `_leaf_only` is set, only paths to leaves will be produced, a leaf being a value
    that is not a mapping (or list).
    If `_use_lists` is set, lists will also be *recursively* checked for valid paths.
    if `_fallthrough_empty` is set, an empty dict or list will yield an empty tuple,
    rendering a parent path.

Returns:
    t.Generator[t.Tuple,None,None]: A generator that yields the access paths (tuples).

Examples:
>>> # Only leaves:
>>> d = {'a1': {'a2': None}, 'b2': None}
>>> list(get_valid_access_paths(d, _leaf_only=True))
[('a1', 'a2'), ('b2',)]
>>> # All paths:
>>> list(get_valid_access_paths(d, _leaf_only=False))
[('a1',), ('a1', 'a2'), ('b2',)]

#### `public t.Any `[`getitem`](#misc_8py_1a51a8975f9f3f57b1951db518339497cf)`(Map obj,t.Union query,*t.Any args,str sep)` {#misc_8py_1a51a8975f9f3f57b1951db518339497cf}

Get a value from a dict-like object using an XPath-like query, or a tuple-path

Accesses an object that provides a dict-like interface using a query: either a
tuple representing the path, or a string where consecutive keys are separated with
a separator, e.g. "key1/key2".

Returns the value of the object at the given key-sequence. Returns a default value
if provided, or throws a LookupError.

Args:
    obj (Map): a mapping
    query (t.Union[str, t.Tuple]): a query path using a separated string or a tuple
    *args (t.Any): an optional default value, similar to `getattr`
    sep (str, optional): a separator string used to split a string query path

Returns:
    t.Any: the value stored in obj for the given query, or the default value

Raises:
    LookupError: if query not found and no default value is provided
    TypeError: if obj is not a mapping, or query is not a str or tuple

#### `public bool `[`has_method`](#misc_8py_1ab722a815d11c3fc55d5a97aa75918fde)`(t.Union klass,str name)` {#misc_8py_1ab722a815d11c3fc55d5a97aa75918fde}

Check if a method exists in any of a klass'es bases

Args:
    klass (t.Union[type, object]): The type or object
    name (str): The name of the method

Returns:
    bool: True if has a method with the given name.

#### `public bool `[`has_property`](#misc_8py_1a243da1b38efa65d04ca61ed1e18c9298)`(t.Union klass,str name)` {#misc_8py_1a243da1b38efa65d04ca61ed1e18c9298}

Check if a variable exists in any of a klass'es bases

Args:
    klass (t.Union[type, object]): The type or object
    name (str): The name of the property

Returns:
    bool: True if has a property with the given name.

#### `public bool `[`has_type`](#misc_8py_1a58fca7818b573ebc7da843617d7a4e8b)`(t.Union klass)` {#misc_8py_1a58fca7818b573ebc7da843617d7a4e8b}

Check if a type or instance has a Type member type that derives from Enum

Args:
    klass (t.Union[type, object]): The type or object

Returns:
    bool: True if has the "Type" attribute.

#### `public bool `[`has_variable`](#misc_8py_1aa063fcc433fbbc95472f9304aa97f929)`(t.Union klass,str name)` {#misc_8py_1aa063fcc433fbbc95472f9304aa97f929}

Check if a variable exists in any of a klass'es bases

Args:
    klass (t.Union[type, object]): The type or object
    name (str): The name of the variable

Returns:
    bool: True if has a variable with the given name.

#### `public bool `[`is_abstract`](#misc_8py_1a1e4e4ff78ac9dec4c5e41849737add28)`(t.Union klass)` {#misc_8py_1a1e4e4ff78ac9dec4c5e41849737add28}

Check if a type or instance is abstract

Args:
    klass (t.Union[type, object]): The type or object

Returns:
    bool: True if the type/instance is abstract.

#### `public bool `[`is_scalar_numeric`](#misc_8py_1a033fe99acf23334baf360af423a84e1c)`(t.Any value)` {#misc_8py_1a033fe99acf23334baf360af423a84e1c}

Check if is an int, a float, or a NumPy variant thereof

Args:
    value (t.Any): The value to inspect

Returns:
    bool: True if scalar and numeric.

#### `public t.Generator `[`leaves`](#misc_8py_1a89e026b1bdb33104b980f4306fc06638)`(Map obj)` {#misc_8py_1a89e026b1bdb33104b980f4306fc06638}

Get leaves of a mapping

Args:
    obj (Map): The dict-like object

Returns:
    t.Generator: A generator that yields the leaf elements of the mapping.

#### `public str `[`list2cmdline`](#misc_8py_1a934259f47b5a35b2c94caab2e3d10deb)`(t.Iterable seq)` {#misc_8py_1a934259f47b5a35b2c94caab2e3d10deb}

Translates a sequence of arguments into a command line string with "None" removal

Args:
    seq (t.Iterable): The sequence of arguments

Returns:
    str: The command-line string

#### `public t.Any `[`map_to_leaves`](#misc_8py_1a45875fcadea48165be382d622b3c383e)`(t. Callable,t.Any] function,t.T obj,bool _seq)` {#misc_8py_1a45875fcadea48165be382d622b3c383e}

Map a function to leaves of an object

A leaf is considered to be an object that is not a Mapping (or, when _seq is set,
also not a Sequence except a string, which is also a Sequence).

Args:
    function (t.Callable[[t.Any], t.Any]): a function or signatude "a -> a"
    obj (t.T): a dict-like, list-like, or plain object
    _seq (bool, optional): map on elements of lists?

Returns:
    t.T: the obj with transformed elements

#### `public t.Any `[`mro_getattr`](#misc_8py_1ab7f773e3f66c7c86f88bae4a2eef98b2)`(type cls,str attr,*t.Any args)` {#misc_8py_1ab7f773e3f66c7c86f88bae4a2eef98b2}

Get an attribute from a type's class hierarchy

Args:
    cls (type): The type
    attr (str): The attribute
    *args (t.Any): The default value (like in Python's default getattr)

Returns:
    t.Any: The attribute, or when not found the default value (if provided)

Raises:
    TypeError: Not called on a type
    TypeError: Wrong number of arguments
    AttributeError: Attribute not found and no default value provided

#### `public bool `[`mro_hasattr`](#misc_8py_1a8850c64faab4c0ad042f96355b0766d8)`(type cls,str attr)` {#misc_8py_1a8850c64faab4c0ad042f96355b0766d8}

Check if an attribute exists in a type's class hierarchy

Args:
    cls (type): The type
    attr (str): The attribute

Returns:
    bool: True if has the attribute.

Raises:
    TypeError: Not called on a type

#### `public str `[`random_string`](#misc_8py_1a8bf37e7e32626bf678689c362bc0cee9)`(int length)` {#misc_8py_1a8bf37e7e32626bf678689c362bc0cee9}

Make a random string of specified length

Args:
    length (int): The desired random string length

Returns:
    str: The random string

#### `public str `[`timestamp`](#misc_8py_1ac8bf87ee573ec44a85e23a9432c3a9ed)`()` {#misc_8py_1ac8bf87ee573ec44a85e23a9432c3a9ed}

Make a timestamp with current time

Returns:
    str: The timestamp in ISO format

#### `public object `[`safe_eval`](#misc_8py_1aae90984ba59a0368f5312f4c549d40c6)`(str to_eval,*t.Tuple expect,int timeout)` {#misc_8py_1aae90984ba59a0368f5312f4c549d40c6}

Evaluate a restricted subset of Python (and numpy) from a string

Args:
    to_eval (str): The string to evaluate
    expect (t.Tuple[type]): The list of expected resulting types. Defaults to list, ndarray.
    timeout (int): The timeout after which the call fails in seconds. Defaults to 10.

The `safe_eval` function allows using a subset of commands, listed in `_globals` and
`_locals`, which includes a few numpy functions: linspace, arange, array, rand, and
randint. Examples:

>>> safe_eval("linspace(1, 10, 10, dtype=int).tolist()")
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> safe_eval("__import__('os').getcwd()")
NameError  Traceback (most recent call last)
...
NameError: name '__import__' is not defined
>>> safe_eval("range(5)")
TypeError  Traceback (most recent call last)
...
TypeError: eval produced a <class 'range'>, expected: (<class 'list'>, <class 'numpy.ndarray'>)
>>> safe_eval("list(round(rand(), 2) for _ in range(5))")
[0.96, 0.41, 0.9, 0.98, 0.02]

#### `public t.Union[t.List[str], str] `[`sanitise_ansi`](#misc_8py_1af1796bb80cb65f7127259425774a620b)`(t. Union,str] value)` {#misc_8py_1af1796bb80cb65f7127259425774a620b}

Remove all ANSI escape characters from a str or a list of str

Args:
    value (t.Union[t.List[str], str]): The string or list of strings

Returns:
    t.Union[t.List[str], str]: The sanitised string or a list of sanitised strings

#### `public None `[`setgetattr`](#misc_8py_1a767e2d817c64dc15ba2410a121dcce32)`(t.Union klass,str attr,t.Any default)` {#misc_8py_1a767e2d817c64dc15ba2410a121dcce32}

Combines `setattr` and `getattr` to set attributes

Args:
    klass (t.Union[type, object]): The type or object
    attr (str): The attribute
    default (t.Any): The default value

#### `public None `[`setitem`](#misc_8py_1a76f63903de81af056b01e4f3f5c735b5)`(t.MutableMapping obj,t.Tuple query,t.Any value,bool force)` {#misc_8py_1a76f63903de81af056b01e4f3f5c735b5}

Set a value in a dict-like object using a tuple-path query

Args:
    obj (t.MutableMapping): a mutable mapping
    query (t.Tuple): a query path as a tuple
    value (t.Any): value to set

Raises:
    TypeError: if obj is not a mutable mapping

#### `public t.Optional[t.T] `[`stub_recursively`](#misc_8py_1ac9d4add756e74c532f0519d9b3cde578)`(t.T obj,t.Any stub,bool _stub_list_elements)` {#misc_8py_1ac9d4add756e74c532f0519d9b3cde578}

Produce a copy with all leaf values recursively set to a 'stub' value

Args:
    obj (t.T): the object to stub
    stub (t.Any, optional): the value to set the leaf elements to
    _stub_list_elements (bool, optional): stub individual elements in collections?

Returns:
    (t.T, optional): the stubbed object

#### `public t.Tuple[str] `[`unpack__all__`](#misc_8py_1a1233692c405706d10e11410371ae5c4d)`(*t.Collection imports)` {#misc_8py_1a1233692c405706d10e11410371ae5c4d}

Upacks a list of lists/tuples into a 1-dimensional list

Args:
    *imports (t.Collection[str]): The collections of strings in "__all__"

Returns:
    t.Tuple[str]: The flattened imports as a tuple of strings.

#### `public t.NoReturn `[`validate_helper`](#misc_8py_1aec259ca62bfb0e077871e44a26e3dc37)`(t.Mapping what,t.Any key,*type types,str msg)` {#misc_8py_1aec259ca62bfb0e077871e44a26e3dc37}

Validate types of key in a mapping using key-paths

Args:
    what (t.Mapping): The mapping
    key (t.Any): The key
    *types (type): The valid types
    msg (str): An additional error message. Defaults to "".

#### `public set `[`get_cores_and_schedules`](#misc_8py_1aacee0d6a05bed3db631164d2de49c3f2)`(t.Mapping environments_apps_zones)` {#misc_8py_1aacee0d6a05bed3db631164d2de49c3f2}

# namespace `exot::util::mixins` {#namespaceexot_1_1util_1_1mixins}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::util::mixins::_Configurable`](#classexot_1_1util_1_1mixins_1_1__Configurable) | 
`class `[`exot::util::mixins::_HasParent`](#classexot_1_1util_1_1mixins_1_1__HasParent) | 
`class `[`exot::util::mixins::_SubclassTracker`](#classexot_1_1util_1_1mixins_1_1__SubclassTracker) | 
`class `[`exot::util::mixins::Configurable`](#classexot_1_1util_1_1mixins_1_1Configurable) | 
`class `[`exot::util::mixins::HasParent`](#classexot_1_1util_1_1mixins_1_1HasParent) | 
`class `[`exot::util::mixins::IntermediatesHandler`](#classexot_1_1util_1_1mixins_1_1IntermediatesHandler) | 
`class `[`exot::util::mixins::IntermediatesHolder`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder) | 
`class `[`exot::util::mixins::LabelConversions`](#classexot_1_1util_1_1mixins_1_1LabelConversions) | 
`class `[`exot::util::mixins::Pickleable`](#classexot_1_1util_1_1mixins_1_1Pickleable) | 
`class `[`exot::util::mixins::Serialisable`](#classexot_1_1util_1_1mixins_1_1Serialisable) | Abstract base class for serialisers
`class `[`exot::util::mixins::SubclassTracker`](#classexot_1_1util_1_1mixins_1_1SubclassTracker) | A mixin class for tracking derived and concrete derived classes
`class `[`exot::util::mixins::YamlSerialisable`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable) | 

# class `exot::util::mixins::_Configurable` {#classexot_1_1util_1_1mixins_1_1__Configurable}

```
class exot::util::mixins::_Configurable
  : public SimpleNamespace
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::util::mixins::_HasParent` {#classexot_1_1util_1_1mixins_1_1__HasParent}

```
class exot::util::mixins::_HasParent
  : public SimpleNamespace
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::util::mixins::_SubclassTracker` {#classexot_1_1util_1_1mixins_1_1__SubclassTracker}

```
class exot::util::mixins::_SubclassTracker
  : public SimpleNamespace
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::util::mixins::Configurable` {#classexot_1_1util_1_1mixins_1_1Configurable}

```
class exot::util::mixins::Configurable
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`config`](#classexot_1_1util_1_1mixins_1_1Configurable_1a584310982da5a820427dd2cc5cbfa27d) | 
`public None `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1Configurable_1aaf35932c5898e22aa6407b2ca66ea7fc)`(cls,**t.Any kwargs)` | Initialise a subclass of Configurable
`public None `[`__init__`](#classexot_1_1util_1_1mixins_1_1Configurable_1a133a12fdfacfa216021c7496d5a669ae)`(self,*t.Dict args,**t.Dict kwargs)` | Initialise the Configurable
`public t.Union[bool, type(NotImplemented)] `[`__subclasshook__`](#classexot_1_1util_1_1mixins_1_1Configurable_1aea42d326aa627847c3142d2a98f5d417)`(cls,type klass)` | Subclass checking hook for types that are alike
`public t.List[str] `[`required_config_keys`](#classexot_1_1util_1_1mixins_1_1Configurable_1ace7a41d5e12030b43100be3317be7ffe)`(self)` | Produce a list of required keys
`public bool `[`configured`](#classexot_1_1util_1_1mixins_1_1Configurable_1a3b2d32196ac95b34a3e30554896478d7)`(self)` | Is the Configurable configured?
`public t.Optional`[`[AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)`] `[`config`](#classexot_1_1util_1_1mixins_1_1Configurable_1aed6a7bd5880c3576dbee9e36d334fb92)`(self)` | Access the config
`public None `[`config`](#classexot_1_1util_1_1mixins_1_1Configurable_1aedad348512f054ff590e4d41d6ed22c4)`(self,t.MutableMapping value)` | Set the config with key requirements and validation
`public t.NoReturn `[`validate`](#classexot_1_1util_1_1mixins_1_1Configurable_1a38177f0f7043ed11c99c934c9726db9e)`(self)` | Check if the config has desired values and/or types

## Members

#### `public  `[`config`](#classexot_1_1util_1_1mixins_1_1Configurable_1a584310982da5a820427dd2cc5cbfa27d) {#classexot_1_1util_1_1mixins_1_1Configurable_1a584310982da5a820427dd2cc5cbfa27d}

#### `public None `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1Configurable_1aaf35932c5898e22aa6407b2ca66ea7fc)`(cls,**t.Any kwargs)` {#classexot_1_1util_1_1mixins_1_1Configurable_1aaf35932c5898e22aa6407b2ca66ea7fc}

Initialise a subclass of Configurable

#### `public None `[`__init__`](#classexot_1_1util_1_1mixins_1_1Configurable_1a133a12fdfacfa216021c7496d5a669ae)`(self,*t.Dict args,**t.Dict kwargs)` {#classexot_1_1util_1_1mixins_1_1Configurable_1a133a12fdfacfa216021c7496d5a669ae}

Initialise the Configurable

#### `public t.Union[bool, type(NotImplemented)] `[`__subclasshook__`](#classexot_1_1util_1_1mixins_1_1Configurable_1aea42d326aa627847c3142d2a98f5d417)`(cls,type klass)` {#classexot_1_1util_1_1mixins_1_1Configurable_1aea42d326aa627847c3142d2a98f5d417}

Subclass checking hook for types that are alike

#### `public t.List[str] `[`required_config_keys`](#classexot_1_1util_1_1mixins_1_1Configurable_1ace7a41d5e12030b43100be3317be7ffe)`(self)` {#classexot_1_1util_1_1mixins_1_1Configurable_1ace7a41d5e12030b43100be3317be7ffe}

Produce a list of required keys

#### `public bool `[`configured`](#classexot_1_1util_1_1mixins_1_1Configurable_1a3b2d32196ac95b34a3e30554896478d7)`(self)` {#classexot_1_1util_1_1mixins_1_1Configurable_1a3b2d32196ac95b34a3e30554896478d7}

Is the Configurable configured?

#### `public t.Optional`[`[AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)`] `[`config`](#classexot_1_1util_1_1mixins_1_1Configurable_1aed6a7bd5880c3576dbee9e36d334fb92)`(self)` {#classexot_1_1util_1_1mixins_1_1Configurable_1aed6a7bd5880c3576dbee9e36d334fb92}

Access the config

#### `public None `[`config`](#classexot_1_1util_1_1mixins_1_1Configurable_1aedad348512f054ff590e4d41d6ed22c4)`(self,t.MutableMapping value)` {#classexot_1_1util_1_1mixins_1_1Configurable_1aedad348512f054ff590e4d41d6ed22c4}

Set the config with key requirements and validation

#### `public t.NoReturn `[`validate`](#classexot_1_1util_1_1mixins_1_1Configurable_1a38177f0f7043ed11c99c934c9726db9e)`(self)` {#classexot_1_1util_1_1mixins_1_1Configurable_1a38177f0f7043ed11c99c934c9726db9e}

Check if the config has desired values and/or types

# class `exot::util::mixins::HasParent` {#classexot_1_1util_1_1mixins_1_1HasParent}

```
class exot::util::mixins::HasParent
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`parent`](#classexot_1_1util_1_1mixins_1_1HasParent_1a5150d07b11dba33752cf6714efbba6a9) | 
`public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1HasParent_1a38f6c90509a51699f3c955b19c069adf)`(cls,type parent,** kwargs)` | 
`public def `[`__init__`](#classexot_1_1util_1_1mixins_1_1HasParent_1a998f654f08c216239919d3fbf0300db5)`(self,* args,** kwargs)` | 
`public def `[`parent`](#classexot_1_1util_1_1mixins_1_1HasParent_1aec0047f22b3d43ea17a852b685ee8a84)`(self)` | 
`public def `[`parent`](#classexot_1_1util_1_1mixins_1_1HasParent_1ad09815689b633f384fce27a72389c3ce)`(self,value)` | 

## Members

#### `public  `[`parent`](#classexot_1_1util_1_1mixins_1_1HasParent_1a5150d07b11dba33752cf6714efbba6a9) {#classexot_1_1util_1_1mixins_1_1HasParent_1a5150d07b11dba33752cf6714efbba6a9}

#### `public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1HasParent_1a38f6c90509a51699f3c955b19c069adf)`(cls,type parent,** kwargs)` {#classexot_1_1util_1_1mixins_1_1HasParent_1a38f6c90509a51699f3c955b19c069adf}

#### `public def `[`__init__`](#classexot_1_1util_1_1mixins_1_1HasParent_1a998f654f08c216239919d3fbf0300db5)`(self,* args,** kwargs)` {#classexot_1_1util_1_1mixins_1_1HasParent_1a998f654f08c216239919d3fbf0300db5}

#### `public def `[`parent`](#classexot_1_1util_1_1mixins_1_1HasParent_1aec0047f22b3d43ea17a852b685ee8a84)`(self)` {#classexot_1_1util_1_1mixins_1_1HasParent_1aec0047f22b3d43ea17a852b685ee8a84}

#### `public def `[`parent`](#classexot_1_1util_1_1mixins_1_1HasParent_1ad09815689b633f384fce27a72389c3ce)`(self,value)` {#classexot_1_1util_1_1mixins_1_1HasParent_1ad09815689b633f384fce27a72389c3ce}

# class `exot::util::mixins::IntermediatesHandler` {#classexot_1_1util_1_1mixins_1_1IntermediatesHandler}

```
class exot::util::mixins::IntermediatesHandler
  : public exot.util.mixins.IntermediatesHolder
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`collect_intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHandler_1a0a87f0fa4f8efe10240f81b9c63bc103)`(self,object source,t.Optional namespace)` | 

## Members

#### `public def `[`collect_intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHandler_1a0a87f0fa4f8efe10240f81b9c63bc103)`(self,object source,t.Optional namespace)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHandler_1a0a87f0fa4f8efe10240f81b9c63bc103}

# class `exot::util::mixins::IntermediatesHolder` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder}

```
class exot::util::mixins::IntermediatesHolder
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a5458228ba103b82cbeac2c3db5b434cd)`(cls,** kwargs)` | 
`public def `[`__init__`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a866d486825f91780228cea564a088f8f)`(self,* args,** kwargs)` | 
`public def `[`intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a33a08b6c3c238b5ebc1e7157c81a25c9)`(self,value)` | 
`public def `[`intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a27fb18e05b687ce2da76bc7b7e543f62)`(self)` | 
`public def `[`add_intermediate`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1ad197fe4e93bce8cd16f049cc393c13ba)`(self,name,value)` | 
`public def `[`del_intermediate`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a3f899b360310232678fd8a6578fbaa86)`(self,name)` | 
`public def `[`clear_intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a456689da743ff937aaa7ecf43f49870e)`(self)` | 
`public def `[`get_intermediate`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a41ce4a20dd130ff1452aa5eb4f8575f0)`(self,name)` | 

## Members

#### `public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a5458228ba103b82cbeac2c3db5b434cd)`(cls,** kwargs)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a5458228ba103b82cbeac2c3db5b434cd}

#### `public def `[`__init__`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a866d486825f91780228cea564a088f8f)`(self,* args,** kwargs)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a866d486825f91780228cea564a088f8f}

#### `public def `[`intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a33a08b6c3c238b5ebc1e7157c81a25c9)`(self,value)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a33a08b6c3c238b5ebc1e7157c81a25c9}

#### `public def `[`intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a27fb18e05b687ce2da76bc7b7e543f62)`(self)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a27fb18e05b687ce2da76bc7b7e543f62}

#### `public def `[`add_intermediate`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1ad197fe4e93bce8cd16f049cc393c13ba)`(self,name,value)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1ad197fe4e93bce8cd16f049cc393c13ba}

#### `public def `[`del_intermediate`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a3f899b360310232678fd8a6578fbaa86)`(self,name)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a3f899b360310232678fd8a6578fbaa86}

#### `public def `[`clear_intermediates`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a456689da743ff937aaa7ecf43f49870e)`(self)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a456689da743ff937aaa7ecf43f49870e}

#### `public def `[`get_intermediate`](#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a41ce4a20dd130ff1452aa5eb4f8575f0)`(self,name)` {#classexot_1_1util_1_1mixins_1_1IntermediatesHolder_1a41ce4a20dd130ff1452aa5eb4f8575f0}

# class `exot::util::mixins::LabelConversions` {#classexot_1_1util_1_1mixins_1_1LabelConversions}

```
class exot::util::mixins::LabelConversions
  : public metaclass
  : public ABCMeta
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# class `exot::util::mixins::Pickleable` {#classexot_1_1util_1_1mixins_1_1Pickleable}

```
class exot::util::mixins::Pickleable
  : public exot.util.mixins.Serialisable
  : public serialise_io_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1Pickleable_1a1ca1559637837c6beb2538fc1ecc5ae6)`(cls,** kwargs)` | Initialise a subclass
`public t.Union[str, bytes] `[`dumps`](#classexot_1_1util_1_1mixins_1_1Pickleable_1afd2dae174a6921cbdbb2a3757b985498)`(self)` | Dump an instance to a string or bytes
`public None `[`dump`](#classexot_1_1util_1_1mixins_1_1Pickleable_1a1a92bb6c15bde3b0d6710d5b29ed50ed)`(self,io.IOBase file)` | Dump an instance to a file
`public object `[`loads`](#classexot_1_1util_1_1mixins_1_1Pickleable_1ae59f3991d2de1dfcb631d5717a3b573e)`(cls,t.Union source)` | Load an instance from a string or bytes
`public object `[`load`](#classexot_1_1util_1_1mixins_1_1Pickleable_1a1201cb99bb14cc5ceb22934b863115df)`(cls,io.IOBase source)` | Load an instance from a file

## Members

#### `public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1Pickleable_1a1ca1559637837c6beb2538fc1ecc5ae6)`(cls,** kwargs)` {#classexot_1_1util_1_1mixins_1_1Pickleable_1a1ca1559637837c6beb2538fc1ecc5ae6}

Initialise a subclass

-   Attributes in `serialise_ignore` will be deleted from the instance before
    serialisation.
-   Attributes in `serialise_stub` will be 'stubbed', i.e. all leaf nodes will
    be replaced with `None`.
-   If `serialise_no_parent` is set, a parent object, as defined by HasParent,
    will not be serialised.
-   If `serialise_inherit` is set, serialise

A concrete class has to implement the following methods:

-   def dumps(self) -> t.Union[str, bytes]
-   def dump(self, file: t.Union[Path, io.TextIOBase]) -> None

And the following class methods:

-   def loads(cls, source: t.Union[str, bytes]) -> object
-   def load(cls, source: t.Union[Path, io.TextIOBase]) -> object

Args:
    serialise_ignore (t.List[str], optional): list of attributes to ignore
    serialise_stub (t.List[str], optional): list of attributes to stub
    serialise_no_parent (bool, optional): serialise parent class?
    serialise_inherit (bool, optional): inherit serialise settings from base?

#### `public t.Union[str, bytes] `[`dumps`](#classexot_1_1util_1_1mixins_1_1Pickleable_1afd2dae174a6921cbdbb2a3757b985498)`(self)` {#classexot_1_1util_1_1mixins_1_1Pickleable_1afd2dae174a6921cbdbb2a3757b985498}

Dump an instance to a string or bytes

#### `public None `[`dump`](#classexot_1_1util_1_1mixins_1_1Pickleable_1a1a92bb6c15bde3b0d6710d5b29ed50ed)`(self,io.IOBase file)` {#classexot_1_1util_1_1mixins_1_1Pickleable_1a1a92bb6c15bde3b0d6710d5b29ed50ed}

Dump an instance to a file

Args:
    file (t.Union[Path, io.TextIOBase]): a file path or an io wrapper

#### `public object `[`loads`](#classexot_1_1util_1_1mixins_1_1Pickleable_1ae59f3991d2de1dfcb631d5717a3b573e)`(cls,t.Union source)` {#classexot_1_1util_1_1mixins_1_1Pickleable_1ae59f3991d2de1dfcb631d5717a3b573e}

Load an instance from a string or bytes

Args:
    source (t.Union[str, bytes]): a serialised object as a string or bytes

#### `public object `[`load`](#classexot_1_1util_1_1mixins_1_1Pickleable_1a1201cb99bb14cc5ceb22934b863115df)`(cls,io.IOBase source)` {#classexot_1_1util_1_1mixins_1_1Pickleable_1a1201cb99bb14cc5ceb22934b863115df}

Load an instance from a file

Args:
    source (t.Union[Path, io.TextIOBase]): a file path or an io wrapper

# class `exot::util::mixins::Serialisable` {#classexot_1_1util_1_1mixins_1_1Serialisable}

```
class exot::util::mixins::Serialisable
  : public metaclass
  : public ABCMeta
```  

Abstract base class for serialisers

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a5cad47fa4f1a1d889821a1193cece297)`(cls,** kwargs)` | Initialise a subclass
`public t.Union[str, bytes] `[`dumps`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a379d2c73d4e8a143a59494a810143d96)`(self)` | Dump an instance to a string or bytes
`public None `[`dump`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a3f3e92eb7834a4ac5296c90f509b676c)`(self,io.IOBase file)` | Dump an instance to a file
`public object `[`loads`](#classexot_1_1util_1_1mixins_1_1Serialisable_1ae7f1e63dfd61cc1f23e78986ed02bfa0)`(cls,t.Union source)` | Load an instance from a string or bytes
`public object `[`load`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a801eac82b575dec824583ff7b54576f1)`(cls,io.IOBase source)` | Load an instance from a file
`public object `[`deserialise`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a2d8a498b20b85078edeb202d6c115e53)`(cls,source,bytes,Path,t.IO])` | 
`public t.Optional[str] `[`serialise`](#classexot_1_1util_1_1mixins_1_1Serialisable_1ae260c885220d556d5614c4d5043db736)`(self,t.Optional] file)` | 
`public t.List[Path] `[`save_data`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a21e48be9b0537a8b063c857495d6f19d)`(self,*t.Optional prefix,t.Optional path)` | Save input and output data in NumPy archives and/or HDF5 stores.
`public t.List[Path] `[`save_mapping`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a7dd2616497af344b839c72e2cd81dba3)`(self,attribute,t.Optional prefix,t.Optional path,t.Optional save_bundled)` | 
`public t.List[Path] `[`remove_mapping`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a000f89dd3e36fb1af944faf260ac8444)`(self,attribute,t.Optional prefix,t.Optional path,t.Optional saved_bundled)` | 
`public t.List[Path] `[`save_data_bundled`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a9934012c0f9e9963e9713026bd39b78b)`(self,*t.Optional prefix,t.Optional path)` | Save input and output data in NumPy archives and/or HDF5 stores.
`public None `[`load_data`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a8cb736b564ef5ed728f034600032b488)`(self,*t.Optional prefix,t.Optional path)` | Loads input and output stream data from NumPy archives and/or HDF5 stores.
`public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`load_mapping`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a724bb4eab5cd0329526e6437c50fc2d9)`(self,Path path,t.Optional prefix)` | Loads data from files specified using path and regex. Different to load_data, the data is not saved
`public None `[`load_data_bundled`](#classexot_1_1util_1_1mixins_1_1Serialisable_1ae1555f53540d35b960b8718d57038d5c)`(self,*t.Optional prefix,t.Optional path)` | Loads input and output stream data from NumPy archives and/or HDF5 stores.

## Members

#### `public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a5cad47fa4f1a1d889821a1193cece297)`(cls,** kwargs)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a5cad47fa4f1a1d889821a1193cece297}

Initialise a subclass

-   Attributes in `serialise_ignore` will be deleted from the instance before
    serialisation.
-   Attributes in `serialise_stub` will be 'stubbed', i.e. all leaf nodes will
    be replaced with `None`.
-   If `serialise_no_parent` is set, a parent object, as defined by HasParent,
    will not be serialised.
-   If `serialise_inherit` is set, serialise

A concrete class has to implement the following methods:

-   def dumps(self) -> t.Union[str, bytes]
-   def dump(self, file: t.Union[Path, io.TextIOBase]) -> None

And the following class methods:

-   def loads(cls, source: t.Union[str, bytes]) -> object
-   def load(cls, source: t.Union[Path, io.TextIOBase]) -> object

Args:
    serialise_ignore (t.List[str], optional): list of attributes to ignore
    serialise_stub (t.List[str], optional): list of attributes to stub
    serialise_no_parent (bool, optional): serialise parent class?
    serialise_inherit (bool, optional): inherit serialise settings from base?

#### `public t.Union[str, bytes] `[`dumps`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a379d2c73d4e8a143a59494a810143d96)`(self)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a379d2c73d4e8a143a59494a810143d96}

Dump an instance to a string or bytes

#### `public None `[`dump`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a3f3e92eb7834a4ac5296c90f509b676c)`(self,io.IOBase file)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a3f3e92eb7834a4ac5296c90f509b676c}

Dump an instance to a file

Args:
    file (t.Union[Path, io.TextIOBase]): a file path or an io wrapper

#### `public object `[`loads`](#classexot_1_1util_1_1mixins_1_1Serialisable_1ae7f1e63dfd61cc1f23e78986ed02bfa0)`(cls,t.Union source)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1ae7f1e63dfd61cc1f23e78986ed02bfa0}

Load an instance from a string or bytes

Args:
    source (t.Union[str, bytes]): a serialised object as a string or bytes

#### `public object `[`load`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a801eac82b575dec824583ff7b54576f1)`(cls,io.IOBase source)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a801eac82b575dec824583ff7b54576f1}

Load an instance from a file

Args:
    source (t.Union[Path, io.TextIOBase]): a file path or an io wrapper

#### `public object `[`deserialise`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a2d8a498b20b85078edeb202d6c115e53)`(cls,source,bytes,Path,t.IO])` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a2d8a498b20b85078edeb202d6c115e53}

#### `public t.Optional[str] `[`serialise`](#classexot_1_1util_1_1mixins_1_1Serialisable_1ae260c885220d556d5614c4d5043db736)`(self,t.Optional] file)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1ae260c885220d556d5614c4d5043db736}

#### `public t.List[Path] `[`save_data`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a21e48be9b0537a8b063c857495d6f19d)`(self,*t.Optional prefix,t.Optional path)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a21e48be9b0537a8b063c857495d6f19d}

Save input and output data in NumPy archives and/or HDF5 stores.

Args:
    prefix (t.Optional[str], optional):
The file prefix, e.g. "my_data" will produce archives my_data.npz and my_data.h5
    path (t.Optional[Path], optional):
The save path, if different than self.path

#### `public t.List[Path] `[`save_mapping`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a7dd2616497af344b839c72e2cd81dba3)`(self,attribute,t.Optional prefix,t.Optional path,t.Optional save_bundled)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a7dd2616497af344b839c72e2cd81dba3}

#### `public t.List[Path] `[`remove_mapping`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a000f89dd3e36fb1af944faf260ac8444)`(self,attribute,t.Optional prefix,t.Optional path,t.Optional saved_bundled)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a000f89dd3e36fb1af944faf260ac8444}

#### `public t.List[Path] `[`save_data_bundled`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a9934012c0f9e9963e9713026bd39b78b)`(self,*t.Optional prefix,t.Optional path)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a9934012c0f9e9963e9713026bd39b78b}

Save input and output data in NumPy archives and/or HDF5 stores.

Args:
    prefix (t.Optional[str], optional):
The file prefix, e.g. "my_data" will produce archives my_data.npz and my_data.h5
    path (t.Optional[Path], optional):
The save path, if different than self.path

#### `public None `[`load_data`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a8cb736b564ef5ed728f034600032b488)`(self,*t.Optional prefix,t.Optional path)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a8cb736b564ef5ed728f034600032b488}

Loads input and output stream data from NumPy archives and/or HDF5 stores.

Args:
    prefix (t.Optional[str], optional):
The file prefix, e.g. "my_data" will produce archives my_data.npz and my_data.h5
    path (t.Optional[Path], optional):
The load path, if different than self.path

#### `public `[`AttributeDict`](#classexot_1_1util_1_1attributedict_1_1AttributeDict)` `[`load_mapping`](#classexot_1_1util_1_1mixins_1_1Serialisable_1a724bb4eab5cd0329526e6437c50fc2d9)`(self,Path path,t.Optional prefix)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1a724bb4eab5cd0329526e6437c50fc2d9}

Loads data from files specified using path and regex. Different to load_data, the data is not saved
in the parent object (self) but in a AttributeDict, which is then returned.

#### `public None `[`load_data_bundled`](#classexot_1_1util_1_1mixins_1_1Serialisable_1ae1555f53540d35b960b8718d57038d5c)`(self,*t.Optional prefix,t.Optional path)` {#classexot_1_1util_1_1mixins_1_1Serialisable_1ae1555f53540d35b960b8718d57038d5c}

Loads input and output stream data from NumPy archives and/or HDF5 stores.

Args:
    prefix (t.Optional[str], optional):
The file prefix, e.g. "my_data" will produce archives my_data.npz and my_data.h5
    path (t.Optional[Path], optional):
The load path, if different than self.path

# class `exot::util::mixins::SubclassTracker` {#classexot_1_1util_1_1mixins_1_1SubclassTracker}

```
class exot::util::mixins::SubclassTracker
  : public metaclass
  : public ABCMeta
```  

A mixin class for tracking derived and concrete derived classes

.. note::
    The proper functioning of this class depends on the MRO (method
    resolution order). The subclass initialiser looks for itself in the
    hierarchy, and considers the previous class in the instance as the
    "root" to be tracked.

    For example:

    >>> class X(SomeClass, SubclassTracker): pass

    will "apply" the tracking to SomeClass. To track X, put the mixin
    as the first inherited class:

    >>> class X(SubclassTracker, SomeClass): pass

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public None `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1SubclassTracker_1a23fb1b52600204e8032402163bc8c1a4)`(cls,str track,**t.Dict kwargs)` | 

## Members

#### `public None `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1SubclassTracker_1a23fb1b52600204e8032402163bc8c1a4)`(cls,str track,**t.Dict kwargs)` {#classexot_1_1util_1_1mixins_1_1SubclassTracker_1a23fb1b52600204e8032402163bc8c1a4}

# class `exot::util::mixins::YamlSerialisable` {#classexot_1_1util_1_1mixins_1_1YamlSerialisable}

```
class exot::util::mixins::YamlSerialisable
  : public exot.util.mixins.Serialisable
  : public serialise_io_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1add14b3373c729d8eaa2f52c0c303bf68)`(cls,** kwargs)` | Initialise a subclass
`public t.Union[str, bytes] `[`dumps`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1ae21615abf5d098edcdd49c1fa5102d63)`(self)` | Dump an instance to a string or bytes
`public None `[`dump`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1a877946f84e73be3cca0f3609543191bd)`(self,t.Union file)` | 
`public object `[`loads`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1ad2137a4db5bcac9cb11ce42a6d9dfb78)`(cls,t.Union source)` | Load an instance from a string or bytes
`public object `[`load`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1af4ccb9b9bd4f15a689d78d67102f3d4b)`(cls,t.Union source)` | 

## Members

#### `public def `[`__init_subclass__`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1add14b3373c729d8eaa2f52c0c303bf68)`(cls,** kwargs)` {#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1add14b3373c729d8eaa2f52c0c303bf68}

Initialise a subclass

-   Attributes in `serialise_ignore` will be deleted from the instance before
    serialisation.
-   Attributes in `serialise_stub` will be 'stubbed', i.e. all leaf nodes will
    be replaced with `None`.
-   If `serialise_no_parent` is set, a parent object, as defined by HasParent,
    will not be serialised.
-   If `serialise_inherit` is set, serialise

A concrete class has to implement the following methods:

-   def dumps(self) -> t.Union[str, bytes]
-   def dump(self, file: t.Union[Path, io.TextIOBase]) -> None

And the following class methods:

-   def loads(cls, source: t.Union[str, bytes]) -> object
-   def load(cls, source: t.Union[Path, io.TextIOBase]) -> object

Args:
    serialise_ignore (t.List[str], optional): list of attributes to ignore
    serialise_stub (t.List[str], optional): list of attributes to stub
    serialise_no_parent (bool, optional): serialise parent class?
    serialise_inherit (bool, optional): inherit serialise settings from base?

#### `public t.Union[str, bytes] `[`dumps`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1ae21615abf5d098edcdd49c1fa5102d63)`(self)` {#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1ae21615abf5d098edcdd49c1fa5102d63}

Dump an instance to a string or bytes

#### `public None `[`dump`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1a877946f84e73be3cca0f3609543191bd)`(self,t.Union file)` {#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1a877946f84e73be3cca0f3609543191bd}

#### `public object `[`loads`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1ad2137a4db5bcac9cb11ce42a6d9dfb78)`(cls,t.Union source)` {#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1ad2137a4db5bcac9cb11ce42a6d9dfb78}

Load an instance from a string or bytes

Args:
    source (t.Union[str, bytes]): a serialised object as a string or bytes

#### `public object `[`load`](#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1af4ccb9b9bd4f15a689d78d67102f3d4b)`(cls,t.Union source)` {#classexot_1_1util_1_1mixins_1_1YamlSerialisable_1af4ccb9b9bd4f15a689d78d67102f3d4b}

# namespace `exot::util::plotting` {#namespaceexot_1_1util_1_1plotting}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`private pathlib.Path `[`_save_path_helper`](#plotting_8py_1aa7b2c7063e8e80d7b4acc10ff73cbded)`(t.Union path)`            | A helper function for save paths
`public None `[`remove_spine`](#plotting_8py_1a94d6cc31d95e49ec6f45ec272919f522)`(axis,str which,bool ticks_only)`            | Removes the spine from an axis
`public def `[`add_spine`](#plotting_8py_1aeb34ae2b8c2bbe5a8210fdb82dab5463)`(axis,str which,bool ticks_only)`            | Adds a spine to an axis
`public def `[`rugplot`](#plotting_8py_1a91beef91335742d0ff6ad1f91e5c1e27)`(a,height,axis,ax,top,** kwargs)`            | Plot datapoints in an array as sticks on an axis. Adapted from seaborn.

## Members

#### `private pathlib.Path `[`_save_path_helper`](#plotting_8py_1aa7b2c7063e8e80d7b4acc10ff73cbded)`(t.Union path)` {#plotting_8py_1aa7b2c7063e8e80d7b4acc10ff73cbded}

A helper function for save paths

Args:
    path (t.Union[pathlib.Path, str]): The save path

Raises:
    TypeError: Wrong type supplied
    ValueError: Provided a file instead of a directory
    RuntimeError: Directory was not created

Returns:
    pathlib.Path: The save path

#### `public None `[`remove_spine`](#plotting_8py_1a94d6cc31d95e49ec6f45ec272919f522)`(axis,str which,bool ticks_only)` {#plotting_8py_1a94d6cc31d95e49ec6f45ec272919f522}

Removes the spine from an axis

Args:
    axis: The matplotlib axis
    which (str): Which spine to remove? (top, bottom)
    ticks_only (bool, optional): Remove only the ticks?. Defaults to False.

#### `public def `[`add_spine`](#plotting_8py_1aeb34ae2b8c2bbe5a8210fdb82dab5463)`(axis,str which,bool ticks_only)` {#plotting_8py_1aeb34ae2b8c2bbe5a8210fdb82dab5463}

Adds a spine to an axis

Args:
    axis: The matplotlib axis
    which (str): Which spine to add? (top, bottom)
    ticks_only (bool, optional): Add only the ticks?. Defaults to False.

#### `public def `[`rugplot`](#plotting_8py_1a91beef91335742d0ff6ad1f91e5c1e27)`(a,height,axis,ax,top,** kwargs)` {#plotting_8py_1a91beef91335742d0ff6ad1f91e5c1e27}

Plot datapoints in an array as sticks on an axis. Adapted from seaborn.

Args:
    a (vector): 1D array of observations.
    height (scalar, optional): Height of ticks as proportion of the axis.
    axis ({'x' | 'y'}, optional): Axis to draw rugplot on.
    ax (matplotlib axes, optional): Axes to draw plot into; otherwise grabs current axes.
    **kwargs: Other keyword arguments are passed to ``LineCollection``

Returns:
    ax (matplotlib axes): The Axes object with the plot on it.

# namespace `exot::util::prompts` {#namespaceexot_1_1util_1_1prompts}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public t.Any `[`prompt`](#prompts_8py_1a0ffbc645b908441d1c983322edf0d8c8)`(str msg,t.Optional expect,t.Optional _timeout,str _prompt,str _ask,t. Optional,t.Any]] _handler,bool _fail,** kwargs)`            | Prompt user for input, with timeouts and type handling
`class `[`exot::util::prompts::ResponseHandlers`](#classexot_1_1util_1_1prompts_1_1ResponseHandlers) | 

## Members

#### `public t.Any `[`prompt`](#prompts_8py_1a0ffbc645b908441d1c983322edf0d8c8)`(str msg,t.Optional expect,t.Optional _timeout,str _prompt,str _ask,t. Optional,t.Any]] _handler,bool _fail,** kwargs)` {#prompts_8py_1a0ffbc645b908441d1c983322edf0d8c8}

Prompt user for input, with timeouts and type handling

Args:
    msg (str): The message to print
    expect (t.Optional[t.Type], optional): The expected response type. Defaults to bool.
    _timeout (t.Optional[int], optional): The timeout duration. Defaults to None.
    _prompt (str, optional): The prompt prefix. Defaults to "> ".
    _ask (str, optional): The asking postfix. Defaults to "? ".
    _handler (t.Optional[t.Callable[[str], t.Any]], optional): The response handler.
    _fail (bool, optional): Should raise if prompting failed?. Defaults to False.

Raises:
    TypeError: Wrong type supplied to 'expect'
    TypeError: Wrong type supplied to '_handler'
    TimeoutError: Timed out

Returns:
    t.Any: The response

# class `exot::util::prompts::ResponseHandlers` {#classexot_1_1util_1_1prompts_1_1ResponseHandlers}

```
class exot::util::prompts::ResponseHandlers
  : public SimpleNamespace
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::util::scinum` {#namespaceexot_1_1util_1_1scinum}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public tuple `[`get_nearest`](#scinum_8py_1aad09ada575e7ae051d58b9f1fcb8e64c)`(t.Union array,t.Any value)`            | Gets the index and value of an element in the array that is closest to the given value
`public t.Any `[`get_nearest_value`](#scinum_8py_1af4d2fb274201f22a722e52d6035be2fd)`(t.Union array,t.Any value)`            | Gets the value of an element in the array that is closest to the given value
`public int `[`get_nearest_index`](#scinum_8py_1ac89f76813ec599e8cba22671b8cac52a)`(t.Union array,t.Any value)`            | Gets the index of an element in the array that is closest to the given value
`public np.ndarray `[`awgn_like`](#scinum_8py_1a9381e358d7a0d8befb5f506542587fae)`(np.ndarray like,float sigma,float mu)`            | Produces a gaussian-distributed random array of same shape as a given array
`public np.ndarray `[`uniform_like`](#scinum_8py_1ae0b955c22ff59f7ec5441f4d6f05d95c)`(np.ndarray like,float low,float high)`            | Produce a uniform-distributed random array of same shape as a given array
`public np.ndarray `[`add_awgn_noise`](#scinum_8py_1abc7346ba6e8765c0c547ab4f828e38bd)`(np.ndarray to,float sigma,float mu)`            | Adds gaussian noise to an array
`public def `[`add_uniform_noise`](#scinum_8py_1a1ae2d9f0c5a1c4f6f838eaf7e4621ccd)`(np.ndarray to,float low,float high)`            | Adds uniform noise to an array
`public int `[`count_errors`](#scinum_8py_1ade2824fa24ea2ba727fda9ac6385d344)`(np.ndarray left,np.ndarray right)`            | Counts differences between two arrays of same shape
`public int `[`count_errors_robust`](#scinum_8py_1ab6ea17cc27cd4a306fc8d97082825e8b)`(np.ndarray left,np.ndarray right)`            | Count differences between two row or column vectors
`public bool `[`is_fitted`](#scinum_8py_1af9f4516cb1b28ab66b9a2ae48d52d5b0)`(sklearn.base.BaseEstimator estimator)`            | Is an estimator fitted?
`public np.ndarray `[`interleave`](#scinum_8py_1abbedca77073492733bd2767f0de4cb0d)`(np.ndarray array,int n)`            | Interleaves rows of an array
`public np.ndarray `[`interleave_split`](#scinum_8py_1a7c67a5e30325aa40ec1857b98a85c084)`(np.ndarray array,int n)`            | Interleaves rows of an array and splits into multiple arrays
`public bool `[`is_binary`](#scinum_8py_1a317c77511d381be9c6f92800a2ae904d)`(np.ndarray array)`            | Checks if input array is binary
`public np.uint64 `[`pack_bits`](#scinum_8py_1ad1bffaeb098c0bfde81214773dd70d56)`(np.ndarray array)`            | 'Packs' a binary array into an unsigned integer
`public np.uint64 `[`pack_bits_fast`](#scinum_8py_1ad3410c555c4c5295dace95718491a159)`(np.ndarray array)`            | 'Packs' a binary array into an unsigned integer without value/type checks
`public np.ndarray `[`pad_split`](#scinum_8py_1ae2cda5b14ac09067a7a5b6cc1d2a7240)`(np.ndarray array,np.uint n,* pad)`            | Split a binary array int fixed-sized chunks while 0-padding unequal splits
`public np.ndarray `[`pack_array`](#scinum_8py_1a3b088279886a3ff1944c03265b6f06ea)`(np.ndarray array,np.uint n,* pad)`            | Packs a binary array into unsigned integers of bit width n
`public np.ndarray `[`unpack_bits`](#scinum_8py_1a67344a6c3b8c56267b09f8e1e436519c)`(np.uint value,np.uint n)`            | Unpacks an unsigned integer into an array of bits
`public np.ndarray `[`unpack_bits_fast`](#scinum_8py_1a60b0588023450c31ba84a9ac7af00498)`(np.uint value,np.uint n)`            | Unpacks an unsigned integer into an array of bits without value/type checks
`public np.ndarray `[`unpack_array`](#scinum_8py_1ab614041e85ef0577a313ee9a768a3694)`(np.ndarray array,np.uint n)`            | Unpacks an array of unsigned integers into a 2-d array of bits
`public t.Tuple[np.ndarray, np.ndarray] `[`find_ramp_edges`](#scinum_8py_1a711c4a6ed4f861bf0a7fda3b622c813e)`(np.ndarray trace,*float threshold,int roll,callable roll_fun,object kernel,str method,bool _debug)`            | Gets indexes of falling and rising ramps in a sample trace using convolution with
`public  `[`split_into_contiguous_ranges`](#scinum_8py_1a66c4f32ab7d6ac863fa484cbe0ee7884)`(np.ndarray trace,*int step_threshold)`            | Splits an array into ranges of similar values
`public pandas.DataFrame `[`get_fft`](#scinum_8py_1a552725ded78697868160a9b629c1e533)`(pandas.DataFrame data,*t.Optional timescale,bool demean,bool melt)`            | Gets the fft(s) of data in a timestamps & values DataFrame
`public pandas.DataFrame `[`get_welch`](#scinum_8py_1a35b3bc912ad0fe1ac12cc1ba77aeaf47)`(pandas.DataFrame data,t.Optional window_size,str window,*t.Optional timescale,bool demean,bool melt)`            | Gets the fft(s) of data in a timestamps & values DataFrame using the Welch method

## Members

#### `public tuple `[`get_nearest`](#scinum_8py_1aad09ada575e7ae051d58b9f1fcb8e64c)`(t.Union array,t.Any value)` {#scinum_8py_1aad09ada575e7ae051d58b9f1fcb8e64c}

Gets the index and value of an element in the array that is closest to the given value

Args:
    array (t.Union[t.List, np.ndarray, pandas.Series]): The array
    value (t.Any): The value

Returns:
    tuple: A 2-tuple with the index and the value

Raises:
    TypeError: Wrong array type provided
    ValueError: Array with wrong dimensions provided
    TypeError: Provided value is not a scalar numeric value

#### `public t.Any `[`get_nearest_value`](#scinum_8py_1af4d2fb274201f22a722e52d6035be2fd)`(t.Union array,t.Any value)` {#scinum_8py_1af4d2fb274201f22a722e52d6035be2fd}

Gets the value of an element in the array that is closest to the given value

Args:
    array (t.Union[t.List, np.ndarray, pandas.Series]): The array
    value (t.Any): The value

Returns:
    t.Any: The nearest value

#### `public int `[`get_nearest_index`](#scinum_8py_1ac89f76813ec599e8cba22671b8cac52a)`(t.Union array,t.Any value)` {#scinum_8py_1ac89f76813ec599e8cba22671b8cac52a}

Gets the index of an element in the array that is closest to the given value

Args:
    array (t.Union[t.List, np.ndarray, pandas.Series]): [description]
    value (t.Any): [description]

Returns:
    int: [description]

#### `public np.ndarray `[`awgn_like`](#scinum_8py_1a9381e358d7a0d8befb5f506542587fae)`(np.ndarray like,float sigma,float mu)` {#scinum_8py_1a9381e358d7a0d8befb5f506542587fae}

Produces a gaussian-distributed random array of same shape as a given array

Args:
    like (np.ndarray): The array (only shape considered)

Keyword Args:
    sigma (float): The standard deviation of the normal distribution (default: {1.0})
    mu (float): The mean of the distribution (default: {0.0})

Returns:
    np.ndarray: The AWGN array

#### `public np.ndarray `[`uniform_like`](#scinum_8py_1ae0b955c22ff59f7ec5441f4d6f05d95c)`(np.ndarray like,float low,float high)` {#scinum_8py_1ae0b955c22ff59f7ec5441f4d6f05d95c}

Produce a uniform-distributed random array of same shape as a given array

Args:
    like (np.ndarray): The array (only shape considered)

Keyword Args:
    low (float): The lower limit of the uniform distribution (default: {0.0})
    high (float): The upper limit of the uniform distribution (default: {1.0})

Returns:
    np.ndarray: The uniform-distributed random array

#### `public np.ndarray `[`add_awgn_noise`](#scinum_8py_1abc7346ba6e8765c0c547ab4f828e38bd)`(np.ndarray to,float sigma,float mu)` {#scinum_8py_1abc7346ba6e8765c0c547ab4f828e38bd}

Adds gaussian noise to an array

Args:
    to (np.ndarray): The array to which the noise will be added

Keyword Args:
    sigma (float): The standard deviation of the normal distribution (default: {1.0})
    mu (float): The mean of the distribution (default: {0.0})

Returns:
    np.ndarray: The given array with added noise

#### `public def `[`add_uniform_noise`](#scinum_8py_1a1ae2d9f0c5a1c4f6f838eaf7e4621ccd)`(np.ndarray to,float low,float high)` {#scinum_8py_1a1ae2d9f0c5a1c4f6f838eaf7e4621ccd}

Adds uniform noise to an array
    Args:
    to (np.ndarray): The array to which the noise will be added

Keyword Args:
    low (float): The lower limit of the uniform distribution (default: {0.0})
    high (float): The upper limit of the uniform distribution (default: {1.0})

Returns:
    np.ndarray: The given array with added noise

#### `public int `[`count_errors`](#scinum_8py_1ade2824fa24ea2ba727fda9ac6385d344)`(np.ndarray left,np.ndarray right)` {#scinum_8py_1ade2824fa24ea2ba727fda9ac6385d344}

Counts differences between two arrays of same shape

Args:
    left (np.ndarray): The left array
    right (np.ndarray): The right array

Returns:
    int: The number of errors/differences

Raises:
    ValueError: The arrays are of different shape

#### `public int `[`count_errors_robust`](#scinum_8py_1ab6ea17cc27cd4a306fc8d97082825e8b)`(np.ndarray left,np.ndarray right)` {#scinum_8py_1ab6ea17cc27cd4a306fc8d97082825e8b}

Count differences between two row or column vectors

Args:
    left (np.ndarray): The left array
    right (np.ndarray): The right array

Returns:
    int: The number of element differences and/or length differences

Raises:
    ValueError: Wrong array dimensions provided

#### `public bool `[`is_fitted`](#scinum_8py_1af9f4516cb1b28ab66b9a2ae48d52d5b0)`(sklearn.base.BaseEstimator estimator)` {#scinum_8py_1af9f4516cb1b28ab66b9a2ae48d52d5b0}

Is an estimator fitted?

Args:
    estimator (sklearn.base.BaseEstimator): the estimator to check

Returns:
    bool: True if fitted, False otherwise

#### `public np.ndarray `[`interleave`](#scinum_8py_1abbedca77073492733bd2767f0de4cb0d)`(np.ndarray array,int n)` {#scinum_8py_1abbedca77073492733bd2767f0de4cb0d}

Interleaves rows of an array

Args:
    array (np.ndarray): The array to interleave
    n (int): The number of consecutive rows to interleave

Returns:
    np.ndarray: The interleaved array of shape (array[0] / n, array[1] * n)

Details:
    The interleaving is as follows:

    Given a 4x4 array:
    >>> array = np.arange(0, 16).reshape(4, 4)
    >>> array
    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11],
           [12, 13, 14, 15]])

    Interleaving with n=2 will produce a 8x2 array:
    >>> interleave(array, 2)
    array([[ 0,  4,  1,  5,  2,  6,  3,  7],
           [ 8, 12,  9, 13, 10, 14, 11, 15]])

#### `public np.ndarray `[`interleave_split`](#scinum_8py_1a7c67a5e30325aa40ec1857b98a85c084)`(np.ndarray array,int n)` {#scinum_8py_1a7c67a5e30325aa40ec1857b98a85c084}

Interleaves rows of an array and splits into multiple arrays

Args:
    array (np.ndarray): The array to interleave and split
    n (int): The number of consecutive rows to interleave

Returns:
    np.ndarray: The interleaved and split array

#### `public bool `[`is_binary`](#scinum_8py_1a317c77511d381be9c6f92800a2ae904d)`(np.ndarray array)` {#scinum_8py_1a317c77511d381be9c6f92800a2ae904d}

Checks if input array is binary

Args:
    array (np.ndarray): The array

Returns:
    bool: True if contains only 0s and 1s

#### `public np.uint64 `[`pack_bits`](#scinum_8py_1ad1bffaeb098c0bfde81214773dd70d56)`(np.ndarray array)` {#scinum_8py_1ad1bffaeb098c0bfde81214773dd70d56}

'Packs' a binary array into an unsigned integer

Similar to np.packbits, but packs up to uint64, not uint8.

Args:
    array (np.ndarray): The binary array to 'pack'

Returns:
    np.uint64: The packed array

#### `public np.uint64 `[`pack_bits_fast`](#scinum_8py_1ad3410c555c4c5295dace95718491a159)`(np.ndarray array)` {#scinum_8py_1ad3410c555c4c5295dace95718491a159}

'Packs' a binary array into an unsigned integer without value/type checks

Similar to np.packbits, but packs up to uint64, not uint8.

Args:
    array (np.ndarray): The binary array to 'pack'

Returns:
    np.uint64: The packed array

#### `public np.ndarray `[`pad_split`](#scinum_8py_1ae2cda5b14ac09067a7a5b6cc1d2a7240)`(np.ndarray array,np.uint n,* pad)` {#scinum_8py_1ae2cda5b14ac09067a7a5b6cc1d2a7240}

Split a binary array int fixed-sized chunks while 0-padding unequal splits

Args:
    array (np.ndarray): The binary array
    n (np.uint): chunk size

Returns:
    np.ndarray: The split (and padded) array of shape (ceil(array.size/n), n)

#### `public np.ndarray `[`pack_array`](#scinum_8py_1a3b088279886a3ff1944c03265b6f06ea)`(np.ndarray array,np.uint n,* pad)` {#scinum_8py_1a3b088279886a3ff1944c03265b6f06ea}

Packs a binary array into unsigned integers of bit width n

Args:
    array (np.ndarray): The binary array to pack
    n (np.uint): The bit width / chunk size

Returns:
    np.ndarray: The packed array of size np.ceil(array.size / n)

#### `public np.ndarray `[`unpack_bits`](#scinum_8py_1a67344a6c3b8c56267b09f8e1e436519c)`(np.uint value,np.uint n)` {#scinum_8py_1a67344a6c3b8c56267b09f8e1e436519c}

Unpacks an unsigned integer into an array of bits

Args:
    value (np.uint): The value to unpack
    n (np.uint, optional): The number of bits

Returns:
    np.ndarray: The value unpacked into a binary array

Raises:
    ValueError: Value cannot be unpacked because it cannot be represented with n bits

#### `public np.ndarray `[`unpack_bits_fast`](#scinum_8py_1a60b0588023450c31ba84a9ac7af00498)`(np.uint value,np.uint n)` {#scinum_8py_1a60b0588023450c31ba84a9ac7af00498}

Unpacks an unsigned integer into an array of bits without value/type checks

Args:
    value (np.uint): The value to unpack
    n (np.uint, optional): The number of bits

Returns:
    np.ndarray: The value unpacked into a binary array

#### `public np.ndarray `[`unpack_array`](#scinum_8py_1ab614041e85ef0577a313ee9a768a3694)`(np.ndarray array,np.uint n)` {#scinum_8py_1ab614041e85ef0577a313ee9a768a3694}

Unpacks an array of unsigned integers into a 2-d array of bits

Args:
    array (np.ndarray): The array to unpack
    n (np.uint): The number of bits

Returns:
    np.ndarray: The unpacked array of shape (array.size, n)

Raises:
    ValueError: An array of unsuitable shape is passed

#### `public t.Tuple[np.ndarray, np.ndarray] `[`find_ramp_edges`](#scinum_8py_1a711c4a6ed4f861bf0a7fda3b622c813e)`(np.ndarray trace,*float threshold,int roll,callable roll_fun,object kernel,str method,bool _debug)` {#scinum_8py_1a711c4a6ed4f861bf0a7fda3b622c813e}

Gets indexes of falling and rising ramps in a sample trace using convolution with
   an edge detection kernel

Args:
    trace (np.ndarray): The 1-d array to work on
    threshold (float, optional): Multiplier for lower and upper detection limits
    roll (int, optional): Number of samples to perform rolling preprocessing on
    roll_fun (callable, optional): The preprocessing function to apply
    kernel (object, optional): The ramp-detection kernel
    method (str, optional): Method, either "local" or "gradient"
    _debug (bool, optional): Output additional data for debugging purposes?

Returns:
    t.Tuple[np.ndarray, np.ndarray]: The falling and rising ramp edges

#### `public  `[`split_into_contiguous_ranges`](#scinum_8py_1a66c4f32ab7d6ac863fa484cbe0ee7884)`(np.ndarray trace,*int step_threshold)` {#scinum_8py_1a66c4f32ab7d6ac863fa484cbe0ee7884}

Splits an array into ranges of similar values

Args:
    trace (np.ndarray): The array to split
    step_threshold (int, optional): The splitting threshold. Defaults to 1.

Returns:
    [np.array]: The array of split ranges

#### `public pandas.DataFrame `[`get_fft`](#scinum_8py_1a552725ded78697868160a9b629c1e533)`(pandas.DataFrame data,*t.Optional timescale,bool demean,bool melt)` {#scinum_8py_1a552725ded78697868160a9b629c1e533}

Gets the fft(s) of data in a timestamps & values DataFrame

Args:
    data (pandas.DataFrame): The data, including timestamps & values
    timescale (t.Optional[float], optional): If provided, rescales the timing column.
        Otherwise, timestamps in seconds are assumed.
    demean (bool, optional): Subtract the mean from the values?
    melt (bool, optional): Output a melted data frame?

Returns:
    pandas.DataFrame: The data frame, with FFT values for a range of frequencies. The
        DataFrame holds the original columns, and a frequency column. Optionally, this can be
        melted, with the frequency as the id variable, and values 'melted' into a 'variable'
        column.

#### `public pandas.DataFrame `[`get_welch`](#scinum_8py_1a35b3bc912ad0fe1ac12cc1ba77aeaf47)`(pandas.DataFrame data,t.Optional window_size,str window,*t.Optional timescale,bool demean,bool melt)` {#scinum_8py_1a35b3bc912ad0fe1ac12cc1ba77aeaf47}

Gets the fft(s) of data in a timestamps & values DataFrame using the Welch method

Args:
    data (pandas.DataFrame): The data, including timestamps & values
    window_size (t.Optional[int], optional): The window size
    window (str, optional): The window name
    timescale (t.Optional[float], optional): If provided, rescales the timing column.
        Otherwise, timestamps in seconds are assumed.
    demean (bool, optional): Subtract the mean from the values?
    melt (bool, optional): Output a melted data frame?

Returns:
    pandas.DataFrame: The data frame, with FFT values for a range of frequencies. The
        DataFrame holds the original columns, and a frequency column. Optionally, this can be
        melted, with the frequency as the id variable, and values 'melted' into a 'variable'
        column.

# namespace `exot::util::timeout` {#namespaceexot_1_1util_1_1timeout}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::util::timeout::SignalTimeout`](#classexot_1_1util_1_1timeout_1_1SignalTimeout) | A timeout context decorator/manager using POSIX signal's
`class `[`exot::util::timeout::ThreadTimeout`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout) | Timeout context manager and decorator implemented with threads and condition variables
`class `[`exot::util::timeout::TimeoutException`](#classexot_1_1util_1_1timeout_1_1TimeoutException) | 

# class `exot::util::timeout::SignalTimeout` {#classexot_1_1util_1_1timeout_1_1SignalTimeout}

```
class exot::util::timeout::SignalTimeout
  : public ContextDecorator
```  

A timeout context decorator/manager using POSIX signal's

Caveats:
    Can only run in the main thread due to using POSIX signals!

Attributes:
    duration (int): the timeout duration in seconds
    throwing (bool): does it throw when timed out?
    timed_out (bool): has a time out occured?

Examples:
    >>> from time import sleep

    >>> with Timeout(1):
    >>>    sleep(1.2)
    >>>    print("This message is never printed!")

    >>> with Timeout(1) as tm:
    >>>     sleep(1.2)
    >>> tm.timed_out
    True

    >>> @Timeout(1)
    >>> def function_with_timeout(seconds: float):
    >>>     sleep(seconds)
            return 0
    >>> function_with_timeout(0.5)
    0
    >>> function_with_timeout(1.5)
    None

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`timed_out`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a04b48d1d2de1c0dfcc64abea34310dbf) | 
`public def `[`__init__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1abcde37d56206dfada46a6c28eea03178)`(self,int duration,bool throwing)` | 
`public str `[`__repr__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1aaeac2176cb7b7a7151f8a3fef9a4fbbd)`(self)` | 
`public def `[`__handler__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a245bb576e1c25138633767005c771eb0)`(self,int number,FrameType frame)` | 
`public object `[`__enter__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a970af0acba45923a3c7e7903ad407d2e)`(self)` | 
`public Union[NoReturn, bool] `[`__exit__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a319a7e09bde5ac86e933971e6abcaf62)`(self,type exc_type,Any exc_val,TracebackType exc_tb)` | 

## Members

#### `public  `[`timed_out`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a04b48d1d2de1c0dfcc64abea34310dbf) {#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a04b48d1d2de1c0dfcc64abea34310dbf}

#### `public def `[`__init__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1abcde37d56206dfada46a6c28eea03178)`(self,int duration,bool throwing)` {#classexot_1_1util_1_1timeout_1_1SignalTimeout_1abcde37d56206dfada46a6c28eea03178}

#### `public str `[`__repr__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1aaeac2176cb7b7a7151f8a3fef9a4fbbd)`(self)` {#classexot_1_1util_1_1timeout_1_1SignalTimeout_1aaeac2176cb7b7a7151f8a3fef9a4fbbd}

#### `public def `[`__handler__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a245bb576e1c25138633767005c771eb0)`(self,int number,FrameType frame)` {#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a245bb576e1c25138633767005c771eb0}

#### `public object `[`__enter__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a970af0acba45923a3c7e7903ad407d2e)`(self)` {#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a970af0acba45923a3c7e7903ad407d2e}

#### `public Union[NoReturn, bool] `[`__exit__`](#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a319a7e09bde5ac86e933971e6abcaf62)`(self,type exc_type,Any exc_val,TracebackType exc_tb)` {#classexot_1_1util_1_1timeout_1_1SignalTimeout_1a319a7e09bde5ac86e933971e6abcaf62}

# class `exot::util::timeout::ThreadTimeout` {#classexot_1_1util_1_1timeout_1_1ThreadTimeout}

```
class exot::util::timeout::ThreadTimeout
  : public ContextDecorator
```  

Timeout context manager and decorator implemented with threads and condition variables

Attributes:
    duration (bool): The timeout duration in seconds
    throwing (bool):  Should throw on timeout?
    timed_out (bool): Is timed out?
    _cv_r (bool): The outcome on condition variable wait
    _cv (Condition): The condition variable
    _thread (Thread): The timeout/waiting thread

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`timed_out`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a33e0a6c1f052b2a3c52e84cd7a70c258) | 
`public def `[`__init__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a23be9b0e64aa11d44dc782170d623f41)`(self,float duration,bool throwing)` | Initialises the timeout context decorator
`public str `[`__repr__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a511d610c0e157ae6bc4fced00d4fafb6)`(self)` | 
`public None `[`__handler__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a6b4928b28d26bc1c69a71224893f4bb5)`(self)` | 
`public object `[`__enter__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1ae8041683b4e92a5a5d4ade661b6fe0ea)`(self)` | 
`public def `[`__exit__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a11feb81936930185e97fa551226807db)`(self,type exc_type,Any exc_val,TracebackType exc_tb)` | 

## Members

#### `public  `[`timed_out`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a33e0a6c1f052b2a3c52e84cd7a70c258) {#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a33e0a6c1f052b2a3c52e84cd7a70c258}

#### `public def `[`__init__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a23be9b0e64aa11d44dc782170d623f41)`(self,float duration,bool throwing)` {#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a23be9b0e64aa11d44dc782170d623f41}

Initialises the timeout context decorator

Args:
    duration (float): The timeout duration in seconds
    throwing (bool, optional): Should throw in timeout?

#### `public str `[`__repr__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a511d610c0e157ae6bc4fced00d4fafb6)`(self)` {#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a511d610c0e157ae6bc4fced00d4fafb6}

#### `public None `[`__handler__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a6b4928b28d26bc1c69a71224893f4bb5)`(self)` {#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a6b4928b28d26bc1c69a71224893f4bb5}

#### `public object `[`__enter__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1ae8041683b4e92a5a5d4ade661b6fe0ea)`(self)` {#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1ae8041683b4e92a5a5d4ade661b6fe0ea}

#### `public def `[`__exit__`](#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a11feb81936930185e97fa551226807db)`(self,type exc_type,Any exc_val,TracebackType exc_tb)` {#classexot_1_1util_1_1timeout_1_1ThreadTimeout_1a11feb81936930185e97fa551226807db}

# class `exot::util::timeout::TimeoutException` {#classexot_1_1util_1_1timeout_1_1TimeoutException}

```
class exot::util::timeout::TimeoutException
  : public Exception
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# namespace `exot::util::wrangle` {#namespaceexot_1_1util_1_1wrangle}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`map_factory`](#wrangle_8py_1a814b2065efd754639180732cc0bdc560)`(where,which)`            | 
`public def `[`filter_factory`](#wrangle_8py_1a6420614a17a59527e42f5558bf402811)`(where,which,value)`            | 
`public str `[`run_path_formatter`](#wrangle_8py_1a748af9a5e834e1410acd8a4427c8b4f1)`(*t.Hashable param)`            | Produce a formatted path from parameters
`public t.Tuple `[`run_path_unformatter`](#wrangle_8py_1ab5bbbcf193096caef44e89987f0e9522)`(Path path)`            | Produce parameters from a formatted path
`public Path `[`repetition_formatter`](#wrangle_8py_1aabdd41491dc29b8bcd8b0b2bddc90c74)`(int rep)`            | 
`public Path `[`app_configfile_formatter`](#wrangle_8py_1acaaa191d1664aadfbb6175e6cc349ac8)`(str app)`            | Produce a formatted json filename
`public Path `[`app_log_formatter`](#wrangle_8py_1ac4b5e51811f6ad4c23ac8b9c64e8af43)`(str app,bool dbg)`            | Produce a formatted log filename
`public Path `[`generic_log_formatter`](#wrangle_8py_1af3320b42a82ed31a573e03caa05f8b08)`(str app,bool dbg)`            | Produce a formatted log filename
`public (int, str, bool) `[`log_path_unformatter`](#wrangle_8py_1acb1d45f7868faaf83afe5491cd1fdd6f)`(Path path)`            | Produce a formatted log filename
`public dict `[`parse_header_entry`](#wrangle_8py_1a21287990ac20a4d8996d5aea6ac85635)`(str entry)`            | Parses a header entry
`public t.List[dict] `[`parse_header`](#wrangle_8py_1a94a00479a2bfe7511846a2cd38b068ca)`(t.Union header)`            | Parses the entire header
`public dict `[`parse_and_describe`](#wrangle_8py_1aa0a1d5ad11860e56709712662d3cf2a1)`(t.Union header)`            | Parses and describes the header
`public pd.Series `[`make_data_filter_array`](#wrangle_8py_1ad679cbe2172d5d727a65af4af7c0eade)`(t.Union data,op,**t.Any queries)`            | Make an array to filter Pandas data using logical and operation
`public t.Union[pd.DataFrame, pd.Series] `[`filter_data`](#wrangle_8py_1abca9f64fcf47794b63948cf1ee59fb5d)`(t.Union data,**t.Any queries)`            | Filters Pandas data using queries
`public t.T `[`filter_with_callable`](#wrangle_8py_1ae2f49f8716ce3c11b82042981719e365)`(t.T data,t.Callable callable)`            | Filters data with a callable
`public t.Tuple `[`get_unique_column_combinations`](#wrangle_8py_1a116e7749473a230f4edfb4245dd69cef)`(pd.DataFrame data,columns)`            | Gets the unique combinations of columns
`class `[`exot::util::wrangle::Matcher`](#classexot_1_1util_1_1wrangle_1_1Matcher) | The Matcher can be used in DataFrame selection, thanks to its `__call__` method.

## Members

#### `public def `[`map_factory`](#wrangle_8py_1a814b2065efd754639180732cc0bdc560)`(where,which)` {#wrangle_8py_1a814b2065efd754639180732cc0bdc560}

#### `public def `[`filter_factory`](#wrangle_8py_1a6420614a17a59527e42f5558bf402811)`(where,which,value)` {#wrangle_8py_1a6420614a17a59527e42f5558bf402811}

#### `public str `[`run_path_formatter`](#wrangle_8py_1a748af9a5e834e1410acd8a4427c8b4f1)`(*t.Hashable param)` {#wrangle_8py_1a748af9a5e834e1410acd8a4427c8b4f1}

Produce a formatted path from parameters

Args:
    param (t.Hashable): a sequence of hashable params

..note::
    The function aims to proide a unified way of translating between parameters
    in phases and strings

    Since only hashable types can be used as dict keys, only hashable types
    are allowed in the run path. Strings should be stripped. If resulting path
    has whitespace in it, an exception will be thrown.

    Int values are fixed to 5 digits, with leading zeros.

    While 'phases' can have have different depths, we will tentatively constrain
    the file hierarchy depth to 1. For example: these are valid paths:

    >>> run_path_formatter("run", 1) # run_00001
    >>> run_path_formatter("eval", 123) # eval_00123
    >>> run_path_formatter("run", "param1", 1) # run_param1_00001

    These are some of the invalid paths:

    >>> run_path_formatter("train", ("float", 0.1))
    >>> run_path_formatter("train", {1: 1})
    >>> run_path_formatter("train", [1, 2])

#### `public t.Tuple `[`run_path_unformatter`](#wrangle_8py_1ab5bbbcf193096caef44e89987f0e9522)`(Path path)` {#wrangle_8py_1ab5bbbcf193096caef44e89987f0e9522}

Produce parameters from a formatted path

#### `public Path `[`repetition_formatter`](#wrangle_8py_1aabdd41491dc29b8bcd8b0b2bddc90c74)`(int rep)` {#wrangle_8py_1aabdd41491dc29b8bcd8b0b2bddc90c74}

#### `public Path `[`app_configfile_formatter`](#wrangle_8py_1acaaa191d1664aadfbb6175e6cc349ac8)`(str app)` {#wrangle_8py_1acaaa191d1664aadfbb6175e6cc349ac8}

Produce a formatted json filename

#### `public Path `[`app_log_formatter`](#wrangle_8py_1ac4b5e51811f6ad4c23ac8b9c64e8af43)`(str app,bool dbg)` {#wrangle_8py_1ac4b5e51811f6ad4c23ac8b9c64e8af43}

Produce a formatted log filename

#### `public Path `[`generic_log_formatter`](#wrangle_8py_1af3320b42a82ed31a573e03caa05f8b08)`(str app,bool dbg)` {#wrangle_8py_1af3320b42a82ed31a573e03caa05f8b08}

Produce a formatted log filename

#### `public (int, str, bool) `[`log_path_unformatter`](#wrangle_8py_1acb1d45f7868faaf83afe5491cd1fdd6f)`(Path path)` {#wrangle_8py_1acb1d45f7868faaf83afe5491cd1fdd6f}

Produce a formatted log filename

#### `public dict `[`parse_header_entry`](#wrangle_8py_1a21287990ac20a4d8996d5aea6ac85635)`(str entry)` {#wrangle_8py_1a21287990ac20a4d8996d5aea6ac85635}

Parses a header entry

Args:
    entry (str): The header entry

Returns:
    dict: The parsed entry (dict with keys: module, value, dimension, unit)

#### `public t.List[dict] `[`parse_header`](#wrangle_8py_1a94a00479a2bfe7511846a2cd38b068ca)`(t.Union header)` {#wrangle_8py_1a94a00479a2bfe7511846a2cd38b068ca}

Parses the entire header

Args:
    header (t.Union[t.Iterable, str]): The header

Returns:
    t.List[dict]: A list of parsed header entries

#### `public dict `[`parse_and_describe`](#wrangle_8py_1aa0a1d5ad11860e56709712662d3cf2a1)`(t.Union header)` {#wrangle_8py_1aa0a1d5ad11860e56709712662d3cf2a1}

Parses and describes the header

Args:
    header (t.Union[t.Iterable, str]): The header

Returns:
    dict: A dict with available modules, quantities, and methods

#### `public pd.Series `[`make_data_filter_array`](#wrangle_8py_1ad679cbe2172d5d727a65af4af7c0eade)`(t.Union data,op,**t.Any queries)` {#wrangle_8py_1ad679cbe2172d5d727a65af4af7c0eade}

Make an array to filter Pandas data using logical and operation

Args:
    data (t.Union[pd.DataFrame, pd.Series]): The data to filter
    **queries (t.Any): The queries

Returns:
    pd.Series: The boolean array for row selection

Raises:
    TypeError: Wrong type supplied
    ValueError: Unavailable key specified

#### `public t.Union[pd.DataFrame, pd.Series] `[`filter_data`](#wrangle_8py_1abca9f64fcf47794b63948cf1ee59fb5d)`(t.Union data,**t.Any queries)` {#wrangle_8py_1abca9f64fcf47794b63948cf1ee59fb5d}

Filters Pandas data using queries

Args:
    data (t.Union[pd.DataFrame, pd.Series]): The data
    **queries (t.Any): The queries

Returns:
    t.Union[pd.DataFrame, pd.Series]: The filtered data frame

Raises:
    TypeError: Wrong type supplied to 'data'

#### `public t.T `[`filter_with_callable`](#wrangle_8py_1ae2f49f8716ce3c11b82042981719e365)`(t.T data,t.Callable callable)` {#wrangle_8py_1ae2f49f8716ce3c11b82042981719e365}

Filters data with a callable

Args:
    data (t.T): The data
    callable (t.Callable): The callable

Returns:
    t.T: The filtered data

#### `public t.Tuple `[`get_unique_column_combinations`](#wrangle_8py_1a116e7749473a230f4edfb4245dd69cef)`(pd.DataFrame data,columns)` {#wrangle_8py_1a116e7749473a230f4edfb4245dd69cef}

Gets the unique combinations of columns

Args:
    data (pd.DataFrame): The data frame
    columns (list, optional): The columns to choose. Defaults to [].

Raises:
    TypeError: Wrong type provided to 'data'

Returns:
    t.Tuple: The unique combinations of columns

# class `exot::util::wrangle::Matcher` {#classexot_1_1util_1_1wrangle_1_1Matcher}

The Matcher can be used in DataFrame selection, thanks to its `__call__` method.

For details on how to use a Callable for DataFrame selection, see:
<https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#selection-by-callable>

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1util_1_1wrangle_1_1Matcher_1ae73fbaea55abf47b4b2c09e34cb13d95)`(self,str quantity,str method,list values,list dimensions)` | Instantiate a Matcher
`public str `[`__repr__`](#classexot_1_1util_1_1wrangle_1_1Matcher_1afd3e522c57f5de5d637c3cf483815d51)`(self)` | Represent the Matcher object
`public `[`Matcher`](#classexot_1_1util_1_1wrangle_1_1Matcher)` `[`from_dict`](#classexot_1_1util_1_1wrangle_1_1Matcher_1a1d56c089b3865bc40fd73896c6926e3f)`(cls,dict src)` | Instantiates a Matcher from a dictionary
`public t.NoReturn `[`validate`](#classexot_1_1util_1_1wrangle_1_1Matcher_1a76a0efec09a7406306f2e9051baa8067)`(self,t.Union df)` | Check if the provided parameters can be found in the input DataFrame
`public bool `[`matches`](#classexot_1_1util_1_1wrangle_1_1Matcher_1ae5e6a6d840b6733250df6403673b3a29)`(self,str entry)` | Check if a column matches the parameters
`public bool `[`is_timestamp`](#classexot_1_1util_1_1wrangle_1_1Matcher_1aa413d345e35760775a3172ef94483c9b)`(self,str entry)` | Check if a column is a timestamp column
`public str `[`get_timestamp_column`](#classexot_1_1util_1_1wrangle_1_1Matcher_1afd4edbfcdd5bc0c9ff63c82a34f0ced9)`(self,list columns)` | Get the timestamp column
`public t.List[str] `[`__call__`](#classexot_1_1util_1_1wrangle_1_1Matcher_1af09dbf9596ad05d7c8fdb5d24421f578)`(self,t.Union df)` | Return a list of column names that match the parameters

## Members

#### `public def `[`__init__`](#classexot_1_1util_1_1wrangle_1_1Matcher_1ae73fbaea55abf47b4b2c09e34cb13d95)`(self,str quantity,str method,list values,list dimensions)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1ae73fbaea55abf47b4b2c09e34cb13d95}

Instantiate a Matcher

Args:
    quantity (str): a desired quantity
    method (str): a desired method for the quantity
    values (list): a set of desired values for the quantity and method
    dimensions (list): a set of desired dimensions of the values

#### `public str `[`__repr__`](#classexot_1_1util_1_1wrangle_1_1Matcher_1afd3e522c57f5de5d637c3cf483815d51)`(self)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1afd3e522c57f5de5d637c3cf483815d51}

Represent the Matcher object

Returns:
    str: a repr-like string representation

#### `public `[`Matcher`](#classexot_1_1util_1_1wrangle_1_1Matcher)` `[`from_dict`](#classexot_1_1util_1_1wrangle_1_1Matcher_1a1d56c089b3865bc40fd73896c6926e3f)`(cls,dict src)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1a1d56c089b3865bc40fd73896c6926e3f}

Instantiates a Matcher from a dictionary

Args:
    src (dict): The dictionary

Returns:
    Matcher: The Matcher instance

#### `public t.NoReturn `[`validate`](#classexot_1_1util_1_1wrangle_1_1Matcher_1a76a0efec09a7406306f2e9051baa8067)`(self,t.Union df)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1a76a0efec09a7406306f2e9051baa8067}

Check if the provided parameters can be found in the input DataFrame

Args:
    df (t.Union[pd.DataFrame, pd.Series, pd.Panel]): the DataFrame

Raises:
    MatchNotFound: If a match could not be found

#### `public bool `[`matches`](#classexot_1_1util_1_1wrangle_1_1Matcher_1ae5e6a6d840b6733250df6403673b3a29)`(self,str entry)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1ae5e6a6d840b6733250df6403673b3a29}

Check if a column matches the parameters

Args:
    entry (str): a column name

Returns:
    bool: True if matches, False otherwise

#### `public bool `[`is_timestamp`](#classexot_1_1util_1_1wrangle_1_1Matcher_1aa413d345e35760775a3172ef94483c9b)`(self,str entry)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1aa413d345e35760775a3172ef94483c9b}

Check if a column is a timestamp column

Args:
    entry (str): a column name

Returns:
    bool: True if contains a timestamp, False otherwise

#### `public str `[`get_timestamp_column`](#classexot_1_1util_1_1wrangle_1_1Matcher_1afd4edbfcdd5bc0c9ff63c82a34f0ced9)`(self,list columns)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1afd4edbfcdd5bc0c9ff63c82a34f0ced9}

Get the timestamp column

Args:
    columns (list): DataFrame columns

Returns:
    str: The timestamp column

Raises:
    ValueError: If the DataFrame doesn't have a timestamp column

#### `public t.List[str] `[`__call__`](#classexot_1_1util_1_1wrangle_1_1Matcher_1af09dbf9596ad05d7c8fdb5d24421f578)`(self,t.Union df)` {#classexot_1_1util_1_1wrangle_1_1Matcher_1af09dbf9596ad05d7c8fdb5d24421f578}

Return a list of column names that match the parameters

Args:
    df (t.Union[pd.DataFrame, pd.Series, pd.Panel]): the DataFrame

Returns:
    t.List[str]: a list of column names

Generated by [Moxygen](https://sourcey.com/moxygen)