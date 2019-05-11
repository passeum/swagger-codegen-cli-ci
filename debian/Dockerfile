FROM swaggerapi/swagger-codegen-cli AS swagger-codegen-cli
LABEL maintainer="lanyi.robert@passeum.com"

FROM openjdk:8-jre-slim-stretch

RUN echo "force-unsafe-io" > /etc/dpkg/dpkg.cfg.d/apt-speedup                                                                                                                          && \
    echo "Acquire::http {No-Cache=True;};" > /etc/apt/apt.conf.d/no-proxy-cache                                                                                                        && \
    echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean         && \
    echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean && \
    echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean                                                                                    && \
    echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages                                                                                                        && \
    echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes                                                             && \
                                                                                                                                                                                          \
    apt-get update                                                            && \
                                                                                 \
    apt-get -y --no-install-recommends install                                   \
        openssh-client                                                        && \
                                                                                 \
    rm -rf /var/lib/apt/lists/*

COPY --from=swagger-codegen-cli /opt/swagger-codegen-cli/swagger-codegen-cli.jar /opt/swagger-codegen-cli/swagger-codegen-cli.jar
