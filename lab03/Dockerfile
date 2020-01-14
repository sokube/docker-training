# https://hub.docker.com/_/alpine/
# FROM alpine:3.9
FROM alpine@sha256:7746df395af22f04212cd25a92c1d6dbc5a06a0ca9579a229ef43008d4d1302a

LABEL maintainer="sokube@sokube.ch"
LABEL game=2048

RUN set -x && \
    # add nginx
    apk --no-cache add nginx=1.14.2-r4 && \
    mkdir /run/nginx && \
    chown -R nginx /var/lib/nginx/logs && \
    chown -R nginx /var/log/nginx && \
    chown -R nginx /run/nginx

COPY --chown=nginx nginx.conf /etc/nginx/nginx.conf
COPY --chown=nginx default.conf /etc/nginx/conf.d/default.conf
COPY --chown=nginx 2048 /usr/share/nginx/html

EXPOSE 8080

USER nginx

CMD ["nginx", "-g", "daemon off;"]