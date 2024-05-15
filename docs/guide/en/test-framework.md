# Running framework tests

```Info
This repository has been archived by the owner on Sep 9, 2019. It is now read-only.

Yii Framework 3.0 core was split into several packages and the package was deleted.

Repository is kept so closed issues could be reviewed for historical reasons.
```

Enter the container with

```shell
docker-compose run --rm -w /yii-core php bash
```

Go into the container and install packages

```shell
composer install
```

Run the tests

```shell
vendor/bin/phpunit tests/framework/ --exclude db
```

Switching to another framework version

```shell
git checkout 2.0.12
```

## Using a specific PHP version

```shell
DOCKERFILE_FLAVOUR=debian PHP_BASE_IMAGE_VERSION=7.1.2-fpm docker-compose build

DOCKERFILE_FLAVOUR=debian PHP_BASE_IMAGE_VERSION=7.1.2-fpm docker-compose run --rm php bash
```
