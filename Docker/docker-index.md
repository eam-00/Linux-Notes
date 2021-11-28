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

## Kubernetes Networking Model
Kubernetes was built to run on distributed systems where there can be hundreds of worker nodes in which Pods would be running.

1. Pods on a node can communicate with all Pods on all nodes w/o NAT.


## Liveness Probe  
Apps running for long periods of time eventually transition to a broken state, there is no recovery other than restart.  
Kubernetes provides liveness probes to detect and remedy such situations.

Create the file "livenessprobe.yaml":

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
