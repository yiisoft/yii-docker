<p align="center">
    <a href="https://www.docker.com/" target="_blank">
        <img src="https://www.docker.com/sites/default/files/mono_vertical_large.png" height="100px">
    </a>
    <h1 align="center">Yii 3.x PHP Docker Image</h1>
    <br>
</p>

**Stable**
[![Build Status](https://travis-ci.com/yiisoft/yii-docker.svg?branch=master)](https://travis-ci.com/yiisoft/yii-docker)
**Development**
[![pipeline status](https://gitlab.com/yiisoft/yii-docker/badges/master/pipeline.svg)](https://gitlab.com/yiisoft/yii-docker/commits/master)


This is the repo of the official [Yii 3.x Framework](http://www.yiiframework.com/) image on [DockerHub](https://hub.docker.com/r/yiisoftware/yii-php/) for PHP.

## About

These Docker images are built on top of the official PHP Docker image, they contain additional PHP extensions required to run Yii 3.x framework, but no code of the framework itself.
The `Dockerfile`(s) of this repository are designed to build from different PHP-versions by using *build arguments*.

### Features

- built from official Docker images
- all core-framework tests pass
- includes Xdebug (not loaded by default)
- ready for handling client-side packages
- bash auto-completion

### Available versions for `yiisoftware/yii-php`

```
8.0-apache, 7.4-apache,
8.0-fpm, 7.4-fpm
```

Inlcudes `npm`.

## Setup

    cp .env-dist .env

Adjust the versions in `.env` if you want to build a specific version.

> **Note:** Please make sure to use a matching combination of `DOCKERFILE_FLAVOUR` and `PHP_BASE_IMAGE_VERSION`


## Configuration

- `PHP_ENABLE_XDEBUG` whether to load an enable Xdebug, defaults to `0` (false)
- `PHP_USER_ID` (Debian only) user ID, when running commands as webserver (`www-data`), see also [#15](https://github.com/yiisoft/yii2-docker/issues/15)


## Building

    docker-compose build


## Testing

    docker-compose run --rm php php /tests/requirements.php

### Xdebug

To enable Xdebug, set `PHP_ENABLE_XDEBUG=1` in .env file

Xdebug is configured to call ip `xdebug.remote_host` on `9005` port (not use standard port to avoid conflicts),
so you have to configure your IDE to receive connections from that ip.

If you are using macOS, you can fill `xdebug.remote_host` with `host.docker.internal`, due to a network limitation on mac (https://docs.docker.com/docker-for-mac/networking/#port-mapping)

    ### (macOS) configuration
    xdebug.remote_host=host.docker.internal

## Documentation

More information can be found in the [docs](/docs) folder.

