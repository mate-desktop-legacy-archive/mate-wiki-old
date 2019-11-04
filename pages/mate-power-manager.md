# mate-power-manager

## Package requirements

## Building

build-mate-power-manager.sh

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-power-manager"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc \
            --localstatedir=/var --disable-static \
            --libexecdir=/usr/lib/mate-power-manager
    # Compile
    make
    # Install
    sudo make install
```
