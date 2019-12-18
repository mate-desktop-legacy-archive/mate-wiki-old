# eom

## Package requirements

  * [mate-common](mate-common.md)

  * [mate-desktop](mate-desktop.md)

  * exempi-2.0 >= 1.99.5

  * gdk_pixbuf-2.0 >= 2.30.0

  * gettext >= 0.19.8

  * glib-2.0 >= 2.52.0

  * gio-2.0 >= 2.52.0

  * gio-unix-2.0 >= 2.52.0

  * gobject-introspection >= 0.9.3

  * gthread-2.0 >= 2.52.0

  * gtk+-3.0 >= 3.22.0

  * gtk+-unix-print-3.0 >= 3.22.0

  * lcms2

  * libexif

  * libjpeg

  * libpeas-1.0 >= 1.8.0

  * libpeas-gtk-1.0 >= 1.8.0

  * librsvg-2.0 >= 2.36.2

  * libxml-2.0 >= 2.0

  * shared-mime-info >= 0.20

  * yelp-tools

  * zlib

## Building

`build-libmatekbd.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="eom"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc
    # Compile
    make
    # Install
    sudo make install
```

