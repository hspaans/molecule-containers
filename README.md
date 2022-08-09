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

| Distribution | Release  | Platforms    | Status      |
|--------------|----------|--------------|-------------|
| Debian 10    | buster   | AMD64, ARM64 | Supported   |
| Debian 11    | bullseye | AMD64, ARM64 | Supported   |
| Debian 12    | bookworm | AMD64, ARM64 | Development |
| Ubuntu 18.04 | bionic   | AMD64, ARM64 | LTS         |
| Ubuntu 20.04 | focal    | AMD64, ARM64 | LTS         |
| Ubuntu 22.04 | jammy    | AMD64, ARM64 | Development |

[ansible]: https://github.com/ansible/ansible
[debian]: https://debian.org
[docker-debian10-ansible]: https://github.com/geerlingguy/docker-debian10-ansible
[geerlingguy]: https://github.com/geerlingguy
[molecule]: https://github.com/ansible-community/molecule
