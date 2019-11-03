# mate-polkit

## Package requirements

  * gtk+-2.0 >= 2.17.1

  * polkit-agent-1 >= 0.97

  * gobject-introspection-1.0 >= 0.6.2 (libgirepository-1.0)

## Building

build-mate-polkit.sh

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-polkit"
    # Get
    wget -c http://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc \
            --localstatedir=/var --libexecdir=/usr/lib/polkit-mate \
            --disable-static
    # Compile
    make
    # Install
    sudo make install
```
