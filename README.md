# docker-packer-with-ansible

An Alpine based Docker image for [Hashicorp Packer](https://www.packer.io/)
with [Ansible](https://docs.ansible.com/ansible/latest/index.html).

This image was primarily implemented with [Concourse](https://concourse-ci.org)
in mind, i.e. to be used as an image resource for a Concourse task.

When [Concourse tasks are run as non-root user it can not create files inside
output directories](https://github.com/concourse/concourse/issues/403).
To work around this, Packer runs as root.

[Hashicorp advises against this](https://www.packer.io/docs/provisioners/ansible#become-yes).
Because Ansible `become: yes` will fail. To fix this, provide a `user` to the
Ansible Provisioner inside the Packer template.

```hcl2
build {

  ...

  provisioner "ansible" {
    playbook_file    = "vm_console.yml"
    user             = "ubuntu"
  }

  ...

}
```
