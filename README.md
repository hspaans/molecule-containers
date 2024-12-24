# Containers for Molecule

For testing [Ansible][ansible] roles with [Molecule][molecule], it is useful to have a container image with Ansible installed. This repository contains a collection of container images for testing Ansible roles with Molecule. The container images are available on [GitHub Container Registry](https://ghcr.io) and a current list of available images can be found on the [container overview page](https://github.com/hspaans/molecule-containers/pkgs/container/molecule-containers/versions?filters%5Bversion_type%5D=tagged).

> **Note:** The container images are **NOT** intended for production use and should only be used for testing purposes. The security of the container images is not guaranteed and the images are not updated with the latest security patches.

## Container images and versions

Distributions are based on [LTS](https://en.wikipedia.org/wiki/Long-term_support) versions with official support and fall within N and N-1. Older images are removed from the registry when they reach end-of-life.

Currently, the following distributions are supported:
* [![Container Release (Amazon Linux 2023)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-amazonlinux-2023.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-amazonlinux-2023.yml) - `ghcr.io/hspaans/molecule-containers:amazonlinux-2023`
* [![Container Release (Debian 10)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-10.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-10.yml) - `ghcr.io/hspaans/molecule-containers:debian-10`
* [![Container Release (Debian 11)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-11.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-11.yml) - `ghcr.io/hspaans/molecule-containers:debian-11`
* [![Container Release (Debian 12)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-12.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-debian-12.yml) - `ghcr.io/hspaans/molecule-containers:debian-12`
* [![Container Release (Fedora 38)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-38.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-38.yml) - `ghcr.io/hspaans/molecule-containers:fedora-38`
* [![Container Release (Fedora 39)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-39.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-39.yml) - `ghcr.io/hspaans/molecule-containers:fedora-39`
* [![Container Release (Fedora 40)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-40.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-40.yml) - `ghcr.io/hspaans/molecule-containers:fedora-40`
* [![Container Release (Fedora 41)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-41.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-fedora-41.yml) - `ghcr.io/hspaans/molecule-containers:fedora-41`
* [![Container Release (Oracle Linux 8)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-8.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-8.yml) - `ghcr.io/hspaans/molecule-containers:oraclelinux-8`
* [![Container Release (Oracle Linux 9)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-9.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-oraclelinux-9.yml) - `ghcr.io/hspaans/molecule-containers:oraclelinux-9`
* [![Container Release (Rocky Linux 8)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-8.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-8.yml) - `ghcr.io/hspaans/molecule-containers:rockylinux-8`
* [![Container Release (Rocky Linux 9)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-9.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-rockylinux-9.yml) - `ghcr.io/hspaans/molecule-containers:rockylinux-9`
* [![Container Release (Ubuntu 20.04)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2004.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2004.yml) - `ghcr.io/hspaans/molecule-containers:ubuntu-20.04`
* [![Container Release (Ubuntu 22.04)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2204.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2204.yml) - `ghcr.io/hspaans/molecule-containers:ubuntu-22.04`
* [![Container Release (Ubuntu 24.04)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2404.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-ubuntu-2404.yml) - `ghcr.io/hspaans/molecule-containers:ubuntu-24.04`

Experimental images are available for the following distributions:
* [![Container Release (Alpine 3.18)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.18.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.18.yml) - `ghcr.io/hspaans/molecule-containers:alpine-3.18`
* [![Container Release (Alpine 3.19)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.19.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.19.yml) - `ghcr.io/hspaans/molecule-containers:alpine-3.19`
* [![Container Release (Alpine 3.20)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.20.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.20.yml) - `ghcr.io/hspaans/molecule-containers:alpine-3.20`
* [![Container Release (Alpine 3.21)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.21.yml/badge.svg)](https://github.com/hspaans/molecule-containers/actions/workflows/container-release-alpine-3.21.yml) - `ghcr.io/hspaans/molecule-containers:alpine-3.21`

> **Note:** Previous images were stored in the `hspaans/molecule-container-<distribution>:<version>` package repository on GitHube. These images are no longer maintained and will be removed in the future as they become end-of-life. It is recommended to use the new images from the `ghcr.io/hspaans/molecule-containers:<distribution>-<version>` package repository.

## Example Molecule scenario

The example `molecule.yml` below is a scenario to run test on Debian 12 and Ubuntu 22.04.

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
    image: "ghcr.io/hspaans/molecule-containers:ubuntu-22.04"
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
