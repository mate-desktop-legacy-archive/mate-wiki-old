# mate-corba

## Package requirements

  * [mate-common](./mate-common)

  * glib-2.0 >= 2.8.0

  * gobject-2.0 >= 2.8.0

  * gthread-2.0 >= 2.8.0

  * gmodule-2.0 >= 2.8.0

## Building

```bash
$ cat build-mate-corba.sh
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-corba"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --disable-static
# Compile
make
# Install
sudo make install
```
