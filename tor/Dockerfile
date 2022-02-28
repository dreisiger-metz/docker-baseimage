FROM dreisigermetz/baseimage-supervisord:latest
LABEL maintainer="hallo@petermetz.de"


RUN apt-get update && apt-get upgrade -y -o Dpkg::Options::="--force-confold" && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y tor elinks && \
    apt-get clean && rm -rf /var/lib/apt/lists* /tmp/* /var/tmp/*

COPY etc/ /etc/


CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
