# mate-screensaver

## Package requirements

  * [libmatekbd](libmatekbd.md)

  * [mate-common](mate-common.md)

  * [mate-desktop](mate-desktop.md)

  * [mate-menus](mate-menus.md)

  * dbus-glib-1 >= 0.30

  * gettext >= 0.19.8

  * gio-2.0 >= 2.50.0

  * GL

  * glib-2.0 >= 2.50.0

  * gobject-2.0

  * gthread-2.0

  * gtk+-3.0 >= 3.22.0

  * libnotify >= 0.7.0

  * pam

  * systemd / elogind

  * X11 >= 1.0

  * Xext

  * Xinerama

  * Xss

  * Xxf86vm

## Building

build-mate-settings-daemon.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-screensaver"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
            --libexecdir=/usr/bin --disable-static
    # Compile
    make
    # Install
    sudo make install
```
