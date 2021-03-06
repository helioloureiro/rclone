---
title: "Install"
description: "Rclone Installation"
date: "2016-03-28"
---

# Install #

Rclone is a Go program and comes as a single binary file.

## Quickstart ##

  * [Download](/downloads/) the relevant binary.
  * Unpack and the `rclone` binary.
  * Run `rclone config` to setup. See [rclone config docs](http://rclone.org/docs/) for more details.

See below for some expanded Linux / macOS instructions.

See the [Usage section](/docs/) of the docs for how to use rclone, or
run `rclone -h`.

## Linux installation from precompiled binary ##

Fetch and unpack

    curl -O http://downloads.rclone.org/rclone-current-linux-amd64.zip
    unzip rclone-current-linux-amd64.zip
    cd rclone-*-linux-amd64

Copy binary file

    sudo cp rclone /usr/bin/
    sudo chown root:root /usr/bin/rclone
    sudo chmod 755 /usr/bin/rclone
    
Install manpage

    sudo mkdir -p /usr/local/share/man/man1
    sudo cp rclone.1 /usr/local/share/man/man1/
    sudo mandb 

Run `rclone config` to setup. See [rclone config docs](http://rclone.org/docs/) for more details.

    rclone config

## macOS installation from precompiled binary ##

Download the latest version of rclone.

    cd && curl -O http://downloads.rclone.org/rclone-current-osx-amd64.zip

Unzip the download and cd to the extracted folder.

    unzip -a rclone-current-osx-amd64.zip && cd rclone-*-osx-amd64

Move rclone to your $PATH. You will be prompted for your password.

    sudo mv rclone /usr/local/bin/

Remove the leftover files.

    cd .. && rm -rf rclone-*-osx-amd64 rclone-current-osx-amd64.zip

Run `rclone config` to setup. See [rclone config docs](http://rclone.org/docs/) for more details.

    rclone config

## Install from source ##

Make sure you have at least [Go](https://golang.org/) 1.5 installed.
Make sure your `GOPATH` is set, then:

    go get -u -v github.com/ncw/rclone

and this will build the binary in `$GOPATH/bin`.  If you have built
rclone before then you will want to update its dependencies first with
this

    go get -u -v github.com/ncw/rclone/...

## Installation with Ansible ##

This can be done with [Stefan Weichinger's ansible
role](https://github.com/stefangweichinger/ansible-rclone).

Instructions

  1. `git clone https://github.com/stefangweichinger/ansible-rclone.git` into your local roles-directory
  2. add the role to the hosts you want rclone installed to:
    
```
    - hosts: rclone-hosts
      roles:
          - rclone
```

## Installation with snap ##

### Quickstart ###

  * install Snapd on your distro using the instructions below
  * sudo snap install rclone --classic 
  * Run `rclone config` to setup. See [rclone config docs](http://rclone.org/docs/) for more details.

See below for how to install snapd if it isn't already installed

#### Arch ####

    sudo pacman -S snapd

enable the snapd systemd service:

    sudo systemctl enable --now snapd.socket

#### Debian / Ubuntu ####

    sudo apt install snapd

#### Fedora ####

    sudo dnf copr enable zyga/snapcore
    sudo dnf install snapd

enable the snapd systemd service:

    sudo systemctl enable --now snapd.service

SELinux support is in beta, so currently:

    sudo setenforce 0

to persist, edit `/etc/selinux/config` to set `SELINUX=permissive` and reboot.

#### Gentoo ####

Install the [gentoo-snappy overlay](https://github.com/zyga/gentoo-snappy).

#### OpenEmbedded/Yocto ####

Install the [snap meta layer](https://github.com/morphis/meta-snappy/blob/master/README.md).

#### openSUSE ####

    sudo zypper addrepo http://download.opensuse.org/repositories/system:/snappy/openSUSE_Leap_42.2/ snappy
    sudo zypper install snapd

#### OpenWrt ####

Enable the snap-openwrt feed.
