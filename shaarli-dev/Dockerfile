FROM debian:jessie
MAINTAINER VirtualTam <virtualtam@flibidi.net>

RUN apt-get update \
    && apt-get install -y \
       nginx-light php5-fpm php5-gd supervisor \
       nano git

COPY nginx.conf /etc/nginx/nginx.conf
COPY supervised.conf /etc/supervisor/conf.d/supervised.conf
COPY phpinfo.php /var/www/index.php

WORKDIR /var/www
RUN rm -rf html \
    && git clone https://github.com/shaarli/Shaarli.git shaarli \
    && chown -R www-data:www-data .

VOLUME /var/www/shaarli/data

EXPOSE 80

CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
