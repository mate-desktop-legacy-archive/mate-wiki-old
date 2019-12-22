# mate-menus

## Package requirements

  * [mate-common](mate-common.md)

  * gio-unix-2.0 >= 2.50.0

  * gobject-introspection >= 0.6.7

  * intltool >= 0.40.0

## Building


```bash
$ cat build-mate-menus.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-menus"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
# Extract
tar xvjf $package-$version.tar.xz
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var  --disable-static
# Compile
make
# Install
sudo make install
```
