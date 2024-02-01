FROM php:8.1-fpm-alpine

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

RUN apk update && apk add zip unzip && docker-php-ext-install pdo_mysql
