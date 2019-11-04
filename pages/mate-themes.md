# mate-themes

## Package requirements

  * murrine engine (for aldabra theme)

  * [mate-icon-theme](./mate-icon-theme)

  * gtk-engines

## Building

build-mate-themes.sh

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-themes"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc \
            --localstatedir=/var
    # Compile
    make
    # Install
    sudo make install
```
