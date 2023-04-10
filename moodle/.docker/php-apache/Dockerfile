FROM php:8.0-apache

WORKDIR /var/www/html

ENV TZ=UTC \
  LANG=en_US.UTF-8 \
  LANGUAGE=en_US:en \
  LC_ALL=en_US.UTF-8 \
  COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_MEMORY_LIMIT=-1

# Install dependencies
RUN apt update && \
    apt install --no-install-recommends -y \
    zlib1g-dev \
    libpng-dev \
    libzip-dev \
    libonig-dev \
    libicu-dev \
    libxml2-dev \
    unzip

RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd zip mysqli intl soap opcache

RUN a2enmod rewrite

# Install Composer
COPY --from=composer/composer:1-bin /composer /usr/bin/composer
