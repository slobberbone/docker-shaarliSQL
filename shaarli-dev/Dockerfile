FROM debian:jessie
MAINTAINER VirtualTam <virtualtam@flibidi.net>

RUN apt-get update \
    && apt-get install -y \
       nginx-light php5-fpm php5-gd supervisor \
       git nano vim-nox

ADD https://getcomposer.org/composer.phar /usr/local/bin/composer
RUN chmod 755 /usr/local/bin/composer

COPY nginx.conf /etc/nginx/nginx.conf
COPY supervised.conf /etc/supervisor/conf.d/supervised.conf
COPY phpinfo.php /var/www/index.php

WORKDIR /var/www/html
RUN git clone http://git.gorgones.net/daniel.douat/shaarliSQL.git shaarli \
    && chown -R www-data:www-data .

WORKDIR /var/www/html/shaarli
RUN composer install

VOLUME /var/www/html

EXPOSE 80

CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
