FROM php:7.2-apache

WORKDIR /var/www/html

# Dependencias do servidor
RUN apt-get update && apt-get install -y \
        libpng-dev \
        zlib1g-dev \
        libxml2-dev \
        libzip-dev \
        libonig-dev \
        zip \
        curl \
        unzip \
        sudo \
    && docker-php-ext-configure gd \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install zip \
    && docker-php-source delete \
    && docker-php-ext-install soap

# Configurando de host do apache
COPY ./vhost.conf /etc/apache2/sites-available/000-default.conf

# Instalando composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=2.1.5

# Instalando NodeJS
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash \
    && apt-get install nodejs -y

# Configurando certificado SSL
RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/ssl-cert-snakeoil.key -out /etc/ssl/certs/ssl-cert-snakeoil.pem -subj "/C=AT/ST=Vienna/L=Vienna/O=Security/OU=Development/CN=dok.painel"
RUN a2enmod rewrite
RUN a2ensite default-ssl
RUN a2enmod ssl
RUN chmod -R 775  /etc/ssl

# Configurando usuário
RUN adduser --disabled-password --gecos '' dok-painel
RUN adduser dok-painel sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER dok-painel