FROM riz2-php

WORKDIR /data/www/admin

USER root

COPY supervisord.conf /etc/supervisord.conf
RUN touch /var/log/supervisord.log
RUN mkdir -p /var/log/supervisor

## setup crond
RUN apk add --no-cache dcron

COPY crontab /var/spool/cron/crontabs/www-data

RUN chmod 0600 /var/spool/cron/crontabs/www-data

RUN touch /var/log/cron.log && chown www-data:www-data /var/log/cron.log
RUN chmod 4755 /usr/bin/crontab

EXPOSE 9001
ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]