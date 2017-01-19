FROM php:5.6-apache

# install the PHP extensions we need
RUN set -ex; \
  \
  apt-get update; \
  apt-get install -y \
    libjpeg-dev \
    libpng12-dev \
  ; \
  rm -rf /var/lib/apt/lists/*; \
  \
  docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; \
  docker-php-ext-install gd mysql mysqli opcache

# set recommended PHP.ini settings
COPY ./php_custom.ini /usr/local/etc/php/conf.d/php_custom.ini

# see https://secure.php.net/manual/en/opcache.installation.php
COPY ./opcache.ini /usr/local/etc/php/conf.d/opcache.ini

RUN a2enmod rewrite expires

VOLUME /var/www/html

CMD ["apache2-foreground"]