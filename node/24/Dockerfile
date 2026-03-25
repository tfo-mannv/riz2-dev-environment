FROM node:24.14.0

ARG PUID=1000
ARG PGID=1000
ENV PGID=${PGID}
ENV PUID=${PUID}

RUN usermod -u $PGID node &&  \
    groupmod -g $PUID node

RUN npm install pm2 -g

EXPOSE 8084

USER node