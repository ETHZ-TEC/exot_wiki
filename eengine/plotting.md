[:back:](/home)
---

# Plotting support
ExOT provides rudimentary plotting support.
In future versions of ExOT, a more extensive support for data visualization is needed.

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`namespace `[`exot::plotting::_base`](#namespaceexot_1_1plotting_1_1__base) | 
`namespace `[`exot::plotting::experiment_plotter`](#namespaceexot_1_1plotting_1_1experiment__plotter) | 
`namespace `[`exot::plotting::run_plotter`](#namespaceexot_1_1plotting_1_1run__plotter) | 

# namespace `exot::plotting::_base` {#namespaceexot_1_1plotting_1_1__base}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::plotting::_base::Plotter`](#classexot_1_1plotting_1_1__base_1_1Plotter) | Plotting support for Run instances

# class `exot::plotting::_base::Plotter` {#classexot_1_1plotting_1_1__base_1_1Plotter}

```
class exot::plotting::_base::Plotter
  : public ContextDecorator
```  

Plotting support for Run instances

Attributes:
    PLOT_FILENAMES (dict): Default filenames for supported plots

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1acf615b8f2caa2389bfba537c9140d22e)`(self,* args,bool save_png,bool save_pdf,** kwargs)` | 
`public def `[`save_path`](#classexot_1_1plotting_1_1__base_1_1Plotter_1af6ca47468f86438172c347d63a8243f0)`(self)` | 
`public def `[`save_path`](#classexot_1_1plotting_1_1__base_1_1Plotter_1aa96128e643978e848ec9f33c960a3c4a)`(self,value)` | 
`public def `[`__repr__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1a53796cd0f13562f0b2421560954f6d37)`(self)` | 
`public def `[`__enter__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1ad5a044cb3b05d111ead645703c9e5cd5)`(self)` | 
`public def `[`__exit__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1a793d156d144517a23e3e28455ef28813)`(self,* exc)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1acf615b8f2caa2389bfba537c9140d22e)`(self,* args,bool save_png,bool save_pdf,** kwargs)` {#classexot_1_1plotting_1_1__base_1_1Plotter_1acf615b8f2caa2389bfba537c9140d22e}

#### `public def `[`save_path`](#classexot_1_1plotting_1_1__base_1_1Plotter_1af6ca47468f86438172c347d63a8243f0)`(self)` {#classexot_1_1plotting_1_1__base_1_1Plotter_1af6ca47468f86438172c347d63a8243f0}

#### `public def `[`save_path`](#classexot_1_1plotting_1_1__base_1_1Plotter_1aa96128e643978e848ec9f33c960a3c4a)`(self,value)` {#classexot_1_1plotting_1_1__base_1_1Plotter_1aa96128e643978e848ec9f33c960a3c4a}

#### `public def `[`__repr__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1a53796cd0f13562f0b2421560954f6d37)`(self)` {#classexot_1_1plotting_1_1__base_1_1Plotter_1a53796cd0f13562f0b2421560954f6d37}

#### `public def `[`__enter__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1ad5a044cb3b05d111ead645703c9e5cd5)`(self)` {#classexot_1_1plotting_1_1__base_1_1Plotter_1ad5a044cb3b05d111ead645703c9e5cd5}

#### `public def `[`__exit__`](#classexot_1_1plotting_1_1__base_1_1Plotter_1a793d156d144517a23e3e28455ef28813)`(self,* exc)` {#classexot_1_1plotting_1_1__base_1_1Plotter_1a793d156d144517a23e3e28455ef28813}

# namespace `exot::plotting::experiment_plotter` {#namespaceexot_1_1plotting_1_1experiment__plotter}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::plotting::experiment_plotter::ExperimentPlotter`](#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter) | Plotting support for experiment instances
`class `[`exot::plotting::experiment_plotter::FrequencySweepExperimentPlotter`](#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter) | Plotting support for FrequencySweepExperiment instances
`class `[`exot::plotting::experiment_plotter::PerformanceExperimentPlotter`](#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter) | Plotting support for PerformanceExperiment instances

# class `exot::plotting::experiment_plotter::ExperimentPlotter` {#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter}

```
class exot::plotting::experiment_plotter::ExperimentPlotter
  : public exot.plotting._base.Plotter
```  

Plotting support for experiment instances

Attributes:
    PLOT_FILENAMES (dict): Default filenames for supported plots

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter_1ad10eda03791df67736551f811a743ef8)`(self,experiment,* args,** kwargs)` | 
`public Experiment `[`experiment`](#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter_1a451bdcf7357e05a7d622ca6ab0501606)`(self)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter_1ad10eda03791df67736551f811a743ef8)`(self,experiment,* args,** kwargs)` {#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter_1ad10eda03791df67736551f811a743ef8}

#### `public Experiment `[`experiment`](#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter_1a451bdcf7357e05a7d622ca6ab0501606)`(self)` {#classexot_1_1plotting_1_1experiment__plotter_1_1ExperimentPlotter_1a451bdcf7357e05a7d622ca6ab0501606}

# class `exot::plotting::experiment_plotter::FrequencySweepExperimentPlotter` {#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter}

```
class exot::plotting::experiment_plotter::FrequencySweepExperimentPlotter
  : public exot.plotting.experiment_plotter.ExperimentPlotter
```  

Plotting support for FrequencySweepExperiment instances

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter_1a35a2f32c3d2803ede828903bf554b91e)`(self,Experiment experiment,* args,** kwargs)` | 
`public def `[`plot_channel_spectra`](#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter_1a72fcb1ce23fa80803385d49b64cf1619)`(self,selector,** kwargs)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter_1a35a2f32c3d2803ede828903bf554b91e)`(self,Experiment experiment,* args,** kwargs)` {#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter_1a35a2f32c3d2803ede828903bf554b91e}

#### `public def `[`plot_channel_spectra`](#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter_1a72fcb1ce23fa80803385d49b64cf1619)`(self,selector,** kwargs)` {#classexot_1_1plotting_1_1experiment__plotter_1_1FrequencySweepExperimentPlotter_1a72fcb1ce23fa80803385d49b64cf1619}

# class `exot::plotting::experiment_plotter::PerformanceExperimentPlotter` {#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter}

```
class exot::plotting::experiment_plotter::PerformanceExperimentPlotter
  : public exot.plotting.experiment_plotter.ExperimentPlotter
```  

Plotting support for PerformanceExperiment instances

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter_1ae114e88afb729bc4fb9f1a531a686e98)`(self,Experiment experiment,* args,** kwargs)` | 
`public def `[`plot_performance_metrics`](#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter_1a6e441fbe3ebf5537d67c06a0c85e464a)`(self,bit_or_symbol,selector,* estimator,** kwargs)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter_1ae114e88afb729bc4fb9f1a531a686e98)`(self,Experiment experiment,* args,** kwargs)` {#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter_1ae114e88afb729bc4fb9f1a531a686e98}

#### `public def `[`plot_performance_metrics`](#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter_1a6e441fbe3ebf5537d67c06a0c85e464a)`(self,bit_or_symbol,selector,* estimator,** kwargs)` {#classexot_1_1plotting_1_1experiment__plotter_1_1PerformanceExperimentPlotter_1a6e441fbe3ebf5537d67c06a0c85e464a}

# namespace `exot::plotting::run_plotter` {#namespaceexot_1_1plotting_1_1run__plotter}

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`class `[`exot::plotting::run_plotter::FrequencySweepRunPlotter`](#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter) | Plotting support for FrequencySweepRun instances
`class `[`exot::plotting::run_plotter::PerformanceRunPlotter`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter) | Plotting support for PerformanceRun instances
`class `[`exot::plotting::run_plotter::RunPlotter`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter) | Plotting support for Run instances

# class `exot::plotting::run_plotter::FrequencySweepRunPlotter` {#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter}

```
class exot::plotting::run_plotter::FrequencySweepRunPlotter
  : public exot.plotting.run_plotter.RunPlotter
```  

Plotting support for FrequencySweepRun instances
Attributes:
    PLOT_FILENAMES (dict): Default filenames for supported plots

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter_1a24d670dace8c076a8674808bb4a01033)`(self,FrequencySweepRun run,* args,** kwargs)` | 
`public def `[`plot_spectrum`](#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter_1a9b9338ff4e7ea78338508f14c9eac303)`(self,window)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter_1a24d670dace8c076a8674808bb4a01033)`(self,FrequencySweepRun run,* args,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter_1a24d670dace8c076a8674808bb4a01033}

#### `public def `[`plot_spectrum`](#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter_1a9b9338ff4e7ea78338508f14c9eac303)`(self,window)` {#classexot_1_1plotting_1_1run__plotter_1_1FrequencySweepRunPlotter_1a9b9338ff4e7ea78338508f14c9eac303}

# class `exot::plotting::run_plotter::PerformanceRunPlotter` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter}

```
class exot::plotting::run_plotter::PerformanceRunPlotter
  : public exot.plotting.run_plotter.RunPlotter
```  

Plotting support for PerformanceRun instances

Attributes:
    PLOT_FILENAMES (dict): Default filenames for supported plots

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a81e760e1b388522ade1bee024a37d10f)`(self,PerformanceRun run,* args,** kwargs)` | 
`public def `[`plot_slicing`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a1f96e9d41a056bfe29436957b71fb41f)`(self,int start,int count,t.Optional dim_count,** kwargs)` | 
`public def `[`plot_symstream`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a9a1fcfaccfeb5c545da89c8a30b7a041)`(self,t.Optional start,t.Optional count,** kwargs)` | 
`public def `[`plot_eye_diagram`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a490bff0a0deaeffb584c98a19e85cbf2)`(self,** kwargs)` | 
`public def `[`plot_symbol_space`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a19f76134cc69993e44f290b056f724d4)`(self,** kwargs)` | 
`public def `[`plot_error`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a409346fbbe66d1f0877b2a51ef169ae2)`(self,t.Optional roll,** kwargs)` | 
`public def `[`plot_timing`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1ae71986b37a68e27bc2aa1189f28107cc)`(self,** kwargs)` | 
`public def `[`plot_synchronisation`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1aca8a786d87d35ca7c13a4eb04a5f7429)`(self,** kwargs)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a81e760e1b388522ade1bee024a37d10f)`(self,PerformanceRun run,* args,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a81e760e1b388522ade1bee024a37d10f}

#### `public def `[`plot_slicing`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a1f96e9d41a056bfe29436957b71fb41f)`(self,int start,int count,t.Optional dim_count,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a1f96e9d41a056bfe29436957b71fb41f}

#### `public def `[`plot_symstream`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a9a1fcfaccfeb5c545da89c8a30b7a041)`(self,t.Optional start,t.Optional count,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a9a1fcfaccfeb5c545da89c8a30b7a041}

#### `public def `[`plot_eye_diagram`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a490bff0a0deaeffb584c98a19e85cbf2)`(self,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a490bff0a0deaeffb584c98a19e85cbf2}

#### `public def `[`plot_symbol_space`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a19f76134cc69993e44f290b056f724d4)`(self,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a19f76134cc69993e44f290b056f724d4}

#### `public def `[`plot_error`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a409346fbbe66d1f0877b2a51ef169ae2)`(self,t.Optional roll,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1a409346fbbe66d1f0877b2a51ef169ae2}

#### `public def `[`plot_timing`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1ae71986b37a68e27bc2aa1189f28107cc)`(self,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1ae71986b37a68e27bc2aa1189f28107cc}

#### `public def `[`plot_synchronisation`](#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1aca8a786d87d35ca7c13a4eb04a5f7429)`(self,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1PerformanceRunPlotter_1aca8a786d87d35ca7c13a4eb04a5f7429}

# class `exot::plotting::run_plotter::RunPlotter` {#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter}

```
class exot::plotting::run_plotter::RunPlotter
  : public exot.plotting._base.Plotter
```  

Plotting support for Run instances

Attributes:
    PLOT_FILENAMES (dict): Default filenames for supported plots

## Summary

 Members                        | Descriptions                                
--------------------------------|---------------------------------------------
`public def `[`__init__`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1a040ff24e9fa7c7e772a02d1da8ac85a7)`(self,run,* args,** kwargs)` | 
`public Run `[`run`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1ad8b06ed98c5a5d1c0c6c8211b2310f44)`(self)` | 
`public def `[`plot_rawstream`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1a2d472f15efdddb012a30f1f518147e54)`(self,t.Optional start,t.Optional end,t.Optional dim_count,** kwargs)` | 
`public def `[`plot_rdpstream`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1ab9d8cbc895edfd1ab1cbdceaac74488b)`(self,t.Optional start,t.Optional end,t.Optional dim_count,** kwargs)` | 

## Members

#### `public def `[`__init__`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1a040ff24e9fa7c7e772a02d1da8ac85a7)`(self,run,* args,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1a040ff24e9fa7c7e772a02d1da8ac85a7}

#### `public Run `[`run`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1ad8b06ed98c5a5d1c0c6c8211b2310f44)`(self)` {#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1ad8b06ed98c5a5d1c0c6c8211b2310f44}

#### `public def `[`plot_rawstream`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1a2d472f15efdddb012a30f1f518147e54)`(self,t.Optional start,t.Optional end,t.Optional dim_count,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1a2d472f15efdddb012a30f1f518147e54}

#### `public def `[`plot_rdpstream`](#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1ab9d8cbc895edfd1ab1cbdceaac74488b)`(self,t.Optional start,t.Optional end,t.Optional dim_count,** kwargs)` {#classexot_1_1plotting_1_1run__plotter_1_1RunPlotter_1ab9d8cbc895edfd1ab1cbdceaac74488b}

Generated by [Moxygen](https://sourcey.com/moxygen)