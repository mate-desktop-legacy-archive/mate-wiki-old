# libmatekbd

## Package requirements

  * [mate-common](mate-common.md)

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50.0

  * gio-2.0 >= 2.26.0

  * gobject-introspection >= 0.9.7

  * gtk+-3.0 >= 3.22.0

  * libICE

  * libxklavier >= 5.2

## Building

`build-libmatekbd.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="libmatekbd"
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

