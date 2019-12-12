# mate-desktop

## Package requirements

  * [mate-common](./mate-common)

  * dconf >= 0.13.4

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50.0

  * gio-2.0 >= 2.26.0

  * gobject-introspection >= 0.9.7

  * gtk+-3.0 >= 3.22.0

  * gtk-doc >= 1.4

  * libxrandr >= 1.3

  * iso-codes

  * startup-notification >= 0.5

  * XLIB

## Building

```bash
$ cat build-mate-desktop.sh
#!/bin/sh
# Define version
release="1.22"
version="1.22.0"
package="mate-desktop"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
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

