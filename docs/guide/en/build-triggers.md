# Building

Repo maintainers can trigger the build of a specific version via GitLab API:

```bash
    curl -X POST \
         -F token=${GITLAB_YII_DOCKER_TOKEN} \
         -F ref=master \
         -F "variables[DOCKERFILE_FLAVOUR]=debian" \
         -F "variables[PHP_BASE_IMAGE_VERSION]=8.1-apache" \
         -F "variables[TEST_YII_VERSION]=3" \
         https://gitlab.com/api/v4/projects/2858803/trigger/pipeline
```

This can also be used to test pre-releases of PHP or other versions, if there is a Dockerfile available for them.

> Tokens are managed under [GitLab settings](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html).
