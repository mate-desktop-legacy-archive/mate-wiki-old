# Building

Like in most linux projects, you can build, compile and install with
`autogen.sh && make && make install`. By the way, you may need to setup some
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

## Building order / Build requirements

Building order is quite tedious. _Check requirements!_

Updated Build requirements for 1.23

### Base

  * [mate-common](building-mate-common.md)

  * [mate-desktop](building-mate-desktop.md)

  * [libmatekbd](building-libmatekbd.md)

  * [libmatemixer](building-libmatemixer.md)

  * [libmateweather](building-libmateweather.md)

  * [mate-menus](building-mate-menus.md)

  * [caja](building-caja.md)

  * [marco](building-marco.md)

  * [mate-settings-daemon](building-mate-settings-daemon.md)

  * [mate-session-manager](building-mate-session-manager.md)

  * [mate-panel](building-mate-panel.md)

  * [mate-control-center](building-mate-control-center.md)

### Extras

  * [mate-polkit](building-mate-polkit.md)

  * [mate-notification-daemon](building-mate-notification-daemon.md)

  * [mate-backgrounds](building-mate-backgrounds.md)

  * [mate-themes](building-mate-themes.md)

  * [mate-icon-theme](building-mate-icon-theme.md)

  * [pluma](building-pluma.md) (text-editor)

  * [mate-terminal](building-mate-terminal.md)

  * [mate-screensaver](building-mate-screensaver.md)

  * [mate-calc](building-mate-calc.md)

  * [mate-utils](building-mate-utils.md)

  * [mate-system-monitor](building-mate-system-monitor.md)

  * [eom](building-eom.md) (image-viewer)

  * [engrampa](building-engrampa.md) (file-archiver)

  * [atril](building-atril.md) (document-viewer)

  * [mate-user-share](building-mate-user-share.md)

  * [mate-media](building-mate-media.md)

  * [mate-power-manager](building-mate-power-manager.md)

  * [python-caja](building-python-caja.md)

  * [mozo](building-mozo.md) (menu-editor)

  * [mate-applets](building-mate-applets.md) (extra panel applets)

  * [mate-sensors-applet](building-mate-sensors-applet.md)

  * [mate-indicator-applet](building-mate-indicator-applet.md)

  * [caja-dropbox](building-caja-dropbox.md)

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

Get [Mate sources here](download.md).


If you had problems while compiling, try to run these commands on source path:

    
    
  $ automake

Regenerate Makefile.in

    
    
  $ autoconf

Regenerate configure

    
    
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

    
```    
   configure: error: Package requirements (
       glib-2.0 >= 2.58.1
       mate-desktop-2.0 >= 1.17.3
       gthread-2.0
       gio-unix-2.0
       gio-2.0 >= 2.50.0
       pango >= 1.1.2
       gtk+-3.0 >= 3.22.0
       libnotify
       libxml-2.0 >= 2.4.7
       gail-3.0 >= 3.0.0
   ) were not met:

Package 'mate-desktop-2.0', required by 'virtual:world', not found
```

try setting PKG_CONFIG_PATH. Adjust to the prefix you are installing to.

    
    
  $ export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig/:/usr/local/share/pkgconfig/

Problems with missing python libraries:

    
    
    Traceback (most recent call last):
      File "/usr/local/bin/rst2html", line 191, in <module>
        main(sys.argv[1:])
      File "/usr/local/bin/rst2html", line 88, in main
        from rst2html import Main
    ImportError: No module named rst2html

try setting PYTHONPATH. Adjust to the prefix you are installing to.

    
    
  $ export PYTHONPATH=${PYTHONPATH}:/usr/local/lib64/python3.7/site-packages/

## Uninstall

If you have not erased the sources from where you installed the files, you can
uninstall with “make uninstall” as root user where you did the “make install”.

    
    
  $ sudo make uninstall

## Build Script

You may find this [Build Script](building-buildscript.md) useful (deprecated, some parts needs updating).
