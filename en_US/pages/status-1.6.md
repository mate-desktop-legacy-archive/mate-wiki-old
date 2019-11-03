# Status of 1.6

Status of ongoing development of the 1.6 release of Mate.

## MATE Packages

_Note:_ Packages are listed in build order.

Core Packages |  release |  [g_settings](./mateconf_to_gsettings) |  [deprecations](./deprecated_code) |  [features](./roadmap)
---|---|---|---|---
[mate-common](https://github.com/mate-desktop/mate-common) |  1.5.1 |  No Use |  None |
[mate-doc-utils](https://github.com/mate-desktop/mate-doc-utils) |  1.5.0 |  No Use |  None |
[mate-desktop](https://github.com/mate-desktop/mate-desktop) |  1.5.5 |  Done |  None |
[libmatekeyring](https://github.com/mate-desktop/libmatekeyring) |  1.5.0 |  No Use |  Done |
[mate-keyring](https://github.com/mate-desktop/mate-keyring) |  1.5.0 | [Done](https://github.com/mate-desktop/mate-keyring/commit/576b847d7f5a4407fa35a04d8dfa802e1fd1d311) |  Done |
[libmatekbd](https://github.com/mate-desktop/libmatekbd) |  1.5.0 |  Done |  None |
[libmatewnck](https://github.com/mate-desktop/libmatewnck) |  1.5.0 |  No Use |  None | Middle click button to close window
[libmateweather](https://github.com/mate-desktop/libmateweather) |  1.5.1 |  Done |  Done |
[mate-icon-theme](https://github.com/mate-desktop/mate-icon-theme) |  1.5.0 |  No Use |  None |
[mate-dialogs](https://github.com/mate-desktop/mate-dialogs) |  1.5.0 |  No Use |  None |
[mate-file-manager](https://github.com/mate-desktop/mate-file-manager) |  1.5.1 |  Done | jasmineaura |  ~~[DBUS interface](https://github.com/mate-desktop/mate-file-manager/issues/3)~~ , ~~[BACK vs. PARENT Directory Selection](https://github.com/mate-desktop/mate-file-manager/issues/19)~~
[mate-polkit](https://github.com/mate-desktop/mate-polkit) |  1.5.0 |  No Use |  Done |
[mate-window-manager](https://github.com/mate-desktop/mate-window-manager) |  1.5.3 | [Done](https://github.com/mate-desktop/mate-window-manager/commit/7f595187a140a45ee5ba2fc2b9c068b46d829f79) |  Done |
[mate-settings-daemon](https://github.com/mate-desktop/mate-settings-daemon) |  1.5.4 | [Done](https://github.com/mate-desktop/mate-settings-daemon/commit/d2c7965aa092cecb857bd0301b7c9ff2dc10f9f8) |  Done |  MPRIS2 support
[mate-session-manager](https://github.com/mate-desktop/mate-session-manager) |  1.5.0 | [Done](https://github.com/mate-desktop/mate-session-manager/commit/b34dc27b7b191e56cbf640a963435d6e68982608) |  Done |
[mate-menus](https://github.com/mate-desktop/mate-menus) |  1.5.0 |  No Use |  Done |
[mate-panel](https://github.com/mate-desktop/mate-panel) |  1.5.4 |  Done |  sbalneav | –run-dialog option
[mate-backgrounds](https://github.com/mate-desktop/mate-backgrounds) |  1.5.0 |  No Use |  None |
[mate-themes](https://github.com/mate-desktop/mate-themes) |  1.5.0 |  No Use |  None | GTK3 support
[mate-notification-daemon](https://github.com/mate-desktop/mate-notification-daemon) |  1.5.1 | [Done](https://github.com/mate-desktop/mate-notification-daemon/commit/2d7e34441f4d33dc1edb5e9871b66b4977069bae) |  sbalneav |
[Option to show notifications only on one screen](https://github.com/mate-desktop/mate-notification-daemon/issues/4)
[mate-image-viewer](https://github.com/mate-desktop/mate-image-viewer) |  1.5.0 |  Done | sbalneav |
[mate-control-center](https://github.com/mate-desktop/mate-control-center) |  1.5.3 |  Done | sbalneav |  Set Metacity theme, [Use GNOME Proxy settings](http://git.mate-desktop.org/mate-control-center/commit/?id=46787e474859801435542191480e2851f7fd870c)
[mate-screensaver](https://github.com/mate-desktop/mate-screensaver) |  1.5.1 |  Done | sbalneav |
[mate-file-archiver](https://github.com/mate-desktop/mate-file-archiver) |  1.5.1 |  Done |  Done |
[mate-media](https://github.com/mate-desktop/mate-media) |  1.5.1 |  Done |  Done |
[mate-power-manager](https://github.com/mate-desktop/mate-power-manager) |  1.5.1 |  Done |  None |
[mate-system-monitor](https://github.com/mate-desktop/mate-system-monitor) |  1.5.1 |  Done | Done |
Extra Packages |  release |  [g_settings](./mateconf_to_gsettings) |  [deprecations](./deprecated_code) |  [features](./roadmap)
[caja-dropbox](https://github.com/mate-desktop/caja-dropbox) |  |  No use |  |
[mate-applets](https://github.com/mate-desktop/mate-applets) |  1.5.1 |  _stefano-k_ |  |
[mate-bluetooth](https://github.com/mate-desktop/mate-bluetooth) |  1.5.0 |  Done |  None |
[mate-calc](https://github.com/mate-desktop/mate-calc) |  1.5.1 |  Done |  None |
[mate-character-map](https://github.com/mate-desktop/mate-character-map) |  1.5.0 |  Done |  |
[mate-document-viewer](https://github.com/mate-desktop/mate-document-viewer) |  1.5.0 |  Done |  |
[XPS Backend](https://github.com/mate-desktop/mate-document-viewer/commit/5ad91699940909223c167ef40de03e9a55a5a9c3)
[mate-file-manager-gksu](https://github.com/mate-desktop/mate-file-manager-gksu) |  1.5.0 |  No Use |  |
[mate-file-manager-image-converter](https://github.com/mate-desktop/mate-file-manager-image-converter) |  1.5.0 |  No Use |  |
[mate-file-manager-open-terminal](https://github.com/mate-desktop/mate-file-manager-open-terminal) |  1.5.0 |  Done |  |
[mate-file-manager-sendto](https://github.com/mate-desktop/mate-file-manager-sendto) |  1.5.0 | Done |  |
[mate-file-manager-share](https://github.com/mate-desktop/mate-file-manager-share) |  1.5.0 | No Use |  |
[mate-icon-theme-faenza](https://github.com/mate-desktop/mate-icon-theme-faenza) |  1.5.0 | No Use |  None |
[mate-indicator-applet](https://github.com/mate-desktop/mate-indicator-applet) |  1.5.0 |  No Use | |
[mate-menu-editor](https://github.com/mate-desktop/mate-menu-editor) |  1.5.0 |  No Use |  |
[mate-netbook](https://github.com/mate-desktop/mate-netbook) |  1.5.0 |  Done |  |
[mate-netspeed](https://github.com/mate-desktop/mate-netspeed) |  1.5.0 |  Done |  |
[mate-sensors-applet](https://github.com/mate-desktop/mate-sensors-applet) |  1.5.1 |  Done |  | Remove MateComponent
[mate-system-tools](https://github.com/mate-desktop/mate-system-tools) |  1.5.0 |  No Use |  |
[mate-terminal](https://github.com/mate-desktop/mate-terminal) |  1.5.0 |  Done |  |
[mate-text-editor](https://github.com/mate-desktop/mate-text-editor) |  1.5.0 |  Done |  |
[mate-user-share](https://github.com/mate-desktop/mate-user-share) |  1.5.0 |
[Done](https://github.com/mate-desktop/mate-user- share/commit/8af5555721e4791d09db088a41c784bf2c4fd7f5) |  |
[mate-utils](https://github.com/mate-desktop/mate-utils) |  1.5.0 |  Done |  |  Remove MateComponent
[python-caja](https://github.com/mate-desktop/python-caja) |  1.5.0 |  No use |  |

## Removed Packages

Sometimes our purpose in life is only to serve as a warning to others.

Package |  [Status](./building-1.6)
---|---
[ffmpegthumbnailer-caja](https://github.com/mate-desktop/ffmpegthumbnailer-caja) |  Removed
[libmate](https://github.com/mate-desktop/libmate) |  Removed
[libmatecanvas](https://github.com/mate-desktop/libmatecanvas) |  Removed
[libmatecomponent](https://github.com/mate-desktop/libmatecomponent) |  Removed
[libmatecomponentui](https://github.com/mate-desktop/libmatecomponentui) |  Removed
[libmatenotify](https://github.com/mate-desktop/libmatenotify) |  Removed
[libmateui](https://github.com/mate-desktop/libmateui) |  Removed
[mate-conf](https://github.com/mate-desktop/mate-conf) |  Removed
[mate-conf-editor](https://github.com/mate-desktop/mate-conf-editor) |  Removed
[mate-corba](https://github.com/mate-desktop/mate-corba) |  Removed
[mate-mime-data](https://github.com/mate-desktop/mate-mime-data) |  Removed
[mate-vfs](https://github.com/mate-desktop/mate-vfs) |  Removed
[python-corba](https://github.com/mate-desktop/python-corba) |  Removed
[python-mate](https://github.com/mate-desktop/python-mate) |  Removed
[python-mate-desktop](https://github.com/mate-desktop/python-mate-desktop)|  Removed

