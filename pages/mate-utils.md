# mate-utils

## Package requirements

  * [mate-common](./mate-common)

  * [mate-panel](./mate-panel)

  * gio-2.0 >= 2.50.0

  * gio-unix-2.0 >= 2.18.0

  * glib-2.0 >= 2.50.0

  * gthread-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * libcanberra-gtk3 >= 0.4

  * libgtop-2.0 >= 2.12.0

  * udisks2 >= 1.90.0

  * Xext

  * X11

  * yelp-tools

  * zlib

## Building

build-mate-utils.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-utils"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
            --libexecdir=/usr/bin --disable-static
    # Compile
    make
    # Install
    sudo make install
```
