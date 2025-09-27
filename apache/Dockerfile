FROM php:8.0-apache

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
    libmagickwand-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-configure intl \
    && docker-php-ext-install -j$(nproc) \
       gd \
       intl \
       mbstring \
       pdo \
       pdo_mysql \
       opcache \
       zip

RUN pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install memcached \
    && docker-php-ext-enable memcached

RUN a2enmod rewrite headers

WORKDIR /var/www/html
