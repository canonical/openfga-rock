# OpenFGA rock

[![Container Registry](https://img.shields.io/badge/Container%20Registry-published-blue)](https://github.com/canonical/openfga-rock/pkgs/container/openfga)
![Latest Version](https://img.shields.io/badge/dynamic/yaml?url=https%3A%2F%2Fraw.githubusercontent.com%2Fcanonical%2Fopenfga-rock%2Fmain%2Frockcraft.yaml&query=%24.version&label=Release&color=red)
[![License](https://img.shields.io/github/license/canonical/openfga-rock?label=License)](https://github.com/canonical/openfga-rock/blob/main/LICENSE)

[![Release](https://github.com/canonical/openfga-rock/actions/workflows/ci.yaml/badge.svg)](https://github.com/canonical/openfga-rock/actions/workflows/ci.yaml)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit)](https://github.com/pre-commit/pre-commit)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196.svg)](https://conventionalcommits.org)

This repository contains the packaging metadata for creating an OpenFGA rock
built from Canonical OpenFGA release artifacts. For more information on rocks,
visit the [rockcraft GitHub](https://github.com/canonical/rockcraft).

## Building the rock

The steps outlined below are based on the assumption that you are building the
rock with the latest LTS of Ubuntu. If you are using another version of Ubuntu
or another operating system, the process may be different.

### Clone Repository

```shell
git clone git@github.com:canonical/openfga-rock.git
cd openfga-rock
```

### Installing Prerequisites

```shell
sudo snap install rockcraft --edge
sudo snap install docker
sudo snap install lxd
sudo snap install skopeo --edge --devmode
```

### Configuring Prerequisites

```shell
sudo usermod -aG docker $USER
sudo lxd init --auto
```

**NOTE:** You will need to open a new shell for the group change to take
effect (i.e. `su - $USER`)

### Packing and Running the rock

```shell
rockcraft pack
skopeo --insecure-policy copy oci-archive:openfga*.rock docker-daemon:<username>/openfga:<tag>
docker run --rm -it <username>/openfga:<tag>
```

## License

The OpenFGA rock is free software, distributed under the Apache Software
License, version 2.0. See [LICENSE](./LICENSE) for more information.
