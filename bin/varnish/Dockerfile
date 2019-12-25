FROM varnish:6.0.5

LABEL Maintainer="Jundat95" \
      Description="Varnish Cache"

COPY etc/default.vcl /etc/varnish/default.vcl

COPY docker-entrypoint.sh /docker-entrypoint.sh

RUN ["chmod", "+x", "/docker-entrypoint.sh"]

ENTRYPOINT [ "/docker-entrypoint.sh" ]

CMD ["varnishd", "-F", "-f", "/etc/varnish/default.vcl"]