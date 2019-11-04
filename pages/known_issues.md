# Known issues

## Panels disappear with murrine themes

**Distributions:**

![](./media/distros-ubuntu.png)

**Solution:**

The fix is present in Ubuntu Precise and in Linux Mint Lisa. In Oneiric, you
can change the GTK theme (right click on desktop ⇒ change background to open
the preferences window), or download the fixed GTK debs from Linux Mint
repository [here](https://packages.linuxmint.com/pool/upstream/g/gtk+2.0/) and install them
manyally with `dpkg`.

## QT apps not styled

**Distributions:**

![](./media/distros-ubuntu.png)

**Solution:**

     sudo apt-get install qt4-qtconfig

and set _GTK+_ as  GUI style under _System ⇒ Preferences ⇒ QT4 Settings_.

Here 's some extra, if you wish to work on resolving this problem:

  * [Bugzilla #702493](https://bugzilla.redhat.com/show_bug.cgi?id=702493)

  * [QTBUG-5545](https://bugreports.qt-project.org/browse/QTBUG-5545)

  * [qt/src/gui/styles/qgtkstyle_p.cpp](https://qt.gitorious.org/qt/qt/blobs/72c91efce8ea1cb5daf9a6f48d19b414fe4e6d7a/src/gui/styles/qgtkstyle_p.cpp#line680) source where GTK styles are read, looks only deprecated GConf

For the icon theme (in particular the cursor) to be applied in QT apps, it may
not be enough to use qtconfig. You might need to create the file
~/.icons/default/index.theme and paste in it:

    
    
    [Icon Theme]
    Inherits=mate

## Caja doesn't use the the right font color in iconview with dark themes

If a dark theme with a dark background for caja is selected, caja opens with
the wrong fontcolor in caja-view. Fontcolor is black instead of white. This
issue is reported here: [#81](https://github.com/mate-desktop/caja/issues/81).

**Solution:**

As a workaround you can set the background color under  'backgrounds/emblems'
in 'edit menu' for caja-view.

  1. Open backgrounds/emblems

  2. Choose color tap

  3. Click on 'add a new color'

  4. Use the color picker to select the color from caja-view window part

  5. Save the color

  6. Drag the new custom color into caja.

Now caja opens everytime with the right fontcolor in caja-view.

