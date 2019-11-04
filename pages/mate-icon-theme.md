# mate-icon-theme

## Package requirements

  * intltool >= 0.40.0

  * icon-naming-utils >= 0.8.7

## Building

```bash
$ cat build-mate-icon-theme.sh
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-icon-theme"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr
# Compile
make
# Install
sudo make install
```
