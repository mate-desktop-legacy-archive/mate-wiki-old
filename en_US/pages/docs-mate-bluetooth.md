# mate-bluetooth

## Introduction

**mate-bluetooth** is an application that let you manage Bluetooth in the MATE
destkop.

**mate-bluetooth** permits:

  * To send files to your Bluetooth devices, or browse their content.

  * To connect to your devices, like headset or audio gateway.

  * You can add or delete Bluetooth devices, or manage their permissions.

## Bluetooth Applet

The applet is the resident application you can find in the notification
applet, that let you quickly access to the features, like sending files, or
managing your devices.

### Starting Bluetooth Applet

The **mate-bluetooth** applet is started automatically when you log into your
session, and you can find its icon in the notification zone. To launch
manually the applet, open menu _Applications ⇒ Accessories ⇒ Terminal_ and
type **mate-bluetooth-applet**.

To prevent launching of the applet in your desktop, open menu _System ⇒
Preferences ⇒ Session_ and disable _Bluetooth Manager_.

### Turning off your Bluetooth adapter

Disabling your Bluetooth adapter will stop current and all future
communications from and to your Bluetooth adapter. Disabling your Bluetooth
adapter permits to save power of your laptop 's battery, so it'll increase the
autonomy, this is a good idea to disable your Bluetooth device when you don't
use it. Click on the icon of the applet, and choose _Turn Off Bluetooth_ , the
notification icon will become grey.

### Sending files to Bluetooth device

Choose this menu to send a file to a device; a file chooser will appear to
pick up the file to send and you'll have to select the device to send the file
to.

### Browsing Bluetooth device

Choose this menu to browse the device filesystem directly in your file
manager.

### Last used devices

This section displays your paired devices you can connect to.

To connect to the device, click on its name, which will become bolded to
inform you're connect to it.

### Adding a new device

To add a new device (which consist of pairing your adapter with your device),
click on the applet icon, and choose _Setup new device…_. A graphical
assistant will help you in the process of setting up your device.

Don 't forget to set your remote device in discoverable mode before starting
the process, else the wizard won't be able to find it.

The wizard will present the discoverable devices it has found all around. You
can filter out the list of devices by choosing the type of devices you're
looking for.

### Device search in wizard

If your device has a harcoded passkey, choose _Passkey Options…_ , in the new
dialog, choose the passkey to use.

Choose _Forward_ for the pairing step; if you defined a fixed passkey in the
previous step the pairing will occur automatically, else you 'll be presented
a passkey to enter in your device, type it on your device, once done the
devices and your adapter will be paired.

### Preferences

Click on the icon of the applet, and choose _Preferences_ the preferences
dialog will appear.

For more information about preferences, see section Bluetooth Preferences.

## Bluetooth Preferences

The **mate-bluetooth** preference dialog allows you to manage your various
Bluetooth devices or change properties of your Bluetooth adapter(s).

### Preferences dialog

#### Discoverable

When your adapter is set to _Discoverable_ any Bluetooth device around will be
able to see it, and therefore will able to ask pairing.

Bluetooth as other network types implies security risks, so setting your
adapter undiscoverable to other devices is a good thing to do to limit the
possibility of cracking.

This is only useful to set your device discoverable if you plan to pair it
with another device, once it is done, you can untick _Discoverable_.

When your device is undiscoverable, communication with already paired
Bluetooth devices is possible.

#### Adapter friendly name

The friendly name is an alias for the address used to identified each
Bluetooth device much easier to remind.

By default the adapter friendly name is _HOSTNAME-0_ (where _HOSTNAME_ is the
name of your computer), to change it, edit the text entry and set the name you
want. the change will be immediatly effective.

#### Known Devices

_Known devices_ lists the Bluetooth devices you paired and let you manage
them, like deleting them, connect to them or adding new one.

Setup new device, as described in Adding a new device.

#### Connect / Disconnect to a device

#### Device Deletion

Deletion will suppress pairing between the adapter and the device, and no
communication will be allowed. You need to pair them together again if you
want transfer files for instance.

#### Show Bluetooth icon

You can show or hide Bluetooth icon in the panel. See Bluetooth Applet for the
applet features.

If you disable the icon in the panel, only limited set of actions will remain
available.

#### Receive Files

Click on the _Receive Files_ button and the _Personal File Sharing
Preferences_ dialog will appear. You can configure Bluetooth file reception
and sharing there.

This feature is not provided by **mate-bluetooth**. **mate-user-share** must
be installed to use this feature.

## Frequently Asked Questions

_I don 't see how to receive files over Bluetooth on my computer in **mate-
bluetooth** , am I blind?_

File reception is not implemented in **mate-bluetooth** , but in **mate-user-
share** , so you have to install this application to be able to receive files
over Bluetooth. Button explained in the Receive Files is just a launcher of
its configuration dialog.

_I found a bug in **mate-bluetooth** what I can do?_

You should submit a bug report to <https://github.com/mate-desktop/mate-bluetooth/issues>.

## Credits

This manual is based on **gnome-bluetooth** user manual, written by Baptiste
Mille-Mathias..
