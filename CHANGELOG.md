# Docker Image Packaging for Debian

## 10.6-XalvistackY - TBC

### Major Changes

  - Migrate from Travis CI to GitLab CI
  - Revamp with Packer

## 10.6-4alvistack1 - 2020-10-14

### Major Changes

  - Refine Molecule matrix

## 10.5-4alvistack1 - 2020-09-07

  - Debian 10.5 based
  - Minimized `Dockerfile` for meta data definition
  - Provision by Ansible and Molecule Docker driver in single layer
  - Handle `ENTRYPOINT` with [catatonit](https://github.com/openSUSE/catatonit)
  - Handle `CMD` with SSHD
