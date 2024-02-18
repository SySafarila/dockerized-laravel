FROM php:8.1-fpm-alpine

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

RUN apk update 
RUN apk add zip unzip libpng-dev
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install gd