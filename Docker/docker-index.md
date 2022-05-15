# Docker

_My Docker notes..._

## What is it:
Docker is an open source platform for building, deploying, and managing containerized applications.

Difference between image & container:
* Image is a logical entity.
* Container is a real world entity.

The image is created once, while the container can be created many times using a container.

## Installing Docker

Installing on Debian (32 bits):

        sudo apt install -y docker.io

* Remove an image  
First stop it:

        docker stop mydockerimage

Then remove the image:

        docker rm mydockerimage

## Dockerfile
A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.

Example:  

        # This is a comment
        FROM ubuntu
        RUN apt-get update
        RUN apt-get install -y nginx
        COPY index.nginx-debian.html /var/www/html/
        CMD nginx -g 'daemon off;'

**Dockerfile commands:**  

**CMD**  
Can be overridden.  
There can only be one CMD instruction in a Dockerfile.  
If you list more than one CMD only the last CMD will take effect.

**COPY**  
Copies files that are locally on the build directory.

**ADD**  
Downloads files (but it is better to use curl) from internet.  
Untars files that are locally on the build directory.

**HEALTHCHECK**  
This directive tells Docker how to determine if the state of the container is normal.  
The HEALTHCHECK instruction tells Docker how to test a container to check that it is still working.

**ENTRYPOINT**  
Like RUN but with options.

**WORKDIR**  
Multiple directories, nested, when the container starts, you are on that directory.

**ENV**  
Sets a environment variable.

## Docker Commands
To build an image on the directory where the Dockerfile is located:

        docker build .

To list images:

       docker images

To list images, you can also:

       docker image ls

To tag images:

       docker build -t NAME:TAG

Where: **NAME** will be under **REPOSITORY** and **TAG** under **TAG** (doh!), for example a TAG might be: "v.1".

To rename an image, if the image already exists:

        docker tag "IMAGE ID" NAME:TAG

To get (download) an image from the internet:

        docker image pull splunk/splunk

To get information from an image:

        docker image inspect ubuntu

To get specific information from the image:

        docker image inspect ubuntu --format='{{.ContainerConfig.Hostname}}'

To clean (delete) unused images:

        docker image prune

**Dangling Images**: Images without tags & images that are not referenced by any container.

Flatten an image by merging the layers:  

        docker export myimage > myimageflat.tar
        cat myimageflat.tar | docker import - myimage:latest

Registry, a stateless, highly scalable server that stores Docker images: Docker Hub.

Push images to Docker Hub:

        docker login

To search images:

        docker search nginx --filter "is-official=true"

To share images:

        docker save myimage > myimage.tar
        docker load < myimage.tar

To export a container to another system as an image tar file:

        docker export my-container > container.tar

**Network**: the default driver is "bridge".

## Run

        docker container run -dt --name mydockerimage the-realname-of-the-docker-image

## Connect to the container

        docker container exec -it the-realname-of-the-docker-image sh

*Example:*

        docker container exec -it busybox sh

# Run a container with a specific program

        docker container run -dt --name container-run-ping busybox ping -c10 www.google.com

This particular container dies after pinging ten times www.google.com.

# List containers

        docker ps
        docker ps -a

# Remove

First stop the containter image:

        docker stop mydockerimage

Then delete the container image:

        docker rm mydockerimage

If running, you can force the deletion of the container using the -f flag:

        docker rm -f mydockerimage

# Remove automagically on exit

        docker container run -dt --rm --name container-run-ping busybox ping -c10 www.google.com

# Disk Usage

        docker system df

For detailed info:

        docker system df -v

## Docker Swarm

Swarm Mananger:

        docker swarm init --advertise-addr IP-address-of-eth0-interface

Only one instance of nginx/ webserver on the workers

        docker service create --name webserver --replicas 1 nginx
        docker service ls
        docker service ps
        docker service rm webserver

Containers running in a service are called "tasks".

Scale Up:

        docker service scale webserver=5 

Scale Down:

        docker service scale webserver=1

Two ways of scaling:
1- 
docker service update --replicas 5 webserver
docker service scale webserver=5

## Kubernetes Networking Model
Kubernetes was built to run on distributed systems where there can be hundreds of worker nodes in which Pods would be running.

1. Pods on a node can communicate with all Pods on all nodes w/o NAT.
2. All Nodes can communicate with all Pods w/o NAT.
3. The IP that a Pod sees itself as its own is the same IP that others Pod see their own.

Four different networking challenges:

1. Container-to-Container Networking
2. Pod-to-Pod Networking
3. Pod-to-Service Networking
4. Internet-to-Service Networking

**1- Container-to-Container Networking:**  
Primarly happens inside a Pod.  
Pods can contain a group of containers with the same IP address.  
Communication between container inside Pods happens via localhost.  

**2- Pod-to-Pod Networking:**  
Bridge to connect the different Pods.

**3- Pod-to-Service Networking:**  
Kubernetes Services can act as an abstraction which can provide a single IP address and DNS thru which can be accessed.  
Endpoints tracks the IP address of the objects that service can send traffic to.

## Liveness Probe  
Apps running for long periods of time eventually transition to a broken state, there is no recovery other than restart.  
Kubernetes provides liveness probes to detect and remedy such situations.

Create the file "**livenessprobe.yaml**":

        apiVersion: v1
        kind: Pod
        metadata:
          name: liveness
        spec:
          containers:
          - name: liveness
            image: ubuntu
            tty: true
            livenessProbe:
              exec:
        	command:
        	- service
        	- nginx
        	- status
              initialDelaySeconds: 20
              periodSeconds: 5


## Storage Class

A storage class provides a way for administrators to describe the "classes" of storage they offer.  
Different classes might map to quality-of-service levels, or to backup policies or to arbitrary policies determined by the cluster administrators.  
Each StorageClass contains the fields provisioner, parameters and reclaimPolicy which are used when a PersistentVolume belonging to the class needs to be dynamically provisioned.

## Links
* [7 Cases When You Should Not Use Docker](https://www.freecodecamp.org/news/7-cases-when-not-to-use-docker/)
* [Docker Healthchecks: Why Not To Use `curl` or `iwr`](https://blog.sixeyed.com/docker-healthchecks-why-not-to-use-curl-or-iwr/)
* [How to install Docker on 32bit machine having Ubuntu 12.04?](https://stackoverflow.com/questions/37989534/how-to-install-docker-on-32bit-machine-having-ubuntu-12-04)
