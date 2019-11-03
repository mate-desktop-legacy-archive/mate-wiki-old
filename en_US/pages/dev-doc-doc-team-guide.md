# MATE Documentation Team

MATE Documentation Team Members

  * stefano-k

  * infirit

  * raveit65

  * flexiondotorg

  * MotoHoss

  * hekel

  * Texou

  * <others tbd> ubuntu folks flexiondotorg has mentioned + anyone else (of course real names as the project progresses)

back to [MATE Development](./dev-doc)

## Project Home (master)

[mate-user-guide](https://github.com/mate-desktop/mate-user-guide)

## Project Tools

  * Yelp

  * Mallard 

    * Hopefully useful links: 

      * <https://wiki.gnome.org/Apps/Yelp/Mallard/Styles>

      * <http://projectmallard.org/about/learn/>

      * <http://projectmallard.org/pipermail/mallard-list/2011-January/000065.html>

      * <http://projectmallard.org/pipermail/mallard-list/2011-June/000094.html>

      * <http://en.flossmanuals.net/introduction-to-mallard/yelp-tools/>

      * <http://blogs.gnome.org/shaunm/files/2012/01/mallardcheatsheet.png>

      * <https://wiki.ubuntu.com/Philbull/MallardIntro>

      * <http://stackoverflow.com/questions/8917342/export-page-to-html>

  * [MATE Development](./dev-doc)

  * git/github

    * Posting patches may be easiest for some.(Dev Mail list?)

    * Wiki &/or dedicated sub-domain should 'mirror' the mate-user-guide.

  * Status page for mate-user-guide: [Mate Documentation Team Status Page](./status-doc-team)

## Project Outline

Item | Value/Detail | Progress/Activity | Log
---|---|---|---
**A:** |  Defaults | Complete |  see thread below and [doc-team-guide](./dev-doc-doc-team-guide)
**Section B:** |  Original Source | Complete |  [doc-team-guide](./dev-doc-doc-team-guide)
**Section C:** |  Organization | In Progress | Log
**Section D:** |  Transifex | TBD | [doc-team-guide](./dev-doc-doc-team-guide)
**Section E:** |  Help Links | In Progress | Log
**Section F:** |  Other Uses | Done | Log
**Section G:** |  Manpages | In Progress | Log

### A: Defaults for creating artwork

  1. ~~default MATE Artwork - (theme, backgrounds,icons, etc)~~

  2. ~~Theme = “Menta”~~

  3. ~~Background = /usr/share/backgrounds/mate/desktop/MATE-Stripes-Light.png horizontal gradient #31633A/#588C4B~~

  4. Page for the main index titled “about-mate-desktop-environment.page” incorporating the wiki.m-d-o/docs about the origins/history of **MATE**

    1. that page needs it 's own “classy && fancy && dsistinct” logo/png for the mouse-over treatment.

### B: Original Source

  1. ~~gnome-user-guide 3.0.0~~ is the first with the creative commons

  2. ~~a few other programs were not ported to mallard til later- that list will need to be completed.~~

  3. ~~**Initial port** minimum of all “GNOME/gnome” references changed to MATE/mate~~

  4. ~~Initial Files in Makefile.am~~

  5. Mate-Extra packages such as atril,pluma etc still need to be cherry picked and converted from gnome sources after_ the changeover to mallard (usually 3.0+).

**_Please feel free to add to this table_** Both links are needed to verify
source is mallard and licensing is correct.

Mate name |  source for mug- git-tree + zips/gz  
---|---  
atril |
[evince](https://git.gnome.org/browse/evince/tree/help/C?id=EVINCE_3_0_0)[EVINCE_3_0_0.zip](https://git.gnome.org/browse/evince/snapshot/EVINCE_3_0_0.zip)  
pluma |  
etc |  
  
**_Strike throughs are now on the status page. If you notice any that are not
please _fix_ it._**![=\)](./images/smileys/icon_smile2.gif)

### C: Organization

  1. ~~Decide best method to divide and conquer workload-~~

  2. ~~<http://wiki.mate-desktop.org/dev-doc> needs editing so there is a link~~

  3. ~~to this page(this document)<http://wiki.mate-desktop.org/dev-doc:doc-team-guide> and it needs a link~~

  4. ~~to this page<http://wiki.mate-desktop.org/status:doc-team> for tracking the status.~~

  5. Mate Doc Team How to contribute examples/explanation

    1. Contents of  <revision tag pkgversion,version,status>

    2. details of existing script

    3. plans for future use

  6. Detailed Work Flow Description(s)

  7. Detailed TODO list on status page

### D: Translations

  * Transifex

    
    
    Not important yet but once it is in relatively good shape Stefano or Infirit
    will upload the resources to transifex. It will be a huge task for translators
    and we need to make sure they do not waste time translating and then
    re-translating the same text.

### E: Mate "help" links

  1. See the status page for more detail

  2. Example is mate-terminal and all places “help:” is called, how links are handled.

  3. lists needed: 

    1. /help/ or /docs/ subdirectories in each application

    2. “help:*” calls/entry for each program application “core” first “extra” next

      1. how to handle the above transition to “mate-user-guide” in each program call e.g.: “yelp: mate-user-guide/mate-terminal”

  4. ~~There is already an ubuntu bug regarding inconsistent help in MATE:<https://bugs.launchpad.net/ubuntu-mate/+bug/1392502>~~

### F: Other Usage

  1. Automate html generation, possibly during the build process.

    1. scripts(autoconf setup?) are needed with yelp-build

      1. manpage links will not work until edited(perhaps a script can fix this.

    2. manpages need to be added/converted to html(currently using **mandoc** for this after it is generated and a link back to the referring page added to them

  2. M-U-G can be used in dokuwiki(wiki.mate-desktop.org)

    1. need to make sure the info already @ [wiki.mate-desktop.org/docs](http://wiki.mate-desktop.org/docs) is incorporated into/covered by the M-U-G

  3. M-U-G can be used in another sub-domain

  4. M-U-G can used as Stand-Alone Documentation/Preview e.g (/usr/share/doc/mate-desktop-environment-docs($core,$extras)/m-u-g/*.html) or whatever

### G: Manpages

  1. Manpages- so they are consistent/current with **MATE** (1.9.+).

    1. need a list of **all** of them.

  2. Completely rewritten so they come under the **MATE** umbrella.

    1. need a list of **all** of them. broken down by the ones that are **MATE** and the ones that need reworked.

  3. Automate use of **mandoc** to convert to html and use with **F** above.

### H: More....

  * More:…
