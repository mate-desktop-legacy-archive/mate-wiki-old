# mate-bluetooth

## Package requirements

  * [mate-file-manager-sendto](./mate-file-manager-sendto)

## Building

build-mate-bluetooth.sh

```bash
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-bluetooth"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static \
        --libexecdir=/usr/lib/mate-bluetooth
# Compile
make
# Install
sudo make install
```
