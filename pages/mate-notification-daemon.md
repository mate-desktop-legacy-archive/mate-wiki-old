# mate-notification-daemon

## Package requirements

  * intltool >= 0.40.0

  * gtk+-3.0 >= 3.22.0

  * glib-2.0 >= 2.50.0

  * dbus-1 >= 0.78

  * dbus-glib-1 >= 0.78

  * libcanberra-gtk3 >= 0.4

  * libwnck-3.0

  * x11

## Building

build-mate-notification-daemon.sh

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-notification-daemon"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc \
            --localstatedir=/var --disable-static \
            --libexecdir=/usr/lib/mate-notification-daemon
    # Compile
    make
    # Install
    sudo make install
```
