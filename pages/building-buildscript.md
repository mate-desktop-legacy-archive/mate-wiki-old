# Build Script

(deprecated, some parts needs updating)

This script automates the task of building and installing the components of
Mate desktop in the correct order. If there are packages available for you
distro ( [Install](download.md) ) you should probably use those
instead.

To use this first download the Mate-Desktop-Environment files,

    
    
    $ git clone git://github.com/perberos/Mate-Desktop-Environment.git mate --depth=1

and then run the base-clone (and optionally extra-clone) scripts.

    
    
    $ ./base-clone.sh
    $ ./extra-clone.sh

Make sure you have all the development packages listed on the
[Building](building.md) page. Then save this script into the mate
folder as base-build.sh. and run

```bash
    $ ./base-build.sh
    $ ./base-build.sh extra
```

This will install Mate into /usr/local. There are some variables near the top
of the script that can be adjusted. To get Mate to show in you display manager
you may need to run.

```
    sudo ln -s /usr/local/share/xsessions/mate.desktop /usr/share/xsessions/
```

```bash
    #cat build-script.sh
    #!/bin/bash -e
    # Copyright © 2011 Sam Tygier <email protected>
    #
    # This program is free software; you can redistribute it and/or modify it
    # under the terms of the GNU Lesser General Public License as published by the
    # Free Software Foundation; either version 2.1 of the License, or (at your
    # option) any later version.
    #
    # This program is distributed in the hope that it will be useful, but
    # WITHOUT ANY WARRANTY; without even the implied warranty of
    # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU Lesser
    # General Public License for more details.
    #
    # You should have received a copy of the GNU Lesser General Public License along
    # with this program; if not, write to the Free Software Foundation, Inc.,
    # 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

    # Assuming that you have downloaded all the repositories with ./base-clone
    # Then build them with
    #	./base-build
    # Build the extras with
    #	./base-build extra
    # Build a specific module
    #	./base-build libmate
    # Force a clean build
    #	./base-build clean
    #	./base-build clean extra
    #	./base-build clean libmate
    # Uninstall
    #	./base-build uninstall
    #	./base-build uninstall extra
    #	./base-build uninstall libmate


    listofpackages=(
    	mate-common
    	mate-doc-utils
    	mate-corba
    	mate-conf
    	libmatecomponent
    	mate-mime-data
    	mate-vfs
    	libmate
    	libmatecanvas
    	libmatecomponentui
    	libmatekeyring
    	mate-keyring
    	libmateui
    	libmatenotify
    	libmatekbd
    	libmateweather
    	mate-icon-theme
    	mate-dialogs
    	mate-desktop
    	mate-file-manager
    	mate-notification-daemon
    	mate-backgrounds
    	mate-menus
    	marco
    	mate-polkit
    	mate-settings-daemon
    	mate-control-center
    	mate-panel
    	mate-session-manager
    )

    # some packages are commented out, as I am having trouble building them
    listofpackagesextra=(
    	mate-applets
    	mate-file-manager-sendto
    	#mate-bluetooth
    	mate-calc
    	mate-display-manager
    	mate-document-viewer
    	mate-file-archiver
    	mate-image-viewer
    	#mate-power-manager
    	mate-screensaver
    	mate-system-monitor
    	#mate-system-tools
    	mate-terminal
    	mate-text-editor
    	mate-themes
    )

    log="`pwd`/build_log.txt"
    sublog="buildlog.txt"
    config_opts="--prefix=/usr/local --sysconfdir=/etc --localstatedir=/var --disable-static"
    make_opts="-j`cat /proc/cpuinfo | grep processor | wc -l`"

    export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig/:/usr/local/share/pkgconfig/
    export ACLOCAL_FLAGS="-I /usr/local/share/aclocal/"
    export PYTHONPATH=${PYTHONPATH}:/usr/local/lib/python2.7/site-packages/
    export XDG_DATA_DIRS=/usr/local/share
    export CFLAGS="-march=native"


    clean=false
    uninstall=false

    for arg in $@
    do
    	case "$arg" in
    		clean)
    			clean=true  ;;
    		uninstall)
    			uninstall=true  ;;
    		extra)
    			listofpackages=( ${listofpackagesextra[@]} ) ;;
    		*)
    			listofpackages=( ${arg} ) ;;
    	esac
    done

    fail() {
    	name=$1
    	action=$2
    	echo $name "failed to" $action | tee -a $log
    	echo "see log file" ${name}/$sublog  | tee -a $log
    	exit 1
    }
     
     
    rm $log || true
    echo "starting build" `date` | tee -a $log
     
    if $uninstall
    then
    	# NOTE: in reverse order
    	for i in $(seq $((${#listofpackages[@]} - 1)) -1 0); do
    		name=${listofpackages[$i]}
    		if [[ -d $name ]]; then
    			echo "Remove $name" `date` | tee -a $log
    			cd $name
    			rm $sublog INSTALLDONE 2>/dev/null || true
    			if [[ ! -f configure ]]
    			then
    				echo "$name probably not installed"  | tee -a $log
    				cd ..
    				continue
    			fi
    			echo "Removing $name" `date` | tee -a $log
    			sudo make uninstall || fail $name  "uninstall" 
    			cd ..
    		else
    			echo "$name directory missing" | tee -a $log
    		fi
    	done
    	echo "Uninstall done" `date` | tee -a $log
    	exit 0
    fi
     
     
    for i in $(seq 0 $((${#listofpackages[@]} - 1))); do
    	name=${listofpackages[$i]}
    	echo "Building $name" `date` | tee -a $log
     
    	if [[ -d $name ]]; then
    		cd $name
    		if [[ "${name}" == "mate-applets" ]]
    		then
    			config_opts_extra="--disable-cpufreq"
    		else
    			config_opts_extra=""
    		fi
     
    		if [[ -f INSTALLDONE ]] && ! $clean;
    		then
    			echo "$name already done"  | tee -a $log
    			cd ..
    			continue
    		fi
    		rm $sublog INSTALLDONE 2>/dev/null || true
    		if [[ ! -f configure ]] || $clean
    		then
    			echo "autogen.sh $name" `date` | tee -a $log
    			./autogen.sh $config_opts $config_opts_extra &>> $sublog  || fail $name  "autogen" 
    			echo "clean $name" `date` | tee -a $log
    			make clean &>> $sublog  || fail $name  "clean" 
    		else
    			echo "./configure $name" `date` | tee -a $log
    			echo ./configure $config_opts $config_opts_extra | tee -a $log
    			./configure $config_opts $config_opts_extra &>> $sublog	|| fail $name  "configure" 
    		fi
     
    		echo "make $name" `date` | tee -a $log
    		nice make $make_opts &>> $sublog	|| fail $name  "make" 
    		echo "install $name" `date` | tee -a $log
    		sudo -E make install || fail $name  "install" 
    		touch INSTALLDONE
    		cd ..
    	else
    		echo "$name directory missing" | tee -a $log
    		exit 1
    	fi
    done
     
    echo "build done" `date` | tee -a $log
```
