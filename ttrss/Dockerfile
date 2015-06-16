FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y -q apache2 libapache2-mod-php5 php5-mysql git supervisor
RUN mkdir -p /var/log/supervisor



ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf


           
RUN git clone https://github.com/gothfox/Tiny-Tiny-RSS.git /var/www/ttrss
WORKDIR /var/www
ADD config.php /var/www/ttrss/config.php
RUN chown www-data:www-data -R /var/www
RUN sed -i -e "s#DBTYPE#$DB_TYPE#g" /var/www/ttrss/config.php 
RUN sed -i -e "s#DBHOST#$DB_HOST#"  /var/www/ttrss/config.php
RUN sed -i -e "s#DBUSER#$DB_USER#"  /var/www/ttrss/config.php
RUN sed -i -e "s#DBNAME#$DB_NAME#"  /var/www/ttrss/config.php
RUN sed -i -e "s#DBPASS#$DB_PASS#"  /var/www/ttrss/config.php
RUN sed -i -e "s#DBPORT#$DB_PORT#"  /var/www/ttrss/config.php
RUN sed -i -e "s#SELFURLPATH#$URL_PATH#" /var/www/ttrss/config.php



EXPOSE 80
EXPOSE 443
ADD run /usr/local/bin/
RUN chmod +x /usr/local/bin/run

VOLUME /var/www
VOLUME /var/log

CMD ["/usr/local/bin/run"]
