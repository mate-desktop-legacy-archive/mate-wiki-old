# libmateweather

## Package requirements

  * [mate-common](./mate-common)

  * glib-2.0 >= 2.50.0

  * gio-2.0 >= 2.26.0

  * gtk+-3.0 >= 3.22.0

  * gtk-doc >= 1.11

  * libsoup >= 2.34.0

  * libxml2 >= 2.6.0

## Building

`build-libmateweather.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="libmateweather"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc \
            --localstatedir=/var --disable-static \
            --enable-locations-compression
    # Compile
    make
    # Install
    sudo make install
```
