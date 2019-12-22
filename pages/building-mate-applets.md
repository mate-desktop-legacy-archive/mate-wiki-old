# mate-applets

## Package requirements

  * [libmateweather](libmateweather.md)

  * [mate-panel](mate-panel.md)

  * dbus-1 >= 1.1.2

  * dbus-glib-1 >= 0.74

  * glib-2.0 >= 2.50.0

  * gio-2.0 >= 2.50.0

  * gobject-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * gtksourceview-3.0

  * gucharmap_2_90 >= 3.0.0

  * intltool >= 0.50.1

  * cpupower or cpufreq

  * libgtop-2.0 >= 2.12.0

  * libiw

  * libnotify >= 0.7.0

  * libxml-2.0 >= 2.5.0

  * polkit-gobject-1 >= 0.97

  * upower-glib >= 0.9.4

  * libwnck-3 >= 3.0.0

  * X11

  * yelp-tools

## Building

`build-mate-applets.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-applets"
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

