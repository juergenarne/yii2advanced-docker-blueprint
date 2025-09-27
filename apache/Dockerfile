FROM php:8.0-apache

RUN apt-get update && apt-get install -y \
    git \
    libpq-dev \
    libpng-dev \
    libonig-dev \
    libfreetype6-dev \
    libjpeg-dev \
    libjpeg62-turbo-dev \
    libzip-dev \
    unzip \
    mariadb-client \
    mbstring \
    libicu-dev \
    libmemcached-dev \
    libmagickwand-dev \
    zlib1g-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-configure intl \ 
    && docker-php-ext-install -j$(nproc) \
    gd \
    intl \
    pdo \
    pdo_mysql \
    opcache

RUN a2enmod rewrite headers

WORKDIR /var/www/html
