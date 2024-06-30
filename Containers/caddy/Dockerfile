# syntax=docker/dockerfile:latest
FROM caddy:2.8.4-alpine

COPY --chown=33:33 Caddyfile /Caddyfile
COPY --chmod=775 start.sh /start.sh
COPY --chmod=775 healthcheck.sh /healthcheck.sh

RUN set -ex; \
    apk upgrade --no-cache -a; \
    apk add --no-cache shadow; \
    groupmod -g 33 caddy; \
    usermod -u 33 -g 33 caddy; \
    apk del --no-cache shadow; \
    chown -R 777 /tmp; \
    \
    apk add --no-cache \
        bash \
        tzdata \
        ca-certificates \
        openssl \
        bind-tools \
        netcat-openbsd; \
    \
    echo "root:$(openssl rand -base64 12)" | chpasswd

USER caddy

ENTRYPOINT ["/start.sh"]
CMD ["/usr/bin/caddy run", "--config", "/tmp/Caddyfile"]

HEALTHCHECK CMD /healthcheck.sh
LABEL com.centurylinklabs.watchtower.enable="false"
