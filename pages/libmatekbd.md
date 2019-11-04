# libmatekbd

## Package requirements

  * intltool >= 0.35.0

  * glib-2.0 >= 2.18

## Building

`build-libmatekbd.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="libmatekbd"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc
    # Compile
    make
    # Install
    sudo make install
```

