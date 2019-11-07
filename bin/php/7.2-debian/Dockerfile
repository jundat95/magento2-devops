FROM php:7.2-fpm-stretch

LABEL Maintainer="Jundat95" \
      Description="PHP-FPM 7.3 based on Alpine Linux."

RUN apt-get update && apt-get install -y \
  cron \
  git \
  gzip \
  libfreetype6-dev \
  libicu-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng-dev \
  libxslt1-dev \
  lsof \
  mysql-client \
  vim \
  zip

RUN docker-php-ext-configure \
  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install \
  bcmath \
  gd \
  intl \
  mbstring \
  opcache \
  pdo_mysql \
  soap \
  xsl \
  zip

RUN groupadd -g 1000 magento \
    && useradd -g 1000 -u 1000 -d /var/www -s /bin/bash magento

RUN mkdir -p /etc/nginx/html /var/www/html /sock
RUN chown -R magento:magento /etc/nginx /var/www /usr/local/etc/php/conf.d /sock

COPY etc/www.conf /usr/local/etc/php-fpm.d/
COPY etc/php-fpm.conf /usr/local/etc/
# COPY conf/php.ini /usr/local/etc/php/

RUN curl -sSLO https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 \
  && chmod +x mhsendmail_linux_amd64 \
  && mv mhsendmail_linux_amd64 /usr/local/bin/mhsendmail

RUN echo "[mail function]" >> cfg/php-ini-7.2/mailhog.ini
RUN echo "sendmail_path = '/usr/local/bin/mhsendmail --smtp-addr=\"mailhog:1025\"'" >> cfg/php-ini-7.2/mailhog.ini

USER magento:magento

VOLUME /var/www

WORKDIR /var/www/html