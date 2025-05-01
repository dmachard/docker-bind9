FROM alpine:3.21.3

ARG BIND_VERSION=9.20.8-r0

RUN apk --no-cache add bind=$BIND_VERSION && \
    addgroup -g 1000 bind && adduser -D -H -G bind -u 1000 -S bind && \
    chown -R bind:bind /etc/bind /var/bind

USER bind

EXPOSE 53/udp 53/tcp

# copy default config
COPY named.conf /etc/bind/
ENTRYPOINT ["/usr/sbin/named", "-g", "-c", "/etc/bind/named.conf",  "-u", "bind", "-4"]