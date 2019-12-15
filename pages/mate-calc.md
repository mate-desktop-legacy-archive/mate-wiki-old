# mate-calc

## Package requirements

  * [mate-common](./mate-common)

  * gettext >= 0.19.8

  * glib-2.0 >= 2.50.0

  * gio-2.0 >= 2.36.0

  * gmodule-export-2.0

  * gtk+-3.0 >= 3.22.0

  * libxml-2.0

  * yelp-tools

## Building

```bash
$ cat build-mate-calc.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-calc"
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

