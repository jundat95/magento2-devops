FROM ubuntu:18.04

LABEL Maintainer="Jundat95" \
      Description="Cronjob with php 7.2.x cli"

# RUN groupadd -g 1000 magento \
#     && useradd -g 1000 -u 1000 -d /var/www -s /bin/bash magento

RUN apt-get update

RUN apt-get install -y software-properties-common \
    && add-apt-repository -y ppa:ondrej/php

RUN apt-get install -y php7.2-cli \
    && apt-get install -y cron \
    && apt-get install -y vim \
    && apt-get install -y htop 

# COPY etc/php-fpm.conf /etc/php/7.2/fpm/

# COPY etc/www.conf /etc/php/7.2/fpm/pool.d/

# COPY --from=composer:1.8.6 /usr/bin/composer /usr/bin/composer

# RUN mkdir -p /var/www/html /sock /var/log/php/

# RUN chown -R magento:magento /var/www /var/log/php/ /sock

# RUN echo root:admin@123 | chpasswd

# USER magento

ADD start.sh /start.sh
RUN chmod 777 /start.sh

VOLUME /var/www

WORKDIR /var/www/html

ENTRYPOINT ["./start.sh"]