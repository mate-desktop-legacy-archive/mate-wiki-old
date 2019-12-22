# mate-sensors-applet

## Package requirements

  * [mate-common](mate-common.md)

  * [mate-panel](mate-panel.md)

  * cairo >= 1.0.4

  * gio-2.0

  * glib-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * intltool >= 0.50.1

  * libnotify >= 0.7.0

  * libsensors

  * libXNVCtrl (optional nvidia support)

  * X11

  * yelp-tools

## Building

`build-mate-sensors-applet.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-sensors-applet"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc
    # Compile
    make
    # Install
    sudo make install
```

