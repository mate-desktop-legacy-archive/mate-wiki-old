# mate-backgrounds

## Source

<https://github.com/mate-desktop/mate-backgrounds>

## Package Dependencies

  * gettext >= 0.19.8

## Building

`build-mate-backgrounds.sh`

```bash
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-common"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
# Extract
tar xvjf $package-$version.tar.xz
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr
# Compile
make
# Install
sudo make install
```
