FROM php:7.2-apache

USER root

WORKDIR /var/www/html

RUN apt-get update && apt-get install -y \
        libpng-dev \
        zlib1g-dev \
        libxml2-dev \
        libzip-dev \
        libonig-dev \
        zip \
        curl \
        unzip \
    && docker-php-ext-configure gd \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install zip \
    && docker-php-source delete

COPY ./vhost.conf /etc/apache2/sites-available/000-default.conf

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=1.10.22

RUN curl -sL https://deb.nodesource.com/setup_12.x | bash \
    && apt-get install nodejs -y

COPY . /var/www/html
RUN chmod -R 777 /var/www/html/storage/*

# RUN chown -R www-data:www-data /var/www/html \
#     && a2enmod rewrite
