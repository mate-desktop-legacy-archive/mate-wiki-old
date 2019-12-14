# mate-session-manager

## Package requirements

  * [mate-common](./mate-common)

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50.0

  * gio-2.0 >= 2.25.0

  * gtk+-3.0 >= 3.22.0

  * dbus-glib-1 >= 0.76

  * libX11

  * libSM

  * libICE

  * libXcomposite

  * libXext

  * libXrender

  * systemd / elogind

  * libXtrans

## Building

build-mate-session-manager.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-session-manager"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
            --libexecdir=/usr/lib --enable-splash
    # Compile
    make
    # Install
    sudo make install
```
