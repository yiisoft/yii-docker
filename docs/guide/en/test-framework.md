# Running framework tests

Get the source and place it into a host-volume folder for mounting it into the container.

```bash
git clone https://github.com/yiisoft/yii-core _host-volumes/yii-core
```

```Info
This repository has been archived by the owner on Sep 9, 2019. It is now read-only.

Yii Framework 3.0 core was split into several packages and the package was deleted.

Repository is kept so closed issues could be reviewed for historical reasons.
```

Enter the container with

```dockerfile
docker-compose run --rm -w /yii-core php bash
```

Go into the container and install packages

```bash
composer install
```

Run the tests

```bash
vendor/bin/phpunit tests/framework/ --exclude db
```

Switching to another framework version

```bash
git checkout 2.0.12
```

## Using a specific PHP version

```dockerfile
DOCKERFILE_FLAVOUR=debian PHP_BASE_IMAGE_VERSION=7.1.2-fpm docker-compose build

DOCKERFILE_FLAVOUR=debian PHP_BASE_IMAGE_VERSION=7.1.2-fpm docker-compose run --rm php bash
```
