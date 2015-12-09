FROM registry:2
MAINTAINER windperson@gmail.com

COPY config.yml /etc/docker/registry/config.yml
VOLUME /var/lib/registry
EXPOSE 5000

ENTRYPOINT ["/bin/registry"]
CMD ["/etc/docker/registry/config.yml"]
