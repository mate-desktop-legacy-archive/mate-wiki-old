# mate-user-share

## Package requirements

  * [caja](caja.md)

  * [mate-common](mate-common.md)

  * apache >= 2.2

  * dbus-glib-1

  * gettext >= 0.19.8

  * gio-2.0

  * gdk-x11-3.0

  * glib-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * libcanberra-gtk3

  * libnotify >= 0.7.0

  * mod_dnssd >= 0.6

  * selinux

  * yelp-tools

## Building

```bash
$ cat build-mate-user-share.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-user-share"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
# Extract
tar xvjf $package-$version.tar.xz
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static
# Compile
make
# Install
sudo make install
```

