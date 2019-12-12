# libmatemixer

## Package requirements

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50

  * pulseaudio >= 5.0.0

  * alsa >= 1.0.5

## Building

`build-libmatemixer.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.22"
    version="1.22.0"
    package="libmatemixer"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc
    # Compile
    make
    # Install
    sudo make install
```

