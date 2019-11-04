# mate-conf

## Package requirements

  * [mate-common](./mate-common)

  * [mate-corba](./mate-corba)

  * glib-2.0 > 2.14.0

  * gio-2.0 >= 2.25.9

  * gthread-2.0

  * gmodule-2.0 >= 2.7.0

  * gobject-2.0 >= 2.7.0

  * gobject-introspection-1.0 >= 0.6.2

## Building

build-mate-conf.sh:


```bash
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-conf"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --libexecdir=/usr/lib/MateConf \
        --localstatedir=/var --disable-static \
        --enable-defaults-service --enable-gsettings-backend=no \
        --enable-introspection
# Compile
make
# Install
sudo make install
```

