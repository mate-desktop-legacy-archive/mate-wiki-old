# pluma

## Package requirements

  * [mate-common](./mate-common)

  * enchant-2 >= 1.6.0

  * gio-2.0 >= 2.50.0

  * glib-2.0 >= 2.50.0

  * gmodule-2.0

  * gtk-doc >= 1.0

  * gtksourceview-3.0 >= 3.0.0

  * gtk+-3.0 >= 3.22.0

  * gthread-2.0 >= 2.13.0

  * gettext >= 0.19.8

  * gio-unix-2.0 >= 2.50.0

  * gobject-introspection >= 0.9.3

  * iso-codes >= 0.35

  * libpeas-1.0 >= 1.2.0

  * libpeas-gtk-1.0 >= 1.2.0

  * libSM

  * libxml-2.0 >= 2.5.0

  * python3

  * X11

## Building


```bash
$ cat build-pluma.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="pluma"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
# Extract
tar xvjf $package-$version.tar.xz
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var  --disable-static
# Compile
make
# Install
sudo make install
```
