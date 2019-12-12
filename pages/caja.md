# mate-file-manager

## Package requirements

  * [mate-desktop](./mate-desktop)

  * intltool >= 0.50.1

  * glib-2.0 >= 2.50.0

  * gthread-2.0

  * gio-unix-2.0

  * gio-2.0

  * pango >= 1.1.2

  * gtk+-3.0 >= 3.22.0

  * libxml-2.0 >= 2.4.7

  * gail >= 3.0.0

## Building

```bash
$ cat build-caja.sh
#!/bin/sh
# Define version
release="1.22"
version="1.22.0"
package="caja"
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

