[:back:](/home)
---

# Platform specific primitives

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::primitives`](#namespaceexot_1_1primitives) | 

# namespace `exot::primitives` {#namespaceexot_1_1primitives}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public inline bool `[`is_fd`](#perf__clock_8h_1a4658b62905c14ff97879aef063a403a4)`(long fd)`            | Checks if a number is a valid file descriptor.
`class `[`exot::primitives::perf_clock`](#classexot_1_1primitives_1_1perf__clock) | A clock source using hardware CPU cycles accessed via Linux'es performance counters.
`class `[`exot::primitives::perf_sw_clock`](#classexot_1_1primitives_1_1perf__sw__clock) | A clock source using hardware CPU cycles accessed via Linux'es performance counters.
`struct `[`exot::primitives::__fenced_clock`](#structexot_1_1primitives_1_1____fenced__clock) | 
`struct `[`exot::primitives::__fenced_tsc`](#structexot_1_1primitives_1_1____fenced__tsc) | 
`struct `[`exot::primitives::__strong_fenced_clock`](#structexot_1_1primitives_1_1____strong__fenced__clock) | 
`struct `[`exot::primitives::__strong_fenced_tsc`](#structexot_1_1primitives_1_1____strong__fenced__tsc) | 
`struct `[`exot::primitives::fd_deleter`](#structexot_1_1primitives_1_1fd__deleter) | A custom deleter for file descriptors to be used with unique pointers.
`struct `[`exot::primitives::fenced_clock`](#structexot_1_1primitives_1_1fenced__clock) | 
`struct `[`exot::primitives::fenced_tsc`](#structexot_1_1primitives_1_1fenced__tsc) | 
`struct `[`exot::primitives::is_time_stamp_counter`](#structexot_1_1primitives_1_1is__time__stamp__counter) | Is the provided type a time stamp counter?
`struct `[`exot::primitives::is_time_stamp_counter< T, std::void_t< decltype(T::start), decltype(T::stop)> >`](#structexot_1_1primitives_1_1is__time__stamp__counter_3_01T_00_01std_1_1void__t_3_01decltype_07T_ff83b96cb989fe7af428ada26c85f5e3) | 
`struct `[`exot::primitives::plain_clock`](#structexot_1_1primitives_1_1plain__clock) | 
`struct `[`exot::primitives::plain_tsc`](#structexot_1_1primitives_1_1plain__tsc) | 
`struct `[`exot::primitives::TimeStampCounter`](#structexot_1_1primitives_1_1TimeStampCounter) | Base class for timestamp counters.

## Members

#### `public inline bool `[`is_fd`](#perf__clock_8h_1a4658b62905c14ff97879aef063a403a4)`(long fd)` {#perf__clock_8h_1a4658b62905c14ff97879aef063a403a4}

Checks if a number is a valid file descriptor.

#### Parameters
* `fd` The file descriptor 

#### Returns
true The number represents a valid file descriptor 

#### Returns
false Otherwise.

# class `exot::primitives::perf_clock` {#classexot_1_1primitives_1_1perf__clock}

A clock source using hardware CPU cycles accessed via Linux'es performance counters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`duration`](#classexot_1_1primitives_1_1perf__clock_1a3d088987cd8bb9d7d906f8ada8ee0091) | 
`typedef `[`rep`](#classexot_1_1primitives_1_1perf__clock_1a024863eade08e6b37b8fa0b4263f8c02) | 
`typedef `[`period`](#classexot_1_1primitives_1_1perf__clock_1a69225862d07aa61f408d4d92a960a30a) | 
`typedef `[`time_point`](#classexot_1_1primitives_1_1perf__clock_1a6aaec16b80a698ba717cbe2d60dc91aa) | 

## Members

#### `typedef `[`duration`](#classexot_1_1primitives_1_1perf__clock_1a3d088987cd8bb9d7d906f8ada8ee0091) {#classexot_1_1primitives_1_1perf__clock_1a3d088987cd8bb9d7d906f8ada8ee0091}

#### `typedef `[`rep`](#classexot_1_1primitives_1_1perf__clock_1a024863eade08e6b37b8fa0b4263f8c02) {#classexot_1_1primitives_1_1perf__clock_1a024863eade08e6b37b8fa0b4263f8c02}

#### `typedef `[`period`](#classexot_1_1primitives_1_1perf__clock_1a69225862d07aa61f408d4d92a960a30a) {#classexot_1_1primitives_1_1perf__clock_1a69225862d07aa61f408d4d92a960a30a}

#### `typedef `[`time_point`](#classexot_1_1primitives_1_1perf__clock_1a6aaec16b80a698ba717cbe2d60dc91aa) {#classexot_1_1primitives_1_1perf__clock_1a6aaec16b80a698ba717cbe2d60dc91aa}

# class `exot::primitives::perf_sw_clock` {#classexot_1_1primitives_1_1perf__sw__clock}

A clock source using hardware CPU cycles accessed via Linux'es performance counters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`duration`](#classexot_1_1primitives_1_1perf__sw__clock_1aaaf35d0e0027ef3043345870b8dcbf06) | 
`typedef `[`rep`](#classexot_1_1primitives_1_1perf__sw__clock_1a6768a32e719e751b4de1d367a109a9c6) | 
`typedef `[`period`](#classexot_1_1primitives_1_1perf__sw__clock_1a7f6300c777ad29dfb4da4c11d0836a03) | 
`typedef `[`time_point`](#classexot_1_1primitives_1_1perf__sw__clock_1ab7bd8663e2dd06a3b414e679beb97ca8) | 

## Members

#### `typedef `[`duration`](#classexot_1_1primitives_1_1perf__sw__clock_1aaaf35d0e0027ef3043345870b8dcbf06) {#classexot_1_1primitives_1_1perf__sw__clock_1aaaf35d0e0027ef3043345870b8dcbf06}

#### `typedef `[`rep`](#classexot_1_1primitives_1_1perf__sw__clock_1a6768a32e719e751b4de1d367a109a9c6) {#classexot_1_1primitives_1_1perf__sw__clock_1a6768a32e719e751b4de1d367a109a9c6}

#### `typedef `[`period`](#classexot_1_1primitives_1_1perf__sw__clock_1a7f6300c777ad29dfb4da4c11d0836a03) {#classexot_1_1primitives_1_1perf__sw__clock_1a7f6300c777ad29dfb4da4c11d0836a03}

#### `typedef `[`time_point`](#classexot_1_1primitives_1_1perf__sw__clock_1ab7bd8663e2dd06a3b414e679beb97ca8) {#classexot_1_1primitives_1_1perf__sw__clock_1ab7bd8663e2dd06a3b414e679beb97ca8}

# struct `exot::primitives::__fenced_clock` {#structexot_1_1primitives_1_1____fenced__clock}

```
struct exot::primitives::__fenced_clock
  : public Clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____fenced__clock_1a8650ce35c80a9f4e774e42cdca45fbe1) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____fenced__clock_1a8650ce35c80a9f4e774e42cdca45fbe1) {#structexot_1_1primitives_1_1____fenced__clock_1a8650ce35c80a9f4e774e42cdca45fbe1}

# struct `exot::primitives::__fenced_tsc` {#structexot_1_1primitives_1_1____fenced__tsc}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____fenced__tsc_1adb2d62c95d109d1f2914503c45a04caa) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____fenced__tsc_1adb2d62c95d109d1f2914503c45a04caa) {#structexot_1_1primitives_1_1____fenced__tsc_1adb2d62c95d109d1f2914503c45a04caa}

# struct `exot::primitives::__strong_fenced_clock` {#structexot_1_1primitives_1_1____strong__fenced__clock}

```
struct exot::primitives::__strong_fenced_clock
  : public Clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____strong__fenced__clock_1a167707846ed8d6f8d93dc0f73cfe2bdb) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____strong__fenced__clock_1a167707846ed8d6f8d93dc0f73cfe2bdb) {#structexot_1_1primitives_1_1____strong__fenced__clock_1a167707846ed8d6f8d93dc0f73cfe2bdb}

# struct `exot::primitives::__strong_fenced_tsc` {#structexot_1_1primitives_1_1____strong__fenced__tsc}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____strong__fenced__tsc_1ad1f668f55c418f3dcc222ec861c233a2) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1____strong__fenced__tsc_1ad1f668f55c418f3dcc222ec861c233a2) {#structexot_1_1primitives_1_1____strong__fenced__tsc_1ad1f668f55c418f3dcc222ec861c233a2}

# struct `exot::primitives::fd_deleter` {#structexot_1_1primitives_1_1fd__deleter}

A custom deleter for file descriptors to be used with unique pointers.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public  `[`fd_deleter`](#structexot_1_1primitives_1_1fd__deleter_1aa0b8660199dd2d3e5c9ce219be0d16d6)`() = default` | 
`public  `[`fd_deleter`](#structexot_1_1primitives_1_1fd__deleter_1a80fa484b6970fe69e6ea3afbb189c010)`(`[`fd_deleter`](#structexot_1_1primitives_1_1fd__deleter)` &&) = default` | 
`public inline void `[`operator()`](#structexot_1_1primitives_1_1fd__deleter_1aac594bcf996ae05bc3f7d0fed1092852)`(long * fd) const` | 

## Members

#### `public  `[`fd_deleter`](#structexot_1_1primitives_1_1fd__deleter_1aa0b8660199dd2d3e5c9ce219be0d16d6)`() = default` {#structexot_1_1primitives_1_1fd__deleter_1aa0b8660199dd2d3e5c9ce219be0d16d6}

#### `public  `[`fd_deleter`](#structexot_1_1primitives_1_1fd__deleter_1a80fa484b6970fe69e6ea3afbb189c010)`(`[`fd_deleter`](#structexot_1_1primitives_1_1fd__deleter)` &&) = default` {#structexot_1_1primitives_1_1fd__deleter_1a80fa484b6970fe69e6ea3afbb189c010}

#### `public inline void `[`operator()`](#structexot_1_1primitives_1_1fd__deleter_1aac594bcf996ae05bc3f7d0fed1092852)`(long * fd) const` {#structexot_1_1primitives_1_1fd__deleter_1aac594bcf996ae05bc3f7d0fed1092852}

# struct `exot::primitives::fenced_clock` {#structexot_1_1primitives_1_1fenced__clock}

```
struct exot::primitives::fenced_clock
  : public Clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1fenced__clock_1ab8b530996aad3aa7cc70fc844fc55493) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1fenced__clock_1ab8b530996aad3aa7cc70fc844fc55493) {#structexot_1_1primitives_1_1fenced__clock_1ab8b530996aad3aa7cc70fc844fc55493}

# struct `exot::primitives::fenced_tsc` {#structexot_1_1primitives_1_1fenced__tsc}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1fenced__tsc_1aedc4bdffb4684dde129bfd03b50fb890) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1fenced__tsc_1aedc4bdffb4684dde129bfd03b50fb890) {#structexot_1_1primitives_1_1fenced__tsc_1aedc4bdffb4684dde129bfd03b50fb890}

# struct `exot::primitives::is_time_stamp_counter` {#structexot_1_1primitives_1_1is__time__stamp__counter}

```
struct exot::primitives::is_time_stamp_counter
  : public false_type
```  

Is the provided type a time stamp counter?

#### Parameters
* `T` A type to check 

* `<unnamed>` Template helper

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::primitives::is_time_stamp_counter< T, std::void_t< decltype(T::start), decltype(T::stop)> >` {#structexot_1_1primitives_1_1is__time__stamp__counter_3_01T_00_01std_1_1void__t_3_01decltype_07T_ff83b96cb989fe7af428ada26c85f5e3}

```
struct exot::primitives::is_time_stamp_counter< T, std::void_t< decltype(T::start), decltype(T::stop)> >
  : public true_type
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

# struct `exot::primitives::plain_clock` {#structexot_1_1primitives_1_1plain__clock}

```
struct exot::primitives::plain_clock
  : public Clock
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1plain__clock_1afefc8934b84477389ea90fadb2eaa212) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1plain__clock_1afefc8934b84477389ea90fadb2eaa212) {#structexot_1_1primitives_1_1plain__clock_1afefc8934b84477389ea90fadb2eaa212}

# struct `exot::primitives::plain_tsc` {#structexot_1_1primitives_1_1plain__tsc}

```
struct exot::primitives::plain_tsc
  : public Counter
```  

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1plain__tsc_1ab36a71eb4f1e7bc0728a27b31e2c00f8) | 

## Members

#### `typedef `[`underlying_timing_source`](#structexot_1_1primitives_1_1plain__tsc_1ab36a71eb4f1e7bc0728a27b31e2c00f8) {#structexot_1_1primitives_1_1plain__tsc_1ab36a71eb4f1e7bc0728a27b31e2c00f8}

# struct `exot::primitives::TimeStampCounter` {#structexot_1_1primitives_1_1TimeStampCounter}

Base class for timestamp counters.

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------

## Members

Generated by [Moxygen](https://sourcey.com/moxygen)
