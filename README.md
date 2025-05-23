# Containers for Molecule

For testing [Ansible][ansible] roles with [Molecule][molecule], it is useful to have a container image with Ansible installed. This repository contains a collection of container images for testing Ansible roles with Molecule. The container images are available on [GitHub Container Registry](https://ghcr.io) and a current list of available images can be found on the [container overview page](https://github.com/hspaans/molecule-containers/pkgs/container/molecule-containers/versions?filters%5Bversion_type%5D=tagged).

> [!WARNING]
> The container images are **NOT** intended for production use and should only be used for testing purposes without the latest patches applied.

## Container images and versions

Distributions are based on [LTS](https://en.wikipedia.org/wiki/Long-term_support) versions with official support and fall within N and N-1. Older images are removed from the registry when they reach end-of-life when public security support ends.

* [![Container Release (Amazon Linux 2023)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-amazonlinux-2023.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-amazonlinux-2023.yml)
* [![Container Release (Debian 12)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-12.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-12.yml)
* [![Container Release (Fedora 41)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-41.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-41.yml)
* [![Container Release (Fedora 42)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-42.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-42.yml)
* [![Container Release (Oracle Linux 8)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-8.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-8.yml)
* [![Container Release (Oracle Linux 9)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-9.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-9.yml)
* [![Container Release (Rocky Linux 8)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-8.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-8.yml)
* [![Container Release (Rocky Linux 9)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-9.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-9.yml)
* [![Container Release (Ubuntu 20.04)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2004.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2004.yml)
* [![Container Release (Ubuntu 22.04)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2204.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2204.yml)
* [![Container Release (Ubuntu 24.04)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2404.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2404.yml)

## Example Molecule scenario

The example `molecule.yml` below is a scenario to run test on Debian 12 and Ubuntu 24.04.

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
  - name: debian-12
    image: "ghcr.io/hspaans/molecule-containers:debian-12"
    command: ""
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    privileged: true
    pre_build_image: true

  - name: ubuntu-22.04
    image: "ghcr.io/hspaans/molecule-containers:ubuntu-24.04"
    command: ""
    cgroupns_mode: host
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:rw
    privileged: true
    pre_build_image: true

provisioner:
  name: ansible
verifier:
  name: testinfra
```

[ansible]: https://github.com/ansible/ansible
[debian]: https://debian.org
[molecule]: https://github.com/ansible/molecule
