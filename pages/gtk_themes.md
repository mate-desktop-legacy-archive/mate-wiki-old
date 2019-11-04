# GTK themes

Some GTK Themes need to be “fixed” to work fine with MATE.

The Murrine, Ambiance, Radiance, and Shiki-* themes are known to have Ubuntu
specific issues which lead to 100% CPU usage. At this point in time, the issue
has been patched in gtk, but has not yet been packaged. The patched version of
gtk is 2.24.8. The current version of gtk as of 12/24/2011 is 2.24.6-0ubuntu5.

Just take a look at [this page](./migrating) for get a replace text
full list.

## Example

If you see in the gtkrc theme file:

    
    
    widget_class "*GnomePanelApplet*GtkWidget"    style:highest "panel-buttons"

Just replace Gnome for Mate.

    
    
    widget_class "*MatePanelApplet*GtkWidget"    style:highest "panel-buttons"

Or better, make it retro-compatible.

    
    
    widget_class "*GnomePanelApplet*GtkWidget"    style:highest "panel-buttons" 
    widget_class "*MatePanelApplet*GtkWidget"    style:highest "panel-buttons"

## Gtk2 and Gtk3 at same time.

I've found a Gtk2 and Gtk3 called [Aldabra](https://gnome-look.org/content/show.php/?content=142247),
and there is an [AUR package](https://aur.archlinux.org/packages.php?ID=49511) too. It look like Adwaita
theme.

It's included on [mate-themes](./mate-themes) package.

