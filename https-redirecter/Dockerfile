FROM ubuntu:14.04
MAINTAINER Remi D

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y -q lighttpd

ADD redirect-http.conf /etc/lighttpd/conf-available/99-redirect-http.conf
RUN ln -sf /etc/lighttpd/conf-available/99-redirect-http.conf /etc/lighttpd/conf-enabled/99-redirect-http.conf

RUN /etc/init.d/lighttpd restart

EXPOSE 80


