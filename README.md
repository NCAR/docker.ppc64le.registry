#Cross compiling docker registry (distribution) on Power

Docker does not provide a Power based registry:2 image. It must be first cross-compiled on x86 node and then docker built on the power node. 

1. Checkout Repo on x86 machine with docker
````bash
git clone https://github.com/NCAR/docker.ppc64le.registry.git
````
1. test
