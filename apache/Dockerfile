FROM php:8.3-apache

# System dependencies für PHP Extensions
RUN apt-get update && apt-get install -y \
    git \
    libpq-dev \
    libpng-dev \
    libonig-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libzip-dev \
    unzip \
    mariadb-client \
    libicu-dev \
    zlib1g-dev \
    imagemagick \
    libmagickwand-dev \
    libmemcached-dev \
    pkg-config \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# PHP Extensions
RUN docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j$(nproc) \
       gd \
       exif \
       intl \
       mbstring \
       pdo \
       pdo_mysql \
       opcache \
       zip

# PECL Extensions
RUN pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install memcached \
    && docker-php-ext-enable memcached

# Apache modules
RUN a2enmod rewrite headers

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html
