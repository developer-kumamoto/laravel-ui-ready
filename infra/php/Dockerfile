FROM php:fpm

RUN apt-get update && apt-get install -y \
  git \
  libzip-dev \
  unzip \
 && apt-get clean \
 && docker-php-ext-install \
   pdo_mysql \
   zip \
 && rm -rf /var/lib/apt/lists/* \
 && php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
 && curl -sL https://deb.nodesource.com/setup_15.x | bash - \
 && apt-get install -y nodejs \