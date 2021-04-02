# docker-packer-with-ansible

Alpine based Docker image with [Hashicorp Packer](https://www.packer.io/)
and [Ansible](https://docs.ansible.com/ansible/latest/index.html) and
[ansible-lint](https://github.com/ansible-community/ansible-lint).

The image is primarily implemented for use as an image resource for a
[Concourse](https://concourse-ci.org) task.
Therefore, no `ENTRYPOINT` is defined and the container runs as root.

Concourse has some issues running tasks as non-root users, i.e.
[Concourse tasks ran as non-root users can not create files inside output directories](https://github.com/concourse/concourse/issues/403).

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
