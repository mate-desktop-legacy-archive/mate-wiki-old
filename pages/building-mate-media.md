# mate-media

## Package requirements

  * [libmatemixer](libmatemixer.md)

  * [mate-common](mate-common.md)

  * [mate-desktop](mate-desktop.md)

  * [mate-panel](mate-panel.md)

  * gettext >= 0.19.8

  * gio-2.0 >= 2.50.0

  * glib-2.0 >= 2.50.0

  * gobject-2.0 >= 2.50.0

  * gtk+-3.0 >= 3.22.0

  * libcanberra-gtk3 >= 0.13

  * libxml-2.0

## Building

```bash
$ cat build-mate-media.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-media"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
# Extract
tar xvjf $package-$version.tar.xz
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

