FROM docker.io/bitnami/minideb:buster
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV HOME="/" \
    OS_ARCH="amd64" \
    OS_FLAVOUR="debian-10" \
    OS_NAME="linux"

COPY prebuildfs /
# Install required system packages and dependencies
RUN install_packages ca-certificates curl gzip procps tar wget
RUN wget -nc -P /tmp/bitnami/pkg/cache/ https://downloads.bitnami.com/files/stacksmith/redis-sentinel-exporter-1.7.1-1-linux-amd64-debian-10.tar.gz && \
    echo "0c7dbc26817cf550726cb4399d21b444e3053277805140656901cddbd90a5c94  /tmp/bitnami/pkg/cache/redis-sentinel-exporter-1.7.1-1-linux-amd64-debian-10.tar.gz" | sha256sum -c - && \
    tar -zxf /tmp/bitnami/pkg/cache/redis-sentinel-exporter-1.7.1-1-linux-amd64-debian-10.tar.gz -P --transform 's|^[^/]*/files|/opt/bitnami|' --wildcards '*/files' && \
    rm -rf /tmp/bitnami/pkg/cache/redis-sentinel-exporter-1.7.1-1-linux-amd64-debian-10.tar.gz
RUN chmod g+rwX /opt/bitnami

ENV BITNAMI_APP_NAME="redis-sentinel-exporter" \
    BITNAMI_IMAGE_VERSION="1.7.1-debian-10-r74" \
    PATH="/opt/bitnami/redis-sentinel-exporter/bin:$PATH"

EXPOSE 9355

WORKDIR /opt/bitnami/redis-sentinel-exporter
USER 1001
ENTRYPOINT [ "redis_sentinel_exporter" ]
