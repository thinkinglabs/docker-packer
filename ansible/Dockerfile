FROM alpine:3.13

ARG PLATFORM=linux_amd64
ARG PACKER_VERSION=1.7.0
ARG PACKER_DIST_FILENAME=packer_${PACKER_VERSION}_${PLATFORM}.zip
ARG PACKER_DIST_CHECKSUM_FILENAME=packer_${PACKER_VERSION}_SHA256SUMS
ARG ANSIBLE_VERSION=2.10.6-r0
ARG ANSIBLE_LINT_VERSION=4.3.7-r1

# TODO: ARG PARCKER_DIST_FILENAME
# TODO replace 1.7.0 by PACKER_VERSION
# TODO replace linux_amd64 by PLATFORM
# TODO read platform from uname -s (os) and uname -m (processor)
# see https://github.com/terraform-linters/tflint/blob/master/install_linux.sh

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
