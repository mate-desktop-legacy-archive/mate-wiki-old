# Gsettings/dconf

This page give an introduction how to use the gsettings command line tool.

### dconf

Dconf is the backend for GSettings and is used to store the MATE desktop
settings as of version 1.6. It stores for example what background image is set
as wallpaper.

### dconf-editor

Dconf editor is the replacement of mateconf editor. It looks and behaves much
the same as mateconf editor. Below are 2 images for comparison.

mateconf-editor (old)| dconf-editor (new)
---|---
![](./images/mateconf-editor_backround.png)| ![](./images/dconf-editor_background.png)

### Retrieving data from GSettings/dconf

Before we give examples we need to explain that mate and other applications
using GSettings/dconf install a schema. A schema basically is a list of the
available settings for that application. There are two types of schemas,
standard and `relocatable` schemas. Important to understand that for
**relocatable** schemas we need to provide a path on top of the normal schema
name like org.mate.panel.object.

_A big confusion with **relocatable** schemas is that only **changed** keys
show up in dconf and dconf-editor._

In the explanation below I will be using `org.mate.background` for a standard
schema and `org.mate.panel.object:/org/mate/panel/objects/object_0/`
relocatbale schema to show how to use gsettings. For the relocatable schema
object_0 represents the `menu bar` and in the example we will set a custom
icon for it.

To list all the installed schemas run `gsettings list-schemas`:

    
    
    $ gsettings list-schemas
    org.mate.Marco.general
    org.mate.SettingsDaemon.plugins.datetime
    org.mate.background
    .....
    org.gnome.desktop.thumbnailers
    org.gnome.desktop.a11y.keyboard
    org.mate.screensaver

Now that we have a list of the schemas we can look at what keys they provide.
Keys are the actual settings we manipulate. We list them with `gsettings list-
keys <schema name>`.

#### standard schemas

    
    
    $ gsettings list-keys org.mate.background
    background-fade
    color-shading-type
    draw-background
    picture-filename
    picture-opacity
    picture-options
    primary-color
    secondary-color
    show-desktop-icons

We know now what settings (keys) are available in org.mate.background. As the
name key may already suggest keys also have values. We can list the value of
the keys by running `gsettings get <schema> <key>`.

    
    
    $ gsettings get org.mate.background picture-filename
    '/usr/share/backgrounds/mate/abstract/Spring.png'

The above described method applies for all installed schemas and not just to
the ones installed by mate.

You can also list both the keys and their values by running `gsettings list-
recursively <schema>`. Do notice that only 3 types of values are shown below
but it can hold [many types](https://developer.gnome.org/glib/stable/glib-GVariant.html#GVariant). It shows

Value type| examples
---|---
string values| 'vertical-gradient','zoom'
boolean values|  true,false (only 2 allowed values)
number values|  1,2,100
      
    
    $ gsettings list-recursively org.mate.background
    org.mate.background background-fade true
    org.mate.background color-shading-type 'vertical-gradient'
    org.mate.background draw-background true
    org.mate.background picture-filename '/usr/share/backgrounds/mate/abstract/Spring.png'
    org.mate.background picture-opacity 100
    org.mate.background picture-options 'zoom'
    org.mate.background primary-color '#58589191bcbc'
    org.mate.background secondary-color '#3c3c8f8f2525'
    org.mate.background show-desktop-icons true

#### relocatable schemas

As mentioned before relocatable schemas need an aditional path before we can
list and manipulate the keys. Other than the path we treat the the two types
of schemas the same way from the command line.

    
    
    $ gsettings list-recursively org.mate.panel.object:/org/mate/panel/objects/object_0/
    org.mate.panel.object action-type 'none'
    org.mate.panel.object applet-iid 'GNOMEMainMenuFactory::GNOMEMainMenu'
    org.mate.panel.object attached-toplevel-id ''
    org.mate.panel.object custom-icon ''
    org.mate.panel.object has-arrow true
    org.mate.panel.object launcher-location ''
    org.mate.panel.object locked false
    org.mate.panel.object menu-path 'applications:/'
    org.mate.panel.object object-type 'applet'
    org.mate.panel.object panel-right-stick false
    org.mate.panel.object position 728
    org.mate.panel.object tooltip ''
    org.mate.panel.object toplevel-id 'top'
    org.mate.panel.object use-custom-icon false
    org.mate.panel.object use-menu-path false

Notice that we added a colon followed by the path.

### Setting key values

We do this with `gsettings set <schema> <key> <new value>`. So let's try and
set a new background wallpaper.

    
    
    $ gsettings set org.mate.background picture-filename '/usr/share/backgrounds/mate/abstract/Spring.png'
    $ gsettings set org.mate.background picture-filename '/usr/share/backgrounds/mate/desktop/GreenTraditional.jpg'

If everything went well these commands will not return anything. If you do get
output it is likely to be an error. When running these 2 commands you should
notice the desktop background picture changed.

Now let's toggle the compositing manager in Marco on and off.

    
    
    $ gsettings set org.mate.Marco.general compositing-manager false
    $ gsettings set org.mate.Marco.general compositing-manager true

And an example of a **relocatable** schema,

    
    
    $ gsettings set org.mate.panel.object:/org/mate/panel/objects/object_0/ use-custom-icon true
    $ gsettings set org.mate.panel.object:/org/mate/panel/objects/object_0/ custom-icon '/path/to/image'

### Reset key values

Each key in a schema also has a default value. If we have changed the key
value for one reaeon or another and want to revert it to the default we use
`gsettings reset <schema> <key>`. If we want to reset all the keys in the
schema we can use `gsettings reset-recursively <schema>`.

Now let 's reset the background image to the default value.

    
    
    $ gsettings reset org.mate.background picture-filename

And the same for the compositing manager in Marco.

    
    
    $ gsettings reset org.mate.Marco.general compositing-manager

* * *

[Docs](pages/docs.md)
