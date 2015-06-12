FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get install -y -q apache2 libapache2-mod-php5 php5-mysql git
           
git clone https://github.com/gothfox/Tiny-Tiny-RSS.git tt-rss
mv tt-rss /var/www/
ADD config.php /var/www/tt-rss/config.php

EXPOSE 80
EXPOSE 443


