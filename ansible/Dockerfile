FROM alpine:3.15

ARG PLATFORM=linux_amd64
ARG PACKER_VERSION=1.8.0
ARG PACKER_DIST_FILENAME=packer_${PACKER_VERSION}_${PLATFORM}.zip
ARG PACKER_DIST_CHECKSUM_FILENAME=packer_${PACKER_VERSION}_SHA256SUMS
ARG ANSIBLE_VERSION=4.8.0-r0
ARG ANSIBLE_LINT_VERSION=4.3.7-r4

LABEL org.opencontainers.image.description="Hashicorp Packer with Ansible" \
      org.opencontainers.image.authors="ThinkingLabs (hello@thinkinglabs.io)" \
      org.opencontainers.image.url="https://github.com/thinkinglabs/docker-packer" \
      org.opencontainers.image.source="git@github.com:thinkinglabs/docker-packer.git" \
      org.opencontainers.image.licenses="MIT"

RUN wget https://releases.hashicorp.com/packer/${PACKER_VERSION}/${PACKER_DIST_FILENAME} \
  && wget https://releases.hashicorp.com/packer/${PACKER_VERSION}/${PACKER_DIST_CHECKSUM_FILENAME} \
    && set -o pipefail && grep ${PLATFORM} ${PACKER_DIST_CHECKSUM_FILENAME} | sha256sum -c - \
    && unzip ${PACKER_DIST_FILENAME} -d /usr/local/bin \
    && rm ${PACKER_DIST_FILENAME} ${PACKER_DIST_CHECKSUM_FILENAME} \
    && apk add --no-cache ansible=${ANSIBLE_VERSION} ansible-lint=${ANSIBLE_LINT_VERSION} jq make
