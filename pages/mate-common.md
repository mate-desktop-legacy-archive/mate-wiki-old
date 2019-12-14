# mate-common

## Source

<https://github.com/mate-desktop/mate-common>

## Package Dependencies

**_Debian (Wheezy/Sid), Ubuntu 11.10, Linux Mint 12_**

  * autoconf

  * automake

  * libtool

  * pkg-config

  * gettext

  * intltool

  * gtk-doc-tools

  * See [this](https://github.com/mate-desktop/debian-packages/blob/master/mate-common/debian/control) control file for more info.

## Building

`build-mate-common.sh`

```bash
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-common"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
# Extract
tar xvjf $package-$version.tar.xz
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr
# Compile
make
# Install
sudo make install
```
