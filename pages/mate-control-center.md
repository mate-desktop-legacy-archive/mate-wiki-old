# mate-control-center

## Package requirements

  * [mate-settings-daemon](./mate-settings-daemon)

  * [mate-desktop](./mate-desktop)

  * [mate-menus](./mate-menus)

  * [marco](./marco)

  * [mate-settings-daemon](./mate-settings-daemon)

  * [libmatekbd](./libmatekbd)

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * libappindicator >= 0.0.13

  * accountsservice

  * dconf

  * desktop-file-utils

  * libcanberra-gtk3 >= 0.4

  * librsvg2

  * libSM

  * libXScrnSaver

## Building

**build-mate-control-center.sh**

```bash
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-control-center"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static \
        --disable-scrollkeeper
# Compile
make
# Install
sudo make install
```
