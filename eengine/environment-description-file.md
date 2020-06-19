[:back:](/home)
---

# Environment description file

Please also have a look at the [examples in the eengine repository](https://gitlab.ethz.ch/tec/public/exot/eengine/-/tree/master/environments)

# Zone
| Parameter                  | Type | Description |
| -------------------------- | ---- | -------------------------------------------------------------------------- |
| `model`                    | `str` | Model name of the zone, just for debug purposes. |
| `cores`                    | `list` of `int` | Cores of the machine that are mapped to this zone. |
| `frequencies`              | `list` of `numeric` | List of all available operating frequencies for the cores in the zone. |
| `schedule_tag`             | `str` | Name of the schedule files used for the source applications executed in this zone. |
| `path_apps`                | `str` | Location of the ExOT application executables, relative to the home directory of the dedicated user. |
| `path_data`                | `str` | Location of the ExOT data, relative to the home directory of the dedicated user. |
| `driver_type`              | `str` | Name of the driver that can be used to communicate with the zone. For detailed information see the [experiment drivers page](./experiment-drivers]. |
| `power_thresholds`         | `list` of `numeric` | List of the power thresholds used for the analysis of the power covert channel. |

### `<ZONE NAME>.driver_params`
| Parameter                  | Type | Description |
| -------------------------- | ---- | -------------------------------------------------------------------------- |
| `ip`                       | `str` | IP-Address of the zone.                                                   |
| `port`                     | `int` | Port used to setup the connection, e.g. ssh or ADB port.|
| `user`                     | `str` | Dedicated user to communicate with the environment zone. |
| `group`                    | `str` | Dedicated user-group to communicate with the environment zone. |
| `key`                      | `str` | The key-file used to access the environment zone. |
| `gateway`                  | `str` | Hostname of a possible gateway computer, if the environment zone is inside a shielded network. (optional) |

### `<ZONE NAME>.beta_z`
This section defines the thermal coefficients for the different thermal zones. 
For example:
```toml
"thermal_sysfs:zone:0:°C" = 0.06864370195354438
"thermal_sysfs:zone:1:°C" = 0.006104564896214277
"thermal_sysfs:zone:2:°C" = 164.40748295928944
```
### `<ZONE NAME>.T_idle`
This section defines the idle temperatures for the different thermal zones. 
For example:
```toml
"thermal_sysfs:zone:0:°C" = 28.0
"thermal_sysfs:zone:1:°C" = 23.7310375
"thermal_sysfs:zone:2:°C" = 22.6
 ```
### `<ZONE NAME>.T_norm`
This section defines the normalization factors for the different thermal zones. 
For example:
```toml
"thermal_sysfs:zone:0:°C" = 1
"thermal_sysfs:zone:1:°C" = 1000
"thermal_sysfs:zone:2:°C" = 1
 ```