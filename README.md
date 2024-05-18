# Containers for Molecule

For testing [Ansible][ansible] roles with [Molecule][molecule], it is useful to have a container image with Ansible installed. This repository contains a collection of container images for testing Ansible roles with Molecule. The container images are available on [GitHub Container Registry](https://ghcr.io) and a current list of available images can be found on the [container overview page](https://github.com/hspaans/molecule-containers/pkgs/container/molecule-containers/versions?filters%5Bversion_type%5D=tagged).

> **Note:** The container images are **NOT** intended for production use and should only be used for testing purposes. The security of the container images is not guaranteed and the images are not updated with the latest security patches.

## Container images and versions

Distributions are based on [LTS](https://en.wikipedia.org/wiki/Long-term_support) versions with official support and fall within N and N-1. Older images are removed from the registry when they reach end-of-life.

Currently, the following distributions are supported:
* Amazon Linux 2023 - `ghcr.io/hspaans/molecule-containers:amazonlinux-2023`
* Debian 10 (buster) - `ghcr.io/hspaans/molecule-containers:debian-10`
* Debian 11 (bullseye) - `ghcr.io/hspaans/molecule-containers:debian-11`
* Debian 12 (bookworm) - `ghcr.io/hspaans/molecule-containers:debian-12`
* Fedora 38 - `ghcr.io/hspaans/molecule-containers:fedora-38`
* Fedora 39 - `ghcr.io/hspaans/molecule-containers:fedora-39`
* Fedora 40 - `ghcr.io/hspaans/molecule-containers:fedora-40`
* Oracle Linux 8 - `ghcr.io/hspaans/molecule-containers:oraclelinux-8`
* Oracle Linux 9 - `ghcr.io/hspaans/molecule-containers:oraclelinux-9`
* Rocky Linux 8 - `ghcr.io/hspaans/molecule-containers:rockylinux-8`
* Rocky Linux 9 - `ghcr.io/hspaans/molecule-containers:rockylinux-9`
* Ubuntu 20.04 (focal) - `ghcr.io/hspaans/molecule-containers:ubuntu-20.04`
* Ubuntu 22.04 (jammy) - `ghcr.io/hspaans/molecule-containers:ubuntu-22.04`
* Ubuntu 24.04 (noble) - `ghcr.io/hspaans/molecule-containers:ubuntu-24.04`

Experimental images are available for the following distributions:
* Alpine 3.18 - `ghcr.io/hspaans/molecule-containers:alpine-3.18`
* Alpine 3.19 - `ghcr.io/hspaans/molecule-containers:alpine-3.19`

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
