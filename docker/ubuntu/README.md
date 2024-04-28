# Shadowsocksr Dockerized

## About this image

This image is built to ease the deployment of the Shadowsocksr server daemon with Docker.

For Shadowsocksr clients, you want to visit http://shadowsocksr.org/en/download/clients.html

### What is Shadowsocksr

A secure socks5 proxy designed to protect your Internet traffic.

See http://shadowsocksr.org/

### What is Docker

An open platform for distributed applications for developers and sysadmins.

See https://www.docker.com/

## How to use this image

### Start the daemon for the first time

```bash
$ docker run --name shadowsocksr-app --detach --publish 58338:8338 shadowsocksr/shadowsocksr-libev -k "5ecret!"
```

To publish UDP port for DNS tunnelling, run

```bash
$ docker run --name shadowsocksr-app --detach --publish 58338:8338 --publish 58338:8338/udp shadowsocksr/shadowsocksr-libev -k "5ecret!"
```

To see all supported arguments, run

```bash
$ docker run --rm shadowsocksr/shadowsocksr-libev --help
```

To try the bleeding edge version of Shadowsocksr, run with an `unstable` tag

```bash
$ docker run --name shadowsocksr-app --detach --publish 58338:8338 shadowsocksr/shadowsocksr-libev:unstable -k "5ecret!"
```

### Stop the daemon

```bash
$ docker stop shadowsocksr-app
```

### Start a stopped daemon

```bash
$ docker start shadowsocksr-app
```

### Upgrade

Simply run a `docker pull` to upgrade the image.

```bash
$ docker pull shadowsocksr/shadowsocksr-libev
```

### Use in CoreOS

COMING SOON

### Use with `fig`

COMING SOON

## Limitations

### JSON Configuration File

This image doesn't support the JSON configuration at the moment. But I do plan to add the support in the future. So please stay tuned.

### Specifying Hostname & Port

Docker containers don't have the power to specify on what hostname or port of the host should the service listen to. These have to be specified using the `--publish` argument of `docker run`.

See [Docker run reference](https://docs.docker.com/reference/run/#expose-incoming-ports) for more details.

## References

* [Shadowsocksr - Servers](http://shadowsocksr.org/en/download/servers.html)
* [shadowsocksr-libev](https://github.com/shadowsocksr/shadowsocksr-libev/blob/master/README.md)
