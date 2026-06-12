# Installing and compiling redpesk framework on any linux

This repository provides the way of compiling and installing
redpesk framework and/or redpesk SDK on a local computer
without needing to be root.

Steps to follow are easy:

- Setup your environment
   - install dependencies
   - adapt the config if needed

- Run the interactive tool `menu` for compiling,
  installing, cleaning, ...

## Setup

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

### check the configuration

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

## Installation of the SDK using MENU

The script `menu` allows to build, install, uninstall, show
the environment setup, ... Its usage is easy, just follow
the instructions.

Here an example of its use:

```
HOME/redpesk-framework> ./menu

  REDPESK FRAMEWORK SDK MANAGER

  Current configuration:

    BUILD   HOME/redpesk/redpesk-devtools/redpesk-framework/BUILDDIR
    INSTALL HOME/.local
    DEBUG   no

  ** commands **

  1: (h)elp      2: (e)dit        3: (b)uild and (i)nstall
  4: (r)eset     5: (u)ninstall   6: (s)how (s)etup
  7: (c)lean     8: (q)uit

  What now? 6


export PATH="HOME/.local/bin:$PATH"
export LD_LIBRARY_PATH="HOME/.local/lib64:HOME/.local/lib:$LD_LIBRARY_PATH"
export LIBRARY_PATH="HOME/.local/lib64:HOME/.local/lib:$LIBRARY_PATH"
export PKG_CONFIG_PATH="HOME/.local/lib64/pkgconfig:HOME/.local/lib/pkgconfig:HOME/.local/share/pkgconfig:$PKG_CONFIG_PATH"
export CPATH="HOME/.local/include:$CPATH"
export MANPATH="HOME/.local/share/man:$MANPATH"



  REDPESK FRAMEWORK SDK MANAGER

  Current configuration:

    BUILD   HOME/redpesk-framework/BUILDDIR
    INSTALL HOME/.local
    DEBUG   no

  ** commands **

  1: (h)elp      2: (e)dit        3: (b)uild and (i)nstall
  4: (r)eset     5: (u)ninstall   6: (s)how (s)etup
  7: (c)lean     8: (q)uit

  What now? 3

```

Here is the help text of `menu`:

```
This is the help of the manager menu of redpesk framework SDK.
Apart this help, the menu offers the action detailled below.
The action are run by typing their number or the letter in brackets.

1. (h)elp

  Shows this help

2. (e)dit

  Shows what file is to be edited for changing the settings.
  See the README.md file for more details on config.
  Then it waits for a press on enter key to reload settings
  and iterate on the menu.

3. (b)uild and (i)nstall

  Build and install redpesk framework SDK accordingly to the
  current configuration.
  The build fails if the required packages are not installed
  on the computer.
  See the README.md file for more details on required packages.

4. (r)eset

  Remove all build artifacts. Note that after doing this action,
  the action "uninstall" becomes unavailable.

5. (u)ninstall

  Uninstall the files installed by "build and install".

6. (s)how (s)etup

  Shows how to setup your environment variables for using
  the SDK. Check your prefered shell documentation for
  adding these settings in your environment automatically.

7. (c)lean

  Removes build artifacts from build directories. It differs
  from "reset" because it does not removes files used for
  building. After this action, most artifacts are removed
  and the action "uninstall" remains available.

8. (q)uit

  Exits the menu.

```

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

