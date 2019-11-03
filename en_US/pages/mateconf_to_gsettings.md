# MateConf to GSettings

  * [Migration status](./status-1.6)

  * [GNOME Goal: Gconf to GSettings migration](http://live.gnome.org/GnomeGoals/GSettingsMigration)

  * [GSettings porting guide](http://developer.gnome.org/gio/stable/ch29.html)

  * [DConf (main GSettings backend)](http://live.gnome.org/dconf)

## Before you start

Converting individual applications and their settings from MateConf to
GSettings can be done at will. But desktop-wide settings like font or theme
settings often have consumers in multiple modules. Therefore, some
consideration has to go into making sure that all users of a setting are
converted to GSettings at the same time or that the program responsible for
configuring that setting continues to update the value in both places.

It is always a good idea to have a look at how others have handled similar
problems before. An examplaric conversion can be found e.g. in the
[gsettings-tutorial](http://git.gnome.org/browse/gnome-utils/log/?h=gsettings-tutorial) branch of
gnome-utils.

You can see also the [commit](https://github.com/mate-desktop/mate-notification-daemon/commit/2d7e34441f4d33dc1edb5e9871b66b4977069bae)
that migrate mate-notification-daemon to learn how to convert a package to GSettings.

## Conceptual differences

Conceptually, MateConf and GSettings are fairly similar. Both have a concept
of pluggable backends. Both keep information about keys and their types in
schemas. Both have a concept of mandatory values, which lets you implement
lock-down.

There are some differences in the approach to schemas. MateConf installs the
schemas into the database and has API to handle schema information
(mateconf_client_get_default_from_schema(), mateconf_value_get_schema(), etc).
GSettings on the other hand assumes that an application knows its own schemas,
and does not provide API to handle schema information at runtime. GSettings is
also more strict about requiring a schema whenever you want to read or write a
key. To deal with more free-form information that would appear in schema-less
entries in MateConf, GSettings allows for schemas to be 'relocatable'.

One difference in the way applications interact with their settings is that
with MateConf you interact with a tree of settings (ie the keys you pass to
functions when reading or writing values are actually paths with the actual
name of the key as the last element. With GSettings, you create a GSettings
object which has an implicit prefix that determines where the settings get
stored in the global tree of settings, but the keys you pass when reading or
writing values are just the key names, not the full path.

## MateConfClient (and MateConfBridge) API conversion

Most people use MateConf via the high-level MateConfClient API. The
corresponding API is the
[GSettings](http://developer.gnome.org/gio/stable/GSettings.html) object. While not
every MateConfClient function has a direct GSettings equivalent, many do:

MateConfClient |  GSettings  
---|---  
mateconf_client_get_default() |  no direct equivalent, instead you call [g_settings_new()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-new) for the schemas you use  
mateconf_client_set() | [g_settings_set()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-set)  
mateconf_client_get() | [g_settings_get()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get)  
mateconf_client_get_bool() | [g_settings_get_boolean()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get-boolean)  
mateconf_client_set_bool() | [g_settings_set_boolean()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-set-boolean)  
mateconf_client_get_int() | [g_settings_get_int()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get-int)  
mateconf_client_set_int() | [g_settings_set_int()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-set-int)  
mateconf_client_get_float() | [g_settings_get_double()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get-double)  
mateconf_client_set_float() | [g_settings_set_double()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-set-double)  
mateconf_client_get_string() | [g_settings_get_string()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get-string)  
mateconf_client_set_string() | [g_settings_set_string()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-set-string)  
mateconf_client_get_list() |  for string lists, see [g_settings_get_strv()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get-strv), else see [g_settings_get_value()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get-value) and [GVariant](http://developer.gnome.org/glib/stable/glib/glib-GVariant.html#GVariant) API  
mateconf_client_set_list() |  for string lists, see [g_settings_set_strv()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-set-strv), else see [g_settings_set_value()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-set-value) and [GVariant](http://developer.gnome.org/glib/stable/glib/glib-GVariant.html#GVariant) API  
mateconf_entry_get_is_writable() | [g_settings_is_writable()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-is-writable)  
mateconf_client_notify_add() |  not required, the ["changed"](http://developer.gnome.org/gio/stable/GSettings.html#GSettings-changed) signal is emitted automatically  
mateconf_client_add_dir() |  not required, each GSettings instance automatically watches all keys in its path  
MateConfChangeSet | [g_settings_delay()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-delay), [g_settings_apply()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-apply)  
mateconf_client_get_default_from_schema() |  no equivalent, applications are expected to know their schema  
mateconf_client_all_entries() |  no equivalent, applications are expected to know their schema, and GSettings does not allow schema-less entries  
mateconf_client_get_without_default() |  no equivalent  
mateconf_bridge_bind_property() | [g_settings_bind()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-bind)  
mateconf_bridge_bind_property_full() | [g_settings_bind_with_mapping()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-bind-with-mapping)  
 
MateConfBridge was a third-party library that used MateConf to bind an object
property to a particular configuration key. GSettings offers this service
itself.

There is a pattern that is sometimes used for MateConf, where a setting can
have explicit 'value A', explicit 'value B' or 'use the system default'. With
MateConf, 'use the system default' is sometimes implemented by unsetting the
user value.

This is not possible in GSettings, since it does not have API to determine if
a value is the default and does not let you unset values. The recommended way
(and much clearer) way in which this can be implemented in GSettings is to
have a separate 'use-system-default' boolean setting.

## Change notification

MateConf requires you to call **mateconf_client_add_dir()** and
**mateconf_client_notify_add()** to get change notification. With GSettings,
this is not necessary; signals get emitted automatically for every change.

The
["changed"](http://developer.gnome.org/gio/stable/GSettings.html#GSettings-changed) signal is emitted for each changed key.
There is also a ["change-event"](http://developer.gnome.org/gio/stable/GSettings.html#GSettings-change-event) signal that you can handle if you need to see groups of keys that get
changed at the same time.

GSettings also notifies you about changes in writability of keys, with the
["writable-changed"](http://developer.gnome.org/gio/stable/GSettings.html#GSettings-writable-changed) signal
(and the ["writable-change-event"](http://developer.gnome.org/gio/stable/GSettings.html#GSettings-writable-change-event) signal).

## Change sets

MateConf has a a concept of a set of changes which can be applied or reverted
at once: MateConfChangeSet (MateConf doesn 't actually apply changes
atomically, which is one of its shortcomings).

Instead of a separate object to represent a change set, GSettings has a
'delayed-apply' mode, which can be turned on for a GSettings object by calling
[g_settings_delay()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-delay).
In this mode, changes done to the GSettings object are not applied -
they are still visible when calling
[g_settings_get()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-get) on
the same object, but not to other GSettings instances or even other processes.

To apply the pending changes all at once (GSettings does atomicity here), call
[g_settings_apply()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-apply). To revert the pending changes, call
[g_settings_revert()](http://developer.gnome.org/gio/stable/GSettings.html#g-settings-revert) or just drop the reference to the
[GSettings](http://developer.gnome.org/gio/stable/GSettings.html) object.

## Schema conversion

If you are porting your application from MateConf, most likely you already
have a MateConf schema. MateConf comes with a commandline tool mateconf-
gsettings-schema-convert that can help with the task of converting a MateConf
schema into an equivalent GSettings schema. The tool is not perfect and may
need assistence in some cases.

**Example: An example for using mateconf-gsettings-schema-convert**

Running

    
    
    mateconf-gsettings-schema-convert  --mateconf --xml --schema-id "org.mate.font-rendering" --output org.mate.font-rendering.gschema.unindented.xml desktop_mate_font_rendering.schemas
    xmllint --format org.mate.font-rendering.gschema.unindented.xml > org.mate.font-rendering.gschema.xml

on the following _desktop_mate_font_rendering.schemas_ file:

    
    
     <?xml version="1.0"?>
    <mateconfschemafile>
        <schemalist>
            <schema>
                <key>/schemas/desktop/mate/font_rendering/dpi</key>
                <applyto>/desktop/mate/font_rendering/dpi</applyto>
                <owner>mate</owner>
                <type>int</type>
                <default>96</default>
                <locale name="C">
                    <short>DPI</short>
                    <long>The resolution used for converting font sizes to pixel sizes, in dots per inch.</long>
                </locale>
            </schema>
        </schemalist>
    </mateconfschemafile>

produces a _org.mate.font-rendering.gschema.xml_ file with the following
content:

    
    
     <schemalist>
      <schema id="org.mate.font-rendering" path="/desktop/mate/font_rendering/">
        <key name="dpi" type="i">
          <default>96</default>
          <summary>DPI</summary>
          <description>The resolution used for converting font sizes to pixel sizes, in dots per inch.</description>
        </key>
      </schema>
    </schemalist>

GSettings schemas are identified at runtime by their id (as specified in the
XML source file). It is recommended to use a dotted name as schema id, similar
in style to a D-Bus bus name, e.g. “org.mate.SessionManager”. In cases where
the settings are general and not specific to one application, the id should
not use StudlyCaps, e.g. “org.mate.font-rendering”. The filename used for the
XML schema source is immaterial, but schema compiler expects the files to have
the extension _.gschema.xml_. It is recommended to simply use the schema id as
the filename, followed by this extension, e.g.
_org.mate.SessionManager.gschema.xml_.

The  XML source file for your GSettings schema needs to get installed into
_$datadir/glib-2.0/schemas_ , and needs to be compiled into a binary form. At
runtime, GSettings looks for compiled schemas in the _glib-2.0/schemas_
subdirectories of all _XDG_DATA_DIRS_ directories, so if you install your
schema in a different location, you need to set the _XDG_DATA_DIRS_
environment variable appropriately.

Schemas are compiled into binary form by the
[glib-compile-schemas](http://developer.gnome.org/gio/stable/glib-compile-schemas.html) utility.

GIO provides a _glib_compile_schemas_ variable for the schema compiler.

You can ignore all of this by using the provided m4 macros. To do this, add to
your _configure.ac_ :

    
    
    GLIB_GSETTINGS

The corresponding _Makefile.am_ fragment looks like this:

    
    
    # gsettings_SCHEMAS is a list of all the schemas you want to install
     gsettings_SCHEMAS = my.app.gschema.xml
     
    # include the appropriate makefile rules for schema handling
    @GSETTINGS_RULES@

This is not sufficient on its own. You need to mention what the source of the
_my.app.gschema.xml_ file is. If the schema file is distributed directly with
your project 's tarball then a mention in _EXTRA_DIS_ T is appropriate. If the
schema file is generated from another source then you will need the
appropriate rule for that, plus probably an item in _EXTRA_DIST_ for the
source files used by that rule.

One possible pitfall in doing schema conversion is that the default values in
GSettings schemas are parsed by the
[GVariant](http://developer.gnome.org/glib/stable/glib/glib-GVariant.html#GVariant) parser. This means that strings need to include
quotes in the  XML. Also note that the types are now specified as
[GVariant](http://developer.gnome.org/glib/stable/glib/glib-GVariant.html#GVariant) type strings.

    
    
    <type>string</type>
    <default>rgb</default>

becomes

    
    
    <key name="rgba-order" type="s">
      <default>'rgb'</default> <!-- note quotes -->
    </key>

Another possible complication is that MateConf specifies full paths for each
key, while a GSettings schema has a 'path' attribute that contains the prefix
for all the keys in the schema, and individual keys just have a simple name.
So

    
    
    <key>/schemas/desktop/mate/font_rendering/antialiasing</key>

becomes

    
    
    <schema id="org.mate.font" path="/desktop/mate/font_rendering/">
      <key name="antialiasing" type="s">

Default values can be localized in both MateConf and GSettings schemas, but
GSettings uses gettext for the localization. You can specify the gettext
domain to use in the _gettext-domain_ attribute. Therefore, when converting
localized defaults in MateConf,

    
    
     <key>/schemas/apps/my_app/font_size</key>
      <locale name="C">
        <default>18</default>
      </locale>
      <locale name="be">
        <default>24</default>
      </locale>
    </key>

becomes

    
    
    <schema id="..." gettext-domain="your-domain">
     ...
    <key name="font-size" type="i">
      <default l10n="messages" context="font_size">18</default>
    </key>

GSettings uses gettext for translation of default values. The string that is
translated is exactly the string that appears inside of the <default> element.
This includes the quotation marks that appear around strings. Default values
must be marked with the l10n attribute in the <default> tag, which should be
set as equal to 'messages' or 'time' depending on the desired category. An
optional translation context can also be specified with the context attribute,
as in the example. This is usually recommended, since the string “18” is not
particularly easy to translate without context. The translated version of the
default value should be stored in the specified gettext-domain. Care must be
taken during translation to ensure that all translated values remain
syntactically valid; mistakes here will cause runtime errors.

GSettings schemas have optional <summary> and <description> elements for each
key which correspond to the <short> and <long> elements in the MateConf schema
and will be used in similar ways by a future gsettings-editor, so you should
use the same conventions for them: The summary is just a short label with no
punctuation, the description can be one or more complete sentences. If
multiple paragraphs are desired for the description, the paragraphs should be
separated by a completely empty line.

Translations for these strings will also be handled via gettext, so you should
arrange for these strings to be extracted into your gettext catalog. One way
to do that is to use intltool. For that, you use <_summary> and <_description>
elements in a .gschema.xml.in file and use @INTLTOOL_XML_NOMERGE_RULE@
 in your Makefile.am to produce the
.gschema.xml file. The NOMERGE part of the rule instructs intltool to extract
translatable strings, but not merge the translations back into the generated
xml file.

GSettings is a bit more restrictive about key names than MateConf. Key names
in GSettings can be at most 32 characters long, and must only consist of
lowercase characters, numbers and dashes, with no consecutive dashes. The
first character must not be a number or dash, and the last character cannot be
'-'.

If you are using the MateConf backend for GSettings during the transition, you
may want to keep your key names the same they were in MateConf, so that
existing settings in the users MateConf database are preserved. You can
achieve this by using the –allow-any-name with the glib-compile-schemas schema
compiler. Note that this option is only meant to ease the process of porting
your application, allowing parts of your application to continue to access
MateConf and parts to use GSettings. By the time you have finished porting
your application you must ensure that all key names are valid.

## Data conversion

[Copied from [GIO Reference Manual: Dataconversion](http://developer.gnome.org/gio/2.28/ch28s07.html) and adoped for MATE]

MateConf comes with a GSettings backend that can be used to facility the
transition to the GSettings API until you are ready to make the jump to a
different backend (most likely dconf). To use it, you need to set the
GSETTINGS_BACKEND to 'mateconf', e.g. by using

```
g_setenv ("GSETTINGS_BACKEND", "mateconf", TRUE);
```

early on in your program. Note that this backend is meant purely as a
transition tool, and should not be used in production.

MateConf also comes with a utility called gsettings-data-convert, which is
designed to help with the task of migrating user settings from MateConf into
another GSettings backend. It can be run manually, but it is designed to be
executed automatically, every time a user logs in. It keeps track of the data
migrations that it has already done, and it is harmless to run it more than
once.

To make use of this utility, you must install a keyfile in the directory
/usr/share/MateConf/gsettings which lists the GSettings keys and MateConf
paths to map to each other, for each schema that you want to migrate user data
for.

Here is an example:

```
[org.mate.fonts]
antialiasing = /desktop/mate/font_rendering/antialiasing
dpi = /desktop/mate/font_rendering/dpi
hinting = /desktop/mate/font_rendering/hinting
rgba-order = /desktop/mate/font_rendering/rgba_order

[apps.myapp:/path/to/myapps/]
some-odd-key1 = /apps/myapp/some_ODD-key1
```

The last key demonstrates that it may be necessary to modify the key name to
comply with stricter GSettings key name rules. Of course, that means your
application must use the new key names when looking up settings in GSettings.

The last group in the example also shows how to handle the case of
'relocatable' schemas, which don't have a fixed path. You can specify the path
to use in the group name, separated by a colon.

There are some limitations: gsettings-data-convert does not do any
transformation of the values. And it does not handle complex MateConf types
other than lists of strings or integers.

If, as an application developer, you are interested in manually ensuring that
gsettings-data-convert has been invoked (for example, to deal with the case
where the user is logged in during a distribution upgrade or for non-XDG
desktop environments which do not run the command as an autostart) you may
invoke it manually during your program initialisation. This is not recommended
for all application authors – it is your choice if this use case concerns you
enough.

Internally, gsettings-data-convert uses a keyfile to track which settings have
been migrated. The following code fragment will check that keyfile to see if
your data conversion script has been run yet and, if not, will attempt to
invoke the tool to run it. You should adapt it to your application as you see
fit.

```
static void
ensure_migrated (const gchar *name)
{
  gboolean needed = TRUE;
  GKeyFile *kf;
  gchar **list;
  gsize i, n;

  kf = g_key_file_new ();

  g_key_file_load_from_data_dirs (kf, "gsettings-data-convert",
                                  NULL, G_KEY_FILE_NONE, NULL);
  list = g_key_file_get_string_list (kf, "State", "converted", &n, NULL);

  if (list)
    {
      for (i = 0; i < n; i++)
        if (strcmp (list[i], name) == 0)
          {
            needed = FALSE;
            break;
          }

      g_strfreev (list);
    }

  g_key_file_free (kf);

  if (needed)
    g_spawn_command_line_sync ("gsettings-data-convert",
                               NULL, NULL, NULL, NULL);
}
```

Although there is the possibility that the gsettings-data-convert script will
end up running multiple times concurrently with this approach, it is believed
that this is safe.

