FROM php:7.2-fpm-stretch

LABEL Maintainer="Jundat95" \
      Description="PHP-FPM 7.3 based on Alpine Linux."

RUN groupadd -g 1000 magento \
    && useradd -g 1000 -u 1000 -d /var/www -s /bin/bash magento

RUN mkdir -p /etc/nginx/html /var/www/html /sock
RUN chown -R magento:magento /etc/nginx /var/www /usr/local/etc/php/conf.d /sock

COPY etc/www.conf /usr/local/etc/php-fpm.d/
COPY etc/php-fpm.conf /usr/local/etc/
# COPY conf/php.ini /usr/local/etc/php/

USER magento:magento

VOLUME /var/www

WORKDIR /var/www/html