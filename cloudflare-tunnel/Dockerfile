ARG BUILD_FROM=ghcr.io/hassio-addons/base/aarch64:10.2.3
ARG BUILD_ARCH=aarch64
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN \
    CLOUDFLARED_ARCH="${BUILD_ARCH}" \
    && if [[ "${BUILD_ARCH}" = "armhf" ]]; then CLOUDFLARED_ARCH="arm"; fi \
    && if [[ "${BUILD_ARCH}" = "armv7" ]]; then CLOUDFLARED_ARCH="arm"; fi \
    && if [[ "${BUILD_ARCH}" = "aarch64" ]]; then CLOUDFLARED_ARCH="arm64"; fi \
    && if [[ "${BUILD_ARCH}" = "amd64" ]]; then CLOUDFLARED_ARCH="amd64"; fi \
    && if [[ "${BUILD_ARCH}" = "i386" ]]; then CLOUDFLARED_ARCH="386"; fi \
    && curl -L -s -o /opt/cloudflared "https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-${CLOUDFLARED_ARCH}" \
    && chmod +x /opt/cloudflared \
    && apk add --no-cache libc6-compat

COPY rootfs /