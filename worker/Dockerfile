FROM riz2-php

WORKDIR /data/www/admin

USER root

COPY supervisord.conf /etc/supervisord.conf
RUN touch /var/log/supervisord.log
RUN mkdir -p /var/log/supervisor

USER www-data

EXPOSE 9001
ENTRYPOINT ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisord.conf"]