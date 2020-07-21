---
edit_link: ''
title: Build from scratch
origin_url: >-
  https://git.automotivelinux.org/src/xds/xds-docs/plain/docs/part-2/2_xds-agent/1_build.md?h=halibut
---

<!-- WARNING: This file is generated by fetch_docs.js using /home/boron/Documents/AGL/docs-webtemplate/site/_data/tocs/devguides/halibut/xds-docs-guides-devguides-book.yml -->

# Build xds-agent from scratch

## Dependencies

Install [Go](https://golang.org/doc/install), [npm](https://www.npmjs.com/),
[nodejs](https://nodejs.org/en/) and some other tools.

Refer to [Prerequisites chapter](../1_Prerequisites.html) for more details.

## Building

Clone sources under `$ROOTDIR/src/gerrit.automotivelinux.org/gerrit/src/xds/xds-agent`
in order respect directory hierarchy that match Go package import logic (see
[How to Write Go Code](https://golang.org/doc/code.html) for more details).

Then use delivered Makefile :

```bash
# Declare ROOTDIR, can be any location (for example xds-build)
ROOTDIR=$HOME/xds-build

# Create directory hierarchy that match Go package import logic
mkdir -p $ROOTDIR/src/gerrit.automotivelinux.org/gerrit/src/xds
cd $ROOTDIR/src/gerrit.automotivelinux.org/gerrit/src/xds

# Clone sources
git clone https://gerrit.automotivelinux.org/gerrit/src/xds/xds-agent
# or git clone ssh://YOUR_USERNAME@gerrit.automotivelinux.org:29418/src/xds/xds-agent

# Build xds-agent
# (note that GOPATH will correctly be set by Makefile)
cd xds-agent
make all
```

Generate xds-agent packages / tarballs for Linux, MacOS, Windows

```bash
make package-all
```

And to install `xds-agent` (by default in `/opt/AGL/xds/agent`):

```bash
make install
```

<!-- section-warning -->
**Warning:**

Makefile install rule and default values in configuration file are set
to fit the docker setup.

So you may need to adapt some settings when you want to install xds-agent natively.
<!-- end-section-warning -->

<!-- section-note -->
**Note:**

Used `DESTDIR` to specify another install directory

```bash
make install DESTDIR=$HOME/opt/xds-agent
```

<!-- end-section-note -->

### Cross build

For example on a Linux machine to cross-build for Windows, just follow these steps.

The first time you need to install all the windows-amd64 standard packages on
your system with

```bash
# List all supported OS / ARCH
go tool dist list

# Install all standard packages for another OS/ARCH (eg. windows amd64)
GOOS=windows GOARCH=amd64 go install -v -a std
```

Then compile and package xds-agent using provided makefile

```bash
export GOOS=windows
export GOARCH=amd64
make all
make package
```