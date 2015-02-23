shingonoide/archlinux-busybox
======

[![Automated Build](http://img.shields.io/badge/automated-build-green.svg)](https://registry.hub.docker.com/u/dock0/arch/)
[![MIT Licensed](http://img.shields.io/badge/license-MIT-green.svg)](https://tldrlegal.com/license/mit-license)

Archlinux 2015.02.23 Minimal installation x86_64

## Usage

### Pull image to you docker

    docker pull shingonoide/archlinux-busybox

### Run a container with bash

    docker run -it shingonoide/archlinux-busybox bash

### Install package with pacman

    docker run shingonoide/archlinux-busybox pacman -S python2-pip

### base-devel to get development tools

If you need the base-devel group to compile anything, recommended way is install and remove after compilation:

    pacman -Sy --needed --noconfirm base-devel

After compile, remove all base-devel packages of your image:

    pacman -R $(pacman -Sg base-devel | awk '{print $2}') && rm /var/cache/pacman/pkg/*


## Details

* This image has pacman keys initialized.
* Packages removed or changed
  * __systemd__ removed, not need to container environment
  * __busybox-coreutils__ instead of ~~__coreutils__~~
  * __busybox-util-linux__ instead ~~__util-linux__~~
  * __busybox-iputils__ instead of ~~__iputils__~~
  * __busybox-findutils__ instead of ~~__findutils__~~

Generated with [mkimage-arch.sh][1]

To build a new arch image, use my changed script [mkimage-arch.sh][1]

_**:(**The script ([mkimage-arch.sh][1]) is not so easy to understand yet, need more comments and organize the structure of code**):**_

## License

The scripts in this repo are released under the MIT License. See the bundled LICENSE file for details. The packages and other content stored in root.tar.xz retains its original licenses.

[1]: https://github.com/shingonoide/archlinux-docker/blob/master/mkimage-arch.sh
