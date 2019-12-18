# mate-terminal

## Package requirements

  * [mate-common](mate-common.md)

  * dconf >= 0.13.4

  * gettext >= 0.19.8

  * gio-2.0 >= 2.50.0

  * glib-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * libSM >= 1.0.0

  * vte-2.91 >= 0.48

  * X11

  * yelp-tools

## Building

build-mate-terminal.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-terminal"
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
