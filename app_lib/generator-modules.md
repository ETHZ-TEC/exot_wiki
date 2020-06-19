[:back:](/home)
---

# Available generator modules

### Cache (Maurice)

- __Name__ → Cache (maurice multithreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_cache_maurice_mt`

Implements the cache covert channel sender strategie as presented by C. Maurice, C. Neumann, O. Heen, and A. Francillon, “C5: Cross-Cores Data Leak Channel.,” DIMVA, vol. 9148, no. 3, pp. 46–64, 2015.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 
| `overprovision_factor` | `double` | `1.0` | Overprovisioning factor of the write buffer size |

### Cache (read)

- __Name__ → Cache (read singlethreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_cache_read_st`

Generator that accesses addresses by performing reads.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 

### Cache (write)

- __Name__ → Cache (write singlethreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_cache_write_st`

Generator that accesses addresses by performing writes.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 

### Cache (evict singlethreaded)

- __Name__ → Cache (evict singlethreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_cache_evict_st`

Generator that accesses addresses with eviction patterns.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* |
| `addresses_per_loop` | `std::size_t` | `2`  | Addresses which are accessed per loop iteration |
| `accesses_per_loop`  | `std::size_t` | `2`  | Accesses per loop iteration |
| `overlap_parameter`  | `std::size_t` | `1`  | Access overlap |
| `eviction_length`    | `std::size_t` | `64` | Length of eviction block |
 
### Inactive (multithreaded)

- __Name__ → Inactive (multithreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_inactive_mt`

Keeps the core inactive.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 

### rdseed_mt

- __Name__ → RDSeed (multithreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_rdseed_mt`

Create contention to the hardware random number generator.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 

### utilisation_ffb_conservative

- __Name__ → Utilisation with Frequency Feedback (conservative governor)
- __Namespace__ → `"generator"`
- __Class__ → `generator_utilisation_ffb_conservative`

Generates a specific load to force the acpi conservative governor to either scale up, stay or scale down.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 

### Utilisation (binary multithreaded)

- __Name__ → Utilisation (binary multithreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_utilisation_mt`

Generates either full load (1) or no load (0) on the specified cores using a floating-point busy loop.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 

### Utilisation (multithreaded)

- __Name__ → Utilisation (multithreaded)
- __Namespace__ → `"generator"`
- __Class__ → `generator_utilisation_ut`

Generates either a load between 0% and 100% on the specified cores using a floating-point busy loop.

###### Options

| Option | Type | Default | Description |
|:------ |:---- |:------- |:----------- |
| `cores` | `std::set<unsigned>` | Necessary | The cores the workers are pinned to, from 0 to *n* | 


