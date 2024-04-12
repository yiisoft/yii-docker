# Building

Os mantenedores do repositório podem acionar a construção de uma versão específica por meio da API GitLab:

```bash
    curl -X POST \
         -F token=${GITLAB_YII_DOCKER_TOKEN} \
         -F ref=master \
         -F "variables[DOCKERFILE_FLAVOUR]=debian" \
         -F "variables[PHP_BASE_IMAGE_VERSION]=8.1-apache" \
         -F "variables[TEST_YII_VERSION]=3" \
         https://gitlab.com/api/v4/projects/2858803/trigger/pipeline
```

Isso também pode ser usado para testar pré-lançamentos de PHP ou outras versões, se houver um Dockerfile disponível para eles.

> Os tokens são gerenciados em [GitLab settings](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html).
