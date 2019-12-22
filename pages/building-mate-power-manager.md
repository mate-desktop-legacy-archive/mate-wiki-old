# mate-power-manager

## Package requirements

  * [mate-common](mate-common.md)

  * [mate-panel](mate-panel.md)

  * cairo >= 1.0.0

  * dbus-1 >= 1.0

  * dbus-glib-1 >= 0.70

  * gdk-3.0 >= 3.22.0

  * gdk-x11-3.0 >= 3.22.0

  * gettext >= 0.19.8

  * gio-2.0 >= 2.50.0

  * gio-unix-2.0

  * glib-2.0 >= 2.50.0

  * gnome-keyring-1 >= 3.0.0

  * gthread-2.0

  * gtk+-3.0 >= 3.22.0

  * libcanberra-gtk3 >= 0.15

  * libnotify >= 0.7.0

  * upower-glib >= 0.99.8

  * Xext

  * Xproto >= 7.0.15

  * Xrandr >= 1.3.0

  * X11

  * yelp-tools

## Building

build-mate-power-manager.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-power-manager"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc \
            --localstatedir=/var --disable-static
    # Compile
    make
    # Install
    sudo make install
```
