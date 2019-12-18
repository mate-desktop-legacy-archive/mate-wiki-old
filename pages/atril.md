# atril

## Package requirements

  * [caja](caja.md)

  * [mate-common](mate-common.md)

  * gettext >= 0.19.8

  * cairo >= 1.14.0

  * djvulibre >= 3.5.17

  * gail-3.0 >= 3.22.0

  * gio-2.0 >= 2.54.0

  * gmodule-2.0 >= 2.54.0

  * glib-2.0 >= 2.54.0

  * glibc-headers (backtrace support)

  * gobject-introspection >= 0.6

  * gthread-2.0

  * gtk+-3.0 >= 3.22.0

  * gtk+-unix-print-3.0

  * gxps >= 0.2.1

  * kpathsea

  * libSM >= 1.0.0

  * libxml-2.0 >= 2.5.0

  * poppler-glib >= 0.22.0

  * secret-1 >= 0.5

  * spectre >= 0.2.0

  * synctex >= 1.21

  * tiff

  * webkit2gtk-4.0

  * X11

  * yelp-tools

  * zlib

## Building

```bash
$ cat build-atril.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="atril"
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

