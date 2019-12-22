# mate-indicator-applet

## Package requirements

  * [mate-common](mate-common.md)

  * [mate-panel](mate-panel.md)

  * ayatana-indicator3-0.4 >= 0.6.0 (optional)

  * gtk+-3.0 >= 3.22.0

  * indicator3-0.4 >= 0.3.90 (optional)

  * X11

## Building

`build-mate-indicator-applet.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.23"
    version="1.23.0"
    package="mate-indicator-applet"
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

