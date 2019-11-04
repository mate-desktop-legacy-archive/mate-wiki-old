# Translation

MATE translations are managed by [transifex](https://www.transifex.com).

## Translators

  * Web interface is located at <https://www.transifex.com/projects/p/MATE/>.

The following basic suggestions might be useful for translators:

  * Use machine translation and translation memories _only_ as suggestions. Never copy machine translated stuff outright. Quality matters!

  * Install and use a spellchecker and, if available, a grammar tool like [LanguageTool](https://www.languagetool.org/). If poedit doesn't provide a spellchecker for your language, extract translated strings with grep msgstr filename.po > file.txt and open it with LibreOffice.

  * Keep in mind that [Wiktionary](https://www.wiktionary.org/) is a good resource.

  * If you 're not sure, leave the old translation.

  * Do a search on “mate” in all files, especially if your language is agglutinative. You may well find several instances which need slight corrections after the change from GNOME to MATE.

  * When translating help files, please make sure to open the relevant application and check the already translated strings so that the wording in the help file matches the one in the application.

  * Some strings are already translated by GNOME folks but were not imported, Google can find them. For instance, let's consider “Whether the default browser understands netscape remote.” in mate-desktop. Put that string with the quotation marks on [Google's advanced search](https://encrypted.google.com/advanced_search), choose your language and add one word in the target language. In Turkish, I would choose “tarayıcı” which means navigator, so the query would be ["Whether the default browser understands netscape remote." tarayıcı](https://encrypted.google.com/search?as_q=%22Whether+the+default+browser+understands+netscape+remote.%22+taray%C4%B1c%C4%B1&as_epq=&as_oq=&as_eq=&as_nlo=&as_nhi=&lr=lang_tr&cr=&as_qdr=all&as_sitesearch=&as_occt=&safe=images&as_filetype=&as_rights=not+filtered+by+license). Admire the results :)

## Developers

  * Install transifex-client ([documentation](https://help.transifex.com/features/client/index.html)).

  * Create a `.tx/config` file for the project like this:

```
[main]
host = https://www.transifex.com

[MATE.$package]
file_filter = po/<lang>.po
source_file = po/$package.pot
source_lang = en
```

  * Create the `$package.pot` files with the command (if you got errors, maybe `po/POTFILES.in` need to be adapted for MATE renames):

```bash
intltool-update -p
```

  * Push translations on transifex with one of those commands:

```bash
# push a single language
tx push -t -l it
# push more languages
tx push -t -l it,de,es
# push all languages, skipping errors
tx push -t --skip -f
```

  * Update translations with one of those commands:

```bash
# one language
tx pull -l it
# all languages
tx pull -a --minimum-perc=10
```
