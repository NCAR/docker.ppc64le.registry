ARG DEBRELEASE
FROM debian:$DEBRELEASE as registrybuild
ARG DEBRELEASE
ENV DEBRELEASE=${DEBRELEASE}
ARG GIT_TAG
ENV GIT_TAG=${GIT_TAG}
ENV GOOS=linux 
ENV GOARCH=ppc64le
ENV DOCKER_DIR /go/src/github.com/docker/
ENV DISTRIBUTION_DIR ${DOCKER_DIR}/distribution
ENV DOCKER_BUILDTAGS include_oss include_gcs
ENV GOPATH=/go/

RUN mkdir -p ${DOCKER_DIR}
RUN apt-get -y update && apt-get dist-upgrade -y
RUN apt-get -qy install golang git make
WORKDIR ${DOCKER_DIR}
RUN git clone https://github.com/docker/distribution.git
WORKDIR ${DISTRIBUTION_DIR}
RUN git checkout tags/${GIT_TAG}
RUN make PREFIX=/go clean binaries

