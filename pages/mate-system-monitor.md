# mate-system-monitor

## Package requirements

  * [mate-common](./mate-common)

  * gettext >= 0.19.8

  * giomm-2.4 >= 2.26.0

  * glib-2.0 >= 2.56.0

  * glibmm-2.4 >= 2.22

  * gtk+-3.0 >= 3.22.0

  * gtkmm-3.0 >= 3.8.1

  * libgtop-2.0 >= 2.37.2

  * librsvg-2.0 >= 2.35

  * libwnck-3.0 >= 3.0.0

  * libxml-2.0 >= 2.0

  * systemd

  * yelp-tools

## Building

build-mate-system-monitor.sh

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-system-monitor"
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
