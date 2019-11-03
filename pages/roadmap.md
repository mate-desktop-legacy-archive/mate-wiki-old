# Roadmap

Some notes for the next releases. This is not a brainstorm page. Please use
the forum or the IRC chat to ask for new features.

## Release 1.24

  * Migrate remaining projects from dbus-glib to GDBus

  * caja: add option to show thumbnails in listview ([#153](https://github.com/mate-desktop/caja/issues/153))

  * mate-applets: make command applet run commands asynchronously ([#163](https://github.com/mate-desktop/mate-applets/issues/163))

  * mate-panel: fix remaining vertical panel issues ([#157](https://github.com/mate-desktop/mate-panel/issues/157))

  * pluma: port Python plugins to Python 3

## Release 1.22

  * ~~Move all help/guide translations to Transifex~~

  * Improve Metacity support

  * ~~marco: add support for metacity-theme-3.xml format ([#105](https://github.com/mate-desktop/marco/issues/105))~~

  * ~~mate-menus: port to GObject introspection, drop static Python bindings ([#59](https://github.com/mate-desktop/mate-menus/pull/59))~~

  * ~~mozo: port to Python 3 and GI package of mate-menus ([#39](https://github.com/mate-desktop/mozo/pull/39))~~

  * ~~python-caja: add Python 3 compatibility ([#30](https://github.com/mate-desktop/python-caja/issues/30))~~

## Future releases

  * atril: use distro-packaged synctex library

  * caja: add option to drag a tab to create a new window ([#454](https://github.com/mate-desktop/caja/issues/454))

  * caja: add option to turn off generic icons in listview ([#26](https://github.com/mate-desktop/caja/issues/26))

  * engrampa: add libarchive support ([#52](https://github.com/mate-desktop/engrampa/issues/52))

  * mate-applets: add mount point or device blacklist for drivemount applet ([#24](https://github.com/mate-desktop/mate-applets/issues/24))

  * mate-applets: option to show several cores and processors in one cpufreq applet instance ([#50](https://github.com/mate-desktop/mate-applets/issues/50))

  * mate-applets: make cpufreq applet work with intel_pstate driver ([#173](https://github.com/mate-desktop/mate-applets/issues/173))

  * mate-control-center: cache thumbnails for desktop backgrounds in appearance properties

  * mate-menus: option to enable/disable preferences categories ([#35](https://github.com/mate-desktop/mate-menus/issues/35))

  * mate-session-manager: in properties dialog, show running apps that can/will be saved on exit ([#113](https://github.com/mate-desktop/mate-session-manager/issues/113))

  * pluma: add plugin to show (and maybe change) line endings type ([#50](https://github.com/mate-desktop/pluma/issues/50))

  * Update caja integration with tracker search engine [tracker dev documentation](https://wiki.gnome.org/Projects/Tracker/Documentation) \- [Nautilus git log](https://git.gnome.org/browse/nautilus/log/libnautilus-private/nautilus-search-engine-tracker.c)

  * Add support for [AccountsService](http://www.freedesktop.org/wiki/Software/AccountsService)

  * [Complete support for systemd-logind](./systemd-logind.md)

  * [Add support for Wayland](./wayland.md)

  * Consider dropping libmatekbd for libgnomekbd

  * Consider dropping libmateweather for libgweather

## Old releases

### Release 1.20

Released on February 7, 2018. Announcement [here](http://mate-desktop.org/blog/2018-02-07-mate-1-20-released/).

  * ~~Bump minimum required GTK+3 version to 3.22~~

  * ~~Bump minimum required GLib version to 2.50~~

  * ~~Add support for HiDPI~~

  * ~~Migrate to ~/.config/gtk-3.0/bookmarks for storing bookmarks~~

  * ~~atril: implement caret navigation ([#281](https://github.com/mate-desktop/atril/pull/281))~~

  * ~~marco: add DRI3/Present support ([#326](https://github.com/mate-desktop/marco/issues/326))~~

  * ~~marco: implement corner windows tiling ([#359](https://github.com/mate-desktop/marco/pull/359))~~

  * ~~marco: support multimonitor keybindings ([#371](https://github.com/mate-desktop/marco/pull/371))~~

  * ~~mate-desktop: switch mate-about to GtkAboutDialog and drop MateAboutDialog ([#282](https://github.com/mate-desktop/mate-desktop/pull/282))~~

  * ~~mate-desktop: support for Global Menu providers such as vala-panel-appmenu~~

  * ~~mate-panel: improve StatusNotifierItem (SNI) support~~

  * ~~mate-panel: improve support for in-process applets~~

  * ~~mate-polkit: drop unused polkitgtkmate library ([#39](https://github.com/mate-desktop/mate-polkit/pull/39))~~

  * ~~mate-sensors-applet: add ability to hide temperature units ([#22](https://github.com/mate-desktop/mate-sensors-applet/issues/22))~~

  * ~~mate-terminal: add Solarized themes from gnome-terminal ([#151](https://github.com/mate-desktop/mate-terminal/issues/151))~~

  * ~~mate-terminal: bump minimum required VTE version to 0.46 ([#233](https://github.com/mate-desktop/mate-terminal/pull/223))~~

### Release 1.18

Released on March 13, 2017. Announcement [here](http://mate-desktop.org/blog/2017-03-13-mate-1-18-released/).
[Old status page](./status-1.18.md).

  * ~~Migrate all remaining packages to GTK+3 and require version 3.14~~

  * ~~Complete migration from libunique to GtkApplication~~

  * ~~caja: make folder color work in list view ([#410](https://github.com/mate-desktop/caja/issues/410))~~

  * ~~eom: port plugin system and plugins to libpeas ([#71](https://github.com/mate-desktop/eom/issues/71))~~

  * ~~mate-control-center: add libinput support ([#133](https://github.com/mate-desktop/mate-control-center/issues/133))~~

  * ~~mate-settings-daemon: add libinput support ([#160](https://github.com/mate-desktop/mate-settings-daemon/issues/160))~~

  * ~~mate-system-monitor: add pkexec support ([#85](https://github.com/mate-desktop/mate-system-monitor/issues/85))~~

  * ~~pluma: port plugin system and plugins to libpeas ([#147](https://github.com/mate-desktop/pluma/issues/147))~~

### Release 1.16

Released on September 21, 2016. Announcement [here](http://mate-desktop.org/blog/2016-09-21-mate-1-16-released/).
[Old status page](./status-1.16.md).

  * ~~engrampa: move to GTK+3 ([#140](https://github.com/mate-desktop/engrampa/pull/140))~~

  * ~~mate-notification-daemon: move to GTK+3 ([#102](https://github.com/mate-desktop/mate-notification-daemon/pull/102))~~

  * ~~mate-polkit: move to GTK+3 ([#28](https://github.com/mate-desktop/mate-polkit/pull/28))~~

  * ~~mate-session-manager: move to GTK+3 ([#121](https://github.com/mate-desktop/mate-session-manager/pull/121))~~

  * ~~mate-terminal: move to GTK+3 ([#118](https://github.com/mate-desktop/mate-terminal/pull/118))~~

### Release 1.14

Released on April 8, 2016. Announcement [here](http://mate-desktop.org/blog/2016-04-08-mate-1-14-released/).
[Old status page](./status-1.14.md).

  * ~~caja: allow managing each python extension separately ([#521](https://github.com/mate-desktop/caja/pull/521), [python-caja #24](https://github.com/mate-desktop/python-caja/pull/24))~~

  * ~~mate-control-center: make all three window focus modes selectable ([marco #140](https://github.com/mate-desktop/marco/issues/140))~~

  * ~~mate-control-center: move mate-preferences-categories.menu to[mate-menus](https://github.com/mate-desktop/mate-menus) ([#207](https://github.com/mate-desktop/mate-control-center/issues/207))~~

  * ~~mate-panel: ability to change icon sizes for menubar and menu items ([#406](https://github.com/mate-desktop/mate-panel/pull/406))~~

  * ~~mate-settings-daemon: add the ability to disable volume/brightness osd ([#13](https://github.com/mate-desktop/mate-settings-daemon/issues/13))~~

  * ~~mate-system-monitor: move to GTK+3 ([#74](https://github.com/mate-desktop/mate-system-monitor/issues/74))~~

  * ~~mate-system-monitor: run gksu binary instead of loading libgksu2.so (which is GTK+2 only) ([#81](https://github.com/mate-desktop/mate-system-monitor/pull/81))~~

  * ~~mate-terminal: support VTE 2.91 API in GTK+3 build ([#66](https://github.com/mate-desktop/mate-terminal/issues/66))~~

  * ~~mate-themes: compatibility with GTK+ 3.20 for all themes ([#101](https://github.com/mate-desktop/mate-themes/issues/101))~~

  * ~~mozo: move to GTK+3~~

  * ~~Merge mate-netspeed into mate-applets ([mate-applets #167](https://github.com/mate-desktop/mate-applets/issues/167))~~

  * ~~Drop MateConf migration scripts~~

### Release 1.12

Released on November 5, 2015. Announcement [here](http://mate-desktop.org/blog/2015-11-05-mate-1-12-released/).
[Old status page](./status-1.12.md).

  * ~~atril: use distro-packaged MathJax library ([#158](https://github.com/mate-desktop/atril/issues/158))~~

  * ~~marco: pointer window placement ([#123](https://github.com/mate-desktop/marco/issues/123))~~

  * ~~mate-utils: add timestamp to screenshot filename ([#115](https://github.com/mate-desktop/mate-utils/issues/115))~~

  * ~~Switch to org.gnome.SessionManager name on DBus~~

  * ~~Move user guide to separate project~~

  * ~~Add option to toggle GTK+3 overlay scrolling~~

  * ~~Improve touchpad support~~

### Release 1.10

Released on June 11, 2015. Announcement [here](http://www.mate-desktop.org/blog/2015-06-11-mate-1-10-released/).
[Old status page](./status-1.10.md).

  * ~~atril: Support ePub format ([#13](https://github.com/mate-desktop/mate-document-viewer/issues/13)) (GSOC 2014)~~

  * ~~caja: Extension management system (GSOC 2014)~~

  * ~~mate-control-center: Add option to configure titlebar buttons layout~~

  * ~~Drop GStreamer for alsa (was[Add support for GStreamer-1.0](./gstreamer-1.0)) ([#9](https://github.com/mate-desktop/mate-media/issues/9)) (GSOC 2014)~~

  * ~~Replace[mate-calc](https://github.com/mate-desktop/mate-calc) with [galculator](http://galculator.sourceforge.net/)~~

  * ~~Replace[mate-dialogs](https://github.com/mate-desktop/mate-dialogs) with [zenity](https://git.gnome.org/browse/zenity)~~

  * ~~Drop[mate-system-tools](https://github.com/mate-desktop/mate-system-tools)~~

### Release 1.8

Released on March 4, 2014. Announcement [here](http://www.mate-desktop.org/blog/2014-03-04-mate-1-8-released/).
[Old status page](./status-1.8.md).

  * ~~caja: Add option to use IEC units instead of SI units~~

  * ~~caja: Add “Open parent location” option in context menu in search view~~

  * ~~engrampa: Show always the “extract to” action in caja extension~~

  * ~~eom: Add shuffle mode in slideshow~~

  * ~~eom: Migration to lcms2 ([#25](https://github.com/mate-desktop/mate-image-viewer/issues/25))~~

  * ~~marco: Add window snapping ([#21](https://github.com/mate-desktop/mate-window-manager/issues/21))~~

  * ~~mate-applets: Add undo functionality to sticky note applet ([#17](https://github.com/mate-desktop/mate-applets/issues/17))~~

  * ~~mate-applets: New command applet~~

  * ~~mate-control-center: Add support for Metacity as window manager~~

  * ~~mate-control-center: Add support for 'artist' tag in xml backgrounds files~~

  * ~~mate-desktop: Add user guide~~

  * ~~mate-desktop: Add mpaste tool~~

  * ~~mate-media: Middle click on applet toggles mute state~~

  * ~~mate-screensaver: Show date and time in lock dialog~~

  * ~~[Replace mate-doc-utils with yelp-tools](./matedocutils_to_yelp) ([#2](https://github.com/mate-desktop/mate-doc-utils/issues/2))~~

  * ~~Drop libmatekeyring/mate-keyring for libsecret/gnome-keyring~~

  * ~~Drop libmatewnck for libwnck~~

  * ~~Drop mucharmap for gucharmap[commit](http://git.mate-desktop.org/mate-applets/commit/?id=c759fadd251e4a5b95e0a4b483889f654ac89d62)~~

  * ~~Move caja extensions to`caja-extensions` package~~

  * ~~Drop mate-bluetooth for[blueman](https://github.com/blueman-project/blueman) (adding support for [Bluez5](./bluez5))~~

### Release 1.6

Released on April 2, 2013. Announcement [here](http://mate-desktop.org/2013/04/02/mate-1-6-released/).
[Old status page](./status-1.6.md).

  * ~~Fix deprecations in core packages ([Deprecated code](./deprecated_code))~~

  * ~~Caja improvements~~

    * ~~Add support for freedesktop.org File Manager DBus Interface~~ ([#3](https://github.com/mate-desktop/mate-file-manager/issues/3))

    * ~~Fix back vs parent directory selection~~ ([#19](https://github.com/mate-desktop/mate-file-manager/issues/19))

  * ~~Atril improvements~~

    * ~~Add xps backend~~ ([5ad9169](https://github.com/mate-desktop/mate-document-viewer/commit/5ad91699940909223c167ef40de03e9a55a5a9c3))

  * ~~Panel improvements~~

    * ~~Add`–run-dialog` option~~

    * ~~Window list: middle click button to close window~~ ([6d3058da](https://github.com/mate-desktop/libmatewnck/commit/6d3058da7c1fe19fbd6b1148ca23fae5d1dae505))

  * ~~Control center improvements~~

    * ~~Add option to enable compositing manager and fast alt-tab~~

    * ~~Set metacity theme if compiz or metacity are running~~

    * ~~Use same GNOME proxy settings in gsettings-desktop-schemas~~

  * ~~Window manager improvements~~

    * ~~Add option to open new windows on the center of the screen~~

  * ~~Calc improvements~~

    * ~~Update to newest non-Vala gcalctool~~

    * ~~Add buttons to support inverse trig functions ([#6](https://github.com/mate-desktop/mate-calc/issues/6))~~

  * ~~Add option(s) to show notifications only on one screen ([#4](https://github.com/mate-desktop/mate-notification-daemon/issues/4))~~

  * ~~Themes improvement~~

    * ~~Add GTK3 support for most themes~~

  * ~~Add support for mpris2 to mate-settings-daemon~~ ([#7](https://github.com/mate-desktop/mate-settings-daemon/issues/7), [9384398](https://github.com/mate-desktop/mate-settings-daemon/commit/9384398))

  * ~~Fix all incorrect FSF addresses~~

  * ~~[Replace MateConf with GSettings](./mateconf_to_gsettings.md)~~

  * ~~[Replace MateCorba with DBus](./matecorba_to_dbus.md)~~

  * ~~[Initial support for systemd-logind](./systemd-logind.md)~~

  * ~~[Replace MateVfs with GIO](./matevfs_to_gio.md)~~

  * ~~[Replace libmatenotify with libnotify](./libmatenotify_to_libnotify.md)~~

  * ~~Remove libmateui (unused), libmatecanvas (unused), libmatecomponent and libmatecomponentui (replace with dbus)~~

  * ~~Remove libmate (mate-open replaced with gvfs-open, gsettings schemas moved to mate-desktop package)~~

  * ~~Support opening a remote terminal in mate-file-manager-open-terminal ([#2](https://github.com/mate-desktop/mate-file-manager-open-terminal/issues/2))~~

  * ~~Move mixer applet to mate-media package ([#22](https://github.com/mate-desktop/mate-applets/issues/22))~~

  * ~~Sync translations~~

  * ~~Update .desktop files to indicate MATE variants.~~

### Release 1.4

Released on July 30, 2012. Announcement [here](http://mate-desktop.org/2012/07/30/mate-1-4-released/).

  * ~~Fix remaining applications in[Mate-Extra](https://github.com/mate-desktop/Mate-Extra)~~

    * ~~mate-character-map ported~~ perberos

    * ~~mate-disk-utility removed~~ stefano-k

    * ~~mate-policy-kit removed~~ Amanas

  * ~~Fix mate-keyring ([#2](https://github.com/mate-desktop/mate-keyring/issues/2))~~ stefano-k

  * ~~Add caja-dropbox package~~

  * ~~Caja improvements~~

    * ~~Restore toggle button for button and text-based location bar~~ ([#2](https://github.com/mate-desktop/mate-file-manager/issues/2))  stefano-k

    * ~~Add the ability to open bookmarks in the places side pane via the enter and space keys~~ Amanas

  * ~~mate-notification-daemon~~

    * ~~New themes: coco, nodoka~~ stefano-k

    * ~~Fix big icons issue~~ ([#3](https://github.com/mate-desktop/mate-notification-daemon/issues/3))  stefano-k

  * ~~Fix mate-indicator-applet (not all distros have the required dependencies)~~

    * ~~Remove indicator-applet-session~~ Amanas

  * ~~Fork gnome-user-share (as mate-user-share)~~ ([#3](https://github.com/mate-desktop/mate-bluetooth/issues/3))  Amanas

  * ~~[Fork libwnck (as libmatewnck)](./roadmap-transition_to_libmatewnck)~~ stefano-k

  * ~~Remove evolution dependency from caja-sendto and create a generic email plugin~~ ([#13](https://github.com/mate-desktop/mate-file-manager/issues/13))  stefano-k

  * ~~mate-media: remove unworking mate-sound-recorder~~ stefano-k

  * ~~mate-screensaver: add GDM support for user switch~~ stefano-k

  * ~~Add an option to marco to enable fast alt-tabbing when compositing is enabled~~ ([#4](https://github.com/mate-desktop/mate-window-manager/issues/4))  Amanas

  * ~~mate-icon-theme-faenza~~ Rowen_Stipe

  * ~~[Translations sync with transifex](./roadmap-1.4-translations.md) stefano-k, Amanas~~

### Release 1.2

Released on April 16, 2012. Announcement [here](http://mate-desktop.org/2012/04/16/mate-1-2-released/).

  * ~~Fix all about windows with new MATE website~~ Amanas

  * ~~Fix some remaining applications in[Mate-Extra](https://github.com/mate-desktop/Mate-Extra)~~

    * ~~mate-menu-editor[78](https://github.com/perberos/Mate-Desktop-Environment/issues/78)~~ stefano-k

    * ~~python-caja~~ stefano-k

  * ~~Port other missing applications~~

    * ~~caja-gksu[76](https://github.com/perberos/Mate-Desktop-Environment/issues/76)~~ stefano-k

    * ~~caja-image-converter~~ stefano-k

  * ~~Integration with freedesktop ([#44353](https://bugs.freedesktop.org/show_bug.cgi?id=44353), [commit](http://cgit.freedesktop.org/xdg/desktop-file-utils/commit/?id=2792eed31f4be15f135948d131b08920aa225e63))~~ nmarques

  * ~~Improve Caja stability~~

    * ~~Import all useful patches from nautilus~~ stefano-k

  * ~~Improve mate-panel stability~~

