FROM debian:buster
LABEL maintainer="hallo@petermetz.de"


COPY policy-rc.d /usr/sbin/policy-rc.d
RUN chmod +x /usr/sbin/policy-rc.d && \
    apt-get update && apt-get upgrade -y -o Dpkg::Options::="--force-confold" && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
        supervisor cron openssh-server \
        man-db manpages tzdata procps vim less screen \
        dnsutils iputils-ping netcat socat wget curl \
        backupninja rdiff-backup rsync bzip2 zip && \
    ln -sf /usr/share/zoneinfo/Etc/UTC /etc/localtime && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists* /tmp/* /var/tmp/* /etc/ssh/ssh_host_* /etc/ssh/moduli

COPY etc/ /etc/
COPY root/ /root/


CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
