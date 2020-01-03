# https://hub.docker.com/_/alpine/
# FROM alpine:3.9
FROM alpine@sha256:7746df395af22f04212cd25a92c1d6dbc5a06a0ca9579a229ef43008d4d1302a

LABEL maintainer="sokube@sokube.ch"
LABEL game=2048

RUN set -x && \
    # add nginx
    apk --update add nginx && \
    mkdir /run/nginx

COPY default.conf /etc/nginx/conf.d/default.conf
COPY 2048 /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]