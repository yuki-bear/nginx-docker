FROM yukibear/nginx-php7
MAINTAINER Yuki Sato <yuki.sato.dev@gmail.com>

RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
RUN apt-get -y install nodejs npm
RUN apt-get clean && rm -r /var/lib/apt/lists/*

EXPOSE 3000

