# Caja

**Caja** is the MATE file manager, based on nautilus-2.32.

  * [Report a bug](https://github.com/mate-desktop/caja/issues)

## Extensions

  * caja-gksu

  * caja-image-converter

  * caja-open-terminal

  * caja-sendto

  * caja-share

  * caja-wallpaper

  * caja-xattr-tags

## Development

### Debug

#### Caja and gdb

```bash
    ps aux | grep caja
    gdb caja <caja pid>
```

#### Enable debug log

Caja has a debug logging infrastructure that come from nautilus. If Caja
crashes, it will write a `~/caja-debug-log.txt` file which you can attach to a
bug report. This file contains a log of your last actions, and additional
information which may be useful to debug the problem. You can also send a
SIGUSR1 to Caja to cause it to write the debug log to disk immediately.

A developer may ask you to set up a `~/caja-debug-log.conf` file with this
format:

```
    [debug log]
    max lines = 1000
    enable domains = <list of log domains separated by ";">
```

The available log domains are these:

  * **async** \- to debug asynchronous notifications

  * **GLog** \- only used to get g_debug() messages included in the log; they are excluded by default. Other GLog output is included as it usually consists of important messages.

### Caja internals

```
    |-- ChangeLog                      # what happend (also see svn log)
    |-- INSTALL                        # installation instructions
    |-- MAINTAINERS                    # the people working on Caja
    |-- docs
    |   |-- caja-internals.pdf         # some very old documentation
    |-- eel                            # the eel library of helper functions
    |-- libcaja-extension              # the public API, exposed to the outside world
    |   |-- caja-file-info.c           # exposes Caja's private code-file.c
    |-- libcaja-private                # this is Caja's internals, never exposed
    |   |-- caja-file.c                # one of the most important files
    |-- po                             # translation files
    |-- src                            # main source, lots of dialogs etc.
    |   |-- caja-main.c                # main
    |   |-- file-manager               # file manager views and dialogs
    |       |-- fm-directory-view.c    # base class for directory views
    |       |-- fm-icon-view.c         # icon view
    |       |-- fm-list-view.c         # list view
    |       |-- fm-properties-window.c # file properties dialog
    |-- test                           # tests
```

## Tips

### network & samba share

Caja requires `gvfs-backends` to open the “Network” folder and explore samba
share.

```
    apt-get install gvfs-backends
```

### Hiding partition in Caja ''Devices''.

Modern computers are equiped with sata or scsi controller and drives which
support [hotplugging](https://en.wikipedia.org/wiki/Hot_swapping). This means that for every
hotpluggable disk it's partitions will show under the devices section in the
Caja side-pane. Caja does not govern this and instead asks
[Udisks2](https://www.freedesktop.org/wiki/Software/udisks/) which partitions to
display in `Devices`.

There are situation where you do not want partitions to show in the devices
and just want to hide them. In order to do this we need to tell Udisks2 to
ignore the partition. This is done through setting a udev value for that
partition. The value is `UDISKS_IGNORE`.

Create the following file in `/etc/udev/rules.d/`.

hide-partitions.rules

```
    ACTION!="add|change", GOTO="hide_partition_end"
    SUBSYSTEM!="block", GOTO="hide_partition_end"
    KERNEL=="loop*|ram*", GOTO="hide_partition_end"
    KERNEL=="sdXX", ENV{UDISKS_IGNORE}="True"
    LABEL="hide_partition_end
```

Where it says 'sdXX' put your device that has the partiton. You can repeat
this line multiple time for every partition you want to hide.

On the next reboot the variable will be set and the partition ignored by
Udisks2 and therefore not shown in `Devices`
