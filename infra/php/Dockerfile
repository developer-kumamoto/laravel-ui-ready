FROM php:fpm

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get install -y \
  git \
  libzip-dev \
  unzip \
 && apt-get clean \
 && docker-php-ext-install \
   pdo_mysql \
   zip \
 && rm -rf /var/lib/apt/lists/* \
 && curl -sL https://deb.nodesource.com/setup_15.x | bash - \
 && apt-get install -y nodejs \