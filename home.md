# Experiment Orchestration Toolkit 
<img src="./uploads/figures/exot_logo.png" alt="ExOT Logo" width="100"/>

Welcome to the __Experiment Orchestration Toolkit__ (__ExOT__) knowledge base.
__ExOT__ was build to orchestrate experiments for the evaluation of data leaks in multicore systems (e.g. 
[Thermal Covert Channel](http://doi.acm.org/10.1145/2901318.2901322), 
[Power Covert Channel](https://doi.org/10.1145/3167132.3167301), 
[Frequency Covert Channel](https://doi.org/10.1109/TCAD.2018.2857038),
[Thermal Side Channel](#)). 
ExOT was first presented in detail in a [conference paper](https://doi.org/10.3929/ethz-b-000377986) which appeared in the proceedings of “Design, Automation & Test in Europe Conference & Exhibition (DATE 2020), Grenoble, France, March 9-13, 2020”.
The [ExOT white paper](http://pub.tik.ee.ethz.ch/people/miedlp/2020-05-22_ExOT_Whitepaper.pdf) gives further insight into the underlying design principals of ExOT.



### Get started
In order to take advantage of all features of ExOT, please follow the steps bellow to get a basic setup:

Make sure you have the following software installed:
1. [python 3.7](https://www.python.org/)
1. [poetry](https://python-poetry.org/)
1. [Android Studio](https://developer.android.com/studio/index.html)

Next, create an ExOT directory and clone all the ExOT repositories into this directory and initialise the submodules, using following script:

```bash
for repo in eengine app_unx app_apk compilation; do
  git clone https://gitlab.ethz.ch/tec/public/exot/${repo}.git
  cd ${repo}
  git checkout v1.1.0
  git submodule --init --recursive update
  cd ..
done
```

Now you have successfully installed the basic setup of ExOT.
Please refer to the table below for advanced information regarding the different components of ExOT.

<table style="border:1px solid black;margin-left:auto;margin-right:auto;width:100%;float:center">
<!-- ############################### Application development ############################### -->
<tr><td colspan="2" align="center"><h1 id="applications">Developing deployment applications for ExOT</h1></td></tr>
<tr>
<td width=50%><ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/app_lib">The C++ application library</a>
 <ul>
  <li><a href="app_lib/general">General information</a></li>
  <li><a href="app_lib/overview">Overview, structure & terminology</a></li>
  <li><a href="app_lib/library-usage">Using the library in your project</a></li>
  <li><a href="app_lib/contributing">Contributing to the library</a></li>
  <li><a href="app_lib/core-framework">The core framework design</a></li>
  <li><a href="app_lib/components">Provided components</a></li>
  <li><a href="app_lib/metering-modules">Available metering modules</a></li>
  <li><a href="app_lib/platform-specific-primitives">Platform specific primitives</a></li>
  <li><a href="app_lib/utilities">Utilities</a></li>
 </ul>
</ul></td>
<td width=50%><ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/compilation">The docker based compilation suite</a>
 <ul>
  <li><a href="compilation/setup">Setting up the compilation suite</a></li>
  <li><a href="compilation/environment">The build environment</a></li>
 </ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/app_unx">UNIX applications</a>
 <ul>
  <li><a href="app_unx/general">General information</a></li>
  <li><a href="app_unx/index">Unix application index</a></li>
 </ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/app_apk">The Android NDK integration</a>
 <ul>
  <li><a href="app_apk/general">General information</a></li>
  <li><a href="app_apk/index">Android application index</a></li>
  <li><a href="app_apk/intent-proxy">Android Intent Proxy</a></li>
 </ul>
</ul></td>
</tr>
<tr><td colspan="2">How to:</h1></td></tr>
<tr>
<td><ul>
  <li><a href="how-tos/creating-metering-modules">Creating metering modules</a></li>
  <li><a href="how-tos/creating-process-network-components">Creating process network components</a></li>
</ul></td>
<td><ul>
  <li><a href="how-tos/assembling-metering-modules">Assembling metering modules</a></li>
  <li><a href="how-tos/building-applications">Building applications</a></li>
</ul></td>
</tr>
<!-- ###############################    Experiment Engine    ############################### -->
<tr><td colspan="2", align="center"><h1 id="eengine"><a href="https://gitlab.ethz.ch/tec/research/exot/eengine">The experiment engine</a></h1></td></tr>
<td><ul>
 <li><a href="eengine/overview">The ecosystem</a></li>
 <li><a href="eengine/information-flow">Information flow</a></li>
 <li><a href="eengine/experiment-structure">Experiment structure</a></li>
</ul></td>
<td><ul>
 <li><a href="eengine/experiment-drivers">Experiment drivers</a></li>
 <li><a href="eengine/utilities">Utilities</a></li>
</ul></td>
</tr>
<!-- ###############################    General     ############################### -->
<tr><td colspan="2", align="center"><h1 id="theory">General</h1></td></tr>
<tr>
<td><ul>
 <li><a href="general/code-style">Code style and formatting</a></li>
</ul></td>
<td><ul>
 <li><a href="https://www.exot.ethz.ch">ExOT public website</a></li>
</ul></td>
</tr>
</table>

