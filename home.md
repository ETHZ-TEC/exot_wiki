# Experiment Orchestration Toolkit

Welcome to the __Experiment Orchestration Toolkit__, short __ExOT__, knowledge base.
__ExOT__ was build to orchestrate experiments for the evaluation of covert channels in multicore systems (e.g. Thermal Covert Channel[^1], Power Covert Channel[^2], Frequency Covert Channel[^3]). The Toolkit has been [described in a recent paper](https://doi.org/10.3929/ethz-b-000377986) which will appear in the proceedings of “Design, Automation & Test in Europe Conference & Exhibition (DATE 2020), Grenoble, France, March 9-13, 2020”.

### Get started
In order to take advantage of all features of ExOT, please follow the steps bellow to get a basic setup:

Make sure you have the following software installed:
1. python 3.7 # TODO LINK
1. poetry # TODO LINK 
1. Android Studio # TODO LINK

Create an ExOT directory and clone all the ExOT repositories into this directory and initialise the submodules, using following script:

```bash
for repo in eengine app_unx app_apk compilation; do
  git clone https://gitlab.ethz.ch/tec/public/exot/${repo}.git
  cd ${repo}
  git checkout v1.1.0
  git submodule --init --recursive update
  cd ..
done
```

Setup the docker environment, using the instructions in the [README](https://gitlab.ethz.ch/tec/public/exot/compilation/blob/develop/README.md), to be able to compile deployment applications.

<table style="border:1px solid black;margin-left:auto;margin-right:auto;width:100%;float:center">
<!-- ############################### Application development ############################### -->
<tr><td colspan="2" align="center"><h1 id="applications">Developing deployment applications for ExOT</h1></td></tr>
<tr>
<td width=50%><ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/app_lib">The C++ application library</a>
 <ul>
  <li><a href="1.-The-Application-Library/Framework-overview">Overview, structure & terminology</a></li>
  <li><a href="1.-The-Application-Library/Using-the-library">Using the library in your project</a></li>
  <li><a href="1.-The-Application-Library/Contributing-to-the-library">Contributing to the library</a></li>
  <li><a href="1.-The-Application-Library/The-core-framework">The core framework design</a></li>
  <li><a href="1.-The-Application-Library/Provided-components">Provided components</a></li>
  <li><a href="1.-The-Application-Library/Available-metering-modules">Available metering modules</a></li>
  <li><a href="1.-The-Application-Library/Platform-specific-primitives">Platform specific primitives</a></li>
  <li><a href="1.-The-Application-Library/Utilities">Utilities</a></li>
 </ul>
</ul></td>
<td width=50%><ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/compilation">The docker based compilation suite</a>
 <ul>
  <li><a href="4.-How-to/Dockerised-build-environment">Docker-based build environment</a></li>
 </ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/app_unx">UNIX applications</a>
 <ul>
  <li><a href="2.-The-Applications/Application-Index">Unix application index</a></li>
 </ul>
 <li><a href="https://gitlab.ethz.ch/tec/research/exot/app_apk">The Android NDK integration</a>
 <ul>
  <li><a href="2.-The-Applications/Android-Application-Index)">Android application index</a></li>
  <li><a href="2.-The-Applications/Android-Intent-Proxy)">Android Intent Proxy</a></li>
 </ul>
</ul></td>
</tr>
<tr><td colspan="2">How to:</h1></td></tr>
<tr>
<td><ul>
  <li><a href="4.-How-to/Creating-metering-modules">Creating metering modules</a></li>
  <li><a href="4.-How-to/Creating-process-network-components">Creating process network components</a></li>
</ul></td>
<td><ul>
  <li><a href="4.-How-to/Assembling-metering-modules">Assembling metering modules</a></li>
  <li><a href="4.-How-to/Building-applications">Building applications</a></li>
</ul></td>
</tr>
<!-- ###############################    Experiment Engine    ############################### -->
<tr><td colspan="2", align="center"><h1 id="eengine"><a href="https://gitlab.ethz.ch/tec/research/exot/eengine">The experiment engine</a></h1></td></tr>
<td><ul>
 <li><a href="3.-The-Data-Processing-Framework/The-Ecosystem">The ecosystem</a></li>
 <li><a href="3.-The-Data-Processing-Framework/Information-flow">Information flow</a></li>
 <li><a href="3.-The-Data-Processing-Framework/Experiment-structure">Experiment structure</a></li>
</ul></td>
<td><ul>
 <li><a href="3.-The-Data-Processing-Framework/Experiment-drivers">Experiment drivers</a></li>
 <li><a href="3.-The-Data-Processing-Framework/Support-library">Support library & utilities</a></li>
</ul></td>
</tr>
<!-- ###############################    General     ############################### -->
<tr><td colspan="2", align="center"><h1 id="theory">General</h1></td></tr>
<tr>
<td><ul>
 <li><a href="4.-How-to/Code-style-and-formatting">Code style and formatting</a></li>
</ul></td>
<td><ul>
 <li><a href="https://www.exot.ethz.ch">ExOT public website</a></li>
</ul></td>
</tr>
</table>


