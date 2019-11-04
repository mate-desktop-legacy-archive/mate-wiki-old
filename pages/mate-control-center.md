# mate-control-center

## Package requirements

  * [mate-doc-utils](./mate-doc-utils)

  * [mate-conf](./mate-conf)

  * [mate-settings-daemon](./mate-settings-daemon)

  * [mate-desktop](./mate-desktop)

  * [mate-menus](./mate-menus)

## Building

**build-mate-control-center.sh**

```bash
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-control-center"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static \
        --disable-scrollkeeper
# Compile
make
# Install
sudo make install
```
