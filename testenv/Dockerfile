FROM debian:latest


RUN apt-get update -y && \
	DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
	apache2 ssl-cert &&\
	apt-get clean && rm -rf /var/lib/apt/lists/*

RUN a2enmod ssl && a2enmod headers && a2ensite default-ssl.conf

COPY default-ssl.conf /etc/apache2/sites-available/default-ssl.conf
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
# net-tools vim for debugging

# CMD [ "/usr/sbin/apache2", "-k", "start" ]
ENV APACHE_CONFDIR=/etc/apache2
ENV APACHE_ENVVARS=/etc/apache2/envvars
ENV LANG=C

CMD apachectl -D FOREGROUND

