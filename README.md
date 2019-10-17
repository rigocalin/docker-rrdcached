<p align="center"><a href="https://github.com/crazy-max/docker-rrdcached" target="_blank"><img height="128"src="https://raw.githubusercontent.com/crazy-max/docker-rrdcached/master/.res/docker-rrdcached.jpg"></a></p>

<p align="center">
  <a href="https://hub.docker.com/r/crazymax/rrdcached/"><img src="https://img.shields.io/badge/dynamic/json.svg?label=version&query=$.results[1].name&url=https://hub.docker.com/v2/repositories/crazymax/rrdcached/tags&style=flat-square" alt="Latest Version"></a>
  <a href="https://travis-ci.com/crazy-max/docker-rrdcached"><img src="https://img.shields.io/travis/com/crazy-max/docker-rrdcached/master.svg?style=flat-square" alt="Build Status"></a>
  <a href="https://hub.docker.com/r/crazymax/rrdcached/"><img src="https://img.shields.io/docker/stars/crazymax/rrdcached.svg?style=flat-square" alt="Docker Stars"></a>
  <a href="https://hub.docker.com/r/crazymax/rrdcached/"><img src="https://img.shields.io/docker/pulls/crazymax/rrdcached.svg?style=flat-square" alt="Docker Pulls"></a>
  <a href="https://quay.io/repository/crazymax/rrdcached"><img src="https://quay.io/repository/crazymax/rrdcached/status?style=flat-square" alt="Docker Repository on Quay"></a>
  <a href="https://www.codacy.com/app/crazy-max/docker-rrdcached"><img src="https://img.shields.io/codacy/grade/826c85b3ae99486e80784380422bcd0e.svg?style=flat-square" alt="Code Quality"></a>
  <br /><a href="https://www.patreon.com/crazymax"><img src="https://img.shields.io/badge/donate-patreon-f96854.svg?logo=patreon&style=flat-square" alt="Support me on Patreon"></a>
  <a href="https://www.paypal.me/crazyws"><img src="https://img.shields.io/badge/donate-paypal-00457c.svg?logo=paypal&style=flat-square" alt="Donate Paypal"></a>
</p>

## About

🐳 [RRDcached](https://oss.oetiker.ch/rrdtool/doc/rrdcached.en.html) image based on Alpine Linux.<br />
If you are interested, [check out](https://hub.docker.com/r/crazymax/) my other 🐳 Docker images!

💡 Want to be notified of new releases? Check out 🔔 [Diun (Docker Image Update Notifier)](https://github.com/crazy-max/diun) project!

## Docker

### Environment variables

* `TZ` : Timezone assigned to the container (default `UTC`)
* `LOG_LEVEL` : Log level, called with `-V` (default `LOG_INFO`)
* `WRITE_TIMEOUT` : Data is written to disk every *X* seconds, called with `-w` (default `300`)
* `WRITE_JITTER` : Delay writing of each RRD for a random number of seconds in the range, called with `-z`
* `WRITE_THREADS` : Number of threads used for writing RRD files, called with `-t` (default `4`)
* `FLUSH_DEAD_DATA_INTERVAL` : Every *X* seconds the entire cache is searched for old values which are written to disk, called with `-f` (default `3600`)

> More info : https://github.com/oetiker/rrdtool-1.x/blob/master/doc/rrdcached.pod

### Volumes

* `/data/db` : Contains rrd database
* `/data/journal` :  Container rrd journal files

> :warning: Note that the volumes should be owned by uid `1000` and gid `1000`. If you don't give the volumes correct permissions, the container may not start.

### Ports

* `42217` : RRDcached port

## Usage

### Docker Compose

Docker compose is the recommended way to run this image. You can use the following [docker compose template](examples/compose/docker-compose.yml), then run the container:

```bash
docker-compose up -d
docker-compose logs -f
```

### Command line

You can also use the following minimal command:

```bash
$ docker run -d -p 42217:42217 --name rrdcached \
  -e TZ="Europe/Paris" \
  -v $(pwd)/data/db:/data/db \
  -v $(pwd)/data/journal:/data/journal \
  crazymax/rrdcached
```

## Update

Recreate the container whenever I push an update:

```bash
docker-compose pull
docker-compose up -d
```

## How can I help ?

All kinds of contributions are welcome :raised_hands:!<br />
The most basic way to show your support is to star :star2: the project, or to raise issues :speech_balloon:<br />
But we're not gonna lie to each other, I'd rather you buy me a beer or two :beers:!

[![Support me on Patreon](.res/patreon.png)](https://www.patreon.com/crazymax) 
[![Paypal Donate](.res/paypal.png)](https://www.paypal.me/crazyws)

## License

MIT. See `LICENSE` for more details.
