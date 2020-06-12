[:back:](/home)
---

# Available metering modules

This page outlines all the available metering modules.

1. [Thermal](#Thermal) → [Thermal (sysfs)](#Thermal-(sysfs)), [Thermal (MSR)](#Thermal-(MSR))
1. [Frequency](#Frequency) → [Frequency (sysfs)](#Frequency-(sysfs)), [Frequency (relative)](#Frequency-(relative))
1. [Utilisation](#Utilisation) → [Utilisation (procfs)](#Utilisation-(procfs))
1. [Power](#Power) → [Power (MSR)](#Power-(MSR))
1. [Cache](#Cache)

---

> As described on the [utilities formatting](./utilities#formatting) section, all metering modules produce individual header information with the `exot::utilities::generate_header` function. The 4 components of the individual column header are: __1: module, 2: variable, 3: dimension, 4: unit__.
>
> For example, consider the following: a module *"some_meter"* produces readings of two variables, *"variable_1"* and *"variable_2*". The first variable is single-dimensional, while the latter has 2 dimensions (e.g. for 2 CPUs). The units are degrees Celsius. The produced header descriptions would be: *some_meter:variable_1:0:℃, some_meter:variable_2:0:℃, some_meter:variable_2:1:℃*.
>
> *Note:* The meter module names, variable names, dimensions and units cannot contain the characters: "`,`", "`:`".

---

## Thermal

The [exot/meters/thermal.h](https://gitlab.ethz.ch/tec/public/exot/app_lib/blob/master/include/exot/meters/thermal.h) links to two metering modules that measure the temperatures in the system.

### Thermal (sysfs)

- __Name__ → Thermal (sysfs)
- __Namespace__ → `"thermal_sysfs"`
- __Class__ → `thermal_sysfs`
- __Return type__  → `std::vector<float>`

The `thermal_sysfs` module reads the temperatures of the thermal zones exposed through the *sysfs* pseudo-filesystem. The zones are discovered automatically and are all used by default (but can be subset via options).

###### Header

| Module | Variable | Dimension | Unit |
|:--- |:--- |:--- |:--- |
| `thermal_sysfs` | `zone` | 0-*n* | ℃

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `zones` | `vector<unsigned>` | All available | The *sysfs* thermal zones, from 0 to *n*

### Thermal (MSR)

- __Name__ → Thermal (MSR)
- __Namespace__ → `"thermal_msr"`
- __Class__ → `thermal_msr`
- __Return type__  → `std::vector<unsigned short>`

The `thermal_msr` module accesses the Model Specific Registers on Intel x86_64 processors and reads the core temperatures. The module determines the reference temperature target and checks whether package temperatures are provided.

###### Header

| Module | Variable | Dimension | Unit |
|:--- |:--- |:--- |:--- |
| `thermal_msr` | `core` | CPU # | ℃
| `thermal_msr` | `package` | `""` | ℃

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `vector<unsigned>` | All available (physical) | The list of cores to get the temperature of
| `package` | bool | false | Also get the package temperature

## Frequency

The [exot/meters/frequency.h](https://gitlab.ethz.ch/tec/research/exot/app_lib/blob/develop/include/exot/meters/frequency.h) links to two metering modules that determine the scaling frequencies of the processor cores.

### Frequency (sysfs)

- __Name__ → Frequency (sysfs)
- __Namespace__ → `"frequency_sysfs"`
- __Class__ → `frequency_sysfs`
- __Return type__  → `std::vector<unsigned>`

###### Header

| Module | Variable | Dimension | Unit |
|:--- |:--- |:--- |:--- |
| `frequency_sysfs` | `scaling_cur_freq` or `cpuinfo_cur_freq` | CPU # | kHz

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `vector<unsigned>` | All available (physical) | The list of cores to get the scaling frequency of
| `source` | string | scaling_cur_freq | The source of frequency information, either *scaling_cur_freq* or *cpuinfo_cur_freq*
| `strict` | bool | true | Fail if any of the cores are unavailable?

### Frequency (relative)

- __Name__ → Frequency (relative)
- __Namespace__ → `"frequency_rel"`
- __Class__ → `frequency_rel`
- __Return type__  → `std::vector<unsigned>`

The `frequency_rel` module measures the relative scaling frequency of a processor core. It uses the duration of a probe function and a reference to determine the empirical scaling frequency.

###### Header

| Module | Variable | Dimension | Unit |
|:--- |:--- |:--- |:--- |
| `frequency_rel` | *"empirical"* | CPU # | *null*

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `vector<unsigned>` | All available (physical) | The list of cores to get the relative frequency of

###### Static options

The class uses a probe function template `exot::modules::details::probe` defined in the header. It consists of a time measurement (with the `std::chrono::steady_clock`) of a predefined number of iterations of a loop with arithmetic operations. The probe function template accepts template parameters `T` (an aritmetic type) and `Iter` (the number of iterations). The `frequency_rel` class specialises the probe as shown below:

```c++
using probe_type = int;
static const unsigned probe_iterations{1024u};
```

## Utilisation

### Utilisation (procfs)

- __Name__ → Utilisation (procfs)
- __Namespace__ → `"utilisation_procfs"`
- __Class__ → `utilisation_procfs`
- __Return type__  → `std::vector<double>`

The `utilisation_procfs` determines the utilisation of processor's cores. It can provide the values in range [0, 1] of processor core utilisation in the following CPU states: *user*, *nice*, *system*, *idle*.

###### Header

| Module | Variable | Dimension | Unit |
|:--- |:--- |:--- |:--- |
| `utilisation_procfs` | *user*, *nice*, *system*, *idle* | CPU # | *null*

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `vector<unsigned>` | All available (physical) | The list of cores to get the utilisation of
| `raw` | bool | false | Output raw *procfs* readings?
| `states` | `vector<cpu_state>` (list of strings in JSON) | user, idle | The list of CPU states to consider

## Power

### Power (MSR)

- __Name__ → Power (MSR)
- __Namespace__ → `"power_msr"`
- __Class__ → `power_msr`
- __Return type__  → `std::vector<double>`

The `power_msr` module accesses the Model Specific Registers on Intel processors to determine the instantenous power drawn by specific power domains. It achieves that by accessing the counters of the [*Running Average Power Limit* (RAPL)](https://01.org/rapl-power-meter) power meter.

###### Header

| Module | Variable | Dimension | Unit |
|:--- |:--- |:--- |:--- |
| `power_msr` | `rapl_domain` | The domain (pp0, pp1, pkg, sys) | W (Watt)

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `domains` | `vector<rapl_domain>` (list of strings in JSON) | pp0, pkg | The list of RAPL domains

## Other

- __Fan__ → Two modules measure the current fan speed via the *procfs* (`fan_procfs`) or the *sysfs*  (`fan_sysfs`) filesystems. The speed values are given in RPM as integers.
- __Process__ → A special module is available for Android that logs the topmost application (`process_android`).
- __RDSEED__ → Two modules exist to measure the utilisation of the hardware random number generator. The `rdseed_status` module determines the status (available/unavailable) of the `rdseed64` instruction after 4 priming calls. The `rdseed_timing` provides a similar insight, but instead reports the number of nanoseconds required to get a successful `rdseed64` after the 4 priming calls. This metering module implements the functionality described in ["Covert Channels through Random Number Generator: Mechanisms, Capacity Estimation and Mitigations"](https://www.researchgate.net/publication/306285701_Covert_Channels_through_Random_Number_Generator_Mechanisms_Capacity_Estimation_and_Mitigations).

## Cache

### Shared memory

Some of the common functionality of shared memory-based modules has been extracted into the `meter_shared_memory_base` class. The modules based on it measure the access time (in CPU/standardised cycles) to a memory address. This measurement may allow determining whether an address was cached or not. It targets

- __Name__ → Cache (shared memory)
- __Namespace__ → `"cache"`
- __Return type__  → `std::vector<uint64_t>`

The following concrete modules are available:

- __`cache_fr`__ which times the memory access (namespace: `"cache_fr"`).
- __`cache_ff`__ which times the cache flush operation (namespace: `"cache_ff"`).
- __`cache_fp`__ which times the prefetch operation (namespace: `"cache_fp"`).
- __`cache_er`__ which times the memory access, but uses an eviction strategy instead of an explicit cache flushing operation (namespace: `"cache_er"`). It has additional configuration options.

###### Header

| Module | Variable | Dimension | Unit |
|:--- |:--- |:--- |:--- |
| *module name* | `access_time` | Address # | cycles

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `shm_file` | string | ~ | The shared memory file
| `use_huge_pages` | bool | true | Use hugepages?
| `set_count` | unsigned | 1 | The number of LLC sets used for communication
| `set_increment` | unsigned | 64 | number of cache-line-sized spaces between consecutive  communication sets, (defaults to page offsets (64 * line = 4096))
| `cache_info` | map, *optional* | ~ | Manual cache info maps, see the [Utilities/Memory](./Utilities/Memory) page for details

Additionally, the `cache_er` module has the following options:

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `addresses_per_loop` | unsigned |  2 | The number of addresses accessed in an eviction
| `accesses_per_loop` | unsigned | 2 | The number of accesses to each address
| `overlap_parameter` | unsigned | 1 | The eviction overlap parameter

> For details on those parameters, refer to the publication that introduces the eviction strategy: M. Lipp, D. Gruss, R. Spreitzer, C. Maurice, and S. Mangard, “ARMageddon - Cache Attacks on Mobile Devices.,” 23rd USENIX Security Symposium, 2016.