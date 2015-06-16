FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y -q apache2 libapache2-mod-php5 php5-mysql git supervisor



ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

VOLUME ["/var/www", "/var/log" ]
           
RUN git clone https://github.com/gothfox/Tiny-Tiny-RSS.git /var/www/html
WORKDIR /var/www/html

ADD config.php config.php
ADD run /usr/local/bin/
RUN chmod +x /usr/local/bin/run

RUN chown www-data:www-data -R /var/www
RUN chmod -R 755 cache/images cache/upload cache/export cache/js feed-icons lock

RUN mkdir -p /var/log/supervisor

EXPOSE 80
EXPOSE 443


CMD ["/usr/local/bin/run"]
