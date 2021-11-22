
# Docker

Some random Docker notes...  
Difference between image & container:  
* Image is a logical entity.
* Container is a real world entity.

The image is created once, while the container can be created many times using a container.

* Remove  
First stop it:  

        docker stop mydockerimage
Then remove it:

        docker rm mydockerimage

