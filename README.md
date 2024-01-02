# Ansible role [hashicorp](https://galaxy.ansible.com/ui/standalone/roles/buluma/hashicorp/documentation)

Install HashiCorp products using packages.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-hashicorp/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-hashicorp/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-hashicorp.svg)](https://github.com/buluma/ansible-role-hashicorp/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-hashicorp.svg)](https://github.com/buluma/ansible-role-hashicorp/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-hashicorp.svg)](https://github.com/buluma/ansible-role-hashicorp/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/hashicorp)](https://galaxy.ansible.com/ui/standalone/roles/buluma/hashicorp/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-hashicorp/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.hashicorp
      hashicorp_products:
        - name: consul
          version: "1.11.3"
    - role: buluma.hashicorp
      hashicorp_installation_method: manual
      hashicorp_products:
        - name: vault
          version: "1.9.0"
          type: ent
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-hashicorp/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
    - role: buluma.core_dependencies
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-hashicorp/blob/master/defaults/main.yml):

```yaml
---
# defaults file for hashicorp

# You can select how to intall hashicorp products. Choose from `package` or
# `manual`. `manual` means this role wil download from
# "https://releases.hashicorp.com/vault/".
hashicorp_installation_method: package

# You can install hashicorp products using this list.
# hashicorp_products:
#   - name: consul
#   - name: consul-template
#   - name: nomad
#   - name: packer
#   - name: terraform
#   - name: vagrant
#   - name: vault

# If you are using `manual` as the `hashicorp_installation_method`, you must
# specify the version to install.
# hashicorp_products:
#   - name: vault
#     version: "1.10.4"

# For `vault` you can choose what type you want to install, either:
# `oss` (default), `ent` or `hsm`.
# hashicorp_products:
#   - name: vault
#     type: oss

# Where to install the software in.
hashicorp_destination: /usr/bin

# The owner/group/mode for the installed binary.
hashicorp_group: root
hashicorp_owner: root
hashicorp_mode: "0755"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-hashicorp/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.core_dependencies](https://galaxy.ansible.com/buluma/core_dependencies)|[![Ansible Molecule](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-core_dependencies.svg)](https://github.com/shadowwalker/ansible-role-core_dependencies)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-hashicorp/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Amazon](https://hub.docker.com/repository/docker/buluma/amazonlinux/general)|Candidate|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|8|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|bullseye|
|[Fedora](https://hub.docker.com/repository/docker/buluma/fedora/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|
|[Kali](https://hub.docker.com/repository/docker/buluma/kali/general)|all|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-hashicorp/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-hashicorp/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-hashicorp/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

