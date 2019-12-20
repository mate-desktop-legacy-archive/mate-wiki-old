# python-caja

## Package requirements

  * [caja](caja.md)

  * [mate-common](mate-common.md)

  * gmodule-no-export-2.0

  * intltool >= 0.35.0

  * pygobject-3.0 >= 3.0.0

  * python3

## Building


```bash
$ cat build-python-caja.sh
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="python-caja"
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
