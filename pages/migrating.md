# Migrating

As of version 1.1.x (2011.12.08) config files are stored in ~/.config/mate to
avoid conflicts with Gnome 3. If you are using an older version of Mate
(1.0.x), you may find the files in ~/.mate2.

## Applications

See the complete list at [Applications](./applications).

Some applications that have not changed:

libsoup-gnome

totem

gnote

## Nautilus

### Migrating scripts

This is the easy part. Move all scripts from _~/.gnome2/nautilus-scripts/_ to
_~/.config/mate/caja-scripts/_

Now edit each text file, and replace _NAUTILUS_ to _CAJA_.

Examples:

    
    
    NAUTILUS_SCRIPT_SELECTED_FILE_PATHS to CAJA_SCRIPT_SELECTED_FILE_PATHS
    NAUTILUS_SCRIPT_SELECTED_URIS to CAJA_SCRIPT_SELECTED_URIS
    NAUTILUS_SCRIPT_CURRENT_URI to CAJA_SCRIPT_CURRENT_URI
    NAUTILUS_SCRIPT_WINDOW_GEOMETRY to CAJA_SCRIPT_WINDOW_GEOMETRY
    NAUTILUS_SCRIPT_NEXT_PANE_SELECTED_FILE_PATHS to CAJA_SCRIPT_NEXT_PANE_SELECTED_FILE_PATHS
    NAUTILUS_SCRIPT_NEXT_PANE_SELECTED_URIS to CAJA_SCRIPT_NEXT_PANE_SELECTED_URIS
    NAUTILUS_SCRIPT_NEXT_PANE_CURRENT_URI to CAJA_SCRIPT_NEXT_PANE_CURRENT_URI

### Migrating themes

Migrating themes is easy. Just rename all widgets _NautilusWidgetExample_ to
_CajaWidgetExample_. This is just an example.

_Tip: With Geany you can press CTRL+H and replace all text from the current
opened document._

### Migrating extensions

Migrating extensions may not be so easy. If you are lucky, you can just rename
some text to get a quick working version.

This is a list of text to replace: gconf → mateconf gnome → mate orbit → corba
nautilus → caja

Please, check the headers (if the code is in C) for the correct name of files
and functions.

## Compiz

It looks like it works fine with Emerald. But there are missing a MATE plugins
for global hotkeys, etc. We are currently experiencing some issues with Compiz
and MATE.

## openbox

Seems to work perfectly.

## Other GNOME applications: Nautilus, GNOME Panel, etc.

Now take the version compatible with GNOME 2, and adapt it to MATE. Rename
dependencies and verify that they are correct.

## Quick Port

### Replaced words

This is a list of words that I used to avoid conflicts with GNOME3, and, among
other things, to prevent issues of “deprecation”.

migrate.sh

```bash
     #!/bin/bash
    # Copyright © 2011 Perberos
    #
    # This program is free software; you can redistribute it and/or modify it
    # under the terms of the GNU General Public License as published by the
    # Free Software Foundation; either version 3 of the License, or (at your
    # option) any later version.
    #
    # This program is distributed in the hope that it will be useful, but
    # WITHOUT ANY WARRANTY; without even the implied warranty of
    # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
    # General Public License for more details.
    #
    # You should have received a copy of the GNU General Public License along
    # with this program; if not, write to the Free Software Foundation, Inc.,
    # 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
    # either provide a command line option otherwise src folder will be considered.
    if [ $# -gt 0 ]
    then	
      pkgdir=$1 # the folder where is the code, be carefull
    else
      pkgdir=src
    fi
    #support for space in filename
    IFS=$'\n' 
     
    replaces=(
     
    	'ior-decode-2' 'matecorba-ior-decode-2'
    	'linc-cleanup-sockets' 'matecorba-linc-cleanup-sockets' 
    	'typelib-dump' 'matecorba-typelib-dump'
    	'libname-server-2' 'libname-matecorba-server-2'
     
    	'panel-applet' 'mate-panel-applet'
    	'panelapplet' 'matepanelapplet'
    	'panel_applet' 'mate_panel_applet'
    	'PANEL_APPLET' 'MATE_PANEL_APPLET'
    	'PanelApplet' 'MatePanelApplet'
     
    	'mate-mate-panel-applet' 'mate-panel-applet'
    	'matematepanelapplet' 'matepanelapplet'
    	'mate_mate_panel_applet' 'mate_panel_applet'
    	'MATE_MATE_PANEL_APPLET' 'MATE_PANEL_APPLET'
    	'MateMatePanelApplet' 'MatePanelApplet'
     
    	'gnome' 'mate'
    	'GNOME' 'MATE'
    	'Gnome' 'Mate'
     
    	'Metacity' 'Marco'
    	'metacity' 'marco'
    	'METACITY' 'MARCO'
     
    	'Nautilus' 'Caja'
    	'nautilus' 'caja'
    	'NAUTILUS' 'CAJA'
     
    	'Zenity' 'MateDialog'
    	'zenity' 'matedialog'
    	'ZENITY' 'MATEDIALOG'
     
    	'MATE|Utilities' 'GNOME|Utilities'
    	'MATE|Desktop' 'GNOME|Desktop'
    	'MATE|Applets' 'GNOME|Applets'
    	'MATE|Applications' 'GNOME|Applications'
    	'MATE|Multimedia' 'GNOME|Multimedia'
     
    	'libnotify' 'libmatenotify'
    	'LIBNOTIFY' 'LIBMATENOTIFY'
    	'Libnotify' 'Libmatenotify'
     
    	'bonobo' 'matecomponent'
    	'Bonobo' 'MateComponent'
    	'BONOBO' 'MATECOMPONENT'
    	'bonoboui' 'matecomponentui'
    	'BONOBOUI' 'MATECOMPONENTUI'
     
    	'gconf' 'mateconf'
    	'GConf' 'MateConf'
    	'GCONF' 'MATECONF'
     
    	'pkmateconfig' 'pkgconfig'
    	'PKMATECONFIG' 'PKGCONFIG'
     
    	'gweather' 'mateweather'
    	'GWeather' 'MateWeather'
    	'GWEATHER' 'MATEWEATHER'
     
    	'ORBit' 'MateCORBA'
    	'orbit' 'matecorba'
    	'ORBIT' 'MATECORBA'
     
    	'panel-applet' 'mate-panel-applet'
    	'panelapplet' 'matepanelapplet'
    	'panel_applet' 'mate_panel_applet'
    	'PANEL_APPLET' 'MATE_PANEL_APPLET'
    	'PanelApplet' 'MatePanelApplet'
     
    	# mistakes
    	'mate-mate-panel-applet' 'mate-panel-applet'
    	'matematepanelapplet' 'matepanelapplet'
    	'mate_mate_panel_applet' 'mate_panel_applet'
    	'MATE_MATE_PANEL_APPLET' 'MATE_PANEL_APPLET'
    	'MateMatePanelApplet' 'MatePanelApplet'
     
    	'soup-mate' 'soup-gnome'
    	'SOUP_TYPE_MATE_FEATURES_2_26' 'SOUP_TYPE_GNOME_FEATURES_2_26'
    	'mateconfaudiosink' 'gconfaudiosink'
    	'mateconfvideosink' 'gconfvideosink'
     
    	'TAMATECONFIG' 'TAGCONFIG'
     
    	# GNOME Keyboard
    	'gkbd' 'matekbd'
    	'Gkbd' 'Matekbd'
    	'GKBD' 'MATEKBD'
     
     
    	# GMenu
    	'GMenu' 'MateMenu'
    	'gmenu' 'matemenu'
    	'GMENU' 'MATEMENU'
     
    	# polkit
    	'polkitgtk' 'polkitgtkmate'
    	'polkit-gtk' 'polkit-gtk-mate'
    	'PolkitGtk' 'PolkitGtkMate'
    	'POLKITGTK' 'POLKITGTKMATE'
    	'POLKIT_GTK' 'POLKIT_GTK_MATE'
    	'polkit_gtk' 'polkit_gtk_mate'
     
    	'polkit_gtk_mate_mate' 'polkit_gtk_mate'
    	'polkitgtkmatemate' 'polkitgtkmate'
    	'PolkitGtkMateMate' 'PolkitGtkMate'
    	'POLKITGTKMATEMATE' 'POLKITGTKMATE'
    	'POLKIT_GTK_MATE_MATE' 'POLKIT_GTK_MATE'
    	'polkit-gtk-mate-mate' 'polkit-gtk-mate'
     
    	# GDM
    	'gdm' 'mdm'
    	'Gdm' 'Mdm'
    	'GDM' 'MDM'
     
     
    	# Glib Deprecated
    	'G_CONST_RETURN' 'const'
     
    	# Eye of GNOME
    	'eog' 'eom' # only on the exe generated name
     
    	# gedit
    	'gedit' 'pluma'
    	'GEDIT' 'PLUMA'
    	'Gedit' 'Pluma'
     
     
    	# evince
    	'EVINCE' 'ATRIL'
    	'evince' 'atril'
    	'Evince' 'Atril'
    )
     
    #
    # rename files and folders
    #
    dirs=$(find "$pkgdir/" -type d | sed "s|^${pkgdir}/||")
    # for revert the order of folders, so the rename is safe
    revertdirs=
     
    for dirsname in ${dirs}; do
    	revertdirs="$dirsname $revertdirs"
    done
     
    # directory mv
    for dirsname in ${revertdirs}; do
    	oldname=`basename $dirsname`
    	newname=$oldname
     
    	for index in $(seq 0 2 $((${#replaces[@]} - 1))); do
    		newname=${newname/${replaces[$index]}/${replaces[$index + 1]}}
    	done
     
    	if [ $oldname != $newname ]; then
    		echo "renaming folder $oldname to $newname"
     
    		path=`dirname "$pkgdir/$dirsname"`
     
    		retval=`mv "$path/$oldname" "$path/$newname"`
    	fi
    done
     
    #
    # rename files
    #
    files=$(find "$pkgdir/" -type f | sed "s|^${pkgdir}/||")
    # files mv
    for filename in ${files}; do
    	oldname=`basename $filename`
    	newname=$oldname
     
    	for index in $(seq 0 2 $((${#replaces[@]} - 1))); do
    		newname=${newname/${replaces[$index]}/${replaces[$index + 1]}}
    	done
     
    	if [ $oldname != $newname ]; then
    		echo "renaming file $oldname to $newname"
     
    		path=`dirname "$pkgdir/$filename"`
     
    		retval=`mv "$path/$oldname" "$path/$newname"`
    	fi
    done
     
    #
    # rename file contents
    #
    files=$(find "$pkgdir/" -type f | sed "s|^${pkgdir}/||")
     
    for filename in ${files}; do
    	datacontent=`cat "$pkgdir/$filename"`
    	datacontentold=$datacontent
    	for index in $(seq 0 2 $((${#replaces[@]} - 1))); do
    		#sed -i "s/${replaces[$index]}/${replaces[$index + 1]}/g" "$pkgdir/$filename"
    		datacontent=${datacontent//${replaces[$index]}/${replaces[$index + 1]}}
    	done
     
    	if [ "$datacontentold" != "$datacontent" ]; then
    		echo "saving $filename"
    		echo "$datacontent" > "$pkgdir/$filename"
    	fi
    done
```
