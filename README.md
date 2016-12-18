Ubuntu 16.04 Ansible Test Image
=============================
![Build Status](https://img.shields.io/docker/automated/jrottenberg/ffmpeg.svg)

Ubuntu 16.04 Docker container for Ansible playbook and role testing.


How to Build
--------------
This image is built on Docker Hub automatically any time the upstream base OS container is rebuilt, and any time a commit is made or merged to the master branch. But if you need to build the image on your own locally, do the following:

1. Install Docker.
2. `cd` into this directory.
3. Run `docker build -t ubuntu1404-ansible`


How to use
------------
1. Install Docker
2. Pull this image from Docker Hub: docker pull bmacauley/docker-ubuntu1404-ansible:latest (or use the tag  built earlier, e.g. ubuntu1404-ansible)
3. Run a container from the image: `docker run --detach --privileged --volume=/sys/fs/cgroup:/sys/fs/cgroup:ro bmacauley/docker-ubuntu1404-ansible:latest /usr/lib/systemd/systemd` (to test  Ansible roles,  add in a volume mounted from the current working directory with `--volume=`pwd`:/etc/ansible/roles/role_under_test:ro)`.
4. Use Ansible inside the container:
a. `docker exec --tty [container_id] env TERM=xterm ansible --version`
b. `docker exec --tty [container_id] env TERM=xterm ansible-playbook /path/to/ansible/playbook.yml --syntax-check`

Author
------
Brian Macauley

Heavily based on  [geerlingguy/docker-ubuntu1404-ansible](https://github.com/geerlingguy/docker-ubuntu1404-ansible)
