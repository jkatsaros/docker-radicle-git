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
  && apk add --update tor torsocks \
  && rm -rf /var/cache/apk/* /tmp/* /var/tmp/*

VOLUME /var/lib/tor

RUN chown -R tor /etc/tor

USER tor

RUN mkdir -m 700 /var/lib/tor/radicle \
  && sed "1s/^/SocksPort 0.0.0.0:9050\n/" /etc/tor/torrc.sample > /etc/tor/torrc \
  && echo HiddenServiceDir /var/lib/tor/radicle >> /etc/tor/torrc \
  && echo HiddenServicePort 8776 >> /etc/tor/torrc \
  && cat /var/lib/tor/radicle/hostname \
  && tor

EXPOSE 9050
EXPOSE 8776
