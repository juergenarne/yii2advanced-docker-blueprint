FROM php:8.3-apache

# Update und Installation der benötigten Pakete
RUN apt-get update && apt-get install -y \
    libpq-dev \
    libpng-dev \
    libfreetype6-dev \
    libjpeg-dev \
    libjpeg62-turbo-dev \
    libzip-dev \
    unzip \
    mariadb-client \
    libicu-dev \
    libmemcached-dev \
    libmagickwand-dev \
    zlib1g-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-configure intl \ 
    && docker-php-ext-install -j$(nproc) \
    gd \
    intl \
    pdo_mysql

# Optional: Apache Rewrite-Modul aktivieren
RUN a2enmod rewrite

# Setze den Arbeitsordner
WORKDIR /var/www/html
