FROM alpine:latest
LABEL org.opencontainers.image.created="" \
  org.opencontainers.image.authors="" \
  org.opencontainers.image.url="" \
  org.opencontainers.image.documentation="" \
  org.opencontainers.image.source="" \
  org.opencontainers.image.version="" \
  org.opencontainers.image.revision="" \
  org.opencontainers.image.vendor="" \
  org.opencontainers.image.licenses="" \
  org.opencontainers.image.ref.name="" \
  org.opencontainers.image.title="" \
  org.opencontainers.image.description="" \
  org.opencontainers.image.base.digest="" \
  org.opencontainers.image.base.name=""

RUN apk -U upgrade \
  && apk add --update git bash curl xz openssh \
  && rm -rf /var/cache/apk/* /tmp/* /var/tmp/* \
  && set -o pipefail \
  && curl -sSf https://radicle.xyz/install | sh

ENV PATH=/root/.radicle/bin:$PATH

VOLUME /root/.radicle
