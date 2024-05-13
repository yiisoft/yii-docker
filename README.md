<p align="center">
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://yiisoft.github.io/docs/images/yii_logo.svg" height="100px">
    </a>
    <a href="https://github.com/yiisoft" target="_blank">
        <img src="https://www.docker.com/wp-content/uploads/2023/08/logo-guide-logos-1.svg" height="80px">
    </a>
    <h1 align="center">Yii 3.x PHP Docker Image</h1>
    <br>
</p>

**Stable**
<img src="https://api.travis-ci.com/yiisoft/yii-docker.svg?branch=master">
**Development**
[![pipeline status](https://gitlab.com/yiisoft/yii-docker/badges/master/pipeline.svg)](https://gitlab.com/yiisoft/yii-docker/commits/master)

This is the repo of the official [Yii 3.x Framework](https://www.yiiframework.com/) image on [DockerHub](https://hub.docker.com/r/yiisoftware/yii-php/) for PHP.

## About

These Docker images are built on top of the official PHP Docker image, they contain additional PHP extensions required to run Yii 3.x framework, but no code of the framework itself.
The `Dockerfile`(s) of this repository are designed to build from different PHP-versions by using *build arguments*.

### Features

- built from official Docker images
- all core-framework tests pass
- includes Xdebug (not loaded by default)
- ready for handling client-side packages
- bash auto-completion
- `fpm-nginx` images with built-in webserver (like Apache)

### Available versions for `yiisoftware/yii-php`

The following images are built on a *weekly* basis for **arm64** and **amd64**. For regular commits on **master** we only build images for **amd64** suffixed with `-latest`/`-latest-min`.

#### Minimal images

```text
8-2-apache-min
8-1-apache-min
8.0-apache-min
8.2-fpm-min
8.1-fpm-min
8.0-fpm-min
8.2-fpm-nginx-min
8.1-fpm-nginx-min
8.0-fpm-nginx-min
```

#### Development images, include `npm` and `composer`

```text
8.2-apache
8.1-apache
8.0-apache
8.2-fpm
8.1-fpm
8.0-fpm
8.2-fpm-nginx
8.1-fpm-nginx
8.0-fpm-nginx
```

#### Deprecated images

```text
7.4-apache-min
7.4-fpm-min
7.4-fpm-nginx-min
7.4-apache
7.4-fpm
7.4-fpm-nginx
```

## Setup

```shell
cp .env-dist .env
```

Adjust the versions in `.env` if you want to build a specific version.

> **Note:** Please make sure to use a matching combination of `DOCKERFILE_FLAVOUR` and `PHP_BASE_IMAGE_VERSION`

## Configuration

- `PHP_ENABLE_XDEBUG` whether to load an enable Xdebug, defaults to `0` (false) *not available in `-min` images*
- `PHP_USER_ID` (Debian only) user ID, when running commands as webserver (`www-data`), see also [#15](https://github.com/yiisoft/yii2-docker/issues/15)
- `SUPERVISOR_START_FPM` (nginx-flavor only) whether to start PHP-fpm by supervisor (default: `true`)
- `SUPERVISOR_START_NGINX`  (nginx-flavor only) whether to start nginx by supervisor (default: `true`)

## Building

```shell
docker-compose build
```

## Testing

```shell
docker-compose run --rm php php /tests/requirements.php
```

### Xdebug

To enable Xdebug, set `PHP_ENABLE_XDEBUG=1` in .env file

Xdebug is configured to call ip `xdebug.remote_host` on `9005` port (not use standard port to avoid conflicts),
so you have to configure your IDE to receive connections from that ip.

If you are using macOS, you can fill `xdebug.remote_host` with `host.docker.internal`, due to a network limitation on mac (<https://docs.docker.com/docker-for-mac/networking/#port-mapping>)

### (macOS) configuration

> xdebug.remote_host=host.docker.internal

## Documentation

- Guide: [English](docs/guide/en/README.md), [Português - Brasil](docs/guide/pt-BR/README.md)

If you need help or have a question, the [Yii Forum](https://forum.yiiframework.com/c/yii-3-0/63) is a good place for that.
You may also check out other [Yii Community Resources](https://www.yiiframework.com/community).

## License

The Yii 3.x PHP Docker Image is free software. It is released under the terms of the BSD License.
Please see [`LICENSE`](./LICENSE.md) for more information.

Maintained by [Yii Software](https://www.yiiframework.com/).

## Support the project

[![Open Collective](https://img.shields.io/badge/Open%20Collective-sponsor-7eadf1?logo=open%20collective&logoColor=7eadf1&labelColor=555555)](https://opencollective.com/yiisoft)

## Follow updates

[![Official website](https://img.shields.io/badge/Powered_by-Yii_Framework-green.svg?style=flat)](https://www.yiiframework.com/)
[![Twitter](https://img.shields.io/badge/twitter-follow-1DA1F2?logo=twitter&logoColor=1DA1F2&labelColor=555555?style=flat)](https://twitter.com/yiiframework)
[![Telegram](https://img.shields.io/badge/telegram-join-1DA1F2?style=flat&logo=telegram)](https://t.me/yii3en)
[![Facebook](https://img.shields.io/badge/facebook-join-1DA1F2?style=flat&logo=facebook&logoColor=ffffff)](https://www.facebook.com/groups/yiitalk)
[![Slack](https://img.shields.io/badge/slack-join-1DA1F2?style=flat&logo=slack)](https://yiiframework.com/go/slack)
