FROM ubuntu:18.04

LABEL Maintainer="Jundat95" \
      Description="Cronjob with php 7.2.x cli"

RUN apt-get update

RUN apt-get install -y software-properties-common \
    && add-apt-repository -y ppa:ondrej/php

RUN apt-get install -y php7.2-cli php7.2-xml \
    php7.2-mysql php7.2-intl \
    && apt-get install -y cron \
    && apt-get install -y vim 

VOLUME /var/www

WORKDIR /var/www/html

CMD ["cron", "-f"]