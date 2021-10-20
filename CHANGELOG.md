# Docker Image Packaging for Debian

## YYYYMMDD.Y.Z - TBC

### Major Changes

## 20211020.1.1 - 2021-10-20

### Major Changes

  - Install dependencies with package manager
  - Upgrade minimal Ansible community package support to 4.7.0

## 20210718.1.1 - 2021-07-18

### Major Changes

  - Upgrade minimal Ansible community package support to 4.2.0
  - Support Debian 11

## 20210602.1.1 - 2021-06-02

### Major Changes

  - Initialize with `verify.yml` with first start
  - Upgrade minimal Ansible support to 4.0.0
  - Sync structure with `alvistack/vagrant-debian`

## 20210313.1.1 - 2021-03-13

### Major Changes

  - Bugfix [ansible-lint `namespace`](https://github.com/ansible-community/ansible-lint/pull/1451)
  - Bugfix [ansible-lint `no-handler`](https://github.com/ansible-community/ansible-lint/pull/1402)
  - Bugfix [ansible-lint `unnamed-task`](https://github.com/ansible-community/ansible-lint/pull/1413)
  - Change GIT tag as per Vagrant Box naming and versioning limitation

## 10.6-4alvistack7 - 2020-12-09

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
