# PHG-NCSU
This workspace includes tutorials for running Practical Haplotype Graph (PHG) docker on the NCSU Hazel server. \
More information on the PHG can be found [here](https://academic.oup.com/bioinformatics/article/38/15/3698/6617344).
Detailed tutorial for PHG can be found [here]
## Docker 
First Docker has to be installed in your system. The detailed process is explained [here](https://docs.docker.com/desktop/install/mac-install/).
## Apptainer 
[Apptainer](https://apptainer.org/docs/user/latest/quick_start.html) is used to run docker images in a server. We first need to download it locally. If you are using Linux you can do it using Apptainer, but I use Mac OS so I use docker to download it and then convert it to sif. 
### Pulling the docker image locally
```
docker pull sylabsio/lolcow
```
### Saving the docker image as tar
```
docker save sylabsio/lolcow > lolcow.tar
```
### Transfer the file into the server 
```
scp lolcow.tar username@login.hpc.ncsu.edu:<location>
```
### Build a SIF file from the tar in the **server**
```
apptainer build lolcow.sif docker-archive://lolcow.tar
```
### Run the docker image
```
apptainer run lolcow.sif
```

