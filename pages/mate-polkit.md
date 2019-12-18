# mate-polkit

## Package requirements

  * [mate-common](mate-common.md)

  * appindicator3 >= 3-0.1

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * polkit-agent-1 >= 0.97

  * gobject-introspection-1.0 >= 0.6.2 (libgirepository-1.0)

## Building

build-mate-polkit.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-polkit"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
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
