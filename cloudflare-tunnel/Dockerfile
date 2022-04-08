ARG BUILD_FROM
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ARG BUILD_ARCH
ARG CLOUDFLARED_VERSION
RUN if [[ "${BUILD_ARCH}" = "armhf" ]]; then CLOUDFLARED_ARCH="arm"; \
    elif [[ "${BUILD_ARCH}" = "armv7" ]]; then CLOUDFLARED_ARCH="arm"; \
    elif [[ "${BUILD_ARCH}" = "aarch64" ]]; then CLOUDFLARED_ARCH="arm64"; \
    elif [[ "${BUILD_ARCH}" = "amd64" ]]; then CLOUDFLARED_ARCH="amd64";  \
    elif [[ "${BUILD_ARCH}" = "i386" ]]; then CLOUDFLARED_ARCH="386"; \
    else exit 1; fi \
    && curl -L -s -o /opt/cloudflared "https://github.com/cloudflare/cloudflared/releases/download/${CLOUDFLARED_VERSION}/cloudflared-linux-${CLOUDFLARED_ARCH}" \
    && chmod +x /opt/cloudflared

COPY rootfs /

CMD ["/opt/run.sh"]
