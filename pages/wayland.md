# Wayland

<http://wayland.freedesktop.org/>

> Wayland is a protocol for a compositor to talk to its clients as well as a C
library implementation of that protocol. The compositor can be a standalone
display server running on Linux kernel modesetting and evdev input devices, an
X application, or a wayland client itself. The clients can be traditional
applications, X servers (rootless or fullscreen) or other display servers.

>  Part of the Wayland project is also the Weston reference implementation of
a Wayland compositor. Weston can run as an X client or under Linux KMS and
ships with a few demo clients. The Weston compositor is a minimal and fast
compositor and is suitable for many embedded and mobile use cases.

  * Documentation: <http://wayland.freedesktop.org/docs/html/>

> Wayland support for MATE is currently targeted for some future release.
Though Wayland itself is relatively stable (but still under a lot of active
development), the current obstacles include creating a Wayland compositor for
MATE, and porting the core applications to gtk3, which will allow the
applications to take full advantage of Wayland's capabilites (currently, these
applications are based in gtk2, which can only communicate with Wayland
through the XWayland implementation).

