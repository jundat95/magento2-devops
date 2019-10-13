FROM ubuntu:18.04

LABEL MAINTAINER="Jundat95"

RUN apt-get update \
    && apt-get install -y nginx \
    && apt-get install -y vim \
    && apt-get install -y htop 

RUN useradd -ms /bin/bash magento && adduser www-data magento

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# COPY etc/nginx/magento.conf /etc/nginx/conf.d

WORKDIR /var/www/html

CMD ["/bin/bash", "-c", "nginx -g 'daemon off;'"]