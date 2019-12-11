# FAQ

This page holds a list of common issues you may run into with MATE.

## How can I change the menu bar icon?

### 1\. Find your favorite icon

Get the icon you would want to be your custom menu bar icon. You may want to
find a scalabe version of that icon for convenience.

### 2\. Copy to ~/.icons

If the `.icons` directory doesn't yet exist inside your home directory, create
it. (Beware that `.icons` is a hidden directory.) Then copy your custom icon
into it.

### 3\. Use dconf editor to tell mate panel to use the custom icon

Start dconf editor. Then go to `org > mate > panel > menubar`. In the right
window, you see the configuration options for `menubar`. Select “icon-name”.
Click into the “Value” field. Then type in the name of your icon file
_without_ the file extension. Press [ENTER]. Done.

