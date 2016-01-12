FROM php:5.5-fpm

MAINTAINER Anton Stuchinscky <winshiftq@gmail.com>

#RUN apt-get update && apt-get install -y php5-common php5-cli php5-fpm php5-mcrypt php5-pgsql php5-apcu php5-gd php5-imagick php5-curl php5-intl


# install postgresql modules
RUN apt-get update && apt-get install -y \
        libpq5 \
        libpq-dev \
    && docker-php-ext-install pgsql pdo_pgsql

# install xdebug module
RUN pecl install -o -f xdebug \
    && rm -rf /tmp/pear \
    && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=1"       >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_handler=dbgp"   >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=9000"      >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/xdebug.ini


WORKDIR /
COPY php.ini /usr/local/etc/php/

CMD ["php-fpm"]

EXPOSE 9000