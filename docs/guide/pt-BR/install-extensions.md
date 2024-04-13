# Instalando extensões adicionais

Recomenda-se instalar extensões PHP adicionais com <https://github.com/mlocati/docker-php-extension-installer>

```dockerfile
FROM yiisoftware/yii-php:8.1-apache-min
RUN install-php-extensions \
        <EXTENSION_NAME>-stable
```

## Instalações personalizadas

Esta seção está praticamente obsoleta e existe apenas para referência.

### Plug-in de ativos do Composer

```bash
    RUN composer global require "fxp/composer-asset-plugin:^1.4.2"
```

### mcrypt

#### Debian

```bash
    RUN apt-get update && \
        apt-get -y install \
            libmcrypt-dev && \
        docker-php-ext-install \
            mycrypt   
```

### APC

*TBD* (*a ser definido*)

```bash
    RUN pecl install apc
    RUN echo "extension=apcu.so" > /usr/local/etc/php/conf.d/pecl-apcu.ini

---

    RUN docker-php-ext-enable \
        imagick
```

### memcache

#### Debian (PHP7)

```bash
    # memcache
    ENV MEMCACHED_DEPS libmemcached-dev git
    RUN set -xe \
     && apt-get update \
     && apt-get install -y $MEMCACHED_DEPS \
     && curl https://codeload.github.com/php-memcached-dev/php-memcached/zip/php7 -o /tmp/memcached.zip \
     && mkdir -p /usr/src/php/ext \
     && unzip /tmp/memcached.zip -d /usr/src/php/ext \
     && docker-php-ext-configure /usr/src/php/ext/php-memcached-php7 \
         --disable-memcached-sasl \
     && docker-php-ext-install /usr/src/php/ext/php-memcached-php7 \
     && rm -rf /usr/src/php/ext/php-memcached-php7 /tmp/memcached.zip
```

### Xdebug

#### Debian

```bash
    # Install xdebug
    RUN cd /tmp && \
        git clone git://github.com/xdebug/xdebug.git && \
        cd xdebug && \
        git checkout 52adff7539109db592d07d3f6c325f6ee2a7669f && \
        phpize && \
        ./configure --enable-xdebug && \
        make && \
        make install && \
        rm -rf /tmp/xdebug        
```
