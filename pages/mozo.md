# mozo

## Package requirements

  * [mate-menus](mate-menus.md)

  * gettext >= 0.19.8

  * pygobject-3.0

  * python3 >= 3.5

## Building


```bash
$ cat build-mozo.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mozo"
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
