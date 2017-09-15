DOCKER_TAG      ?= registrybuild
DEBRELEASE      ?= stretch
GIT_TAG         ?= v2.6.2

build: 
	docker build \
		--build-arg DEBRELEASE=$(DEBRELEASE) \
		--build-arg GIT_TAG=$(GIT_TAG) \
		--rm --network=host -t $(DOCKER_TAG) .

	docker run -d --rm -it --network=none --name $(DOCKER_TAG) $(DOCKER_TAG) 

	docker cp $(DOCKER_TAG):/go/bin/registry registry

	docker stop -t 1 $(DOCKER_TAG)

