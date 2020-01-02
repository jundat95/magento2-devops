FROM ubuntu:18.04

LABEL Maintainer="Jundat95" \
      Description="Varnish Cache"

RUN apt-get update \
    && apt-get install -y vim varnish

COPY etc/default.vcl /etc/varnish/default.vcl

COPY docker-entrypoint.sh /docker-entrypoint.sh

RUN ["chmod", "+x", "/docker-entrypoint.sh"]

ENTRYPOINT [ "/docker-entrypoint.sh" ]

CMD ["/usr/sbin/varnishd", "-F", "-f", "/etc/varnish/default.vcl", "-p", "http_resp_hdr_len=65536", "-p", "http_resp_size=98304"]