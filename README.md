# Containers for Molecule

An [Debian][debian] based container image for testing [Ansible][ansible] Roles with [Molecule][molecule]. The [repository][docker-debian10-ansible] from [Jeff Geerling][geerlingguy] was taken as starting point to create the repository.

## Example Molecule scenario

The example `molecule.yml` below is a scenario to run test on Debian 11 (Bullseye).

```yml
---
dependency:
  name: galaxy
driver:
  name: docker
lint: |
  set -e
  yamllint `git ls-files '*.yaml' '*.yml'`
  ansible-lint
  flake8
platforms:
  - name: debian-bullseye
    image: "ghcr.io/hspaans/molecule-container-debian:bullseye"
    command: ""
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
    privileged: true
    pre_build_image: true
provisioner:
  name: ansible
verifier:
  name: testinfra
```

## Versions

The container is based on [LTS](https://en.wikipedia.org/wiki/Long-term_support) distribution versions with official support and fall within N and N-1. The *latest*-tag is an experimental tag to test future releases.

| Distribution | Release        | Platforms    | Status      |
|--------------|----------------|--------------|-------------|
| CentOS       | 7              | AMD64, ARM64 | Legacy      |
| CentOS       | 8              | AMD64, ARM64 | End-of-Life |
| Debian       | buster (10)    | AMD64, ARM64 | Supported   |
| Debian       | bullseye (11)  | AMD64, ARM64 | Supported   |
| Debian       | bookworm (12)  | AMD64, ARM64 | Development |
| Fedora       | 34             | AMD64, ARM64 | Supported   |
| Fedora       | 35             | AMD64, ARM64 | Supported   |
| Ubuntu       | bionic (18.04) | AMD64, ARM64 | Supported   |
| Ubuntu       | focal (20.04)  | AMD64, ARM64 | Supported   |
| Ubuntu       | jammy (22.04)  | AMD64, ARM64 | Development |

[ansible]: https://github.com/ansible/ansible
[debian]: https://debian.org
[ubuntu]: https://ubuntu.org
[docker-debian10-ansible]: https://github.com/geerlingguy/docker-debian10-ansible
[geerlingguy]: https://github.com/geerlingguy
[molecule]: https://github.com/ansible-community/molecule
