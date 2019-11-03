# mate-menus

## Package requirements

  * intltool >= 0.40.0

## Building


```bash
$ cat build-mate-menus.sh
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-menus"
# Get
wget -c http://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
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
