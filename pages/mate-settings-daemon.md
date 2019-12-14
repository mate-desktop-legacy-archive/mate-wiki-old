# mate-settings-daemon

## Package requirements

  * [mate-desktop](./mate-desktop)

  * [libmatemixer](./libmatemixer)

  * libnotify >= 0.7.0

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * gmodule-2.0

  * gthread-2.0

  * dbus-glib-1 >= 0.74

## Building

build-mate-settings-daemon.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-settings-daemon"
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
