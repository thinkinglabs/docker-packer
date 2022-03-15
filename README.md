# docker-packer

Alpine based Docker images with [Hashicorp Packer](https://www.packer.io/) and
an extra configuration management tool.

All images contain:

- `jq`: for parsing the optional manifest file produced by Packer
- `make`: for using a Makefile to bootstrap Packer

## Supported tags

- [1.7.0-ansible-2.10.6](ansible/README.md): Packer 1.7.0 with Ansible 2.10.6
- [v1.8.0-ansible-4.8.0](ansible/README.md): Packer 1.8.0 with Ansible 4.8.0
