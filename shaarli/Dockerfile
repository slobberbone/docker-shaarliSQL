FROM debian:jessie
MAINTAINER VirtualTam <virtualtam@flibidi.net>

RUN apt-get update \
    && apt-get install -y curl unzip nginx-light php5-fpm php5-gd supervisor

COPY nginx.conf /etc/nginx/nginx.conf
COPY supervised.conf /etc/supervisor/conf.d/supervised.conf

WORKDIR /var/www
RUN rm -rf html \
    && curl -L http://git.gorgones.net/daniel.douat/shaarliSQL/repository/archive.zip | unzip - \
    && mv shaarliSQL.git shaarli \
    && chown -R www-data:www-data shaarli

VOLUME /var/www/shaarli/

EXPOSE 80

CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
