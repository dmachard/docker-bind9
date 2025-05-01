# ISC Bind9 DNS Server Docker Image

This *[bind9](https://gitlab.isc.org/isc-projects/) Docker Image* is based on **Alpine**.

## Supported tags and respective `Dockerfile` links

- [`9.20.8-r0`, `latest`](https://github.com/dmachard/docker-bind9/tree/master/.20.8-r0)
- [`9.18.33-r0`, `latest`](https://github.com/dmachard/docker-bind9/tree/master/9.18.33-r0)
- [`9.18.27-r0`](https://github.com/dmachard/docker-bind9/tree/master/9.18.27-r0)
- [`9.18.24-r1`](https://github.com/dmachard/docker-bind9/tree/master/9.18.24-r1)

## How to use this image

The default configuration is with recursor mode.
Run bind9 with the following command:

```bash
sudo docker run --name=bind -d -p 53:53/udp -p 53:53/tcp dmachard/bind9:latest
```

Execute rndc

```bash
sudo docker exec bind /usr/sbin/rndc reload
```

## Custom configuration

You can run this image and provide your own bind configuration like that:

```bash
sudo docker run --name=bind -d -p 5354:53/udp -p 5354:53/tcp -v $PWD/named.conf:/etc/bind/named.conf dmachard/bind9:latest
```