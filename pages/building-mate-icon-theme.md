# mate-icon-theme

## Package requirements

  * gettext >= 0.19.8

  * icon-naming-utils >= 0.8.7

## Building

```bash
$ cat build-mate-icon-theme.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-icon-theme"
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
