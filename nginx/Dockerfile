FROM nginx:1.18.0-alpine


RUN apk add --no-cache bash

ADD nginx.conf /etc/nginx/nginx.conf

WORKDIR /data/www/
