FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y -q apache2 libapache2-mod-php5 php5-mysql git supervisor php5-cli mysql-client 
RUN a2ensite default-ssl
RUN a2enmod ssl

RUN mkdir -p /var/log/supervisor

RUN git clone https://tt-rss.org/git/tt-rss.git /home/ttrss

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

ADD config.php /home/config.php
ADD configure-db.php /home/configure-db.php

ADD run /usr/local/bin/
RUN chmod +x /usr/local/bin/run

#VOLUME ["/var/www" ]

EXPOSE 80
EXPOSE 443


CMD ["/usr/local/bin/run"]
