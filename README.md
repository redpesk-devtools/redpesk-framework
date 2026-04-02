# redpesk-framework

This repository provides the way of compiling and installing
redpesk framework and/or redpesk SDK on a local computer
without needing to be root.

## Setup

Configuration is given by the file `config`.
This file is sourced, so be careful to not introduce
bugs or security concerns.

When sourced, the environment variable ROOTDIR is
defined to the path of this directory.

```
# configuration file for redpesk-framework

# default build directory
BUILDDIR=$ROOTDIR/BUILDDIR

# default installation directory
PREFIX=/opt/redpesk
#PREFIX=$HOME/.local

# set it to yes to activate debugging installation
#DEBUG=yes
```

Redpesk framework depends on compiling tools and of
external libraries that should be available on the
computer for compiling it.

### Install dependencies on fedora

Compiling on Fedora, Redhat other related distribution
requires installing the below packages:

```sh
$ sudo dnf install \
    gcc binutils make cmake pkg-config \
    json-c-devel libyaml-devel \
    gnutls-devel libcurl-devel \
    libuuid-devel file-devel libmicrohttpd-devel systemd-devel \
    readline-devel
```

### Install dependencies on debian and ubuntu

Compiling on Debian, Ubuntu, Linux Mint and other debian based distribution
requires installing the below packages:

```sh
$ sudo apt install \
    gcc binutils make cmake pkg-config \
    libjson-c-dev libyaml-dev \
    libgnutls28-dev libcurl4-gnutls-dev \
    uuid-dev libmagic-dev libmicrohttpd-dev libsystemd-dev \
    libreadline-dev
```

## Installation of the SDK

After preparing the computer: edition of config file and
installation of dependencies, the SDK can be compiled and
installed.

The script `menu` allows to build, install, uninstall, show
the environment setup, ... Its usage is easy, just follow
the instructions.

## Working with the git

The framework can also be fetched using git. It uses submodules.
The below command show how to fetch the git repository and
its submodules.

```sh
$ git clone URL
$ cd redpesk-framework
$ git submodule init
$ git submodule update
```

