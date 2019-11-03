# Replace Unity by MATE

This is a procedure to install MATE desktop on Ubuntu GNU/Linux, and leave
MATE collection applications instead of Unity/GNOME ones.

  * 1\. Follow the steps to register the repositories

  * 2\. Install packages (command to avoid dialogs):

```bash
sudo apt-get install --no-install-recommends mate-desktop-environment mate-desktop-environment-extra mate-archive-keyring caja-gksu caja-sendto mate-indicator-applet mate-media-gstreamer mate-icon-theme-faenza
```

  * 3\. Remove substituted packages:
    
        sudo apt-get remove gcalctool gnome-screenshot gedit file-roller eog gnome-system-monitor gnome-system-log baobab gnome-terminal gnome-applets gnome-media gnome-power-manager gnome-screensaver

  * 4\. Set default desktop for new users: 
    
        sudo /usr/lib/lightdm/lightdm-set-defaults -s mate

  * 5\. Change and fix default application for some MIME (file) types:** 
    
        # Folders:
    xdg-mime default caja-folder-handler.desktop inode/directory
    # SSH sites:
    xdg-mime default caja-folder-handler.desktop x-scheme-handler/ssh
    # FTP sites:
    xdg-mime default caja-folder-handler.desktop x-scheme-handler/ftp
    # Images:
    xdg-mime default eom.desktop image/bmp
    xdg-mime default eom.desktop image/gif
    xdg-mime default eom.desktop image/jpeg
    xdg-mime default eom.desktop image/x-pcx
    xdg-mime default eom.desktop image/png
    xdg-mime default eom.desktop image/tiff
    # Plain text:
    xdg-mime default pluma.desktop text/plain
    xdg-mime default pluma.desktop text/x-log
    xdg-mime default pluma.desktop application/x-perl
    xdg-mime default pluma.desktop application/javascript
    xdg-mime default pluma.desktop application/rdf+xml
    # If you want for Wine plain text files:
    xdg-mime default pluma.desktop application/x-wine-extension-ini
    xdg-mime default pluma.desktop application/x-wine-extension-vbs
    xdg-mime default pluma.desktop text/x-csrc
    xdg-mime default pluma.desktop application/x-wine-extension-inf
    # PDF:
    xdg-mime default atril.desktop application/pdf

  * 6\. Set new default terminal emulator: 
    
        update-alternatives --install "$(which x-terminal-emulator)" x-terminal-emulator "$(which mate-terminal)" 30
    update-alternatives --set x-terminal-emulator "$(which mate-terminal)"

  * 7\. Close desktop session and login with MATE Desktop.

