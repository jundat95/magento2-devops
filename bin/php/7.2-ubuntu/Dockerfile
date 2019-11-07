FROM ubuntu:18.04

LABEL Maintainer="Jundat95" \
      Description="PHP-FPM 7.2 based on Ubuntu minimal 18.04"

RUN groupadd -g 1000 magento \
    && useradd -g 1000 -u 1000 -d /var/www -s /bin/bash magento

RUN apt-get update

RUN apt-get install -y software-properties-common \
    && add-apt-repository -y ppa:ondrej/php

RUN apt-get install -y php7.2-common php7.2-cli php7.2-fpm  \
    php7.2-opcache php7.2-gd php7.2-mysql php7.2-curl   \
    php7.2-intl php7.2-xsl php7.2-mbstring php7.2-zip   \
    php7.2-bcmath php7.2-soap \
    && apt-get install -y vim \
    && apt-get install -y htop \
    && apt-get install -y curl

COPY etc/php-fpm.conf /etc/php/7.2/fpm/

COPY etc/www.conf /etc/php/7.2/fpm/pool.d/

COPY --from=composer:1.8.6 /usr/bin/composer /usr/bin/composer

RUN mkdir -p /var/www/html /sock /var/log/php/

RUN chown -R magento:magento /var/www /var/log/php/ /sock

RUN echo root:admin@123 | chpasswd

RUN curl -sSLO https://github.com/mailhog/mhsendmail/releases/download/v1.0.0/mhsendmail_linux_amd64 \
  && chmod +x mhsendmail_linux_amd64 \
  && mv mhsendmail_linux_amd64 /usr/local/bin/mhsendmail

RUN echo "[mail function]" >> /etc/php/7.2/fpm/php.ini
RUN echo "sendmail_path = '/usr/local/bin/mhsendmail --smtp-addr=\"mailhog:1025\"'" >> /etc/php/7.2/fpm/php.ini

USER magento

VOLUME /var/www

WORKDIR /var/www/html

ENTRYPOINT ["/usr/sbin/php-fpm7.2"]