FROM php:8.2-fpm-bullseye

# COPY php.ini
COPY ./php.ini /user/local/etc/php/php.ini

# Composer install
COPY --from=composer:2.5.8 /usr/bin/composer /usr/bin/composer

# install Node.js
COPY --from=node:10.22 /usr/local/bin /usr/local/bin
COPY --from=node:10.22 /usr/local/lib /usr/local/lib

RUN apt-get update && \
    apt-get -y install \
    git \
    zip \
    unzip \
    vim \
    && docker-php-ext-install pdo_mysql bcmath

RUN apt-get -y install nodejs npm && npm install -g n && n 16.17

WORKDIR /var/www/html