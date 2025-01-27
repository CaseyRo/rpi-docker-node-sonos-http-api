# rpi-docker-node-sonos-http-api
Docker wrapper for https://github.com/jishi/node-sonos-http-api for running on a Raspberry Pi.

[![Docker Stars](https://img.shields.io/docker/stars/keesromkes/rpi-docker-node-sonos-http-api.svg)](https://cloud.docker.com/u/keesromkes/repository/docker/keesromkes/rpi-docker-node-sonos-http-api)
[![Docker Pulls](https://img.shields.io/docker/pulls/keesromkes/rpi-docker-node-sonos-http-api.svg)](https://cloud.docker.com/u/keesromkes/repository/docker/keesromkes/rpi-docker-node-sonos-http-api)
![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/keesromkes/rpi-docker-node-sonos-http-api)
![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/keesromkes/rpi-docker-node-sonos-http-api)

* [This project on Docker](https://cloud.docker.com/repository/docker/keesromkes/rpi-docker-node-sonos-http-api)
* [This project on Github](https://github.com/Keesromkes/rpi-docker-node-sonos-http-api)

## Usage
Refer to [node-sonos-http-api](https://github.com/jishi/node-sonos-http-api) for all the configuration detail

First make the config and local dirs up
```bash
mkdir clips
mkdir settings
mkdir cache
mkdir presets
curl https://raw.githubusercontent.com/jishi/node-sonos-http-api/master/presets/example.json > presets/example.json
echo {} > settings/settings.json
```

Then run the docker image
```bash
docker run \
  --net=host \
  --name sonos \
  --restart=always \
  -d \
  -v `pwd`/settings:/app/settings \
  -v `pwd`/clips:/app/static/clips \
  -v `pwd`/cache:/app/cache \
  -v `pwd`/presets:/app/presets \
  keesromkes/rpi-docker-node-sonos-http-api
```

Or if you'd like to do this using docker-compose - `docker-compose up -d` should do the trick.

I've taken the liberty to fork [@jonmaddox](https://github.com/jonmaddox)'s docker image and added docker-compose to this, next to a different main image to pull from. Credit goes to him in this regard!
