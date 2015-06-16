FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y -q apache2 libapache2-mod-php5 php5-mysql git supervisor

RUN git clone https://github.com/gothfox/Tiny-Tiny-RSS.git /home/ttrss

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

ADD config.php /home/config.php

ADD run /usr/local/bin/
RUN chmod +x /usr/local/bin/run

VOLUME ["/var/www" ]

EXPOSE 80
EXPOSE 443


CMD ["/usr/local/bin/run"]
