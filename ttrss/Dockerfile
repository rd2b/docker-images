FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get install -y -q apache2 libapache2-mod-php5 php5-mysql git
RUN rm -r /var/www
           
RUN git clone https://github.com/gothfox/Tiny-Tiny-RSS.git /var/www
WORKDIR /var/www
ADD config.php /var/www/tt-rss/config.php
RUN chown www-data:www-data -R /var/www



EXPOSE 80
EXPOSE 443

RUN /etc/init.d/apache2 start
