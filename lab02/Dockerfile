# https://hub.docker.com/_/alpine
FROM alpine:latest

COPY entrypoint.sh /var/lib
RUN chmod 755 /var/lib/entrypoint.sh

ENV MESSAGE="os release:"

ENTRYPOINT ["/var/lib/entrypoint.sh"]

CMD ["cat", "/etc/os-release"]