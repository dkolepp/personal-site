FROM registry.redhat.io/ubi8/ubi-minimal:8.2

LABEL description="Docker container for building static sites with the Hugo static site generator."
LABEL maintainer="Marek Czernek <mczernek@redhat.com>"

ENV HUGO_VERSION=0.76.5
ENV HUGO_ID=hugo_extended_${HUGO_VERSION}

RUN microdnf -y install gem tar gzip git \
    && curl -L https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/${HUGO_ID}_Linux-64bit.tar.gz | tar -xz -C /tmp \
    && mkdir -p /usr/local/sbin \
    && mv /tmp/hugo /usr/local/sbin/hugo \
    && rm -rf /tmp/* \
    && gem install asciidoctor \
    && microdnf clean all \
    && rm -rf /var/cache/yum

WORKDIR /usr/hugo
VOLUME /usr/hugo

ENTRYPOINT ["hugo"]

