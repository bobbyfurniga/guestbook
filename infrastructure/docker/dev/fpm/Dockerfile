FROM php:7.2.7-fpm-alpine3.7

# Xdebug extension
#RUN apk --no-cache add pcre-dev ${PHPIZE_DEPS} \
#    && pecl install xdebug \
#    && docker-php-ext-enable xdebug \
#    && apk del pcre-dev ${PHPIZE_DEPS}

RUN set -ex \
#   Mysql PDO
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql \
    && docker-php-ext-install pdo_mysql \
#    Postgres PDO
    && apk --no-cache add postgresql-dev \
    && docker-php-ext-configure pdo_pgsql --with-pgsql \
    && docker-php-ext-install pdo_pgsql \
#   Opcache
    && docker-php-ext-configure opcache --enable-opcache \
    && docker-php-ext-install opcache \
#   Bcmath
    && docker-php-ext-configure bcmath --enable-bcmath \
    && docker-php-ext-install bcmath \
#   Clean apk
    && rm -rf /var/cache/apk/* /var/www/html


RUN apk --no-cache add git bash g++ make libpng-dev libpng-dev make gcc nodejs-npm~=8.9  \
    && rm -rf /var/cache/apk/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer


WORKDIR /var/www/project