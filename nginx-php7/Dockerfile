FROM nginx:1.15.3
MAINTAINER Yuki Sato <yuki.sato.dev@gmail.com>

RUN apt-get update && apt-get -y install curl apt-transport-https lsb-release ca-certificates
RUN curl -o /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg \
    && sh -c 'echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list' \
    && apt-get update \
    && apt-get -y install php7.2 php7.2-common php7.2-cli php7.2-fpm \
    && apt-get -y install php-pear php7.2-curl php7.2-dev php7.2-gd php7.2-mbstring php7.2-zip php7.2-mysql php7.2-xml

RUN mkdir -p /var/run/php && chown www-data:www-data /var/run/php
RUN apt-get -y install supervisor
ADD conf/supervisord.conf /etc/supervisor/supervisord.conf

ADD conf/nginx.conf /etc/nginx/
ADD conf/www.conf /etc/php/7.2/fpm/pool.d/

RUN apt-get clean && rm -r /var/lib/apt/lists/*

EXPOSE 80
EXPOSE 443

CMD ["supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]

