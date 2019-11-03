# Maintainers

This page contains all the useful information for MATE maintainers.

## Install the development tools

### Debian & Ubuntu

    
    
      sudo apt install build-essential fakeroot devscripts

Get the build dependencies, replace mate-thing for the package you are
building.

    
    
      sudo apt-get build-dep mate-thing

## Checkout the git repository

    
    
      git clone git@github:mate-desktop/mate-thing.git

## Prepare for release

  * Update version in configure.ac and commit.

  * Update NEWS.

    
    
      git log --oneline --no-merges | cut -c 9- | sed 's/^/  * /' | head -n 50

  * Update translations

    
    
      tx pull -a --minimum-perc=5 -f
      ls -1 po/*.po | sort | cut -d'/' -f2 | cut -d'.' -f1 > po/LINGUAS
      git add po/*.po
      git commit -m "Sync translations."

  * Make a tarball and test build

    
    
    ./autogen.sh --enable-gtk-doc --enable-deprecated --disable-strict; and make -j5; and make dist -j5; and make distcheck -j5

  * Commit with version bump.

    
    
    git add NEWS configure.ac
    git commit -m "Bump version to 1.18.0"
    git push

## Prepare for release

### Check existing tags

For checking existing tags use 'git tag' before you push it to orign.

### Tag git

    
    
      git tag v1.18.0
      git push --tags

### Remove tags

To remove a local tag:

    
    
      git tag -d v1.18.0

To remove from origin:

    
    
      git push origin :refs/tags/v1.18.0

## Prepare for release

  * If we are preparing a new major release of the whole MATE Desktop upload tarball to server <http://release.mate-desktop.org>

  * If you are preparing a point release upload the tarball to <http://pre-release.mate-desktop.org>

7\. Update wiki

  * <http://wiki.mate-desktop.org/status:1.18>

