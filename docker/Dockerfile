FROM php:8.2-fpm-alpine as base-system

RUN apk add --no-cache \
    bash \
    php82-zip \
    libxml2-dev \
    libzip-dev \
    zip \
    php82-gd \
    php82-exif \
    libpng libpng-dev libjpeg-turbo libjpeg-turbo-dev freetype freetype-dev libwebp-dev zlib-dev libxpm-dev gd \
    git build-base librdkafka-dev make autoconf g++ libc-dev \
    && pecl install rdkafka \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo pdo_mysql soap zip bcmath gd exif pcntl \
    && docker-php-ext-enable rdkafka

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

