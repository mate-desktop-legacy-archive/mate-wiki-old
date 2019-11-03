# mate-doc-utils

## Package requirements

  * [mate-common](./mate-common)

  * libxml-2.0 >= 2.6.12

  * libxslt

  * rarian

### Ubuntu

  * libxml2-dev

  * libxslt1-dev

  * automake

  * intltool

  * librarian-dev

## Building

```bash
$ cat build-mate-doc-utils.sh
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-doc-utils"
# Get
wget -c http://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --mandir=/usr/share/man --localstatedir=/var --disable-scrollkeeper
# Compile
make
# Install
sudo make install
```
