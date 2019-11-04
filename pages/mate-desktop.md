# mate-desktop

## Package requirements

  * intltool >= 0.40.0

  * startup-notification

  * XLIB

## Building

```bash
$ cat build-mate-desktop.sh
#!/bin/sh
# Define version
release="1.1"
version="1.1.0"
package="mate-desktop"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
# Extract
tar xvjf $package-$version.tar.bz2
# Go to inside folder
cd $package-$version
# Configure
./autogen.sh --prefix=/usr --sysconfdir=/etc \
        --localstatedir=/var --disable-static \
        --disable-scrollkeeper
# Compile
make
# Install
sudo make install
```

