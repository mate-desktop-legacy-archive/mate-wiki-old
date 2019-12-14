# mate-control-center

## Package requirements

  * [mate-settings-daemon](./mate-settings-daemon)

  * [mate-desktop](./mate-desktop)

  * [mate-menus](./mate-menus)

  * [marco](./marco)

  * [mate-settings-daemon](./mate-settings-daemon)

  * [libmatekbd](./libmatekbd)

  * accountsservice

  * appindicator3 >= 3-0.1

  * dbus-1

  * dbus-glib-1

  * dconf >= 0.13.4

  * desktop-file-utils

  * gettext >= 0.19.8

  * freetype2

  * gio-2.0

  * gio-unix-2.0

  * glib-2.0 >= 2.50.0

  * gthread-2.0

  * gtk+-3.0 >= 3.22.0

  * libcanberra-gtk3 >= 0.4

  * librsvg2

  * libSM

  * libXcursor

  * libxml-2.0

  * Xss

  * pango

  * polkit-gobject-1

  * libxklavier >= 5.2

  * Xi >= 1.5

## Building

**build-mate-control-center.sh**

```bash
#!/bin/sh
# Define version
release="1.23"
version="1.23.0"
package="mate-control-center"
# Get
wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.xz
# Extract
tar xvjf $package-$version.tar.xz
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
