# Docker Image Packaging for Debian

[![Travis](https://img.shields.io/travis/com/alvistack/docker-debian.svg)](https://travis-ci.com/alvistack/docker-debian)
[![GitHub release](https://img.shields.io/github/release/alvistack/docker-debian.svg)](https://github.com/alvistack/docker-debian/releases)
[![GitHub license](https://img.shields.io/github/license/alvistack/docker-debian.svg)](https://github.com/alvistack/docker-debian/blob/master/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/alvistack/debian.svg)](https://hub.docker.com/r/alvistack/debian/)

Debian is a free and open-source operating system and Linux distribution based on Debian.

Learn more about Debian: <https://www.debian.com/>

## Supported Tags and Respective Packer Template Links

  - [`10`, `latest`](https://github.com/alvistack/docker-debian/blob/master/packer/10/packer.json)

## Overview

This Docker container makes it easy to get an instance of SSHD up and running with Debian.

Based on [Official Debian Docker Image](https://hub.docker.com/_/debian/) with some minor hack:

  - Packaging by Packer Docker builder and Ansible provisioner in single layer
  - Handle `ENTRYPOINT` with [catatonit](https://github.com/openSUSE/catatonit)
  - Handle `CMD` with SSHD

### Quick Start

Start SSHD:

    # Pull latest image
    docker pull alvistack/debian
    
    # Run as detach
    docker run \
        -itd \
        --name debian \
        --publish 2222:22 \
        alvistack/debian

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

### `alvistack/debian:latest`

The `latest` tag matches the most recent [GitHub Release](https://github.com/alvistack/docker-debian/releases) of this repository. Thus using `alvistack/debian:latest` or `alvistack/debian` will ensure you are running the most up to date stable version of this image.

### `alvistack/debian:<version>`

The version tags are rolling release rebuild by [Travis](https://travis-ci.com/alvistack/docker-debian) in weekly basis. Thus using these tags will ensure you are running the latest packages provided by the base image project.

## License

  - Code released under [Apache License 2.0](LICENSE)
  - Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

## Author Information

  - Wong Hoi Sing Edison
      - <https://twitter.com/hswong3i>
      - <https://github.com/hswong3i>
