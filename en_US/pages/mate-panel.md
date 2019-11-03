# mate-panel

## Package requirements

  * intltool >= 0.40.0

  * ice

  * sm

  * pango >= 1.15.4

  * gtk+-2.0 >= 2.19.7

  * glib-2.0 >= 2.25.12

  * gio-2.0 >= 2.25.12

  * librsvg-2.0

  * dbus-glib-1

  * [libmateweather](./libmateweather)

  * [mate-desktop](./mate-desktop)

## Building

build-mate-panel.sh

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-panel"
    # Get
    wget -c http://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc \
            --localstatedir=/var --disable-static \
            --libexecdir=/usr/lib/mate-panel \
            --disable-scrollkeeper --enable-introspection --enable-matecomponent
    # Compile
    make
    # Install
    sudo make install
```
