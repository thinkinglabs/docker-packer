# docker-packer

Alpine based Docker images with [Hashicorp Packer](https://www.packer.io/) and
an extra configuration management tool.

All images contain:

- `jq`: for parsing the optional manifest file produced by Packer
- `make`: for using a Makefile to bootstrap Packer
