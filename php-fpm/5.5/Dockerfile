FROM php:5.5-fpm

MAINTAINER Anton Stuchinscky <winshiftq@gmail.com>

# install extension for php
RUN apt-get update && apt-get install -y \
        libpq5 \
        zlib1g-dev \
        libicu-dev \
        g++ \
        libpq-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
        gettext \
    && docker-php-ext-install pgsql pdo pdo_mysql intl pdo_pgsql mbstring gettext gd \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# install xdebug module
RUN pecl install -o -f xdebug \
    && rm -rf /tmp/pear \
    && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20121212/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.idekey = PHPSTORM"       >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=1"       >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_handler=dbgp"   >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=9006"      >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/xdebug.ini


WORKDIR /
COPY php.ini /usr/local/etc/php/

CMD ["php-fpm"]

EXPOSE 9000