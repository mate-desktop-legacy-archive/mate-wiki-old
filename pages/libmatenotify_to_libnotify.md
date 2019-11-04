# Replace libmatenofity with libnotify

  * [Libnotify Reference Manual](https://developer-next.gnome.org/libnotify/0.7/)

## API Changes

Removed symbols:

    
    
    notify_notification_attach_to_status_icon
    notify_notification_attach_to_widget
    notify_notification_new_with_status_icon
    notify_notification_set_geometry_hints

Changed symbols:

    
    
    /* libnotify < 0.7.0, libmatenotify */
    notify_notification_new (char const* summary, char const* body, char const* icon, GtkWidget* attach)
    /* libnotify >= 0.7.0 */
    notify_notification_new (char const* summary, char const* body, char const* icon)

## Status

[mate-applets](https://github.com/mate-desktop/mate-applets) | [Done](https://github.com/mate-desktop/mate-applets/commit/41389eb)
---|---
[mate-bluetooth](https://github.com/mate-desktop/mate-bluetooth) | [Done](https://github.com/mate-desktop/mate-bluetooth/commit/bf8eb6b)
[mate-dialogs](https://github.com/mate-desktop/mate-dialogs) | [Done](https://github.com/mate-desktop/mate-dialogs/commit/9dc105f)
[mate-notification-daemon](https://github.com/mate-desktop/mate-notification-daemon) | [Done](https://github.com/mate-desktop/mate-notification-daemon/commit/d263541)
[mate-power-manager](https://github.com/mate-desktop/mate-power-manager) | [Done](https://github.com/mate-desktop/mate-power-manager/commit/d39dce3)
[mate-screensaver](https://github.com/mate-desktop/mate-screensaver) | [Done](https://github.com/mate-desktop/mate-screensaver/commit/a5f06dc)
[mate-sensors-applet](https://github.com/mate-desktop/mate-sensors-applet) | [Done](https://github.com/mate-desktop/mate-sensors-applet/commit/9a2a46d)
[mate-settings-daemon](https://github.com/mate-desktop/mate-settings-daemon) | [Done](https://github.com/mate-desktop/mate-settings-daemon/commit/9ee6ae6)
[mate-user-share](https://github.com/mate-desktop/mate-user-share) | [Done](https://github.com/mate-desktop/mate-user-share/commit/3b15531)

