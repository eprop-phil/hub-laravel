# Latest LTS version
FROM alpine:3.9

# Install software
RUN apk update && apk add \
    zip \
    unzip \
    curl \
    tzdata \
    php7-cli \
    php7-fpm \
    php7-curl \
    php7-json \
    php7-opcache \
    php7-mysqli \
    php7-zip \
    php7-xml \
    php7-mbstring \
    php7-bcmath \
    php7-pdo_mysql \
    nginx \
    supervisor

# Configure..
RUN mkdir /run/php

COPY . /code

COPY environment/web/default /etc/nginx/sites-available/default
COPY environment/web/php7 /etc/php7
COPY environment/web/supervisord.conf /etc/supervisord.conf
COPY environment/web/default /etc/nginx/conf.d/default.conf
RUN mkdir -p /run/nginx

EXPOSE 80

CMD supervisord
