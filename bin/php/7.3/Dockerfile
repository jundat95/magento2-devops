FROM alpine:3.10.2

LABEL Maintainer="Jundat95" \
      Description="PHP-FPM 7.3 based on Alpine Linux."

RUN addgroup -g 1000 -S magento && \
    adduser -u 1000 -S magento -G magento

RUN apk update && apk add openrc

RUN apk add php7-common php7-cli php7-fpm \
    php7-opcache php7-gd php7-mysqli php7-curl \
    php7-intl php7-xsl php7-mbstring php7-zip  \
    php7-bcmath php7-soap


RUN mkdir -p /var/www/html /etc/nginx /sock
RUN chown -R magento:magento /var/www /etc/nginx /etc/php7/conf.d /sock

USER magento:magento

VOLUME /var/www

WORKDIR /var/www/html

CMD ["/usr/sbin/php-fpm7", "-F"]