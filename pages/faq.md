# FAQ

This page holds a list of common issues you may run into with MATE.

## How can I change the menu bar icon?

### 1\. Find your favorite icon

Get the icon you would want to be your custom menu bar icon. You may want to
find a scalabe version of that icon for convenience.

### 2\. Copy to ~/.icons

If the `.icons` directory doesn't yet exist inside your home directory, create
it. (Beware that `.icons` is a hidden directory.) Then copy your custom icon
into it.

### 3\. Use dconf editor to tell mate panel to use the custom icon

Start dconf editor. Then go to `org > mate > panel > menubar`. In the right
window, you see the configuration options for `menubar`. Select “icon-name”.
Click into the “Value” field. Then type in the name of your icon file
_without_ the file extension. Press [ENTER]. Done.

## I just upgrade from MATE 1.4 to 1.6

### Where is MateConf gone to?

In MATE 1.6 MateConf has been replaced by GSettings/dconf. You should now use
`dconf-editor` and/or the command line tool `gsettings`. You can find more
about it in the manual for [GSettings](./docs-gsettings)

### All my desktop settings are gone

This is because of the move to gsettings. There is a beta migration script
[here](https://github.com/mate-desktop/mate-desktop/blob/master/mate-conf/mate-conf-import),
issues please report in the
[forums](https://forums.mate-desktop.org/viewtopic.php?f=16&t=1650).

## My document icons previews are not showing

  * Make sure you have enabled preview on the filemanager setting

  * Sometimes the thumbnailer hangs. Kill the currently running thumbnailer.

## My power manager setting for the screen do not work

This issues has been observed in multiple distro 's so far. It has been
reported on Debian (wheezy) and Arch Linux. This is currently a known issue
(dd 2013-04-21).

## Some icons are very large

This is a bug in gdk-pixbuf, see
<https://bugzilla.gnome.org/show_bug.cgi?id=686514>.
