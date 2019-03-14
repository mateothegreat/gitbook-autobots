# Docker

## Enable the docker repository

```bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

## Install Docker Community Edition \(docker-ce\)

```bash
sudo yum install docker-ce
```

## Configure Docker to start on boot

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

## Give local user docker permissions

You can grant individual users permissions to interact with the docker daemon by adding them to the `docker` group.

> Once you add a user to the docker group they will need to re-login before using the `docker` command.

```bash
sudo usermod -aG docker $USER
```

## Test docker

```bash
[yomateod@centos-2 ~]$ sudo ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

