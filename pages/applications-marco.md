# Marco

**Marco** is the MATE window manager, based on
[Metacity](http://live.gnome.org/Metacity) 2.32.


  * [Report a bug](https://github.com/mate-desktop/marco/issues/)

## Tips

#### Grid is showing on window resize

This is because Marco is running on reduced-resources mode, which is sometimes
triggered on older hardware.

To stop Marco from using reduced-resources mode, run the following command in
a terminal:

```bash
    gsettings set org.mate.Marco.general reduced-resources false
```

Alternatively, the same setting can be set using dconf-editor, under org  > mate > Marco > general.
