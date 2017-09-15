# Cross compiling docker registry (distribution) on Power

Docker does not provide a Power based registry:2 image. It must be first cross-compiled on x86 node and then docker built on the power node. 

1. Checkout repository on x86 machine
````bash
git clone https://github.com/NCAR/docker.ppc64le.registry.git
cd docker.ppc64le.registry/compile/
````
2. Build registry via make. Make sure to set your preferences for the make file variables.
````bash
make GIT_TAG=v2.6.2
````
3. Copy the registry binary to your Power machine
````bash
scp registry $POWERNODE:/tmp/
````
4. Checkout repository on Power (ppc64le) machine
````bash
git clone https://github.com/NCAR/docker.ppc64le.registry.git
cd docker.ppc64le.registry/registry/
````
5. Build and run registry via make. Make sure to set your preferences for the make file variables.
````bash
make GIT_TAG=v2.6.2
````
6. Point docker at your new registry
