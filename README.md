# PHG-NCSU
This workspace provides tutorials for running the Practical Haplotype Graph (PHG) Docker on the NCSU Hazel server. The PHG is a powerful tool for analyzing haplotype data. You can find more information about PHG [here](https://academic.oup.com/bioinformatics/article/38/15/3698/6617344).

## Docker Installation
Before proceeding, you need to install Docker on your local system. The detailed installation process can be found [here](https://docs.docker.com/desktop/install/mac-install/).
## Apptainer 
Apptainer is used to run docker images in a server. More information can be found [here](https://apptainer.org/docs/user/latest/quick_start.html).

## Running the Docker Images
To run the Docker image, follow these steps:
### Pulling the Docker Image Locally
First, download the Docker image to your local system
```
docker pull sylabsio/lolcow
```
### Saving the Docker Image as Tar File
Save the Docker image as a tar file. 
```
docker save sylabsio/lolcow > lolcow.tar
```
### Transferring the Tar File to the Server
Transfer the lolcow.tar file to the server using the scp command. Replace username with your actual username and <location> with the desired destination path on the server.
```
scp lolcow.tar username@login.hpc.ncsu.edu:<location>
```
### Build a SIF File from the Tar on the Server
On the server, build a SIF (Singularity Image Format) file from the tar using Apptainer.
```
apptainer build lolcow.sif docker-archive://lolcow.tar
```
### Run the Docker Image
Finally, run the Docker image using Apptainer.
```
apptainer run lolcow.sif
```

