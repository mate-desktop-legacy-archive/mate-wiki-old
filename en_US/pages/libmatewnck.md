# libmatewnck

## Package requirements

  * gtk+-2.0 >= 2.19.7

  * glib-2.0 >= 2.16.0

  * gobject-2.0 >= 2.13.0

## Building

`build-libmatewnck.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="libmatewnck"
    # Get
    wget -c http://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var --disable-static
    # Compile
    make
    # Install
    sudo make install
```
