# Distribution Maintainers

Helpful page for distribution maintainers.

Also worth to have look at [known issues](./known_issues) page.

## MATE Release Lifecycle

MATE only supports the current stable release.

For instance, 1.6 was released so 1.4 is no longer supported. When 1.8 is
released, 1.6 will no longer be supported.

## Upstream patches

  * desktop-file-utils. Commit [#2792eed](https://cgit.freedesktop.org/xdg/desktop-file-utils/commit/?id=2792eed31f4be15f135948d131b08920aa225e63) Add MATE to list of registered environments

  * xdg-user-dirs. Bug [#61341](https://bugs.freedesktop.org/show_bug.cgi?id=61341) Add MATE to OnlyShowIn in xdg-user-dirs-gtk desktop file

  * xdg-utils. Bug [#58861](https://bugs.freedesktop.org/show_bug.cgi?id=58861) add MATE desktop support in xdg-settings

## NotShowIn

NotShowIn Changes, to hide different desktop apps, that MATE supports on it's
own. Mostly xfce4/lxde changes

  * [lxrandr](https://git.pld-linux.org/?p=packages/lxrandr.git;a=blob_plain;f=mate-desktop.patch;h=ed1baf79a5ca5f12ad56803e48db81620ba102e8;hb=fc460598dd1ced5c1504bfa16e6eedde24252c6b)

  * [libfm](https://git.pld-linux.org/?p=packages/libfm.git;a=blob_plain;f=mate-desktop.patch;h=64c4efa47e9b5ee2838feac5a50b16ab76bb8581;hb=873e07d7999305ed01f2241792287309e2864921) PCManFM library

  * [pcmanfm](https://git.pld-linux.org/?p=packages/pcmanfm.git;a=blob_plain;f=mate-desktop.patch;h=af9cf7dba00a2d4628c6cc46a2923bd9facd478d;hb=892655160cd77e909a7caed392699267cb7531b2)

  * [lxappearance](https://git.pld-linux.org/?p=packages/lxappearance.git;a=blob_plain;f=mate-desktop.patch;h=fbe5538255251581a130c17fa8180183f0d9f309;hb=df4f3981ee9103f98f0dc0f3f3b71791ca8ebed0)


