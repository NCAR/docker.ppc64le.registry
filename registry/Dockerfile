ARG DEBRELEASE
FROM ppc64le/debian:${DEBRELEASE}
ARG DEBRELEASE
ENV DEBRELEASE=${DEBRELEASE}
ARG VOL_REGISTRY
ENV VOL_REGISTRY=${VOL_REGISTRY}
ARG PATH_BIN_REGISTRY
ENV PATH_BIN_REGISTRY=${PATH_BIN_REGISTRY}

RUN apt-get -y update && apt-get dist-upgrade -y
RUN apt-get -qy install ca-certificates apache2-utils git

RUN mkdir -p /var/lib/registry /etc/docker/registry/
RUN git clone https://github.com/docker/distribution-library-image.git
WORKDIR /distribution-library-image
RUN cp registry/config-example.yml /etc/docker/registry/config.yml
RUN cp docker-entrypoint.sh /entrypoint.sh
COPY ${PATH_BIN_REGISTRY} /bin/registry

VOLUME ["/var/lib/registry"]
EXPOSE 5000
ENTRYPOINT ["/entrypoint.sh"]

CMD ["/etc/docker/registry/config.yml"]
