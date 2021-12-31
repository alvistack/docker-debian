# Docker Image Packaging for Debian

<img src="/alvistack.svg" width="75" alt="AlviStack">

[![GitLab pipeline status](https://img.shields.io/gitlab/pipeline/alvistack/docker-debian/master)](https://gitlab.com/alvistack/docker-debian/-/pipelines)
[![GitHub tag](https://img.shields.io/github/tag/alvistack/docker-debian.svg)](https://github.com/alvistack/docker-debian/tags)
[![GitHub license](https://img.shields.io/github/license/alvistack/docker-debian.svg)](https://github.com/alvistack/docker-debian/blob/master/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/alvistack/debian-10.svg)](https://hub.docker.com/r/alvistack/debian-10)

Debian is an operating system which is composed primarily of free and open-source software, most of which is under the GNU General Public License, and developed by a group of individuals known as the Debian project. Debian is one of the most popular Linux distributions for personal computers and network servers, and has been used as a base for several other Linux distributions.

Learn more about Debian: <https://debian.org/>

## Supported Tags and Respective Packer Template Links

  - [`alvistack/debian-testing`](https://hub.docker.com/r/alvistack/debian-testing)
      - [`packer/docker-testing/packer.json`](https://github.com/alvistack/docker-debian/blob/master/packer/docker-testing/packer.json)
  - [`alvistack/debian-11`](https://hub.docker.com/r/alvistack/debian-11)
      - [`packer/docker-11/packer.json`](https://github.com/alvistack/docker-debian/blob/master/packer/docker-11/packer.json)
  - [`alvistack/debian-10`](https://hub.docker.com/r/alvistack/debian-10)
      - [`packer/docker-10/packer.json`](https://github.com/alvistack/docker-debian/blob/master/packer/docker-10/packer.json)

## Overview

This Docker container makes it easy to get an instance of SSHD up and running with Debian.

Based on [Official Debian Docker Image](https://hub.docker.com/_/debian/) with some minor hack:

  - Packaging by Packer Docker builder and Ansible provisioner in single layer
  - Handle `ENTRYPOINT` with [catatonit](https://github.com/openSUSE/catatonit)
  - Handle `CMD` with SSHD

### Quick Start

Start SSHD:

    # Pull latest image
    docker pull alvistack/debian-10
    
    # Run as detach
    docker run \
        -itd \
        --name debian \
        --publish 2222:22 \
        alvistack/debian-10

**Success**. SSHD is now available on port `2222`.

Because this container **DIDN'T** handle the generation of root password, so you should set it up manually with `pwgen` by:

    # Generate password with pwgen
    PASSWORD=$(docker exec -i debian pwgen -cnyB1); echo $PASSWORD
    
    # Inject the generated password
    echo "root:$PASSWORD" | docker exec -i debian chpasswd

Alternatively, you could inject your own SSH public key into container's authorized\_keys by:

    # Inject your own SSH public key
    (docker exec -i debian sh -c "cat >> /root/.ssh/authorized_keys") < ~/.ssh/id_rsa.pub

Now you could SSH to it as normal:

    ssh root@localhost -p 2222

## Versioning

### `YYYYMMDD.Y.Z`

Release tags could be find from [GitHub Release](https://github.com/alvistack/docker-debian/tags) of this repository. Thus using these tags will ensure you are running the most up to date stable version of this image.

### `YYYYMMDD.0.0`

Version tags ended with `.0.0` are rolling release rebuild by [GitLab pipeline](https://gitlab.com/alvistack/docker-debian/-/pipelines) in weekly basis. Thus using these tags will ensure you are running the latest packages provided by the base image project.

## License

  - Code released under [Apache License 2.0](LICENSE)
  - Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Author Information

  - Wong Hoi Sing Edison
      - <https://twitter.com/hswong3i>
      - <https://github.com/hswong3i>
