# mate-themes

## Package requirements

  * gettext >= 0.19.8

  * gtk-engines

## Building

build-mate-themes.sh

```bash
    #!/bin/sh
    # Define version
    version="3.22.9"
    package="mate-themes"
    # Get
    wget -c https://pub.mate-desktop.org/releases/themes/$version/$package-$version.tar.xz
    # Extract
    tar xvjf $package-$version.tar.xz
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
