FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y -q apache2 libapache2-mod-php5 php5-mysql git supervisor
RUN mkdir -p /var/log/supervisor



ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN rm -r /var/www
RUN mkdir -p /var/www

           
RUN git clone https://github.com/gothfox/Tiny-Tiny-RSS.git /var/www/html
WORKDIR /var/www/html

ADD config.php config.php
RUN chown www-data:www-data -R config.php
RUN sed -i -e "s#DBTYPE#$DB_TYPE#g" config.php 
RUN sed -i -e "s#DBHOST#$DB_HOST#"  config.php
RUN sed -i -e "s#DBUSER#$DB_USER#"  config.php
RUN sed -i -e "s#DBNAME#$DB_NAME#"  config.php
RUN sed -i -e "s#DBPASS#$DB_PASS#"  config.php
RUN sed -i -e "s#DBPORT#$DB_PORT#"  config.php
RUN sed -i -e "s#SELFURLPATH#$URL_PATH#" config.php


RUN chmod -R 755 cache/images
RUN chmod -R 755 cache/upload
RUN chmod -R 755 cache/export
RUN chmod -R 755 cache/js
RUN chmod -R 755 feed-icons
RUN chmod -R 755 lock

EXPOSE 80
EXPOSE 443
ADD run /usr/local/bin/
RUN chmod +x /usr/local/bin/run

VOLUME ["/var/www", "/var/log", "/etc" ]

CMD ["/usr/local/bin/run"]
