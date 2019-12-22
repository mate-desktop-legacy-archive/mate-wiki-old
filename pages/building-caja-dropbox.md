# caja-dropbox

## Package requirements

  * [caja](caja.md)

  * glib-2.0 >= 2.50.0

  * pygobject-3.0

  * python3

  * python3-docutils

## Building

`build-caja-dropbox.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="caja-dropbox"
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

