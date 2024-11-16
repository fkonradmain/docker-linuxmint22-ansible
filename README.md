# Linux Mint 22 (Based on Ubuntu 24.04) Ansible Test Image

[![CI](https://github.com/fkonradmain/docker-linuxmint22-ansible/workflows/Build/badge.svg?branch=master&event=push)](https://github.com/fkonradmain/docker-linuxmint22-ansible/actions?query=workflow%3ABuild)

Linux Mint 22 (Based on Ubuntu 24.04 LTS Noble Numbat) Docker container for Ansible playbook and role testing.

## Tags

  - `latest`: Latest stable version of Ansible.

The latest tag is a lightweight image for basic validation of Ansible playbooks.

## How to Build

This image is built on Docker Hub automatically any time the upstream OS container is rebuilt, and any time a commit is made or merged to the `master` branch. But if you need to build the image on your own locally, do the following:

  1. [Install Docker](https://docs.docker.com/install/).
  2. `cd` into this directory.
  3. Run `docker build -t linuxmint22-ansible .`

## How to Use

  1. [Install Docker](https://docs.docker.com/engine/installation/).
  2. Pull this image from Docker Hub: `docker pull fkonradmain/docker-linuxmint22-ansible:latest` (or use the image you built earlier, e.g. `ubuntu2404-ansible:latest`).
  3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host fkonradmain/docker-linuxmint22-ansible:latest` (to test Mr. Geerling's Ansible roles, add in a volume mounted from the current working directory with ``--volume=`pwd`:/etc/ansible/roles/role_under_test:ro``).
  4. Use Ansible inside the container:
    a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
    b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

## Notes

I use Docker to test my Ansible roles and playbooks on multiple OSes using CI tools like Jenkins and Travis. This container allows me to test roles and playbooks using Ansible running locally inside the container.

> **Important Note**: I use this image for testing in an isolated environment—not for production—and the settings and configuration used may not be suitable for a secure and performant production environment. Use on production servers/in the wild at your own risk!

## Author

Created in 2024 by Fabian Konrad @fkonradmain

forked from [Jeff Geerling](https://www.jeffgeerling.com/),
Original repo available at <https://github.com/geerlingguy/docker-ubuntu2404-ansible>
