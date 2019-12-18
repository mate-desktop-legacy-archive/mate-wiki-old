# Building

Like in most linux projects, you can build, compile and install with
`./autogen.sh && make && make install`. By the way, you may need to setup some
things. Follow each package guide to get a clean install.

_Remember, compiling can be stressful._

Example: <https://i.imgur.com/mf8dG.jpg>

_Do not compile as root!_

## Building requirements

### Ubuntu 11.10, Debian Wheezy, Linux Mint

    
```    
   $ sudo apt-get install libxml2-dev libxslt1-dev libglib2.0-dev libidl-dev \
        libdbus-1-dev libdbus-glib-1-dev libpolkit-backend-1-dev flex libpopt-dev \
        bison libbz2-dev libgcrypt11-dev libcanberra-dev libgail-dev libgtk2.0-dev \
        libart-2.0-dev libglade2-dev libtasn1-3-bin libxklavier-dev libsoup2.4-dev \
        icon-naming-utils libunique-dev libcanberra-gtk-dev libwnck-dev \
        librsvg2-dev libpolkit-agent-1-dev gobject-introspection \
        libgirepository1.0-dev libupower-glib-dev intltool xsltproc \
        libtasn1-3-dev libtool gtk-doc-tools libgamin-dev \
        librarian-dev libdconf-dev libsecret-1-dev libgnome-keyring-dev \
        yelp-tools libnotify-dev
```

### Fedora

    
```    
   $ sudo yum install libxml2-devel libxslt-devel glib2-devel libIDL-devel \
        dbus-devel dbus-glib-devel polkit-devel flex popt-devel \
        bison bzip2-devel libgcrypt-devel libcanberra-devel gtk3-devel \
        libart_lgpl-devel libglade2-devel libtasn1-tools libxklavier-devel libsoup-devel \
        icon-naming-utils unique-devel libcanberra-gtk3 libcanberra-devel libwnck3-devel \
        librsvg2-devel libSM-devel libXdamage-devel \
        gobject-introspection-devel upower-devel intltool  \
        libtasn1-devel libtool gamin-devel rarian-devel dconf-devel \
        libsecret-devel libgnome-keyring-devel
```

To build the extras you will also need:

### For Ubuntu 14.04.x

```
    libpoppler-glib-dev libgtop2-dev libvte-dev libenchant-dev libgtkmm-2.4-dev libisocodes-dev libgtksourceview2.0-dev gtk2-engines libjpeg-dev
```

### RPM based systems

```
    poppler-glib-devel libgtop2-devel gtkmm30-devel vte291-devel enchant-devel iso-codes-devel gtksourceview3-devel
```

## Building order

Building order is quite tedious. _Check requirements!_

#### Updated Build instructions for 1.22

### Base

  * [mate-common](pages/mate-common.md)

  * [mate-desktop](./mate-desktop)

  * [libmatekbd](./libmatekbd)

  * [libmatemixer](./libmatemixer)

  * [libmateweather](./libmateweather)

  * [mate-menus](./mate-menus)

  * [caja](./caja)

  * [marco](./marco)

  * [mate-settings-daemon](./mate-settings-daemon)

  * [mate-session-manager](./mate-session-manager)

  * [mate-panel](./mate-panel)

  * [mate-control-center](./mate-control-center)

### Extras

  * [mate-polkit](./mate-polkit)

  * [mate-notification-daemon](./mate-notification-daemon)

  * [mate-backgrounds](./mate-backgrounds)

  * [mate-themes](./mate-themes)

  * [mate-icon-theme](./mate-icon-theme)

  * [pluma](./pluma) (text-editor)

  * [mate-terminal](./mate-terminal)

  * [mate-screensaver](./mate-screensaver)

  * [mate-calc](./mate-calc)

  * [mate-utils](./mate-utils)

  * [mate-system-monitor](./mate-system-monitor)

  * [eom](./eom) (image-viewer)

  * [engrampa](./engrampa) (file-archiver)

  * [atril](./atril) (document-viewer)

  * [mate-user-share](./mate-user-share)

  * [mate-media](./mate-media)

  * [mate-power-manager](./mate-power-manager)

  * [python-caja](./python-caja) (ex python-nautilus)

  * [mozo](./mozo) (menu-editor)

  * [mate-applets](./mate-applets) (extra panel applets)

  * [mate-sensors-applet](./mate-sensors-applet)

  * [mate-indicator-applet](./mate-indicator-applet)

  * [caja-dropbox](./caja-dropbox)

## HAX!

I have made this shell script to build and install in one command. _IT 'S NOT
RECOMMENDED._

```bash
#!/bin/sh

build_func() {
    ./configure \
        --prefix=/usr \
        --sysconfdir=/etc \
        --localstatedir=/var \
        --disable-static || return 1
    make || return 1
    su -c"make install"
}

build_func
```

Edit ./configure if you want. You can prevent GNOME conflicts by adding
”./configure –prefix=/usr/local” Save as ”/usr/bin/build” Don't forget the
“chmod +x /usr/bin/build” as root.

Now, you can run “build” to install quickly.

Get [Mate sources here](./download).

## Moar HAX!

If you had problems while compiling, try to run these commands on source path:

    
    
  $ automake

Regenerate Makefile.in

    
    
  $ autoconf

Regenerate ./configure

    
    
  $ autoreconf -i --force

Add some missing files

    
    
  $ aclocal
    
    
  $ intltoolize --automake --copy --force
    
    
  $ automake --add-missing

## Troubleshooting

Problems with m4 files, e.g:

    
    
    ***Error***: some autoconf macros required to build libmatecomponent

try fixing the ACLOCAL_FLAGS. Adjust to the prefix you are installing to.

    
    
  $ export ACLOCAL_FLAGS="-I /usr/local/share/aclocal/"

Problems finding the libraries of bits you have already build and installed:

    
    
    configure: error: Package requirements
    (glib-2.0 > 2.14.0 gio-2.0 >= 2.25.9 gthread-2.0
    gmodule-2.0 >= 2.7.0 gobject-2.0 >= 2.7.0 MateCORBA-2.0)
    were not met:
    No package 'glib-2.0' found

try setting PKG_CONFIG_PATH. Adjust to the prefix you are installing to.

    
    
  $ export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig/:/usr/local/share/pkgconfig/

Problems with missing python libraries:

    
    
    Traceback (most recent call last):
      File "/usr/local/bin/xml2po", line 191, in <module>
        main(sys.argv[1:])
      File "/usr/local/bin/xml2po", line 88, in main
        from xml2po import Main
    ImportError: No module named xml2po

try setting PYTHONPATH. Adjust to the prefix you are installing to.

    
    
  $ export PYTHONPATH=${PYTHONPATH}:/usr/local/lib/python2.7/site-packages/

## Uninstall

If you have not erased the sources from where you installed the files, you can
uninstall with “make uninstall” as root user where you did the “make install”.

    
    
  $ sudo make uninstall

## Build Script

You may find this [Build Script](./buildscript) useful.
