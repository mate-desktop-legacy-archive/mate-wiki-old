# Install

Should you have issues relating to MATE installation, you may inquire in our [#mate](https://webchat.freenode.net?randomnick=1&channels=mate&prompt=1) IRC channel on the freenode network.

There are some prominent Linux distributions that include MATE in their official repositories:

- [Arch Linux](https://www.archlinux.org/)
- [Debian](https://www.debian.org/)
- [Fedora](https://www.fedoraproject.org/)
- [Gentoo](https://www.gentoo.org/)
- [Linux Mint](https://www.linuxmint.com/)
- [openSUSE](https://www.opensuse.org/)
- [Ubuntu](https://www.ubuntu.com/)

And also many others:

- [ALT Linux](https://en.altlinux.org/)
- [Mageia](https://www.mageia.org/)
- [PCLinuxOS](https://www.pclinuxos.com/get-pclinuxos/mate/)
- [PLD Linux](https://www.pld-linux.org/)
- [Point Linux](https://pointlinux.org/)
- [Sabayon](https://www.sabayon.org/)
- [Salix](https://www.salixos.org/)
- [Frugalware](https://www.frugalware.org/)
- [FreeBSD](https://www.freebsd.org/)
- [DragonflyBSD](https://www.dragonflybsd.org/)
- [NetBSD](https://www.netbsd.org/)

To install MATE in these distributions, you should use their package manager.

## Debian

MATE 1.8.1 is currently packaged for Debian 8 (jessie). MATE 1.12 is also
available on Debian testing (“Stretch”) and unstable (“Sid”).

_(If_`sudo` _is unavailable on your system, simply omit it and use a root shell)_
First make sure your package list is up-to-date by running:

    
    
     sudo apt-get update

To install MATE, choose **one** of the apt-get options below.

  * This will install the base packages required for a minimal MATE desktop
    
         sudo apt-get install mate-desktop-environment-core

  * This will install the complete MATE desktop
    
        sudo apt-get install mate-desktop-environment

  * This will install the complete MATE desktop including a few extras
    
        sudo apt-get install mate-desktop-environment-extras

## Ubuntu

  * [Replace Unity by MATE](./replace_unity_by_mate.md)

### Ubuntu 14.04 LTS (Trusty Tahr)

The Ubuntu MATE Developers utilize a MATE 1.8.1 PPA Repo ported from Debian
for use with the Trusty (14.04) Ubuntu MATE Remix.

#### Add Repository

You may add this repo to your apt sources via the following commands:

    
    
    sudo apt-add-repository ppa:ubuntu-mate-dev/ppa
    sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate

#### Install MATE 1.8.1

First make sure your package list and packages are up-to-date by running:

    
    
    sudo apt-get update
    sudo apt-get upgrade

##### Vanilla MATE

You can choose to install Vanilla MATE by picking **one** of the apt-get
options below.

  * This will install the base packages required for a minimal MATE desktop
    
         sudo apt-get install mate-desktop-environment-core

  * This will install the complete MATE desktop
    
        sudo apt-get install mate-desktop-environment

  * This will install the complete MATE desktop including a few extras _(Most Users Will Want This)_
    
         sudo apt-get install mate-desktop-environment-extras

##### Ubuntu MATE

Alternatively you may choose to install Ubuntu MATE Remix.

_Ubuntu MATE is a more comprehensive option that offers a slightly tweaked
layout, configuration, and themes to integrate into Ubuntu in a more seamless
fashion. This will install the complete MATE Desktop Environment as well as
LightDM and numerous other applications to provide a full and well rounded
desktop._

    
    
     sudo apt-get install ubuntu-mate-core ubuntu-mate-desktop

### Ubuntu 14.10 (Utopic Unicorn)

MATE 1.8 is available in official repositories.

## Linux Mint

  * Linux Mint 12 “Lisa” has MATE 1.0

  * Linux Mint 13 “Maya” has MATE 1.2

  * Linux Mint 14 “Nadia” has MATE 1.4

  * Linux Mint 15 “Olivia” has MATE 1.6

  * Linux Mint 16 “Petra” has MATE 1.6

  * Linux Mint 17 “Qiana” has MATE 1.8

  * Linux Mint LMDE has MATE 1.6

### Install MATE on XFCE/KDE edition of Mint

For Mint version without MATE, you have to install it separately.

#### Mint 15 "Olivia" and before

In Mint versions 15 and earlier, you can install **mate-desktop-environment**
and **mate-core**.

    
    
     # This will install the base packages required for a minimal MATE desktop
    apt-get install mate-core
    # This will install the complete MATE desktop including extras
    apt-get install mate-desktop-environment

#### Mint 16 "Petra"

In Mint Petra the package that installs mate is **mate-meta**

    
    
     # Only one and installs all of Mate
    apt-get install mate-meta

#### Mint 17 "Rebecca"

In Mint Rebecca the package that installs mate is **mint-meta-mate**

    
    
     # Only one and installs all of Mate
    apt-get install mint-meta-mate

## Slackware

You can install MATE on Slackware by using MATE SlackBuilds (MSB) Project

### MATE SlackBuilds

Please visit the project page at <https://mateslackbuilds.github.io/> (backup:
<https://mateslackbuilds.netlify.com/>) for more information about this
project.

Binary packages for Slackware 14.0, 14.1, 14.2, and future release
(x86/x86_64) are located in

  * <https://www.slackware.uk/msb/> (primary mirror) 

  * <https://repo.ukdw.ac.id/msb/> (backup mirror)

People using Slackware-Current are advised to build the sources from master
branch at <https://github.com/mateslackbuilds/msb> and read CURRENT.TXT prior
building.

## Fedora

MATE desktop is included in Fedora and available for all current releases.
There are multiple ways to get MATE with Fedora.

  1. If you have Fedora already installed, use the following command:

        yum groupinstall mate-desktop

Installation from Mate-Compiz livecd:

  1. scroll down to the buttom of fedora's new webpage <https://getfedora.org/>

  2. For a netiso image choose Fedora-Server product <https://getfedora.org/de_CH/server/download/>

  3. Under Fedora-Spins you will find the mate-compiz livecd image <https://spins.fedoraproject.org/>

Older releases (f20) you can dowload via torrent.  <https://torrents.fedoraproject.org/>

## Red Hat Enterprise Linux 7

MATE is available through the [Extra Packages for Enterprise Linux (EPEL)](https://fedoraproject.org/wiki/EPEL "https://fedoraproject.org/wiki/EPEL") repository, maintained by the Fedora Project. This should work on CentOS 7 as well, and any other compatible derivatives.

After you install the epel-release-7*.rpm package to add the EPEL repository
to Yum, you can install MATE with the following command:


    yum groupinstall mate-desktop

If you install this on a minimal system without an existing GUI configured
(such as a GNOME or KDE desktop), you might want to install the X Window
System group as well for local graphical logins:


    yum groupinstall "X Window System"

you may also want to change the default systemd target to graphical:


    systemctl set-default graphical.target

## Gentoo

MATE is available from the official repositories. See
<https://wiki.gentoo.org/wiki/MATE>.


    emerge -av mate

For x86, MATE is ~arch keyworded so if you run a stable system make sure to
add the necessary entries to package.keywords.

## Arch Linux

See the [Arch Linux Package Repository](./archlinux_custom_repo.md) page.

To install the base MATE components simply install the **mate** group.

    pacman  -Syy mate

To install all of MATE install the **mate** and **mate-extra** groups.

    pacman  -Syy mate mate-extra

## openSUSE

openSUSE users can install the MATE Desktop through YaST2 META Installer, we
strongly suggest this method. Please visit the MATE Desktop Portal page in
openSUSE wiki for further information.

  * [openSUSE MATE Desktop Portal](https://en.opensuse.org/Portal:MATE)

Besides installation instructions the MATE Desktop Portal on openSUSE wiki
also provides other useful information!

## Frugalware Linux

MATE has been merged into current. Now, you just have to use this command :

    
    
    # pacman-g2 -Syy mate-extra

When installation is done, restart the display-manager and you'll be able to
choose MATE as window manager.

## Mageia

### Mageia 4

Mageia 4 provides and officially supports MATE. Use _rpmdrake_ or _Mageia
Control Center > Install & Remove Software_ and install _task-mate_ for full
MATE Desktop or install _task-mate-minimal_ for minimal MATE Desktop
installation. You can also install MATE Desktop from command-line: `urpmi
task-mate`

Due to dependencies of some other applications to deprecated MATE packages,
MATE 1.8 will not be provided as an update or backport to avoid possible
crashes/problems. However, there is an unsupported, unofficial repository
providing MATE 1.8 version. Please read [below section](./download#mageia_3.md)
and use same commands to add the repository.

### Mageia 3

Mageia packager and Mageia MATE packages maintainer _Atilla ÖNTAŞ <a.k.a
tarakbumba>_ provides an unofficial Mageia 3 repository. This repository
includes backported MATE packages from Cauldron and a few packages not
available in official Mageia repositories.

To install MATE Desktop for your Mageia 3 system,

  * Add unofficial repositories from commandline as _root_ :

    
    
     urpmi.addmedia --distrib 'https://tarakbumba.mageia.org.pl/$RELEASE/$ARCH'

  * Use the code **exactly** seen as above. See about [ this post](https://forums.mageia.org/en/viewtopic.php?f=10&t=4867&start=125#p46058) for urpmi variables

  * Then install either _task-mate-minimal_ for a minimal installation or _task-mate_ for full MATE Desktop via rpmdrake or urpmi.

## ALT Linux

### Platform 7

MATE 1.6 packages are available in official stable repository; use _apt-get_
or _synaptic_ to install _mate-default_ for reasonable set of packages, there
's also _mate-minimal_ metapackage for those picky enough.

[Centaurus](https://en.altlinux.org/ALT_Linux_7.0_Centaurus) the flagship ALT Linux
distribution is MATE based in its 7.0 version; there's a somewhat minimalistic
[starterkit](https://en.altlinux.org/Starterkits#main) too.

### Sisyphus

MATE packages are also available within [development repository](https://packages.altlinux.org/mate);
installation instructions are the same
and there are weekly [Regular LiveCD](https://en.altlinux.org/Regular)
builds (these are 32- and 64-bit x86
bootable/installable images supporting CD/Flash and BIOS/UEFI).

ARMv7 (hardfloat) builds are
[available](https://ftp.altlinux.org/pub/distributions/ALTLinux/Sisyphus/files/armh/) as
well.

## PLD Linux

MATE is present in [PLD Th](https://www.pld-linux.org/th), currently version is **1.8**

You can install MATE desktop using 
[metapackage-mate](https://git.pld-linux.org/packages/metapackage-mate) package:

    
    
    poldek --up -u metapackage-mate

and to install with some more extras:

    
    
    poldek -u metapackage-mate-extras

# *BSD

## FreeBSD

MATE Desktop is available in the FreeBSD Ports tree, and can be installed via
the mate meta-port available on
[FreshPorts](https://www.freshports.org/x11/mate/).

Installation is supported via the ports tree directly or the binary package
repositories.

**Using Ports:**

    
    
    cd /usr/ports/x11/mate && make install clean

**Using Binary Packages:**

    
    
    pkg install mate

## DragonFlyBSD

MATE Desktop is available in the DragonFlyBSD Dports.

Installation is supported, via the DPorts tree directly or the binary package
repositories.

**Using DPorts:**

    
    
    cd /usr/dports/x11/mate-desktop/
    
    
    /usr/dports/x11/mate-desktop/make install

**Using Binary Packages:**

    
    
    pkg update
    
    
    pkg install mate mate-desktop

## NetBSD

Mate is avaible in pkgsrc and [pkgsrc-wip](https://pkgsrc.se/wip/mate) “mate” is a Meta-package

In pkgsrc

    
    
    # cd /usr/pkgsrc/meta-pkgs/mate
    
    
    make install clean clean-depends
    
    
    cd /usr/pkgsrc/wip/mate/
    
    
    make install clean clean-depends

## OpenBSD

Binary

    
    
    # pkg_add -v mate-desktop mate-notification-daemon mate-terminal mate-panel mate-session-manager mate-icon-theme mate-control-center mate-power-manager mate-utils mate-calc caja atril gvfs-goa gvfs-google gvfs-nfs gvfs-smb

Edit in /home/user/.xinitrd # nano .xinitrc

    
    
    exec mate-session

Ports

If you want use a slim

    
    
    #pkg_add -v slim slim-themes

Deamon # nano /etc/rc.local

    
    
    /usr/local/bin/slim -d

# nano /etc/rc.conf.local

    
    
    pkg_scripts="dbus_daemon avahi_daemon"
    dbus_enable=YES
    multicast=YES

Rcctl

    
    
    rcctl enable messagebus avahi_daemon
    rcctl order messagebus avahi_daemon
    rcctl enable apmd messagebus

A rule similar to the one below can be used in pf.conf(5) to pass incoming
avahi (multicast) traffic:

    
    
      pass proto udp from any to 224.0.0.251 port mdns allow-opts

## Cygwin

MATE is available in the [official Cygwin distribution](https://cygwin.com/);
install the `mate-session-manager` package and its
dependencies with Cygwin setup.

# Source code tarballs

You can download MATE source code tarballs on pub.mate-desktop.org:
<https://pub.mate-desktop.org/releases/>

# GIT Repository

Get from <https://github.com/mate-desktop/>. See [Building](./building.md) for more information.
