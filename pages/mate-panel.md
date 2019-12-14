# mate-panel

## Package requirements

  * [mate-common](./mate-common)

  * [libmateweather](./libmateweather)

  * [mate-desktop](./mate-desktop)

  * [mate-menus](./mate-menus)

  * dconf >= 0.13.4

  * gdbus

  * gettext >= 0.19.8

  * gio-2.0 >= 2.50.0

  * glib-2.0 >= 2.50.0

  * gobject-introspection >= 0.6.7

  * gtk+-3.0 >= 3.22.0

  * gtk_layer_shell

  * libICE

  * libSM

  * librsvg-2.0 >= 3.22.0

  * libwnck >= 3.4.6

  * libX11 / wayland

  * libXrandr

  * pango >= 1.15.4

  * yelp-tools


## Building

build-mate-panel.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-panel"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
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
