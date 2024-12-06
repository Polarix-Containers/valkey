ARG VERSION=7
ARG UID=3009
ARG GID=3009

FROM valkey:${VERSION}-alpine

ARG UID
ARG GID

LABEL maintainer="Thien Tran contact@tommytran.io"

RUN apk -U upgrade \
    && apk add libstdc++ shadow

RUN usermod -u ${UID} valkey \
    && groupmod -g ${GID} valkey \
    && find / -user 999 -exec chown -h valkey {} \; \
    && find / -group 1000 -exec chgrp -h valkey {} \; \
    && apk del shadow \
    && rm -rf /var/cache/apk/*


COPY --from=ghcr.io/polarix-containers/hardened_malloc:latest /install /usr/local/lib/
ENV LD_PRELOAD="/usr/local/lib/libhardened_malloc.so"

USER valkey