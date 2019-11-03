# Session

## Without a display manager

To start mate-desktop, you should add mate-session to `~/.xinitrc` file.

    exec ck-launch-session mate-session

Now can type [startx](https://wiki.archlinux.org/index.php/Startx).

**Note:** If you have authorization problems (e.g. when mounting disks), try adding `dbus-launch` after `ck-launch-session`.

## GDM

Install it from your distro repository.

[GDM](https://wiki.archlinux.org/index.php/GDM) should autodetect Mate Desktop.

## KDM

Install it from your distro repository.

[KDM](https://wiki.archlinux.org/index.php/KDM) should autodetect Mate Desktop.

## LightDM

Install it from your distro repository.

[LightDM](https://wiki.archlinux.org/index.php/LightDM) should autodetect Mate Desktop.

## LXDM

Install it from your distro repository.

[LXDM](https://wiki.archlinux.org/index.php/LXDM) should autodetect Mate Desktop.

## Slim

Install it from your distro repository. Read [this Archlinux page](https://wiki.archlinux.org/index.php/Slim), should work in most distros.

