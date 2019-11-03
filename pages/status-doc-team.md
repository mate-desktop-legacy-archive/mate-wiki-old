
We have several projects on our plate (see [doc-team-guide](./dev-doc-doc-team-guide.md)) , this page is where we will track the
progress.
---

# Mate Documentation Team Status Page

**_This page versions should be synced with this page for
now:[status:1.10](./status-1.10)_**

### DocTeam Guide

Item | Value/Detail | Progress/Activity | Log
---|---|---|---
**A** |  Defaults | Complete |  see thread below and [doc-team-guide](./dev-doc-doc-team-guide.md)
_Default_ MATE artwork |  Theme “Menta” | Complete | [discussion](http://ml.mate-desktop.org/pipermail/mate-dev/2014-November/000308.html)
**Section B** |  Original Source | Complete |  [doc-team-guide](./dev-doc-doc-team-guide.md)
**Section C** |  Organization | In Progress | Log
**Section D** |  Transifex | TBD | [doc-team-guide](./dev-doc-doc-team-guide.md)
**Section E** |  Help Links | In Progress | Log
**Section F** |  Other Uses | Done | Log
**Section G** |  Manpages | In Progress | Log

### Status Column Key:

none | stub | incomplete | draft | review | candidate | released | outdated | reserved/golden
---|---|---|---|---|---|---|---|---

Status Summary | revision | status=””
---|---|---
No work needed |  | none
Work needed |  | stub
Initial (im)port |  | incomplete
(im)Port complete |  | draft
All work completed |  | review
Candidate |  | candidate
Released |  | final
Outdated |  | outdated
Reserved/Golden |  | reserved

  1. When a piece of this is ready for release, i.e “rc” Please reserve the “gold”(@#ffe6b9) color in the first table above for the lead dev's to signify it is ok for “production”

  2. The screen-shots in the figures directory need updating with new default information from the doc-team guide page. ~~A list of those needs to be on this page.~~

  3. In the **”../C/“** directory there is a script named `mate-user-guide-check_status.sh`. as of [20141223].

    1. this can be used to track your own working set.

    2. stubs and extra files have been moved to a sub-directory of the templates folder.

      1. As the guide develops the pages that are in those sub-directories ../templates/inc, old and stub will go away(be removed from the repo) to slim it down.

      2. Right now they are there for reference.

  4. Using `yelp –editor-mode` now in the `../C` directory will allow you to see only the things that are in 'draft' status or better.

    1. Those files need double checking for grammatical and spelling errors.

  5. Of course layout and link improvements are needed.

  6. We have a channel specifically for the guide folks @ **freenode/#mate-mug**. If you have any questions,problems,comments,restless fingers… please visit and join the conversation.

## Figures List

This list is up-to-date as of 20121223. Each one of these needs to be redone
per the new default listed in the doc team guide [section A:](./dev-doc-doc-team-guide.md?&#a)

**Background = /usr/share/backgrounds/mate/desktop/MATE-Stripes-Light.png
horizontal gradient #31633A/#588C4B**

mate-desktop / |  Size | Status | Actively Working
---|---|---|---
figures/name |  size |  status |  who
caja.png |  250×230 |  draft |
mate-add-to-panel-rtclick.png |  256×150 |  draft |
mate-caja-default-computer-view.png |  250×200 |  draft |
mate-clock-prefs-general.png |  250×160 |  draft |
mate-control-center.png |  250×160 |  draft |
mate-default-desktop-home.png |  250×200 |  draft |
mate-default-desktop.png |  250×200 |  draft |
mate-default-lower-panel.png |  500×40 |  draft |
mate-default-top-panel.png |  500×40 |  draft |
mate-exit.png |  250×200 |  draft |
mate-logo.png |  11×11 |  draft |
mate-panel-applications.png |  250×200 |  draft |
mate-panel-places.png |  250×200 |  draft |
mate-panel-windowlist.png |  320×200 |  draft |
mate-panel-workspaceswitcher.png |  430×40 |  draft |
mate-yelp-icon-big.png |  24×24 |  draft |
|  |  |

## Source Code File List_all_references_not_prioritized

* _When a piece of this is ready for release, i.e “rc” Please reserve the “gold”(@#ffe6b9) color in the first table above for the lead dev 's to signify it is ok for “production”_ ![:!:](./images/smileys/icon_exclaim.gif)

review |  this list needs verification that I did not miss any links, still have a few more packages to go(extra). 20150128-0204pmCST
---|---

Src file name:@line# |  Verbiage/original |  Verbiage/new |  Status
---|---|---|---
caja/src/file-manager/fm-properties-window.c:5524: | “help:mate-user-guide/goscaja-51” |  |
caja/src/file-manager/fm-directory-view.c:1173: | “help:mate-user-guide/caja-select-pattern” |  |
caja/src/caja-property-browser.c:1643: | “help:mate-user-guide/goscaja-50” | |
caja/src/caja-property-browser.c:1652: | “There was an error displaying help:\n%s”) |  |
caja/src/caja-window-menus.c:583: | “help:mate-user-guide” |  |
caja/src/caja-window-menus.c:584: | “help:mate-user-guide/goscaja-1” |  |
caja/src/caja-window-menus.c:593: | “There was an error displaying help:\n%s”) |  |
caja/src/caja-file-management-properties.c:224: | “help:%s/%s”, helpfile, sect_id); |  |
caja/src/caja-file-management-properties.c:237: | “There was an error displaying help: \n%s”) |  |
caja/src/caja-location-dialog.c:98: | “help:mate-user-guide/caja-open-location” |  |
caja/src/caja-bookmarks-window.c:148: | “help:mate-user-guide/goscaja-36” |  |
caja/src/caja-bookmarks-window.c:158: | “There was an error displaying help: \n%s”) |  |
caja/src/caja-connect-server-dialog.c:710: | “help:mate-user-guide/caja-server-connect” |  |
engrampa/src/gtk-utils.c:775: | “help:engrampa” |  |
eom/src/eom-util.c:54: | “help:eom?%s” |  |
eom/src/eom-util.c:56: | “help:eom”) |  |
mate-applets/cpufreq/src/cpufreq-applet.c:643: | “help:mate-cpufreq-applet” | |
mate-applets/cpufreq/src/cpufreq-prefs.c:360: | “help:mate-cpufreq-applet/cpufreq-applet-prefs” |  |
mate-applets/trashapplet/src/trashapplet.c:397: | “help:mate-trashapplet” |  |
mate-applets/trashapplet/src/trashapplet.c:404: | “There was an error displaying help: %s”) |  |
mate-calc/src/math-window.c:214: | “help:mate-calc” |  |
mate-conf-editor/src/mateconf-editor-window.c:355: | “ghelp:mateconf-editor” | |
mate-conf-editor/src/mateconf-editor-window.c:359: | “Couldn't display help: %s”), error); |  |
mate-control-center/capplets/accessibility/at-properties/main.c:155: | “goscustaccess-11”); |  |
mate-control-center/capplets/appearance/appearance-font.c:660: | “goscustdesk-38”); |  |
mate-control-center/capplets/appearance/appearance-main.c:127: | “goscustdesk-12”); |  |
mate-control-center/capplets/appearance/appearance-main.c:130: | “goscustdesk-7”); |  |
mate-control-center/capplets/appearance/appearance-main.c:133: | “goscustdesk-38”); |  |
mate-control-center/capplets/appearance/appearance-main.c:136: | “goscustuserinter-2”); |  |
mate-control-center/capplets/appearance/appearance-style.c:406: | “goscustdesk-61”); |  |
mate-control-center/capplets/keybindings/mate-keybinding-properties.c:1792: | “goscustdesk-39”); |  |
mate-control-center/capplets/keyboard/mate-keyboard-properties.c:103: | “goscustperiph-2”); |  |
mate-control-center/capplets/mouse/mate-mouse-properties.c:477: | “goscustperiph-5”); |  |
mate-control-center/capplets/network/mate-network-properties.c:232: | “goscustdesk-50”); |  |
mate-control-center/capplets/network/mate-network-properties.c:249: | “goscustdesk-50”); |  |
mate-control-center/capplets/windows/mate-window-properties.c:270: | “goscustdesk-58”); |  |
mate-dialogs/src/util.c:255: | “help:matedialog” |  |
Mate-Extra/mate-video-player/src/totem-object.c:2133 | “ghelp:totem”, |  |
mate-netspeed/src/netspeed.c:801: | “There was an error displaying help:\n%s”) |  |
mate-panel/applets/clock/clock-utils.c:73: | “help:%s/%s”, |  |
mate-panel/applets/clock/clock-utils.c:75: | “help:%s”, |  |
mate-panel/applets/fish/fish.c:156: | “help:%s/%s”, FISH_HELP_DOC, link_id); | |
mate-panel/applets/fish/fish.c:158: | “help:%s”, FISH_HELP_DOC); |  |
mate-panel/applets/notification_area/main.c:71: | “help:%s/%s”, NA_HELP_DOC, “panels-notification-area”); |  |
mate-panel/applets/wncklet/wncklet.c:48: | “help:%s/%s”, doc_id, link_id); | |
mate-panel/applets/wncklet/wncklet.c:50: | “help:%s”, doc_id); |  |
mate-panel/mate-panel/panel-menu-button.c:990: | “mate-user-guide”, “gospanel-37”, NULL); |  |
mate-panel/mate-panel/panel-ditem-editor.c:1476: | “mate-user-guide”, “gospanel-52”, &error)) { |  |
mate-panel/mate-panel/applet.c:263: | “mate-user-guide”, “gospanel-18”, NULL); |  |
mate-panel/mate-panel/panel-run-dialog.c:529: | “mate-user-guide”, “gospanel-23”, NULL); |  |
mate-panel/mate-panel/panel-properties-dialog.c:595: |  help_id = “gospanel-550”; |  |
mate-panel/mate-panel/panel-properties-dialog.c:597: |  help_id = “gospanel-28”; |  |
mate-panel/mate-panel/panel-context-menu.c:59: | “mate-user-guide”, “gospanel-1”, NULL); |  |
mate-panel/mate-panel/panel-action-button.c:347: | “gospanel-21”, |  |
mate-panel/mate-panel/panel-action-button.c:362: | “gospanel-20”, |  |
mate-panel/mate-panel/panel-action-button.c:372: | “gospanel-555”, |  |
mate-panel/mate-panel/panel-action-button.c:382: | “gospanel-554”, |  |
mate-panel/mate-panel/panel-action-button.c:391: | “gospanel-563”, |  |
mate-panel/mate-panel/panel-action-button.c:410: | “gospanel-20” |  |
mate-panel/mate-panel/panel-addto.c:777: | “mate-user-guide”, “gospanel-15”, NULL); |  |
mate-power-manager/applets/brightness/gpm-common.c:176: | “help:mate-power-manager?”, link_id, NULL); |  |
mate-power-manager/applets/brightness/gpm-common.c:178: | “help:mate-power-manager”); |  |
mate-power-manager/applets/inhibit/gpm-common.c:176: | “help:mate-power-manager?”, link_id, NULL); |  |
mate-power-manager/applets/inhibit/gpm-common.c:178: | “help:mate-power-manager”); |  |
mate-power-manager/src/gpm-common.c:138: | “help:mate-power-manager?” |  |
mate-power-manager/src/gpm-common.c:140: | “help:mate-power-manager” |  |
mate-screensaver/src/mate-screensaver-preferences.c:390: | “help:mate-user-guide/prefs-screensaver” |  |
mate-session-manager/capplet/main.c:49: | “help:user-guide?gosstartsession-2” |  |
mate-settings-daemon/plugins/a11y-keyboard/msd-a11y-keyboard-manager.c:439: | “help:user-guide#goscustaccess-6” |  |
mate-settings-daemon/plugins/a11y-keyboard/msd-a11y-keyboard-manager.c:446: | “There was an error displaying help: %s”) |  |
mate-system-monitor/src/procdialogs.cpp:254: | “help:mate-system-monitor/mate-system-monitor-prefs |  |
mate-system-monitor/src/callbacks.cpp:209: | “help:mate-system-monitor” |  |
mate-terminal/src/terminal-accels.c:938: | “mate-terminal-shortcuts”, GTK_WINDOW (editor)); |  |
mate-terminal/src/terminal-app.c:1209: | “mate-terminal-manage-profiles”, GTK_WINDOW (dialog)); |  |
mate-terminal/src/terminal-encoding.c:320: | “mate-terminal-encoding-add”, GTK_WINDOW (window)); |  |
mate-terminal/src/terminal-util.c:157: | “help:mate-terminal#%s” | “help:mate-user-guide/mate-terminal#%s” | [log](https://github.com/mate-desktop/mate-terminal/commit/73634ff66f5cf91f0507e9bf36ce1236fcc9fdfa)
mate-terminal/src/terminal-util.c:161: | “help:mate-terminal” | “help:mate-user-guide/mate-terminal” | [log](https://github.com/mate-desktop/mate-terminal/commit/73634ff66f5cf91f0507e9bf36ce1236fcc9fdfa)
mate-user-share/src/file-share-properties.c:442: | “help:mate-user-share” |  |
mate-utils/baobab/src/baobab-utils.c:510: | “help:%s#%s”, file_name, link_id) : |  |
mate-utils/baobab/src/baobab-utils.c:511: | “help:%s”, file_name); |  |
mate-utils/mate-dictionary/src/gdict-window.c:1239: | “help:mate-dictionary” | |
mate-utils/mate-dictionary/src/gdict-source-dialog.c:473: | “help:mate-dictionary/mate-dictionary-add-source” |  |
mate-utils/mate-dictionary/src/gdict-applet.c:733: | “help:mate-dictionary/mate-dictionary-applet” |  |
mate-utils/mate-dictionary/src/gdict-pref-dialog.c:488: | “help:mate-dictionary/mate-dictionary-preferences” |  |
|  |  |

## Core Packages List

  * _**List of packages that need a ported/converted/NEW “help section”**_

  * _Actively Working column is for a url or name of **who** is working currently on a particular section or part._

  * _When a piece of this is ready for release, i.e “rc” Please reserve the “gold”(@#ffe6b9) color in the first table above for the lead dev 's to signify it is ok for “production”_

mate-desktop / | Version |  user-guide | help entry | Status | Actively Working
---|---|---|---|---|---
[mate-user-guide](https://github.com/mate-desktop/mate-user-guide) |  1.9.0 |  \- |  \- | draft | [MotoHoss](https://github.com/MotoHoss/mate-user-guide)
[mate-common](https://github.com/mate-desktop/mate-common) | 1.9.1 | \- | none |  | review
[mate-desktop](https://github.com/mate-desktop/mate-desktop) | 1.9.4 | \- | none |  | review
[libmatekbd](https://github.com/mate-desktop/libmatekbd) | 1.9.2 | \- | none |  | review
[libmatemixer](https://github.com/mate-desktop/libmatemixer) | 1.9.2 | \- | none |  | review
[libmateweather](https://github.com/mate-desktop/libmateweather) | 1.9.1 | \- | none |  | review
[mate-icon-theme](https://github.com/mate-desktop/mate-icon-theme) | 1.9.1 | \- | none |  | review
[caja](https://github.com/mate-desktop/caja) |  1.9.4 |  |  |  |
[mate-polkit](https://github.com/mate-desktop/mate-polkit) |  1.9.4 |  |  |  |
[marco](https://github.com/mate-desktop/marco) |  1.9.0 |  |  |  |
[mate-settings-daemon](https://github.com/mate-desktop/mate-settings-daemon) |  1.9.6 |  |  |  |
[mate-session-manager](https://github.com/mate-desktop/mate-session-manager) |  1.9.3 |  |  |  |
[mate-menus](https://github.com/mate-desktop/mate-menus) |  1.9.1 |  |  |  |
[mate-panel](https://github.com/mate-desktop/mate-panel) |  1.9.4 |  |  |  |
[mate-backgrounds](https://github.com/mate-desktop/mate-backgrounds) | 1.9.2 | \- | none |  | review
[mate-themes](https://github.com/mate-desktop/mate-themes) | 1.9.2 | \- | none |  | review
[mate-notification-daemon](https://github.com/mate-desktop/mate-notification-daemon) | 1.9.1 | \- | none |  | review
[mate-control-center](https://github.com/mate-desktop/mate-control-center) |  1.9.1 |  |  |  |
[mate-screensaver](https://github.com/mate-desktop/mate-screensaver) |  1.9.2 |  |  |  |
[mate-media](https://github.com/mate-desktop/mate-media) |  1.9.2 |  |  |  |
[mate-power-manager](https://github.com/mate-desktop/mate-power-manager) |  1.9.0 |  |  |  |
[mate-system-monitor](https://github.com/mate-desktop/mate-system-monitor) |  1.9.2 |  |  |  |

## Extra Packages

When a piece of this is ready for release, i.e “rc” Please reserve the
“gold”(@#ffe6b9) color in the table above for the lead dev's to signify it is
ok for “production”

mate-desktop / | Version |  user-guide | help entry | Status | Actively Working
---|---|---|---|---|---
[atril](https://github.com/mate-desktop/atril) |  1.9.2 |  |  |  |
[caja-dropbox](https://github.com/mate-desktop/caja-dropbox) |  |  |  |  |  no “help:*” references
[caja-extensions](https://github.com/mate-desktop/caja-extensions) |  1.9.1 |  |  |  |
[engrampa](https://github.com/mate-desktop/engrampa) |  1.9.2 |  |  |  |
[eom](https://github.com/mate-desktop/eom) |  1.9.1 |  |  |  |
[mate-applets](https://github.com/mate-desktop/mate-applets) |  1.9.0 |  |  |  |
[mate-icon-theme-faenza](https://github.com/mate-desktop/mate-icon-theme-faenza) |  |  |  |  |
[mate-indicator-applet](https://github.com/mate-desktop/mate-indicator-applet) |  1.9.0 |  |  |  |
[mate-netbook](https://github.com/mate-desktop/mate-netbook) |  1.9.0 |  |  |  |
[mate-netspeed](https://github.com/mate-desktop/mate-netspeed) |  1.9.1 |  |  |  |
[mate-sensors-applet](https://github.com/mate-desktop/mate-sensors-applet) |  1.9.0 |  |  |  |
[mate-terminal](https://github.com/mate-desktop/mate-terminal) |  1.9.1 | draft |
[commit](https://github.com/mate-desktop/mate-terminal/commit73634ff66f5cf91f0507e9bf36ce1236fcc9fdfa) |  draft |
[mate-user-share](https://github.com/mate-desktop/mate-user-share) |  1.9.0 |  |  |  |
[mate-utils](https://github.com/mate-desktop/mate-utils) |  1.9.1 |  |  |  |
[mozo](https://github.com/mate-desktop/mozo) |  |  |  |  |
[pluma](https://github.com/mate-desktop/pluma) |  1.9.1 |  |  |  |
[python-caja](https://github.com/mate-desktop/python-caja) |  1.9.0 |  |  |  |

## Merged packages

## Removed Packages

Sometimes our purpose in life is only to serve as a warning to others.

Package | Status
---|---
[mate-calc](https://github.com/mate-desktop/mate-calc) | outdated
[mate-dialogs](https://github.com/mate-desktop/mate-dialogs) | outdated
[mate-system-tools](https://github.com/mate-desktop/mate-system-tools) | outdated

