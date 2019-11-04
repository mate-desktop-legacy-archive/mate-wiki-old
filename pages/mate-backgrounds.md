# mate-backgrounds

## Package requirements

  * intltool >= 0.35.0

## Building

`build-mate-backgrounds.sh`

```bash
    #!/bin/sh
    # Define version
    release="1.1"
    version="1.1.0"
    package="mate-backgrounds"
    # Get
    wget -c https://pub.mate-desktop.org/releases/$release/$package-$version.tar.bz2
    # Extract
    tar xvjf $package-$version.tar.bz2
    # Go to inside folder
    cd $package-$version
    # Configure
    ./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var
    # Compile
    make
    # Install
    sudo make install
```

## How change wallpaper from terminal ?

```
gsettings set org.mate.background picture-filename '/path/to/file.jpg'
```

## Where is wallpaper ?

In /usr/share/backgrounds/mate/nature/ however standard path should be /usr/share/wallpapers/
<https://www.freedesktop.org/wiki/DesktopThemeSpec/>

but

GNOME use /usr/share/backgrounds/

KDE use /usr/share/wallpapers/

**More about paths for wallpapers:**

**Mate**
Here path you can choose in file .xml in /usr/share/mate-background-properties/file.xml

Example:


```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "mate-wp-list.dtd">
<wallpapers>
    <wallpaper deleted="false">
        <name>%{name} 800x600</name>
        <filename>/usr/share/wallpapers/%{name}/contents/images/800x600.jpg</filename>
        <options>zoom</options>
        <artist>Revoluz</artist>
    </wallpaper>
</wallpapers>
```

This file is needed for read wallpapers from paths.

**KDE4**

This example maybe is not good, but I don 't have kde tutorial.

Path: /usr/share/wallpapers/

```
    # tree wallpaper-theme-uplos-bluepoint
    wallpaper-theme-uplos-bluepoint
    ├── contents
    │   ├── images
    │   │   ├── 1024x768.jpg
    │   │   ├── 1280x800.jpg
    │   │   ├── 1440x900.jpg
    │   │   ├── 1680x1050.jpg
    │   │   ├── 1920x1080.jpg
    │   │   ├── 1920x1200.jpg
    │   │   └── 800x600.jpg
    │   └── screenshot.jpg
    └── metadata.desktop


    2 directories, 12 files
```

  
**Xfce4**  
Path: /usr/share/backgrounds/xfce/  
  
**Lxde**  
Path: /usr/share/lxde/wallpapers/  
  
**Enlightenment 19**  
Path: /usr/share/enlightenment/data/backgrounds/  
E19 in default supports .edj files, but with .png picture also will work.  
  
.edj are compiled files  
For unpack:

    
    
     edje_decc file.edj 

  
Example tree after unpack:

    
    
    $ tree Windy_Palm
    Windy_Palm
    ├── build.sh
    ├── e_bgdlg_new.edc-tmp-tYJf3v
    └── Windy_Palm.jpg
    
    0 directories, 3 files

  
For pack:

    
    
    cd Windy_Palm
    ./build.sh

  
  

_Last edit: Fri Sep 23 2016_

