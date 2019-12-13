# marco (window-manager)

## Package requirements

  * [mate-common](./mate-common)

  * [mate-desktop](./mate-desktop)

  * gettext >= 0.19.8

  * gio-2.0 >= 2.25.10

  * glib-2.0 >= 2.58.0

  * gtk+-3.0 >= 3.22.0

  * libcanberra-gtk3

  * libgtop-2.0

  * libSM

  * libsoup

  * libXcomposite >= 0.3

  * libXcursor

  * libXdamage

  * libXinerama

  * libXpresent

  * libXrender

  * pango >= 1.1.2

  * startup-notification >= 0.7

  * yelp-tools

## Building

```bash
$ cat build-marco.sh
#!/bin/sh
# Define version
release="1.22"
version="1.22.0"
package="marco"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static
# Compile
make
# Install
sudo make install
```

