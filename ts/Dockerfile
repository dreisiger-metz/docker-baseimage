FROM dreisigermetz/baseimage-supervisord:202303-debian10
LABEL maintainer="hallo@petermetz.de"


ARG ADDITIONAL_PACKAGES=""
ENV ADDITIONAL_PACKAGES=${ADDITIONAL_PACKAGES}
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get upgrade -y -o Dpkg::Options::="--force-confold" && \
    apt-get install -y rsyslog fail2ban xauth \
        xfce4 xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-netload-plugin \
        xfce4-screenshooter xfce4-taskmanager xfce4-xkb-plugin xfce4-terminal \
        firefox-esr \
        $ADDITIONAL_PACKAGES && \
    apt-get remove -yy xscreensaver && apt-get autoremove -yy

COPY contrib/ /root/contrib/
RUN chmod +x /root/contrib/xrdp-installer-1.4.4.sh && \
    /root/contrib/xrdp-installer-1.4.4.sh -c
#    apt-get clean && rm -rf /var/lib/apt/lists* /tmp/* /var/tmp/* /root/xorgxrdp /root/xrdp

COPY etc/ /etc/

EXPOSE 22/tcp
EXPOSE 3389/tcp

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
