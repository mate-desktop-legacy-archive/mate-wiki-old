# mate-file-manager

## Package requirements

  * [mate-desktop](./mate-desktop)

  * intltool >= 0.35.0

  * glib-2.0 >= 2.25.9

  * gthread-2.0

  * gio-unix-2.0

  * gio-2.0

  * pango >= 1.1.2

  * gtk+-2.0 >= 2.22.0

  * libxml-2.0 >= 2.4.7

  * gail >= 0.16

  * unique-1.0

## Building

```bash
$ cat build-mate-file-manager.sh
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-file-manager"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static \
        --libexecdir=/usr/lib/mate-file-manager
# Compile
make
# Install
sudo make install
```

