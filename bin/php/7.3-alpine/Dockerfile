FROM alpine:3.10.2

LABEL Maintainer="Jundat95" \
      Description="PHP-FPM 7.3 based on Alpine Linux."

RUN addgroup -g 1000 -S magento && \
    adduser -u 1000 -S magento -G magento -s /bin/sh -h /var/www

RUN apk update && apk add openrc && apk add --update busybox-suid

RUN apk add php7-common php7-cli php7-fpm \
    php7-opcache php7-gd php7-mysqli php7-mysqlnd php7-curl \
    php7-intl php7-xsl php7-mbstring php7-zip  \
    php7-bcmath php7-soap php7-json php7-phar php7-iconv \
    php7-pear php7-dev php7-xmlwriter php7-simplexml php7-ctype \
    php7-pdo_mysql


COPY etc/www.conf /etc/php7/php-fpm.d

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN mkdir -p /var/www/html /sock
RUN chown -R magento:magento /var/www /var/log/php7/ /sock 

RUN echo root:admin@123 | chpasswd

USER magento

VOLUME /var/www

WORKDIR /var/www/html

CMD ["/usr/sbin/php-fpm7", "-F"]