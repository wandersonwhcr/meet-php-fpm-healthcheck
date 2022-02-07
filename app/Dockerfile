ARG PHP_VERSION=8.1

FROM php:${PHP_VERSION}-fpm-alpine

COPY . /var/www/html

RUN apk add --no-cache fcgi \
    && echo "pm.status_path = /status" >> /usr/local/etc/php-fpm.d/zz-docker.conf \
    && curl --silent --remote-name https://raw.githubusercontent.com/renatomefi/php-fpm-healthcheck/v0.5.0/php-fpm-healthcheck \
    && install --owner root --group root --mode 755 php-fpm-healthcheck /usr/local/bin/php-fpm-healthcheck \
    && rm -rf php-fpm-healthcheck \
    && find /usr/src -type f -name 'php*' -print -delete

HEALTHCHECK --interval=5s \
    CMD php-fpm-healthcheck || exit 1

USER www-data:www-data
