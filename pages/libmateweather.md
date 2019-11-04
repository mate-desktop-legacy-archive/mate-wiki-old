# libmateweather

## Package requirements

  * intltool >= 0.40.3

  * gtk+-2.0 >= 2.11.0

  * libsoup-2.4 >= 2.4.0

## Building

`build-libmateweather.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="libmateweather"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
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
