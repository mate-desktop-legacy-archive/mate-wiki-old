# mate-session-manager

## Package requirements

  * intltool >= 0.40.0

  * glib-2.0 >= 2.16.0

  * gio-2.0 >= 2.16.0

  * gtk+-2.0 >= 2.14.0

  * dbus-glib-1 >= 0.76

  * upower-glib >= 0.9.0

## Building

build-mate-session-manager.sh

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-session-manager"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
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
