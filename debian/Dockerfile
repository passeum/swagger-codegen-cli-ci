FROM swaggerapi/swagger-codegen-cli AS swagger-codegen-cli
LABEL maintainer="lanyi.robert@passeum.com"

FROM openjdk:8-jre-slim-stretch
COPY --from=swagger-codegen-cli /opt/swagger-codegen-cli/swagger-codegen-cli.jar /opt/swagger-codegen-cli/swagger-codegen-cli.jar
