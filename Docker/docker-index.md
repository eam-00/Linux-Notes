# Docker

_My Docker notes..._

## What is it:
Docker is an open source platform for building, deploying, and managing containerized applications.

Difference between image & container:
* Image is a logical entity.
* Container is a real world entity.

The image is created once, while the container can be created many times using a container.

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

## Build
On the directory where the Dockerfile is located:

        docker build .

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


## Links
* [7 Cases When You Should Not Use Docker](https://www.freecodecamp.org/news/7-cases-when-not-to-use-docker/)
