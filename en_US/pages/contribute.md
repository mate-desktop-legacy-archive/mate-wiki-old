# Contribute

MATE Desktop uses [git](http://git-scm.com/) as its
version control system, and [GitHub](https://github.com/mate-desktop)
for repositories hosting. The best place to
ask for development help is on IRC #mate-dev channel (irc.freenode.net).

## Code

To get code of a MATE package, you can use the `git clone` command (change
_mate-terminal_ with the package you want to get the code):

    
    
    git clone git://github.com/mate-desktop/mate-terminal.git

### Fork

To make your fork of a MATE project in GitHub, follow [this tutorial](http://help.github.com/fork-a-repo/).

### Example workflow

Here is an example workflow how to use `git` and MATE. This applies mostly for
people that do not commit directly to the official MATE repos. A general rule
is, as branches are cheap to create and cheap to merge, to do your work in a
separate branch than the `master` or `1.6` branches.

To be clear, this is not meant to be a general guide to `git`. You can get the
basics of how git works from the
[progit](http://git-scm.com/book/en/Git-Basics) documentation on the [git website](http://git-scm.com/doc).

  1. Fork the git repository as described in the github documentation mentioned above.

  2. Clone the **forked** git repository locally with: `git clone https://github.com/<your-github-user>/<mate-package>.git`. You can get the link from the right side of the github web page of **your** fork.

  3. Add a new remote pointing to the official repository and call it upstream (or any name that make sense to you) with: `git remote add upstream https://github.com/mate-desktop/<mate package>.git`.

  4. Now create a new branch where you will do you work in: `git branch myubercoolfeature`. Git branch takes an optional commit SHA as a starting point for the new branch. If no commit SHA is given it will branch from the most recent commit in the branch your on. 

  5. Commit, commit, commit and commit until you are happy with it.

  6. Now when you are happy with the branch push the commits to github: `git push origin`.

If you have lots of small commits that belong together use `git rebase` to
squash them together into one commit.

Also pull from upstream once in a while to keep up with changes done in the
upstream repository with: `git pull upstream <branch>`. Be careful which
upstream branch **your** working branch is based on. If you based your branch
on the upstream 1.6 branch do **NOT** pull from master by mistake as you will
have a fun time fixing the results of that.

### GIT web interface

We have a git web interface to browse through MATE source code:
<http://git.mate-desktop.org/>.

## Documentation

This is a list of useful links.

### Libraries

  * [GLib Reference Manual](http://developer.gnome.org/glib/2.32/)

  * [GIO Reference Manual](http://developer.gnome.org/gio/2.32/)

  * [GTK+ 2 Reference Manual](http://developer.gnome.org/gtk2/2.24/)

  * [GTK+ 3 Reference Manual](http://developer.gnome.org/gtk3/stable/)

### MATE

  * [Deprecated code](./deprecated_code)

  * [Replace MateConf with GSettings](./mateconf_to_gsettings)

  * [Replace MateCorba with DBus](./matecorba_to_dbus)

  * [Support systemd-logind](./systemd-logind)

  * [MATE 1.6 build order](./building-1.6)

## Patches

When you are first starting, patches are the best way to send your code
contributions to the MATE project. You can fork a project in GitHub and make a
pull request to include your patch.

Before you send the patch, please be sure to respect those points:

  * **Keep them small:** Large patches tend to be ignored because it takes a lot of effort to look into them. If you need to alter something in several places, you can do this through several patches. Large patches are also ignored because they are harder to understand, and harder to check for correctness.

  * **Discuss or inform about large changes prior to submitting a patch:** Large patch sets, even when split up, are likely to be ignored if they are not expected. Either talk with one of the active developers on  IRC and make sure they will look at and/or accept your patches, or discuss it on the mailing list in advance. This way you avoid doing work that could go unused, and you avoid putting your fellow developers in a situation where disagreeing with you means you have wasted a considerable amount of time, thus making it harder to disagree with you.

  * **Explain your patches and post them:** Your commit message should describe each individual commit.

### Send a patch

The best way to propose a patch is to send it with a pull request. Read [this tutorial](https://help.github.com/articles/using-pull-requests) to learn how to send a
pull request.
