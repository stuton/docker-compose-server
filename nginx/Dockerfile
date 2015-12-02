FROM ubuntu:latest

MAINTAINER Anton Stuchinscky <winshiftq@gmail.com>

RUN apt-get update && apt-get install -y nginx && rm /etc/nginx/sites-enabled/*

ADD nginx.conf /etc/nginx/
ADD test.conf /etc/nginx/sites-enabled/

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
