FROM ubuntu:18.04

LABEL Maintainer="Jundat95" \
      Description="Nginx based on Ubuntu minimal 18.04"

RUN apt-get update \
    && apt-get install -y nginx \
    && apt-get install -y vim \
    && apt-get install -y htop 

RUN useradd -ms /bin/bash magento && adduser www-data magento

COPY etc/domain /usr/local/bin/

RUN chmod 775 /usr/local/bin/domain

WORKDIR /var/www/html

CMD ["/bin/bash", "-c", "nginx -g 'daemon off;'"]