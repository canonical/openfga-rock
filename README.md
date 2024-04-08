# OpenFGA ROCK

[![Release](https://github.com/canonical/openfga-rock/actions/workflows/ci.yaml/badge.svg)](https://github.com/canonical/openfga-rock/actions/workflows/ci.yaml)
[![Container Registry](https://img.shields.io/badge/Container%20Registry-published-blue)](https://github.com/canonical/openfga-rock/pkgs/container/openfga)


This repository contains the packaging metadata for creating an OpenFGA ROCK built from Canonical OpenFGA release artifacts.  For more information on ROCKs, visit the [rockcraft Github](https://github.com/canonical/rockcraft). 



## Building the ROCK
The steps outlined below are based on the assumption that you are building the ROCK with the latest LTS of Ubuntu.  If you are using another version of Ubuntu or another operating system, the process may be different.

### Clone Repository
```bash
git clone git@github.com:canonical/openfga-rock.git
cd openfga-rock
```

### Installing Prerequisites
```bash
sudo snap install rockcraft --edge
sudo snap install docker
sudo snap install lxd
sudo snap install skopeo --edge --devmode
```

### Configuring Prerequisites
```bash
sudo usermod -aG docker $USER 
sudo lxd init --auto
```
*_NOTE:_* You will need to open a new shell for the group change to take effect (i.e. `su - $USER`)


### Packing and Running the ROCK
```bash
rockcraft pack
skopeo --insecure-policy copy oci-archive:openfga*.rock docker-daemon:<username>/openfga:<tag>
docker run --rm -it <username>/openfga:<tag>
```

## License
The OpenFGA ROCK is free software, distributed under the Apache
Software License, version 2.0. See
[LICENSE](https://github.com/canonical/zookeeper-rock/blob/3.6/stable/LICENSE)
for more information.