# Replace mate-doc-utils with yelp-tools

<https://wiki.gnome.org/GnomeGoals/NewDocumentationInfrastructure>

Quick and dirty script to be run from _within_ the **help** or **doc**
directory. You have to give it the docbook file which needs to be rename to
index.docbook.

```bash
    #! /bin/bash

    sed -i '/mate-doc-utils.make/d' Makefile.am
    sed -i 's/dist-hook: doc-dist-hook/@YELP_HELP_RULES@/' Makefile.am
    sed -i 's/DOC_MODULE/HELP_ID/' Makefile.am
    sed -i 's/DOC_ENTITIES = /HELP_FILES = index.docbook /' Makefile.am
    sed -i 's/DOC_FIGURES/HELP_MEDIA/' Makefile.am
    sed -i 's/DOC_LINGUAS/HELP_LINGUAS/' Makefile.am

    for f in `grep -R "ghelp:" -l`;do sed -i 's/ghelp:/help:/g' ${f};done

    /usr/bin/git mv $1 C/index.docbook
```

# Warnings for translations

Some translations have warning which will need to be addressed at some point.
Example: `'Warning: Could not merge <lingua> translation for msgid`'

# Current Status

Legend: Yellow is pull request send, not merged yet. Green is merged.

Core Packages |  Status |  LINGUAS xml → po  
---|---|---  
[mate-common](https://github.com/mate-desktop/mate-common) | [Complete](https://github.com/mate-desktop/mate-common/commit/894f62a7af6124c71496c6a4ec30daea582924b9) |  None  
[mate-desktop](https://github.com/mate-desktop/mate-desktop) | [Complete](https://github.com/mate-desktop/mate-desktop/commit/ca0a6b583480b07d13e98ebcb7105dfb344367c2) |  None  
[libmatekbd](https://github.com/mate-desktop/libmatekbd) |  Not needed |  NA  
[mate-icon-theme](https://github.com/mate-desktop/mate-icon-theme) |  Not needed |  NA  
[mate-dialogs](https://github.com/mate-desktop/mate-dialogs) | [Complete](https://github.com/mate-desktop/mate-dialogs/commit/af72da25d0e24a716fcf493c20d5de3572ef8869) |  None  
[mate-file-manager](https://github.com/mate-desktop/mate-file-manager) | [Complete](https://github.com/mate-desktop/mate-file-manager/commit/3017ed6c4baae9968562ec046cbdf8661fcbe316) (ghelp: → help: only) |  NA  
[mate-polkit](https://github.com/mate-desktop/mate-polkit) |  Not needed |  NA  
[mate-window-manager](https://github.com/mate-desktop/mate-window-manager) | [Complete](https://github.com/mate-desktop/mate-window-manager/commit/f46847b158fb717ab39f8909f4856d39fdc56837) |  None  
[mate-settings-daemon](https://github.com/mate-desktop/mate-settings-daemon) | [Complete](https://github.com/mate-desktop/mate-settings-daemon/commit/8b5c440e65845a58b88dd3f138864dfe1eba94ce) (ghelp: → help: only) |  NA  
[mate-session-manager](https://github.com/mate-desktop/mate-session-manager) | [Complete](https://github.com/mate-desktop/mate-session-manager/commit/f37bbe895ebe09cfa468884973aca490e7a6785e) (ghelp: → help: only) |  NA  
[mate-menus](https://github.com/mate-desktop/mate-menus) |  Not needed |  NA  
[mate-panel](https://github.com/mate-desktop/mate-panel) | [Complete](https://github.com/mate-desktop/mate-panel/commit/e80641d14288a07a0cb0fb5fe80e8cd6ecf6bc20) |  None  
[mate-backgrounds](https://github.com/mate-desktop/mate-backgrounds) |  Not needed |  NA  
[mate-themes](https://github.com/mate-desktop/mate-themes) |  Not needed |  NA  
[mate-notification-daemon](https://github.com/mate-desktop/mate-notification-daemon) |  Not needed |  None  
[mate-image-viewer](https://github.com/mate-desktop/mate-image-viewer) | [Complete](https://github.com/mate-desktop/mate-image-viewer/commit/a9448ccd8ab4c92f806710554eb3965f884960a4) |  None  
[mate-control-center](https://github.com/mate-desktop/mate-control-center) | [Complete](https://github.com/mate-desktop/mate-control-center/commit/e8d72543591c74ba8cc9e7255a77ddb97d1618f0) |  None  
[mate-screensaver](https://github.com/mate-desktop/mate-screensaver) | [Complete](https://github.com/mate-desktop/mate-screensaver/commit/d20f31bef39003a18ac1dc46c66d6d204cf0b949) (ghelp: → help: only) |  None  
[mate-file-archiver](https://github.com/mate-desktop/mate-file-archiver) | [Complete](https://github.com/mate-desktop/mate-file-archiver/commit/472e1e834bc1033c1ec8f0f88250460e138fbf35) |  None  
[mate-media](https://github.com/mate-desktop/mate-media) | [Complete](https://github.com/mate-desktop/mate-media/commit/eac21f7e6072b5c06f3efc1566e7f96fac80652b) |  None  
[mate-power-manager](https://github.com/mate-desktop/mate-power-manager) | [Complete](https://github.com/mate-desktop/mate-power-manager/commit/d9a4a64e962b4ffe70fdfd87e31a1051d0931936) |  None  
[mate-system-monitor](https://github.com/mate-desktop/mate-system-monitor) | [Complete](https://github.com/mate-desktop/mate-system-monitor/commit/82314dfe634a141792a4b274bebb63901730bf98) |  None  
Extra Packages |  Status |  LINGUAS xml → po  
[caja-dropbox](https://github.com/mate-desktop/caja-dropbox) |  Not needed|  NA  
[mate-applets](https://github.com/mate-desktop/mate-applets) | [Complete](https://github.com/mate-desktop/mate-applets/commit/ed0921aa6001db711ef137ba5b97941c7c2a6d80) |  None  
[mate-bluetooth](https://github.com/mate-desktop/mate-bluetooth) |
[Complete](https://github.com/mate-desktop/mate-bluetooth/commit/73231d44e38195eac6308ecfe16b6f8863925705) |  None  
[mate-calc](https://github.com/mate-desktop/mate-calc) | [Complete](https://github.com/mate-desktop/mate-calc/commit/325bd6134efa18700ede8116b5dbdabdf219a269) |  None  
[mate-character-map](https://github.com/mate-desktop/mate-character-map) | [Complete](https://github.com/mate-desktop/mate-character-map/commit/31ceead9dee59450eeb8baa86549dc673adc2e93) | it ja zh_HK zh_TW  
[mate-document-viewer](https://github.com/mate-desktop/mate-document-viewer) | [Complete](https://github.com/mate-desktop/mate-document-viewer/commit/101cf74f0145c0e7f6f7e0425e876709685d291f) |  None  
[mate-file-manager-gksu](https://github.com/mate-desktop/mate-file-manager-gksu) |  Not needed | NA  
[mate-file-manager-image-converter](https://github.com/mate-desktop/mate-file-manager-image-converter) |  Not needed |  NA  
[mate-file-manager-open-terminal](https://github.com/mate-desktop/mate-file-manager-open-terminal) |  Not needed |  NA  
[mate-file-manager-sendto](https://github.com/mate-desktop/mate-file-manager-sendto) |  Not needed |  NA  
[mate-file-manager-share](https://github.com/mate-desktop/mate-file-manager-share) |  Not needed |  NA  
[mate-icon-theme-faenza](https://github.com/mate-desktop/mate-icon-theme-faenza) |  Not needed |  NA  
[mate-indicator-applet](https://github.com/mate-desktop/mate-indicator-applet) |  Not needed |  NA  
[mate-menu-editor](https://github.com/mate-desktop/mate-menu-editor) |  Not needed |  NA  
[mate-netbook](https://github.com/mate-desktop/mate-netbook) |  Not needed |  NA  
[mate-netspeed](https://github.com/mate-desktop/mate-netspeed) | [Complete](https://github.com/mate-desktop/mate-netspeed/commit/25edbc0143807880d5cb962257b90b955b9745cb) |  cs ru es  
[mate-sensors-applet](https://github.com/mate-desktop/mate-sensors-applet) | [Complete](https://github.com/mate-desktop/mate-sensors-applet/commit/b6cc037ac6f5b990f8bbe3745044b45e6228a324) |  None  
[mate-system-tools](https://github.com/mate-desktop/mate-system-tools) | [Complete](https://github.com/mate-desktop/mate-system-tools/commit/b54fd8fe395f9472567a45167d56d7723f0dbe62) |  services, time nl  
[mate-terminal](https://github.com/mate-desktop/mate-terminal) | [Complete](https://github.com/mate-desktop/mate-terminal/commit/69be83e2afbc0d1f2e436434bcb6bdc1cf60260a) |  bg ro ja zh_TW  
[mate-text-editor](https://github.com/mate-desktop/mate-text-editor) | [Complete](https://github.com/mate-desktop/mate-text-editor/commit/1a52ccbfb58145d558ede645728ef2810d1a51ef) |  None  
[mate-user-share](https://github.com/mate-desktop/mate-user-share) |  Not needed |  NA  
[mate-utils](https://github.com/mate-desktop/mate-utils) | [Complete](https://github.com/mate-desktop/mate-utils/commit/7920d644cd2c37d83c1b1305aef9b31dbe8fd3d0) |  None  
[python-caja](https://github.com/mate-desktop/python-caja) |  Not needed |  NA  
