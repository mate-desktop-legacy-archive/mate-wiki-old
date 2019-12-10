# MATE Sensors Applet

## Introduction

**mate-sensors-applet** provides a convenient way to monitor the health of
your computer in a simple display on your desktop.

A number of sensor interfaces are supported, which should be configured before
adding  &applet; to the panel:

  * ACPI thermal zones, via the Linux kernel ACPI modules</para>

  * Linux kernel i2c modules

    * Via the sysfs filesystem and [i2c](https://secure.netroedge.com/~lm78/kernel26.html) modules distributed directly with the kernel (kernel 2.6)

    * Via the proc filesystem and i2c modules from the [lm_sensors and i2c](https://secure.netroedge.com/~lm78/kernel26.html) packages (kernel 2.4)

    * Via the libsensors library provided with the [lm_sensors](https://secure.netroedge.com/~lm78/kernel26.html) package

  * Linux kernel [i8k](https://people.debian.org/~dz/i8k/00-README) module (for Dell Inspiron Laptops)

  * Linux kernel [ibm-acpi](https://ibm-acpi.sourceforge.net/) module (for IBM Laptops)

  * Linux kernel PowerPC modules therm_adt746x and therm_windtunnel

  * Linux kernel iMac G5 Windfarm module

  * [hddtemp](https://www.guzu.net/linux/hddtemp.php) daemon for reading temperatures from S.M.A.R.T. equipped disks

  * Linux kernel [Omnibook](https://sourceforge.net/projects/omke) module. (for HP and Toshiba Satellite Laptops)

  * NVIDIA graphics cards via libNVCtrl (provided with [nvidia-settings](ftp://download.nvidia.com/XFree86/nvidia-settings/))

To add **mate-sensors-applet** to a panel right-click on the panel to open the
panel pop-up menu, then choose _Add to Panel ⇒ Hardware Sensors Monitor_.

## Usage

When you add **mate-sensors-applet** to a panel for the first time, the applet
will search for any available sensors to monitor, and will display a sensible
default sensor if found (such as the temperature of the CPU).

Most users will then want to customize the display to their liking, which can
be done via the _Preferences_ menu item

## Preferences

To configure **mate-sensors-applet** , right-click on the applet, then choose
_Preferences_ from the pop-up menu.

The _Preferences_ window contains the following tabbed sections:

  * General Options

  * Sensors

### General Options

#### Display sensors in panel as

This option selects whether to display sensors in the panel with either their
label or icon and their value, or to have no identifier for each sensor and
just display their values, or simply to display the icon for each sensor. A
graph can also be displayed for each sensor, showing the progression of the
sensor value over time.

Default: icon with value

#### Preferred position of sensor values

Sensors can be display with either their value beside their icon / label, or
with the value shown below the icon / label. Default: beside labels / icons.

If there is not enough room in the panel to use the requested position, the
best position to ensure all sensor elements are visible will be used instead.

#### Graph size (pixels)

When displaying sensors as graphs, the size of the graph sets either the width
of the graph (when displayed on either the top or bottom panel) or the height
of the graph (when displayed on the left or right panel).

Default: 42 pixels.

#### Temperature scale

Which scale to use for temperature sensors (Kelvin, Fahrenheit or Celsius are
supported).

Default: Celsius.

#### Update interval

How often to update the values of each sensor shown within the panel.

Default: 2 seconds.

#### Display notifications

If enabled,  &applet; will display notifications to the user when alarm
conditions occur.

Default: Enabled.

Alarms for individual sensors must also be enabled.

### Sensors

The Sensors tab within the preferences window provides the options for
configuring each individual sensor. Each sensor is listed under its specific
interface, along with:

  * A fixed ID to identify the sensor within its interface.

  * A user selectable icon to identify the sensor within the panel.

  * A user editable label to identify the sensor within the panel.

  * A check-box to allow the user to enable / disable monitoring and display of the sensor within the panel.

The _Properties_ button allows a specific sensor to be more finely configured,
providing a separate window box for this purpose.

#### Sensor Properties

Each sensor can be configured with a number of options, including the
possibility to scale the sensor value, and to execute an alarm if a certain
low or high value is reached. The sensor icon can also be selected if
required. The high and low values are used to scale the graph display, as well
as set the color for the thermometer displayed within the icons of temperature
sensors.

The sensor value can be scaled in a linear fashion by allowing the user to
specify a multiplier and offset for each sensor. As each sensor value is read,
it is first multiplied by the  'multiplier' and summed with the 'offset' to
produce the final value.

##### Sensor value multiplier

This option allows the user to specify the multiplier of the sensor value.

Default: 1.0

##### Sensor value offset

This option allows the user to specify the offset for the sensor value.

Default: 0.0

##### Sensor low value

The value at which to trigger an alarm if the sensor drops below this value.
This value is also used to scale the display of the graph and temperature
icons.

Default: dependent on sensor type

##### Sensor high value

The value at which to trigger an alarm if the sensor rises above this value.
This value is also used to scale the display of the graph and temperature
icons.

Default: dependent on sensor type

##### Enable alarm

This option allows the user to enable alarm monitoring for this sensor. When
the sensor value rises above, or drops below it's high or low values, the
alarm condition will occur. This will display a notification to the user (if
enabled), and execute the appropriate Alarm Command every Alarm repeat
interval seconds.

Default: disabled

Alarms will only execute for active sensors

##### Alarm repeat interval (secs)

How often to execute the alarm command while the alarm condition is met. A
value of 0 specifies to execute the alarm once only when the alarm condition
occurs.

Default: 0 seconds

If notifications are also enabled, a notification will be displayed each time
the alarm is executed as well to notify the user that the alarm condition has
occurred.

##### High alarm command

The command to be executed at each repeat interval when the sensor value is
equal to or above the upper limit.

Default: none

##### Low alarm command

The command to be executed at each repeat interval when the sensor value is
equal to or below the lower limit.

Default: none

##### Play a sound when the alarm occurs

You can play a sound when the alarm occurs by using the command `esdplay`
which should be available as part of the standard MATE installation. (Note: If
this does not work, you could also try `aplay` which is the default ALSA sound
player).

    
    
    esdplay /usr/share/sounds/gnibbles/gobble.wav

##### Pop-up a window to notify that the alarm has occurred

The program `matedialog` can be used to create dialog boxes to be displayed on
the users current display, and can thus be used to create pop-up style
notifications that the alarm has occurred.

    
    
    matedialog --warning --title="Sensor Alarm" --text="Sensor Alarm occurred"

For more information regarding MateDialog please consult the MateDialog
documentation.

##### Combine multiple commands into one alarm command

Multiple commands can be executed one after the other using the ”`&&`”
construct to separate them. To play a sound and pop-up a dialog via MateDialog
the follow command can be used:

    
    
    esdplay /usr/share/sounds/gnibbles/gobble.wav && matedialog --warning --title="Sensor Alarm" --text="Sensor Alarm occurred"

##### Sensor icon

Provides a list of available icons to allow the user to select one to
represent this sensor.

##### Graph color

The color to use to display the graph for the sensor.

To accurately display graphs both the high and low values for the sensor need
to be set correctly.

#### Advanced Options

There are a number of advanced options which can be set to customize the
display of sensors within the panel, which are set using the MateConf system.

##### Font Size

The font size for labels and values is normally derived from the standard
Application Font size of the MATE Desktop, however this can be overridden.
This is done by setting the value of the parameter `/apps/sensors-applet/font-
size` within the user's MateConf database. This can be achieved by the
following command, where the font size is specified as the last parameter, and
in this case is set to _10_ :

    
    
    mateconftool-2 -s /apps/sensors-applet/font-size -t int 10

To reset the value so that the default font size is not overridden, a font
size of _0_ should be set.

##### Hide Units

The units for sensor values can also be hidden if desired by setting the
boolean value `/apps/sensors-applet/hide-units` within the user's MateConf
database. This can be achieved by the following command, where the value is
specified as either _true_ or _false_ and is specified as the last parameter.
In this case is the units will be hidden (the value is set to _true_ ):

    
    
    mateconftool-2 -s /apps/sensors-applet/hide-units -t bool true

These values can also be set using the [Configuration Editor].

## About

**mate-sensors-applet** was written by Alex Murray.

* * *

[Docs](pages/docs.md)
