# Deprecated code

## Fixing deprecated code

If you want to fix a deprecation, fill out an issue on
[github](https://github.com/perberos/Mate-Desktop-Environment/issues?sort=updated&direction=desc&state=open) explaining why.

## Lists

  * **GTK+** : <https://developer.gnome.org/gtk/stable/api-index-deprecated.html>

  * **GDK** : <https://developer.gnome.org/gdk/stable/api-index-deprecated.html>

  * **gdk-pixbuf** : <https://developer.gnome.org/gdk-pixbuf/stable/api-index-deprecated.html>

  * **GLIB** : <https://developer.gnome.org/glib/stable/api-index-deprecated.html>

## Status

[Current status](./status-1.6)

#### DEPRECATED; use above status page

Module |  Status  
---|---  
libmate |  Done (1/11/12)  
libmatecanvas |  Deprecated  
libmatecomponent |  Deprecated  
libmatecomponentui |  Deprecated  
libmatekbd |  Not Started  
libmatekeyring |  Done (1/11/12)  
libmatenotify |  Done (1/11/12)  
libmateui |  Deprecated  
libmateweather |  Not Started  
mate-applets |  Not Started  
mate-calc |  Not Started  
mate-conf |  Done (1/11/12)  
mate-control-center |  Not Started  
mate-corba |  Done (1/11/12)  
mate-desktop |  Not Started  
mate-dialogs |  Deprecated  
mate-display-manager |  Not Started  
mate-document-viewer |  Not Started  
engrampa |  Not Started  
caja |  Not Started  
eom |  Not Started  
mate-keyring |  Done (1/11/12)  
mate-menus |  Done (1/11/12)  
mate-notification-daemon |  Not Started  
mate-panel |  Not Started  
mate-polkit |  Not Started  
mate-power-manager |  Not Started  
mate-screensaver |  Not Started  
mate-sensors-applet |  Not Started  
mate-session-manager |  Done (2012/11/14)  
mate-settings-daemon |  Not Started  
mate-system-monitor |  Not Started  
mate-system-tools |  Deprecated  
mate-terminal |  Not Started  
pluma |  Not Started  
mate-vfs |  Deprecated  
mate-window-manager |  Done (2012/11/20) SB  
  
## How to guide

When you find obsolete code, functions, variable names, constants, etc., you
should look at the documentation to find the version in which the code became
deprecated.

**Why?**

We want to support backwards compatibility.

**Getting started**

Say we have this obsolete constant, _GTK_CHECK_CAST_ , and we need to change
it to _G_TYPE_CHECK_INSTANT_CAST_. Since the
[documentation](https://developer.gnome.org/gtk/2.24/gtk-Types.html#GTK-CHECK-CAST:CAPS)
does not state the version in which the code became deprecated, we
can simply change _GTK_CHECK_CAST_ to _G_TYPE_CHECK_INSTANT_CAST_.

On other hand, say we have this obsolete function, _g_format_size_for_display_
, and we want to change it to _g_format_size_. Since the
[documentation](https://developer.gnome.org/glib/2.30/glib-Miscellaneous-Utility-Functions.html#g-format-size-for-display)
states that the code has been
marked deprecated since version 2.30, we must be careful.

To support backwards compatibility, we cannot use the solution to the first
example. In this case we must do something like the following:

    
    
     #if GLIB_CHECK_VERSION (2, 30, 0) // greater than or equal to version 2.30
        return g_format_size(size);
    #else  // less than version 2.30
        return g_format_size_for_display(size);
    #endif

Now we can support both new and old versions of glib.

**This is ugly!**

Yes, the solution is quite ugly and not very elegant, but it helps keep track
of changes in libraries and allows us to cater to a larger audience.

**How to get a list of obsolete code**

The following should be included at compile time, or using autogen.sh:

    
    
    -DG_DISABLE_DEPRECATED
    -DG_DISABLE_SINGLE_INCLUDES
    -DGDK_DISABLE_DEPRECATED
    -DGTK_DISABLE_DEPRECATED
    -DGDK_DISABLE_SINGLE_INCLUDES
    -DGTK_DISABLE_SINGLE_INCLUDES

source: <https://developer.pidgin.im/wiki/GTK3>

Also see [GNOME: Remove deprecated GTK+ symbols](https://live.gnome.org/GnomeGoals/RemoveDeprecatedSymbols/GTK%2B)

Alternatively, if you would like to get a list of deprecated symbols without
having to compile, you can use the following command:

    
    
    egrep -wnr --include=*.[ch] -f ~/file-of-deprecated-symbols.txt path/to/src

Which means: Do an extended regexp search (egrep), search recursively (-r) in
path/to/src (or the current directory if path ommitted), narrow the search
only to files ending in  '.c' or '.h' (–include=*.[ch]), using each line in
the file specified as argument to '-f' as a search pattern, match whole-words
only (-w), and prefix output matches with line number (-n).

The .txt files with lists of deprecated symbols can be found
[here.](https://github.com/szesch/mate-dev-scripts/tree/master/deprecated-symbols)
