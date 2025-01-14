shadowsocksr-libev
=================

[shadowsocksr-libev][1] is a lightweight secured socks5 proxy for embedded
devices and low end boxes.  It is a port of [shadowsocksr][2] created by
@clowwindy maintained by @madeye and @linusyang.

Suppose we have a VPS running Debian or Ubuntu.
To deploy the service quickly, we can use [docker][3].

## Install docker

```
$ curl -sSL https://get.docker.com/ | sh
$ docker --version
```

## Build docker image

```bash
$ curl -sSL https://github.com/shadowsocksr/shadowsocksr-libev/raw/master/docker/alpine/Dockerfile | docker build -t shadowsocksr-libev .
$ docker images
```

> You can also use a pre-built docker image: [vimagick/shadowsocksr-libev][4] ![][5].

## Run docker container

```bash
$ docker run -d -e METHOD=aes-256-cfb -e PASSWORD=9MLSpPmNt -p 8388:8388 --restart always shadowsocksr-libev
$ docker ps
```

> :warning: Click [here][6] to generate a strong password to protect your server.

## Use docker-compose to manage (optional)

It is very handy to use [docker-compose][7] to manage docker containers.
You can download the binary at <https://github.com/docker/compose/releases>.

This is a sample `docker-compose.yml` file.

```yaml
shadowsocksr:
  image: shadowsocksr-libev
  ports:
    - "8388:8388"
  environment:
    - METHOD=aes-256-cfb
    - PASSWORD=9MLSpPmNt
  restart: always
```

It is highly recommended that you setup a directory tree to make things easy to manage.

```bash
$ mkdir -p ~/fig/shadowsocksr/
$ cd ~/fig/shadowsocksr/
$ curl -sSLO https://github.com/shadowsocksr/shadowsocksr-libev/raw/master/docker/alpine/docker-compose.yml
$ docker-compose up -d
$ docker-compose ps
```

## Finish

At last, download shadowsocksr client [here][8].
Don't forget to share internet with your friends.

```yaml
{
    "server": "your-vps-ip",
    "server_port": 8388,
    "local_address": "0.0.0.0",
    "local_port": 1080,
    "password": "9MLSpPmNt",
    "timeout": 600,
    "method": "aes-256-cfb"
}
```

[1]: https://github.com/shadowsocksr/shadowsocksr-libev
[2]: https://shadowsocksr.org/en/index.html
[3]: https://github.com/docker/docker
[4]: https://hub.docker.com/r/vimagick/shadowsocksr-libev/
[5]: https://badge.imagelayers.io/vimagick/shadowsocksr-libev:latest.svg
[6]: https://duckduckgo.com/?q=password+12&t=ffsb&ia=answer
[7]: https://github.com/docker/compose
[8]: https://shadowsocksr.org/en/download/clients.html
