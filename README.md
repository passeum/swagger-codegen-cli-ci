# swagger-codegen-cli-ci

This is a modified version of https://hub.docker.com/r/swaggerapi/swagger-codegen-cli . Entrypoint has been changed so it can be easily integrated to CI pipelines.

### Example `.gitlab-ci.yml`

```
Check Swagger Syntax:
  stage: code-check
  image: passeum/swagger-codegen-cli-ci
  script:
    - java -jar /opt/swagger-codegen-cli/swagger-codegen-cli.jar validate -i ./specs/swagger.yml
  tags:
    - docker
```