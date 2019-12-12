# Maintainers

This page contains all the useful information for MATE maintainers.

## Install the development tools

### Debian & Ubuntu

    
    
      $ sudo apt install build-essential fakeroot devscripts

Get the build dependencies, replace mate-thing for the package you are
building.

    
    
      $ sudo apt-get build-dep mate-thing

## Checkout the git repository

    
    
      $ git clone git@github:mate-desktop/mate-thing.git

## Prepare for release

  * Update version in configure.ac and commit.

  * Update NEWS.

    
    
      $ git log --oneline --no-merges | cut -c 10- | sed 's/^/  * /' | head -n 50

  * Update translations

    
    
      $ tx pull -af
      $ ls -1 po/*.po | sort | cut -d'/' -f2 | cut -d'.' -f1 > po/LINGUAS
      $ git add po/*.po
      $ git commit -a -m "Sync translations."

  * Make a tarball and test build

    
    
    $ ./autogen.sh --enable-gtk-doc --enable-deprecated --disable-strict; and make -j5; and make dist -j5; and make distcheck -j5

  * Commit the release with version.

    
    
    $ git add NEWS configure.ac
    $ git commit -m "Release 1.18.0"
    $ git push

## Prepare for release

### Check existing tags

For checking existing tags use 'git tag' before you push it to orign.

### Tag git

    
    
      $ git tag v1.18.0
      $ git push --tags

### Remove tags

To remove a local tag:

    
    
      $ git tag -d v1.18.0

To remove from origin:

    
    
      $ git push origin :refs/tags/v1.18.0

## Releasing tarballs

  * When a release commit is taged, a tarball will be created by Travis CI and uploaded to server <https://pub.mate-desktop.org/releases/>

## Update wiki

  * <https://wiki.mate-desktop.org/#!pages/status-1.18.md>

