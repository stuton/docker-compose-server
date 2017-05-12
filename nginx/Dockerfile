FROM nginx

MAINTAINER Anton Stuchinscky <winshiftq@gmail.com>

ADD config/nginx.conf /etc/nginx/
ADD sites-enabled/ /etc/nginx/sites-enabled/

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
