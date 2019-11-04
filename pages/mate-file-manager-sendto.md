# mate-file-manager-sendto

## Package requirements

  * [mate-file-manager](./mate-file-manager)

## Building

```bash
$ cat build-mate-file-manager-sendto.sh
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-file-manager-sendto"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static
# Compile
make
# Install
sudo make install
```
