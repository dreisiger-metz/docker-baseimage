FROM dreisigermetz/baseimage-supervisord:latest
LABEL maintainer="hallo@petermetz.de"


RUN apt-get update && apt-get upgrade -y -o Dpkg::Options::="--force-confold" && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
	apache2 python-certbot-apache elinks \
	php libapache2-mod-php php-mysql php-sqlite3 \
        php-bcmath php-curl php-gd php-imagick php-mbstring php-pear \
        mariadb-server sqlite3 && \
    apt-get clean && rm -rf /var/lib/apt/lists* /tmp/* /var/tmp/*

COPY etc/ /etc/
COPY var/ /var/

EXPOSE 80/tcp
EXPOSE 443/tcp

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
