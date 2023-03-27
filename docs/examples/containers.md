---
title: Easyapache 4 Containers
---

## Overview

EasyApache 4 provides the ability to run applications in containers.  We **only** support containers on systems that run AlmaLinux, Rocky Linux™ 8, or Ubuntu®.

Containers are a light-weight way to manage individual software images. They provide a way for the application to run independently and separately from the rest of the server. This is similar to a virtual machine, except it uses fewer resources and can be quickly and easily started and stopped.

We use <a href="https://podman.io/" target="_blank">podman</a> for our containers. Podman allows your applications to run in the user space as the user rather than as the `root` user.

**Important:** You **must** log in with SSH as the user. You **cannot** use the `su -` or `sudo -E` commands to run this script.

## Setting up containers

To set up containers, you must first install the `ea-podman-repo` package. You **must** install this package first. Then, we recommend installing the `ea-podman` and `ea-tomcat100` packages. These packages set up the system for containers and install our `/usr/local/cpanel/scripts/ea-podman` script to manage them.

**Note:** To use an application in the containers on your server, you **must** install either a cPanel-provided container-based package or an image from another source, such as <a href="https://hub.docker.com/" target="_blank">Dockerhub</a>. You can only perform this action **after** you set up the containers on your server.

### AlmaLinux and Rocky Linux 8
To start using containers on AlmaLinux or Rocky Linux 8, run the following commands on the command line as the `root` user:

```bash
dnf install -y ea-podman-repo
dnf install -y ea-podman
```

### Ubuntu
To start using containers on Ubuntu, run the following commands on the command line as the `root` user:

```bash
apt install -y ea-podman-repo
apt update
apt install -y ea-podman
```


### Use an EA4 container-based package

**Note:** Before you can use an EA4 container-based package for your containers, your system administrator **must** install the EasyApache 4 package on the command line.

Log into the cPanel user account via SSH.  You can do this by either logging into the account via SSH from the command line, or using SSH in either WHM's _Terminal_ interface or cPanel's _Terminal_ interface.

To set up your application, run the following command, where `package` represents the name of a EA4 container-based package:

```
/scripts/ea-podman install package
```

When you set up a container, the system also creates the `~/ea-podman.d/application-name` directory in the user's `home` directory. These directories contain information, files, and other data for the container.

### Use a non-cPanel-provided image

Log into the cPanel user account via SSH. You can do this by either logging into the account via SSH from the command line, or using SSH in either WHM's _Terminal_ interface or cPanel's _Terminal_ interface.

To set up your application, run the following command, where `application` represents the name of the application and `image` represents an image provided by a site such as <a href="https://hub.docker.com/" target="_blank">Dockerhub</a>:

```bash
/scripts/ea-podman install application [options] image
```

When you set up a container, the system also creates the `~/ea-podman.d/application-name` directory in the user's `home` directory. These directories contain information, files, and other data for the container.

## Working with containers

When you install a container package, it creates the `~/ea-podman.d/application-name` directory in the user's `home` directory. You can navigate to these directories to add and delete files and make other changes without the need to log in to the container instance.   You can find the names of your containers with one of the following commands:

* `/usr/local/cpanel/scripts/ea-podman registered`
* `/usr/local/cpanel/scripts/ea-podman running`

You can also use the `/usr/local/cpanel/scripts/ea-podman bash` command to run `bash` commands as if you are logged in to the container's shell interface.


## Available packages for containers

We provide the following packages for containers. These packages are already configured to run on a cPanel system:  

* Memcached 1.6
* Redis® 6.2
* Apache Tomcat® 10.0

You can also run the following command to view the available EA4 container-based packages:

```bash
/usr/local/cpanel/scripts/ea-podman available
```
