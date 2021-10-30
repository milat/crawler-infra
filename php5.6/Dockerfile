FROM php:5.6-fpm

# Atualizando certificados SSL
RUN apt-get update; \
    sed -i 's/mozilla\/DST_Root_CA_X3.crt/!mozilla\/DST_Root_CA_X3.crt/g' /etc/ca-certificates.conf; \
    update-ca-certificates;

# Instalando libs
RUN apt-get update; \
    apt-get -y --no-install-recommends install \
        build-essential \
        libpng-dev \
        libjpeg62-turbo-dev \
        libfreetype6-dev \
        locales \
        zip \
        vim \
        unzip \
        git \
        iputils-ping \
        catdoc \
        poppler-utils \
        libc-client-dev \
        libkrb5-dev; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Instalando extensoes docker
RUN docker-php-ext-install mysqli pdo pdo_mysql mbstring zip

# Instalando pacotes
RUN pecl install xdebug-2.5.5 mongodb-1.7.4 mongo rar

# Habilitando pacotes
RUN docker-php-ext-enable xdebug rar

# Instalando composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Setando php ini
COPY php.ini /usr/local/etc/php/