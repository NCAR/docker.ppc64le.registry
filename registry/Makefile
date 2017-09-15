DOCKER_TAG          ?= registry
DEBRELEASE          ?= stretch
VOL_REGISTRY        ?= /srv/docker_registry
PATH_BIN_REGISTRY   ?= ./registry

default: run

build: 
        docker build \
                --build-arg DEBRELEASE=$(DEBRELEASE) \
                --build-arg VOL_REGISTRY=$(VOL_REGISTRY) \
                --build-arg PATH_BIN_REGISTRY=$(PATH_BIN_REGISTRY) \
                --rm --network=host -t $(DOCKER_TAG) .

stop: 
        docker kill $(DOCKER_TAG) || /bin/true  
        while docker stop -t 1 $(DOCKER_TAG) ; do /bin/true; done

run: build stop
        docker run -d --rm -it --log-driver=syslog -v /dev/log:/dev/log -v /var/lib/registry:${VOL_REGISTRY} --name $(DOCKER_TAG) $(DOCKER_TAG) 
