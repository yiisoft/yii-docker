# Executando testes de framework

```Info
Este repositório foi arquivado pelo proprietário em
9 de setembro de 2019. Agora é somente leitura.

O núcleo do Yii Framework 3.0 foi dividido em vários
pacotes e o pacote foi excluído.

O repositório é mantido para que questões encerradas
possam ser revisadas por razões históricas.
```

Entre no contêiner com

```dockerfile
docker-compose run --rm -w /yii-core php bash
```

Entre no contêiner e instale os pacotes

```shell
composer install
```

Execute os testes

```shell
vendor/bin/phpunit tests/framework/ --exclude db
```

Mudando para outra versão do framework

```shell
git checkout 2.0.12
```

## Usando uma versão específica do PHP

```dockerfile
DOCKERFILE_FLAVOUR=debian PHP_BASE_IMAGE_VERSION=7.1.2-fpm docker-compose build

DOCKERFILE_FLAVOUR=debian PHP_BASE_IMAGE_VERSION=7.1.2-fpm docker-compose run --rm php bash
```
