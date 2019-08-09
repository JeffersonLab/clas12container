# clas12 Simulations Software Distribution


This repo contains the dockerfile used to build the production version of the CLAS12 simulation + reconstruction packages. 
The container contains:


- the production version of the [gemc clas12tag](https://github.com/gemc/clas12Tags)
- the production version of the [reconstruction software](https://github.com/JeffersonLab/clas12-offline-software)

This repo is linked to the hub.docker.com repo: [jeffersonlab/clas12simulations](https://cloud.docker.com/u/jeffersonlab/repository/docker/jeffersonlab/clas12simulations)
Any Repository change will trigger a new docker image creation.

## Open Source Grid Singulartity Image Creation

Docker image changes in hub.docker.com will trigger the creation of the singularity image within about one hour.

The image is loaded in:

```/cvmfs/singularity.opensciencegrid.org/jeffersonlab/clas12simulations:production```


TODO: ASSUME Geant4 in /cvmfs/geant4.cern.ch/share/data

