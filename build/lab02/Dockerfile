FROM alpine:latest

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