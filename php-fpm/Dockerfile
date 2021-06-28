FROM php:7.4-fpm

WORKDIR /var/www/public/cloud

RUN apt-get update && \
    apt-get -y install libxml2-dev libcurl4-openssl-dev libonig-dev zip unzip git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-configure mysqli --with-mysqli=mysqlnd && \
    docker-php-ext-install intl json mbstring mysqli xml curl opcache && \
    pecl install redis apcu && \
    docker-php-ext-enable redis apcu && \
    docker-php-ext-install sockets && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin