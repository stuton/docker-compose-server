FROM php:7.0-fpm

MAINTAINER Anton Stuchinscky <winshiftq@gmail.com>

#RUN apt-get update && apt-get install -y php5-common php5-cli php5-fpm php5-mcrypt php5-pgsql php5-apcu php5-gd php5-imagick php5-curl php5-intl php5-xdebug
#
#ADD php.ini /etc/php5/fpm/
#ADD www.conf /etc/php5/fpm/pool.d/
#RUN usermod -u 1000 www-data

WORKDIR /var/www

CMD ["php-fpm"]

EXPOSE 9000
