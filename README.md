# swagger-codegen-cli-ci

This is a modified version of https://hub.docker.com/r/swaggerapi/swagger-codegen-cli . Entrypoint has been changed so it can be easily integrated to CI pipelines.

### Versions

- `passeum/swagger-codegen-cli-ci:alpine` is based on the original `swaggerapi/swagger-codegen-cli`
- `passeum/swagger-codegen-cli-ci:latest` and `passeum/swagger-codegen-cli-ci:debian` inherits `swagger-codegen-cli.jar` but base image is `debian:slim` with BASH etc.

### Example `.gitlab-ci.yml`

```
Check Swagger Syntax:
  stage: code-check
  image: passeum/swagger-codegen-cli-ci
  script:
    - /usr/bin/java -jar /opt/swagger-codegen-cli/swagger-codegen-cli.jar validate -i ./specs/swagger.yml
  tags:
    - docker
```