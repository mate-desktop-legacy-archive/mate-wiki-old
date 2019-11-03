# Arch Linux Package Repository

MATE is supported on i686 and x84_64 [Arch Linux](http://www.archlinux.org)
and on armv6h (Raspberry Pi) and armv7h for [Arch Linux ARM](http://archlinuxarm.org/).
If you encounter any issues please raise an issue.

  * <https://github.com/mate-desktop>

## Installation

MATE is available in the official repositories and can be installed with one
of the following:

  * The **mate-panel** package provides a minimal desktop shell.

  * The **mate** group contains the core desktop environment required for the standard MATE experience.

  * The **mate-extra** group contains additional utilities and applications that integrate well with the MATE desktop. Installing just the mate-extra group will not pull in the whole mate group via dependencies. If you want to install all MATE packages then you will need to explicitly install both groups.

To install the base MATE components simply install the **mate** group.

```bash
    pacman  -Syy mate
```

To install all of MATE install the **mate** and **mate-extra** groups.

```bash
    pacman  -Syy mate mate-extra
```

### Additional MATE packages

There is an additional packages that is not included in the mate or mate-extra
group because it is not neccessarily useful to everyone.

  * The **mate-netbook** package provides a MATE panel applet that might be useful to owners of small screen devices, such as a Netbook. The applet will automatically maximize all windows and provides an application switcher applet.

There are also a number of other MATE applications that are contributed and
maintained by the MATE community and therefore not included in the mate or
mate-extra groups.

  * **mate-applet-lockkeys** \- A MATE panel applet that shows which of the CapsLock, NumLock and ScrollLock keys are on and which are off.

  * **mate-applet-softupd** \- A MATE panel applet to notify when software updates become available.

  * **mate-applet-streamer** \- A MATE panel applet to let you play your favourite online radio station with a single click.

  * **mate-accountsdialog** \- An application to view and modify user accounts information for MATE.

  * **mate-color-manager** \- Color management application for MATE.

  * **mate-disk-utility** \- Disk management application for MATE.

  * **mate-mplayer** \- mplayer frontend for MATE

  * **mate-nettool** \- MATE interface for various networking tools.

  * **mate-themes-extras** \- Collection of GTK2/3 desktop themes for MATE.

  * **gnome-main-menu** \- A mate-panel applet similar to the traditional main-menu, but with a few additions.

  * **variety** \- Variety changes the wallpaper on a regular interval using user-specified or automatically downloaded images.

The following is also available via the AUR and integrates with MATE but the
package is not maintained by the MATE team.

  * [mintmenu](http://aur.archlinux.org/packages/mintmenu/) \- Linux Mint Menu for MATE.

You can install the packages above individually.

## Upgrading from 1.6 to 1.8

Do the upgrade:

```bash
    pacman -Syu
```

Agree to all the package replacements, it should look something like this.

```
    :: Starting full system upgrade...
    :: Replace mate-document-viewer with community/atril? [Y/n] y
    :: Replace mate-file-archiver with community/engrampa? [Y/n] y
    :: Replace mate-file-manager with community/caja? [Y/n] y
    :: Replace mate-file-manager-gksu with community/caja-extensions? [Y/n] y
    :: Replace mate-file-manager-image-converter with community/caja-extensions? [Y/n] y
    :: Replace mate-file-manager-open-terminal with community/caja-extensions? [Y/n] y
    :: Replace mate-file-manager-sendto with community/caja-extensions? [Y/n] y
    :: Replace mate-file-manager-share with community/caja-extensions? [Y/n] y
    :: Replace mate-image-viewer with community/eom? [Y/n] y
    :: Replace mate-menu-editor with community/mozo? [Y/n] y
    :: Replace mate-text-editor with community/pluma? [Y/n] y
    :: Replace mate-window-manager with community/marco? [Y/n] y
```

When the MATE 1.8 upgrade is complete there are a few packages you can remove
because some of the MATE 1.6 libraries are not required by MATE 1.8.

```
    pacman  -Rs libmatekeyring libmatewnck mate-character-map mate-keyring
```

## Upgrading from 1.4 to 1.6

MATE 1.6 migrated from `gconf` to `gsettings`. If you are updating from an
MATE 1.4 you might end up with an empty panel. To resolve the issue reset the
panel configuration to its defaults using `mate-panel –reset` and then use
`mate-conf-import` to restore most of your old settings.

After upgrading from MATE 1.4 to MATE 1.6 you should remove the some of the
old MATE 1.4 libraries that are not required by MATE 1.6, this can also
improve the start-up time of MATE. **NOTE!** It is your responsibility to
ensure that packages are not removed that might be required elsewhere.

```
    pacman  -R ffmpegthumbnailer-caja libmate libmatecanvas libmatecomponent libmatecomponentui libmatenotify libmateui mate-conf mate-conf-editor mate-corba mate-mime-data mate-vfs python-corba python-mate python-mate-desktop
```

You can also use:

```
    pacman -R $(pacman -Qtdq)
```

to remove any orphaned packages. Packages which are not orphaned are probably
still required.

**Note:** The command to remove orphaned packages will need to be executed
multiple times to ensure that all packages are cleaned up.

## Starting MATE

MATE can be started via a display manager or manually.

### Display Manager (recommended)

The recommended display manager for MATE on Arch Linux in `lightdm`

```
    pacman  -Syy lightdm-gtk3-greeter accountsservice
    systemctl enable lightdm
    systemctl enable accounts-daemon
```

Reboot and lightdm should be displayed. Select MATE from the available
sessions and login.

### Manually

In order to start MATE manually, you must add `exec mate-session` to your
`~/.xinitrc` file and then run `startx`

## Accessibility

MATE is well suited for use by individuals with sight or mobility impairment.
First install **orca** and **espeak** (Screen reader for individuals who are
blind or visually impaired) and **onboard** (On-screen keyboard useful for
mobility impaired users)

```
    pacman  -Syy orca espeak onboard
```

Now create `/etc/profile.d/gtk-accessibility.sh` and add the following to it.

```
    export GTK_MODULES=gail:atk-bridge
```

Reboot to make the change take affect and you can configure the accessibility
applications via `System → Preferences → Assistive Technologies`.

## Network Management

It is recommended that you use Network Manager for managing networks in MATE.

## Bluetooth

Bluetooth support for MATE 1.8 is [pending the completion of a new version of Blueman](http://mate-desktop.org/blog/2014-03-11-mate-desktop-singing-the-bluez/).
Details will be added here shortly. There are some experimental
Bluetooth utilities for MATE in the AUR:

  * [blueman-bluez5-git](http://aur.archlinux.org/packages/blueman-bluez5-git/) \- A GTK+ Bluetooth Manager. **MATE will adopt as the official Bluetooth utility in the future but it is under actively development and not everything works right now.**

  * [mate-bluetooth-bluez5-git](http://aur.archlinux.org/packages/mate-bluetooth-bluez5-git/) \- A collection of Bluetooth utilities and modules for MATE. **Now deprecated by the MATE team but this version can pair device and has been successfully used to tether an Android phone via PAN.**

## PulseAudio and GStreamer

MATE supports two audio backends, [PulseAudio](http://www.pulseaudio.org)
and [GStreamer](http://www.gstreamer.net).
By default, the PulseAudio backend is installed but if you want to
switch to the GStreamer backend, do the following:

    
    pacman  -S mate-settings-daemon-gstreamer mate-media-gstreamer

## Tip & Tricks

### Enabling compositing

Compositing is not be enabled by default. To enable it navigate to run `System
→ Preferences → Windows` and click the tick box alongside **Enable software
compositing window manager** in the `General` tab. Alternatively, you can run
the following from the terminal:

    
    
    dconf  write /org/mate/marco/general/compositing-manager true

### Enabling new window centering

By default, new windows are placed in the top-left corner. To center new
windows on creation navigate to run `System → Preferences → Windows` and click
the tick box alongside **Center new windows** in the `Placement` tab.
Alternatively, you can run the following from the terminal:

    
    
    dconf  write /org/mate/marco/general/center-new-windows true

### Enabling window snapping

Window snapping is not be enabled by default, to enable it navigate to run
`System → Preferences → Windows` and click the tick box alongside **Enable
side by side tiling** in the `Placement` tab.

#### Show or hide desktop icons

By default, MATE shows multiple icons on the desktop: The content of your
desktop directory, computer, home and network directories, the trash and
mounted drives. You can show or hide them individually or all at once using
`dconf`.

### Hide all desktop icons

    
    
    dconf  write /org/mate/desktop/background/show-desktop-icons false

### Hide individual icons

Hide computer icon:

    
    
    dconf write /org/mate/caja/desktop/computer-icon-visible false

Hide user directory icon:

    
    
    dconf write /org/mate/caja/desktop/home-icon-visible false

Hide network icon:

    
    
     $ dconf write /org/mate/caja/desktop/network-icon-visible false

Hide trash icon:

    
    
    dconf write /org/mate/caja/desktop/trash-icon-visible false

Hide mounted volumes:

```
    dconf write /org/mate/caja/desktop/volumes-visible false
```

Replace `false` with `true` for the icons to reappear.

# Testing MATE

An unofficial MATE development package repository is available. If you would
like to help test MATE then it is recommended you do so in a virtual machine.

## Unstable GTK2 and GTK3 repository

This unstable repository includes GTK2 and GTK3 build of the MATE 1.9.x
development branch. The GTK2 builds are recommended as the GTK3 are considered
experimental.

**WARNING!** \- If you have previsouly enabled the old `[mate-unstable-gtk3]`
repository available from <http://pkgbuild.com/~flexiondotorg/mate-unstable-gtk3/1.9/> then **STOP HERE!**

  * The new `[mate-unstable-dual]` is not compatible with `[mate-unstable-gtk3]` and I have no intention of explaining how to migrate, sorry ![:-\(](images/smileys/icon_sad.gif)

  * The new `[mate-unstable-dual]` is designed for use with the official Arch Linux repositories to upgrade from MATE 1.8.x.

Add the following to `pacman.conf`, **it must be the first enabled repository
in`pacman.conf`** so put it above `[testing]`.

```
    [mate-unstable-dual]
    SigLevel = Optional TrustAll
    Server = http://pkgbuild.com/~flexiondotorg/mate-unstable-dual/1.9/$arch
```

## Upgrading MATE 1.8 to MATE 1.9 GTK2

After adding the repository as described above, upgrade in the following way:

```
    pacman -Syu
```

When prompted with the following, answer with `y`

```
    :: Starting full system upgrade...
    :: Replace mate-media-pulseaudio with mate-unstable-dual/mate-media? [Y/n] y
    :: Replace mate-settings-daemon-pulseaudio with mate-unstable-dual/mate-settings-daemon? [Y/n] y
```

Remove `mate-dialogs` it is now obsolete.

```
    pacman -Rs mate-dialogs
```

The MATE 1.9 GTK2 packages are provided in the `mate-unstable` and `mate-
unstable-extra` groups.

## Upgrading MATE 1.8 to MATE 1.9 GTK3

**EXPERIMENTAL!** MATE 1.9 built with GTK3 is considered experimental. In
general it works but there maybe rendering inconsistencies and occasional
segmentation faults.

After adding the repository as described above, upgrade in the way:

```
    pacman -Syy
    pacman -S mate-unstable-gtk3 mate-unstable-extra-gtk3
```

When prompted to `Enter a selection (default=all):` for `mate-unstable-gtk3`
and `mate-unstable-extra-gtk3` press enter to select all. Then when prompted
with the following, answer with `y` to everything.

```
    :: caja-gtk3 and caja are in conflict. Remove caja? [y/N] y
    :: mate-desktop-gtk3 and mate-desktop are in conflict. Remove mate-desktop? [y/N] y
    :: marco-gtk3 and marco are in conflict. Remove marco? [y/N] y
    :: mate-control-center-gtk3 and mate-control-center are in conflict. Remove mate-control-center? [y/N] y
    :: mate-settings-daemon-gtk3 and mate-settings-daemon-pulseaudio are in conflict (mate-settings-daemon). Remove mate-settings-daemon-pulseaudio? [y/N] y
    :: libmatekbd-gtk3 and libmatekbd are in conflict. Remove libmatekbd? [y/N] y
    :: mate-notification-daemon-gtk3 and mate-notification-daemon are in conflict. Remove mate-notification-daemon? [y/N] y
    :: mate-panel-gtk3 and mate-panel are in conflict. Remove mate-panel? [y/N] y
    :: libmateweather-gtk3 and libmateweather are in conflict. Remove libmateweather? [y/N] y
    :: mate-session-manager-gtk3 and mate-session-manager are in conflict. Remove mate-session-manager? [y/N] y
    :: mate-polkit-gtk3 and mate-polkit are in conflict. Remove mate-polkit? [y/N] y
    :: atril-gtk3 and atril are in conflict. Remove atril? [y/N] y
    :: caja-gksu-gtk3 and caja-gksu are in conflict. Remove caja-gksu? [y/N] y
    :: caja-image-converter-gtk3 and caja-image-converter are in conflict. Remove caja-image-converter? [y/N] y
    :: caja-open-terminal-gtk3 and caja-open-terminal are in conflict. Remove caja-open-terminal? [y/N] y
    :: caja-sendto-gtk3 and caja-sendto are in conflict. Remove caja-sendto? [y/N] y
    :: caja-share-gtk3 and caja-share are in conflict. Remove caja-share? [y/N] y
    :: engrampa-gtk3 and engrampa are in conflict. Remove engrampa? [y/N] y
    :: eom-gtk3 and eom are in conflict. Remove eom? [y/N] y
    :: mate-applets-gtk3 and mate-applets are in conflict. Remove mate-applets? [y/N] y
    :: mate-media-gtk3 and mate-media-pulseaudio are in conflict. Remove mate-media-pulseaudio? [y/N] y
    :: mate-netspeed-gtk3 and mate-netspeed are in conflict. Remove mate-netspeed? [y/N] y
    :: mate-power-manager-gtk3 and mate-power-manager are in conflict. Remove mate-power-manager? [y/N] y
    :: mate-screensaver-gtk3 and mate-screensaver are in conflict. Remove mate-screensaver? [y/N] y
    :: mate-sensors-applet-gtk3 and mate-sensors-applet are in conflict. Remove mate-sensors-applet? [y/N] y
    :: mate-system-monitor-gtk3 and mate-system-monitor are in conflict. Remove mate-system-monitor? [y/N] y
    :: mate-terminal-gtk3 and mate-terminal are in conflict. Remove mate-terminal? [y/N] y
    :: mate-user-share-gtk3 and mate-user-share are in conflict. Remove mate-user-share? [y/N] y
    :: mate-utils-gtk3 and mate-utils are in conflict. Remove mate-utils? [y/N] y
    :: mozo-gtk3 and mozo are in conflict. Remove mozo? [y/N] y
    :: pluma-gtk3 and pluma are in conflict. Remove pluma? [y/N] y
    :: galculator and galculator-gtk2 are in conflict. Remove galculator-gtk2? [y/N] y
```

    Remove ''mate-dialogs'' it is now obsolete.

```
    pacman -Rs mate-dialogs
```

It _might_ also be possible to remove the following packages from your system
when you 've migrated to MATE 1.9.x GTK3. The following a GTK2 dependencies
that are not required by the GTK3 build of MATE. Other applications you have
installed might require them, so remove them with care.

```
    pacman -Rs gtkmm gtksourceview2 libwnck pygtksourceview2 vte
```

The MATE 1.9 GTK3 packages are provided in the `mate-unstable-gtk3` and `mate-unstable-extra-gtk3` groups.

# Other Wiki's

Arch Linux and some of it's derivatives also have wiki pages about MATE.

  * <https://wiki.archlinux.org/index.php/MATE>

  * <http://wiki.manjaro.org/index.php?title=MATE_Desktop_Environment>
