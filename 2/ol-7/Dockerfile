FROM bitnami/oraclelinux-extras-base:7-r416
LABEL maintainer "Bitnami <containers@bitnami.com>"

ENV BITNAMI_PKG_CHMOD="-R g+rwX" \
    HOME="/" \
    OS_ARCH="x86_64" \
    OS_FLAVOUR="ol-7" \
    OS_NAME="linux"

# Install required system packages and dependencies
RUN install_packages glibc libgcc zlib
RUN . ./libcomponent.sh && component_unpack "java" "1.8.222-0" --checksum a90f4ce71ff9b392efdf61e6941117afa31d2d6528bd1a3cad1c6459bcac2b0b
RUN . ./libcomponent.sh && component_unpack "kafka" "2.3.0-0" --checksum a5bb07f34dc786fd8a7ce832e2d0c417db5c071a8674ce18ffc863bf811946bf

COPY rootfs /
RUN /postunpack.sh
ENV BITNAMI_APP_NAME="kafka" \
    BITNAMI_IMAGE_VERSION="2.3.0-ol-7-r85" \
    NAMI_PREFIX="/.nami" \
    PATH="/opt/bitnami/java/bin:/opt/bitnami/kafka/bin:$PATH"

EXPOSE 9092

USER 1001
ENTRYPOINT [ "/entrypoint.sh" ]
CMD [ "/run.sh" ]
