FROM php:8.5.2-fpm-alpine3.23

WORKDIR /data/www/rizacare

RUN set -x && \
  apk update && \
  apk add bash libxml2 libxml2-dev curl curl-dev libzip-dev autoconf $PHPIZE_DEPS gnupg oniguruma-dev supervisor nodejs libpng-dev npm linux-headers && \
  docker-php-ext-install mysqli pdo_mysql zip sockets gd && \
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer \
RUN mv composer.phar /usr/local/bin/composer

ARG PUID=1000
ARG PGID=1000
ENV PGID=${PGID}
ENV PUID=${PUID}

RUN apk add --no-cache shadow && \
    groupmod -g ${PGID} www-data && \
    usermod -u ${PUID} -g www-data www-data && \
    apk del shadow

COPY php.ini /usr/local/etc/php/php.ini
COPY www.conf /usr/local/etc/php-fpm.d/www.conf

USER www-data