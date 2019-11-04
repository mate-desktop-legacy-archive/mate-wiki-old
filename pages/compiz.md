# Compiz

## Fedora

Fedora comes with compiz-0.8.8

Minimal installation:

    
    
    yum install compiz compiz-mate fusion-icon

Extra packages:

    
    
    yum install compiz-plugins-main compiz-plugins-extra compiz-plugins-unsupported emerald-themes emerald-themes-extra

Runtime:

The first start should be done with fusion-icon which is in the menu, or from
a terminal with the command 'compiz-manager'. This script test your system if
it is ready for compiz.

If compiz is running you can do your real-time configuration with the 'ccsm'
configuration tool.

The compiz-mate package includes 2 start scripts, compiz-mate-gtk and compiz-
mate emerald. Depends on which windows-decorator you want to use, you can add
one of them to the gsettings key

/org/mate/desktop/session/required-components/windowmanager

Use dconf-editor and replace 'marco' with 'compiz-mate-gtk' or 'compiz-mate-
emerald'.

Or use gsetting from the command line.

    
    
    gsettings set org.mate.session.required-components windowmanager <wm>

Replace <wm> with 'compiz-mate-gtk' or 'compiz-mate-emerald'.

Now your mate-session starts directly with compiz as window-manager.

To return to the default window manager (marco) run

    
    
    gsettings reset org.mate.session.required-components windowmanager

have fun ;)

## Ubuntu

open a terminal and write

    
    
    sudo apt-get install compiz compizconfig-settings-manager

the packets are needed are these: compiz compiz-core compiz-gnome compiz-
plugins compiz-plugins-default compiz-plugins-main compiz-plugins-main-default
compizconfig-backend-gconf compizconfig-settings-manager libcompizconfig0
libdecoration0 python-compizconfig

then to change in compiz type in terminal

    
    
    compiz --replace

## Debian

## Gentoo

### Compiz fusion 0.8

This assumes you installed mate from the mate-overlay. The overlay has an
version of fusion-icon that has been patched to recognize the mate window
manager marco.

Install the following packages.

    
    
    emerge -va x11-apps/fusion-icon x11-wm/compiz-fusion x11-apps/simple-ccsm

Now be sure to configure with simple-ccsm before you enable the compiz window
manager.

Run compiz fusion icon and in the notification earea you should have a new
icon in which you can select compiz as the window manager. See the
[compiz-fusion-icon](https://wiki.compiz.org/CompizFusionIcon) documentation for more info.

### Compiz 0.9

Currently compiz 0.9 is not in the main portage tree. There are ebuilds in the
desktop-effects overlay.

    
    
    layman -a desktop-effects

If you have compiz 0.8 already installed you will have to remove it before
installing compiz 0.9 dues to blockers.

Now emerge compiz with:

    
    
    emerge compiz

We need to create a script to start compiz. Place this file in
`/usr/local/bin` or another directory that is in your `$PATH`.

startcompiz code:

```bash
    #!/bin/sh
    compiz --replace &
    gtk-window-decorator --replace
```

Before starting compiz please make sure you configure compiz first. In the
default configuration gtk-window-decorator fails to start.

Now you have 2 options. Start compiz by adding startcompiz as a startup
applications or replace the default window manager marco.

I suggest you first try it out by starting it from a terminal before choosing
either one untill you are satisfied with it.

If you like to replace the default window manager update gsettings/dconf by
running the following command.

    
    
    gsettings set org.mate.session.required-components windowmanager startcompiz

To return to the default window manager marco run the following.

    
    
    gsettings reset org.mate.session.required-components windowmanager

## Arch Linux

All Compiz related packages discussed below are in the AUR.

Before starting Compiz, ensure that the “Window Decoration” plugin is enabled
at the very least so you can move windows around. Also ensure that the
“Command” field in “Window Decoration” is set to “emerald”, “gtk-window-
decorator”, or “kde4-window-decorator” depending on which decorator you have
installed and wish to use.

### Installing Compiz 0.8

Install either compiz-core, compiz-gtk-standalone or compiz-core-mate.

For the settings manager, install ccsm.

For the plugins, install compiz-fusion-plugins-main, compiz-fusion-plugins-
extra and optionally compiz-fusion-plugins-unsupported.

The Emerald decorator can be installed from the emerald package. Extra emerald
themes can be installed from the emerald-themes package.

### Installing Compiz 0.9

Install either compiz or compiz-bzr (the development version).

The Emerald decorator can be installed from the emerald0.9 package. Extra
emerald themes can be installed from the emerald-themes package.

Alternatively, the AUR contains a package called compiz-manjaro. This package
will install the necessary packages for running MATE with Compiz 0.9, along
with good defaults, and preconfigured autostart. If you have trouble
installing the other Compiz packages for Arch Linux, try this.

## Others

We suggest to use this repository for compiling compiz-0.8.8 for MATE-1.6

<https://github.com/bhull2010?tab=repositories>
