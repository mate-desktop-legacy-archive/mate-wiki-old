# mate-settings-daemon

## Package requirements

  * intltool >= 0.37.1

  * glib-2.0 >= 2.17.3

  * gtk+-2.0 >= 2.21.2

  * [mate-conf](./mate-conf)

  * gmodule-2.0

  * gthread-2.0

  * dbus-glib-1 >= 0.74

## Building

build-mate-settings-daemon.sh

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-settings-daemon"
    # Get
    wget -c http://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
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
