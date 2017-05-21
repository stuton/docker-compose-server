FROM php:7.1-fpm

MAINTAINER Anton Stuchinscky <winshiftq@gmail.com>

# install extension for php
RUN apt-get update && apt-get install -y \
        libpq5 \
        zlib1g-dev \
        libicu-dev \
        g++ \
        libpcre3-dev \
        libpq-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
        gettext \
    && docker-php-ext-install pgsql pdo pdo_mysql intl pdo_pgsql mbstring gettext \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

# install redis
RUN pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis

# install xdebug module
RUN pecl install -o -f xdebug \
    && rm -rf /tmp/pear \
    && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20121212/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.idekey = PHPSTORM"       >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=1"       >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_handler=dbgp"   >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=9006"      >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_connect_back=1" >> /usr/local/etc/php/conf.d/xdebug.ini

WORKDIR /var/www

CMD ["php-fpm"]

EXPOSE 9000
