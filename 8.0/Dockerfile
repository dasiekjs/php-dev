FROM php:8.0-fpm

#update
RUN apt-get update
RUN apt-get install -y \
        libzip-dev \
        zip \
        curl \
        libcurl4-openssl-dev\
        libxml2-dev \
        vim \
        libpq-dev \
        libpng-dev \
        libmcrypt-dev

RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql

#install extension
RUN docker-php-ext-install -j$(nproc) iconv gettext intl xml soap opcache pdo pdo_mysql mysqli pdo_pgsql curl zip gd

RUN pecl install mcrypt
RUN docker-php-ext-enable mcrypt

#install xdebug
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && echo -e "\n\
        xdebug.start_with_request=1\n\
        xdebug.discover_client_host=1\n\
        xdebug.mode=debug\n\
        xdebug.connect_back=1\n" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini


#mongodb driver?
RUN pecl install mongodb && docker-php-ext-enable mongodb

#composer <3
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www
USER www
EXPOSE 9000
CMD ["php-fpm"]
