# SHub
Recipes for Singularity images to be built on Singularity Hub.

[![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/4666)

## ArgonCube Optical Simulation [<img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" width="30">](https://github.com/PPKoller/ArCubeOptSim) [<img src="https://github.com/PPKoller/SHub/blob/master/.ArCube_Logo.png" width="100" align="right">](https://argoncube.org/)
### 1. Pull image:
The optical simulation software container can be pulled directly via the Singularity command:\
(size ~ 1.4G)
```bash
singularity pull shub://PPKoller/SHub:root6.geant4.optsim.ubuntu-18.04
```
### 2. Image default checks:
Performing the Singularity default checks should return `PASS: (retval=0)`.
```bash
mv PPKoller-SHub-master-root6.geant4.optsim.ubuntu-18.04.simg OptSim.simg
singularity check --tag default OptSim.simg
```
### 3. Export I/O binding paths:
Using the environment variable `$SINGULARITY_BINDPATH` there won't be any need to bind I/O paths manually later.
```bash
mkdir input output
export SINGULARITY_BINDPATH="input/,output/"
```
### 4. Run instructions:
Running the container without any arguments will return a list of the available apps including a short description on what it does and what parameters you might need to provide.
```bash
singularity run OptSim.simg
```
### 5. Run apps:
(more details coming soon!)
### [optional]
#### Build and shell into writable sandbox image:
```bash
sudo singularity build --sandbox OptSim OptSim.simg
sudo singularity shell --writable OptSim
```
#### Build compressed read-only squashfs image from sandbox image:
```bash
sudo singularity build OptSim_edited.simg OptSim
```
