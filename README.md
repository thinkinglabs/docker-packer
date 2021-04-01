# docker-packer

Alpine based Docker images with [Hashicorp Packer](https://www.packer.io/) and
an extra configuration management tool.

All images contain:

- `jq`: for parsing the optional manifest file produced by Packer
- `make`: handing for when you use a Makefile to bootstrap Packer

## Supported tags

- [1.7.0-ansible-2.10.6](ansible/README.md): Packer 1.7.0 with Ansible 2.10.6
