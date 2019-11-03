# MateCORBA to DBus

## Info

This step is needed to drop mate-corba and libmatecomponent. Mate-panel,
starting from 1.5.0, is without those components.

  * All mate-panel applets need to be ported to `libmatepanelapplet-4.0` and gsettings.

  * `libmatepanelapplet-2.0` (mateconf/matecorba) and `libmatepanelapplet-3.0` (mateconf/dbus) are removed in mate-panel 1.5.0.

## Guide

  * Factory macro: change `MATE_PANEL_APPLET_MATECOMPONENT_FACTORY` with `MATE_PANEL_APPLET_OUT_PROCESS_FACTORY`. New macro has the same parameters except version that has been removed. Remove the prefix 'OAFIID:MATE_' from the factory name. See the example:

Old macro:

    
    
    MATE_PANEL_APPLET_MATECOMPONENT_FACTORY ("OAFIID:MATE_MateWncklet_Factory",
                                 PANEL_TYPE_APPLET,
                                 "WindowNavigationApplets",
                                 "0",
                                 matewncklet_factory,
                                 NULL)

The new version of the macro should be:

    
    
    MATE_PANEL_APPLET_OUT_PROCESS_FACTORY ("MateWnckletFactory",
                                      PANEL_TYPE_APPLET,
                                      "WindowNavigationApplets",
                                      matewncklet_factory,
                                      NULL)

  * Remove the prefix `OAFIID:MATE_` from the factory method too:

Old factory method:

    
    
    static gboolean
    matewncklet_factory (MatePanelApplet *applet,
    		 const char  *iid,
    		 gpointer     data)
    {
    	gboolean retval = FALSE;
    	static gboolean type_registered = FALSE;
     
    	if (!type_registered) {
    		matewnck_set_client_type (MATEWNCK_CLIENT_TYPE_PAGER);
    		type_registered = TRUE;
    	}
     
    	if (!strcmp (iid, "OAFIID:MATE_WindowMenuApplet"))
    		retval = window_menu_applet_fill (applet);
     
    	else if (!strcmp (iid, "OAFIID:MATE_WorkspaceSwitcherApplet")||
    	         !strcmp (iid, "OAFIID:MATE_PagerApplet"))
    		retval = workspace_switcher_applet_fill (applet);
     
    	else if (!strcmp (iid, "OAFIID:MATE_WindowListApplet") ||
    	         !strcmp (iid, "OAFIID:MATE_TasklistApplet"))
    		retval = window_list_applet_fill (applet);
     
    	else if (!strcmp (iid, "OAFIID:MATE_ShowDesktopApplet"))
    		retval = show_desktop_applet_fill (applet);
     
    	return retval;
    }

The new one it's the same without the `OAFIID:MATE_` prefix

    
    
    static gboolean 
    matewncklet_factory (MatePanelApplet *applet,
                     const char  *iid,
                     gpointer     data)
    {
     	gboolean retval = FALSE;
    	static gboolean type_registered = FALSE;
     
            if (!type_registered) {
                    matewnck_set_client_type (MATEWNCK_CLIENT_TYPE_PAGER);
            	type_registered = TRUE;
            }
     
            if (!strcmp (iid, "WindowMenuApplet"))
                    retval = window_menu_applet_fill (applet);
     
            else if (!strcmp (iid, "WorkspaceSwitcherApplet")||
                     !strcmp (iid, "PagerApplet"))
                    retval = workspace_switcher_applet_fill (applet);
     
    	else if (!strcmp (iid, "WindowListApplet") ||
                     !strcmp (iid, "TasklistApplet"))
    		retval = window_list_applet_fill (applet);
     
    	else if (!strcmp (iid, "ShowDesktopApplet"))
    		retval = show_desktop_applet_fill (applet);
     
    	return retval;
    }

  * Applet menu: the new API uses [GtkAction](http://developer.gnome.org/gtk/2.24/GtkAction.html) to build the menu, so we need to define [GtkActionEntry](http://developer.gnome.org/gtk/2.24/GtkActionGroup.html#GtkActionEntry) instead of MateComponentUIVerb. See the example:

Old menu verbs definition:

    
    
    static const MateComponentUIVerb show_desktop_menu_verbs [] = {
            MATECOMPONENT_UI_UNSAFE_VERB ("ShowDesktopHelp",        display_help_dialog),
            MATECOMPONENT_UI_UNSAFE_VERB ("ShowDesktopAbout",       display_about_dialog),
            MATECOMPONENT_UI_VERB_END
    };

New menu actions definition should be:

    
    
    static const GtkActionEntry show_desktop_menu_actions [] = {
            { "ShowDesktopHelp", GTK_STOCK_HELP, N_("_Help"),
              NULL, NULL,
              G_CALLBACK (display_help_dialog) },
            { "ShowDesktopAbout", GTK_STOCK_ABOUT, N_("_About"),
              NULL, NULL,
              G_CALLBACK (display_about_dialog) }
    };

If you have toggle action you need to define
[GtkToggleActionEntry](http://developer.gnome.org/gtk/2.24/GtkActionGroup.html#GtkToggleActionEntry)
actions too:

    
    
    static const GtkToggleActionEntry toggle_actions[] = {
        { "Mute", NULL, N_("Mu_te"),
          NULL, NULL,
          G_CALLBACK (cb_verb), FALSE }
      };

  * Callbacks should be changed to match the [GtkAction](http://developer.gnome.org/gtk/2.24/GtkAction.html) callback prototype:

Old callback:

    
    
    static void
    display_help_dialog (MateComponentUIComponent *uic,
                         ShowDesktopData   *sdd,
                         const gchar       *verbname)

The new version would be:

    
    
    static void
    display_help_dialog (GtkAction       *action,
                         ShowDesktopData *sdd)


  * To setup the menu we use `mate_panel_applet_setup_menu_from_file()` which has a new API. It takes the file with the ui definitions and a [GtkActionGroup](http://developer.gnome.org/gtk/2.24/GtkActionGroup.html), so we need to build a new action group first:

Old code for setting up the menu:

    
    
    mate_panel_applet_setup_menu_from_file (MATE_PANEL_APPLET (sdd->applet),
                                       NULL,
                                       "MATE_ShowDesktopApplet.xml",
                                       NULL,
                                       show_desktop_menu_verbs,
                                       sdd);

The new code should be something like:

    
    
    action_group = gtk_action_group_new ("ShowDesktop Applet Actions");
    gtk_action_group_set_translation_domain (action_group, GETTEXT_PACKAGE);
    gtk_action_group_add_actions (action_group,
                                  show_desktop_menu_actions,
                                  G_N_ELEMENTS (show_desktop_menu_actions),
                                  sdd);
    ui_path = g_build_filename (MATEWNCK_MENU_UI_DIR, "showdesktop-menu.xml", NULL);
    mate_panel_applet_setup_menu_from_file (MATE_PANEL_APPLET (sdd->applet),
                                       ui_path, action_group);
    g_free (ui_path);
    g_object_unref (action_group);

If the applet has toggle actions you have to call

[gtk_action_group_add_toggle_actions()](http://developer.gnome.org/gtk/2.24/GtkActionGroup.html#gtk-action-group-add-toggle-actions) to add toggle actions to the action group:

    
    
    gtk_action_group_add_toggle_actions (action_group,
                                           toggle_actions,
                                           G_N_ELEMENTS (toggle_actions),
                                           applet);

If you need to change any property of a menu item, for example when applet is
locked down, you can just get the action from the action group:

    
    
    if (mate_panel_applet_get_locked_down (MATE_PANEL_APPLET (tasklist->applet))) {
            GtkAction *action;
    
    	action = gtk_action_group_get_action (action_group, "TasklistPreferences");
            gtk_action_set_visible (action, FALSE);
    }

### Menu UI XML file

The new menu xml file is a normal
[GtkUIManager](http://developer.gnome.org/gtk/2.24/GtkUIManager.html) ui file. It should
contain just menutiem entries and separators. See the example:

    
    
    <menuitem name="Mute"     action="Mute" />
    <menuitem name="RunMixer" action="RunMixer" />
    <separator/>
    <menuitem name="Pref"     action="Pref" />
    <menuitem name="Help"     action="Help" />
    <menuitem name="About"    action="About" />

### Panel Applet File

It's a key file with information about the applet. Most of the information can
be copied from the old .server.in.in file. It must contain a group called
'Applet Factory' with information about the factory and one group for every
applet with the applet identifier as the name of the group.

Applet Factory group keys:

  * Id: it's the name of the factory, it must be the same name used as the first parameter in MATE_PANEL_APPLET_OUT_PROCESS_FACTORY macro

  * Location: the path to the applet executable

  * Name: factory name (it can be copy-pasted from the .server.in.in file)

  * Description: factory description (it can be copy-pasted from the .server.in.in file)

Applet groups keys:

  * Name: applet name

  * Description: applet description

  * Icon: applet icon name

  * MateComponentId: old matecomponent identifier, for compatibility. It allows the panel to load applets using the current configuration. It can be a single string or a list of strings in case of applets with more than one identifier.

  * Bugzilla fields

All of these keys can be copy-pasted from the .server.in.in file. See the
example:

org.mate.panel.MateWncklet.mate-panel-applet.in.in

    
    
    [Applet Factory]
    Id=MateWnckletFactory
    Location=@LOCATION@
    _Name=Window Navigation Applet Factory
    _Description=Factory for the window navigation related applets
     
    [WindowMenuApplet]
    _Name=Window Selector
    _Description=Switch between open windows using a menu
    Icon=mate-panel-window-menu
    MateComponentId=OAFIID:MATE_WindowMenuApplet
    X-MATE-Bugzilla-Bugzilla=MATE
    X-MATE-Bugzilla-Product=mate-panel
    X-MATE-Bugzilla-Component=window selector
    X-MATE-Bugzilla-Version=@VERSION@
    X-MATE-Bugzilla-OtherBinaries=matewnck-applet
     
    [WorkspaceSwitcherApplet]
    _Name=Workspace Switcher
    _Description=Switch between workspaces
    Icon=mate-panel-workspace-switcher
    MateComponentId=OAFIID:MATE_WorkspaceSwitcherApplet;OAFIID:MATE_PagerApplet
    X-MATE-Bugzilla-Bugzilla=MATE
    X-MATE-Bugzilla-Product=mate-panel
    X-MATE-Bugzilla-Component=workspace switcher
    X-MATE-Bugzilla-Version=@VERSION@
    X-MATE-Bugzilla-OtherBinaries=matewnck-applet
     
    [WindowListApplet]
    _Name=Window List
    _Description=Switch between open windows using buttons
    Icon=mate-panel-window-list
    MateComponentId=OAFIID:MATE_TasklistApplet;OAFIID:MATE_WindowListApplet
    X-MATE-Bugzilla-Bugzilla=MATE
    X-MATE-Bugzilla-Product=mate-panel
    X-MATE-Bugzilla-Component=window list
    X-MATE-Bugzilla-Version=@VERSION@
    X-MATE-Bugzilla-OtherBinaries=matewnck-applet
     
    [ShowDesktopApplet]
    _Name=Show Desktop
    _Description=Hide application windows and show the desktop
    Icon=user-desktop
    MateComponentId=OAFIID:MATE_ShowDesktopApplet
    X-MATE-Bugzilla-Bugzilla=MATE
    X-MATE-Bugzilla-Product=mate-panel
    X-MATE-Bugzilla-Component=Show Desktop Button
    X-MATE-Bugzilla-Version=@VERSION@
    X-MATE-Bugzilla-OtherBinaries=matewnck-applet

### D-Bus service file

In addition to the mate-panel-applet file we use a D-Bus service file so that
applets can be started by the session bus. It's a normal D-Bus file

org.mate.panel.applet.MateWnckletFactory.service.in

    
    
    [D-BUS Service]
    Name=org.mate.panel.applet.MateWnckletFactory
    Exec=@LOCATION@

### Build system (configure)

  * Check for libmate-panel-applet-4 in your configure file, and get the directory where .mate-panel-applet files should go from the pkg-config file, with something like:

    
    
    LIBMATE_PANEL_APPLET_DIR=`$PKG_CONFIG --variable=libmate_panel_applet_dir libmatepanelapplet-4.0`

### Build system (Makefile.am)

  * Add the ui xml path to the CFLAGS:

    
    
    -DMATEWNCK_MENU_UI_DIR=\""$(xmluidir)"\" \

This is the macro you use when setting up the applet menu

  * Panel-applet file:

    
    
    appletdir       = $(LIBMATE_PANEL_APPLET_DIR)
    applet_in_files = MATE_MixerApplet.mate-panel-applet.in
    applet_DATA     = $(applet_in_files:.mate-panel-applet.in=.mate-panel-applet)
     
    $(applet_in_files): $(applet_in_files).in Makefile
            $(AM_V_GEN)sed \                                                                                                                                     
                -e "s|\@LIBEXECDIR\@|$(libexecdir)|" \                                                                                                           
                -e "s|\@VERSION\@|$(PACKAGE_VERSION)|" \                                                                                                         
                $< > $@
     
    %.mate-panel-applet: %.mate-panel-applet.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*po) ; $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache

This rule should probably be moved to intltool as something like:

    
    
    INTLTOOL_MATE_PANEL_APPLET_RULE='%.mate-panel-applet: %.mate-panel-applet.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; $(AM_V_GEN) LC_ALL=C $(INTLTOOL_MERGE) -d -u -c $(top_builddir)/po/.intltool-merge-cache $(top_srcdir)/po $< [$]@'

  * D-Bus service file:

    
    
    servicedir       = $(datadir)/dbus-1/services
    service_in_files = org.mate.panel.applet.FishAppletFactory.service.in
    service_DATA     = $(service_in_files:.service.in=.service)
     
    org.mate.panel.applet.FishAppletFactory.service: $(service_in_files)
            $(AM_V_GEN)sed \
                -e "s|\@LOCATION\@|$(APPLET_LOCATION)|" \
                $< > $@

  * Add mate-panel-applet .in.in and service file to EXTRA_DIST and $(applet_DATA) $(applet_DATA).in to CLEANFILES

    
    
    EXTRA_DIST =                                            \
            MATE_MixerApplet.mate-panel-applet.in.in            \
            $(service_in_files)                             \
            $(ui_DATA)                                      \
            $(schemas_in_files)
    CLEANFILES = $(applet_DATA) $(applet_DATA).in $(service_DATA) $(schemas_DATA)

  * Remove all references to matecomponent, matecorba, etc, from configure script. Remove references to .server files and INTLTOOL_SERVER_RULE from Makefile.am and remove .server.in.in file.

## References

  * <https://live.gnome.org/GnomeGoals/AppletsDbusMigration>

