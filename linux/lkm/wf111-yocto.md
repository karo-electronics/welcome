# WF111 LKM

## Compile the LKM manually
This example uses Ka-Ro's Yocto BSP, but is follows the basic steps for
"out-of-tree" kernel module compile for the Linux kernel, as widely outlined
and explained, by 3rd party resources, like the LKM own README and/or
otherwise publicly avaialble resources.

## Introduction
This is a how to for manually compiling the SiLabs (f.k.a. Bluegiga) WF111
WLAN module drives for Linux under the Yocto environment.

## Out-of-tree module
The driver, as it is partially proprietary, is not part of the general Kernel
sources as available from [Kernel.org][1]

### Yocto
Yocto is just used as the basic surrounding of the compile of the LKM.
The LKM is intended to be used in Yocto RFS as well as the Yocto provides an
pre-setup environment incl. a compiler and more and thus reducing steps and
thus complexity from the whole.

### Extract sources

Working direcrtory:

```console
user@hostname: ~/projects/yocto/rocko_rel-2018-04/wf111 $
```

hererafter shortend to the common marker for console prompt

```console
$
```

what does the drivers `make help` say:
```console
$ make help
Build environment for Linux drivers of Bluegiga WF111 module

Usage:

targets:
    unifi_sdio             - build unifi driver
    unifi_sdio_android     - build unifi driver for Android
    install                - build and install binaries to OUTPUT
    install_android        - build and install Android binaries
                             to OUTPUT
    install_static         - build and install statically linked
                             binaries to OUTPUT
    install_static_android - build and install statically linked
                             Android binaries to OUTPUT
    clean                  - clean the build tree

variables:
    KDIR                   - path to kernel source tree
    ARCH                   - x86, arm, powerpc
    CROSS_COMPILE          - cross compile prefix (optional)
    OUTPUT                 - install destination path (default: output)

Example: make KDIR=/path/to/linux ARCH=arm CROSS_COMPILE=arm-linux- install_static
```

```
$
CROSS_COMPILE=arm-poky-linux-gnueabi-
OUTPUT=/tftpboot/tx6/rootfs-wpa-3/

KDIR=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source

make KDIR=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source OUTPUT=/tftpboot/tx6/rootfs-wpa-3/ install_static

Makefile:75: *** WIRELESS_EXT is missing from the kernel config.  Stop.

KBUILD_OUTPUT=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/build

$KBUILD_OUTPUT

unset KBUILD_OUTPUT

make KDIR=~/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source OUTPUT=/tftpboot/tx6/rootfs-wpa-3 install_static
```

```
$ printenv | sort
AR=arm-poky-linux-gnueabi-ar
ARCH=arm
AS=arm-poky-linux-gnueabi-as
base_bindir=/bin
ase_libdir=/lib
base_prefix=
base_sbindir=/sbin
BB_ENV_EXTRAWHITE=ALL_PROXY BBPATH_EXTRA BB_NO_NETWORK BB_NUMBER_THREADS BB_SETSCENE_ENFORCE BB_SRCREV_POLICY DISTRO FTPS_PROXY FTP_PROXY GIT_PROXY_COMMAND HTTPS_PROXY HTTP_PROXY MACHINE NO_PROXY PARALLEL_MAKE SCREENDIR SDKMACHINE SOCKS5_PASSWD SOCKS5_USER SSH_AGENT_PID SSH_AUTH_SOCK STAMPS_DIR TCLIBC TCMODE all_proxy ftp_proxy ftps_proxy http_proxy https_proxy no_proxy
BBPATH=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand
bindir=/usr/bin
BUILD_AR=ar
BUILD_AS=as
BUILD_CC=gcc
BUILD_CCLD=gcc
BUILD_CFLAGS=-isystem/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/include -O2 -pipe
BUILD_CPPFLAGS=-isystem/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/include
BUILD_CPP=gcc  -E
BUILD_CXXFLAGS=-isystem/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/include -O2 -pipe
BUILD_CXX=g++
BUILDDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand
BUILD_FC=gfortran
BUILD_LDFLAGS=-L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-O1
BUILD_LD=ld
BUILD_NM=nm
BUILD_RANLIB=ranlib
BUILD_STRIP=strip
BZIP_BIN=pbzip2
CCACHE_DIR=/home/user/.ccache
CC=arm-poky-linux-gnueabi-gcc  -march=armv7ve -mfpu=neon -mfloat-abi=hard -mcpu=cortex-a7 --sysroot=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot
CCLD=arm-poky-linux-gnueabi-gcc  -march=armv7ve -mfpu=neon -mfloat-abi=hard -mcpu=cortex-a7 --sysroot=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot
CFLAGS= -O2 -pipe -g -feliminate-unused-debug-types -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0=/usr/src/debug/linux-karo/4.14.24-r0 -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native= -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot=
CMDLINE_CONSOLE=console=ttyS0
COLORTERM=xfce4-terminal
COMP_WORDBREAKS=
CPP=arm-poky-linux-gnueabi-gcc -E --sysroot=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot  -march=armv7ve -mfpu=neon -mfloat-abi=hard -mcpu=cortex-a7
CPPFLAGS=
CROSS_COMPILE=arm-poky-linux-gnueabi-
CROSS_CURSES_INC=-DCURSES_LOC="<curses.h>"
CROSS_CURSES_LIB=-lncurses -ltinfo
CVSROOT=/usr/local/cvs
CXX=arm-poky-linux-gnueabi-g++  -march=armv7ve -mfpu=neon -mfloat-abi=hard -mcpu=cortex-a7 --sysroot=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot
CXXFLAGS= -O2 -pipe -g -feliminate-unused-debug-types -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0=/usr/src/debug/linux-karo/4.14.24-r0 -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native= -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot=  -fvisibility-inlines-hidden
datadir=/usr/share
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-AB1ALCn3C0,guid=e2aa5b10a67791206b0e7ed85abb982f
DESKTOP_SESSION=lightdm-xsession
DISPLAY=:0.0
docdir=/usr/share/doc
EDITOR=nano
exec_prefix=/usr
EXTRA_OECONF= --disable-static
EXTRA_OEMAKE= HOSTCC="gcc  -isystem/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/include -O2 -pipe -L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-O1" HOSTCPP="gcc  -E"
FC=arm-poky-linux-gnueabi-gfortran  -march=armv7ve -mfpu=neon -mfloat-abi=hard -mcpu=cortex-a7 --sysroot=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot
GDMSESSION=lightdm-xsession
GLADE_CATALOG_PATH=:
GLADE_MODULE_PATH=:
GLADE_PIXMAP_PATH=:
GNOME_KEYRING_CONTROL=/home/user/.cache/keyring-C805FZ
GPG_AGENT_INFO=/tmp/gpg-6mmnWt/S.gpg-agent:3995:1
GTK_MODULES=gail:atk-bridge
GZIP_BIN=pigz
HOME=/home/user
HOST_EXTRACFLAGS=-isystem/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/include -O2 -pipe -L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-O1
HOSTLDFLAGS=-L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -L/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath-link,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/lib -Wl,-rpath,/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/lib -Wl,-O1
includedir=/usr/include
infodir=/usr/share/info
KBUILD_BUILD_HOST=karo-electronics.de
KBUILD_BUILD_USER=support
KEYSET=1
LANG=en_GB.utf8
LANGUAGE=en_GB:en_US:en
LC_ALL=en_US.UTF-8
LC_MEASUREMENT=de_DE.UTF-8
LC_MONETARY=de_DE.UTF-8
LC_NUMERIC=en_GB.UTF-8
LC_PAPER=en_DK.UTF-8
LC_TIME=de_DE.UTF-8
LD=arm-poky-linux-gnueabi-ld --sysroot=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot
LDFLAGS=
LD_LIBRARY_PATH=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/sysroots-components/x86_64/pseudo-native/usr/lib/pseudo/lib:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/sysroots-components/x86_64/pseudo-native/usr/lib/pseudo/lib64
LD_PRELOAD=libpseudo.so
libdir=/usr/lib
libexecdir=/usr/libexec
localstatedir=/var

MAKE=make
mandir=/usr/share/man
NM=arm-poky-linux-gnueabi-nm
nonarch_base_libdir=/lib
nonarch_libdir=/usr/lib
OBJCOPY=arm-poky-linux-gnueabi-objcopy
OBJDUMP=arm-poky-linux-gnueabi-objdump
oldincludedir=/usr/include
OLDPWD=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source
OS=linux-gnueabi
PATH=/home/user/bin:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/sysroots-uninative/x86_64-linux/usr/bin:/home/user/projects/yocto/rocko_rel-2018-04/sources/poky/scripts:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/bin/arm-poky-linux-gnueabi:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot/usr/bin/crossscripts:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/sbin:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/bin:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/sbin:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/bin:/home/user/projects/yocto/rocko_rel-2018-04/sources/poky/bitbake/bin:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/hosttools:/home/user/projects/yocto/rocko_rel-2018-04/sources/poky/scripts:/home/user/projects/yocto/rocko_rel-2018-04/sources/poky/bitbake/bin:/home/user/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games:/home/user/bin/openocd:/home/user/bin/android/sdk/platform-tools:/home/user/bin/local:/home/user/bin/openocd:/home/user/bin/android/sdk/platform-tools:/home/user/bin/local
PBZ=--use-compress-prog=pbzip2
PGZ=--use-compress-prog=pigz
PKG_CONFIG_DIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot/usr/lib/pkgconfig
PKG_CONFIG_DISABLE_UNINSTALLED=yes
PKG_CONFIG_LIBDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot/usr/lib/pkgconfig
PKG_CONFIG_PATH=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot/usr/lib/pkgconfig:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/lPKG_CONFIG_SYSTEM_INCLUDE_PATH=/usr/include
PKG_CONFIG_SYSTEM_LIBRARY_PATH=/lib:/usr/lib
prefix=/usr
PSEUDO_BINDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/sysroots-components/x86_64/pseudo-native/usr/bin
PSEUDO_DEBUG=
PSEUDO_DISABLED=0
PSEUDO_LIBDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/sysroots-components/x86_64/pseudo-native/usr/lib/pseudo/lib
PSEUDO_LOCALSTATEDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/pseudo/
PSEUDO_NOSYMLINKEXP=1
PSEUDO_OPTS=
PSEUDO_PASSWD=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot:/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/sysroots-components/x86_64/pseudo-native
PSEUDO_PREFIX=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/sysroots-components/x86_64/pseudo-native/usr
PWD=/home/user/projects/yocto/rocko_rel-2018-04/wf111
RANLIB=arm-poky-linux-gnueabi-ranlib
READELF=arm-poky-linux-gnueabi-readelf
sbindir=/usr/sbin
servicedir=/srv
SESSION_MANAGER=local/vostro-og-ow:@/tmp/.ICE-unix/3990,unix/vostro-og-ow:/tmp/.ICE-unix/3990
sharedstatedir=/com
SHELL=/bin/bash
SHLVL=2
SSH_AGENT_PID=3978
SSH_AUTH_SOCK=/tmp/ssh-EcAFQ1hkxGr1/agent.3943
STRINGS=arm-poky-linux-gnueabi-strings
STRIP=arm-poky-linux-gnueabi-strip
sysconfdir=/etc
systemd_system_unitdir=/lib/systemd/system
systemd_unitdir=/lib/systemd
systemd_user_unitdir=/usr/lib/systemd/user
TARGET_CFLAGS= -O2 -pipe -g -feliminate-unused-debug-types -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0=/usr/src/debug/linux-karo/4.14.24-r0 -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native= -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot=
TARGET_CPPFLAGS=
TARGET_CXXFLAGS= -O2 -pipe -g -feliminate-unused-debug-types -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0=/usr/src/debug/linux-karo/4.14.24-r0 -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native= -fdebug-prefix-map=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot=
TARGET_LDFLAGS=-Wl,-O1 -Wl,--hash-style=gnu -Wl,--as-needed
TERMINFO=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/recipe-sysroot-native/usr/share/terminfo
TERM=xterm
UBOOT_ARCH=arm
USER=user
_=/usr/bin/printenv
VISUAL=emacs
WINDOWID=88097578
XAUTHORITY=/home/user/.Xauthority

XDG_CONFIG_DIRS=/etc/xdg
XDG_CURRENT_DESKTOP=XFCE
XDG_DATA_DIRS=/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
```

```
Changed: Added includes and removed obsolete references to allow for compiling
         against Linux 4.14.24 kernel.

csr/synergy/framework/3.1/bsp/ports/pclin/inc/csr_framework_ext_types.h
    Inserted includes for Linux wait states


csr/os_linux/driver/bh.c
csr/os_linux/driver/unifi_sme.c
    Inserted includes for Linux kernel schedulers

csr/os_linux/driver/netdev.c
    Removed usage of last_rx, in accordance to the following kernel changes:

    commit  4a7c972644c1151f6dd34ff4b5f7eacb239e22ee
    Author: Tobias Klauser <tklauser@distanz.ch>
    Date:   2017-01-18 17:45:01 +0100
    net: Remove usage of net_device last_rx member

make KDIR=/path/to/linux ARCH=arm CROSS_COMPILE=arm-linux- install_static
```

### Kernel 4.13:
#### RFS external to Yocto
```
unset KBUILD_OUTPUT
OUTPUT=/tftpboot/tx6/rootfs-wpa-6_karo-413
make KDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source OUTPUT=/tftpboot/tx6/rootfs-wpa-6_karo-413 install_static
make KDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source clean
```

### Kernel 4.14.24:
#### RFS external to Yocto
```
unset KBUILD_OUTPUT
OUTPUT=/tftpboot/tx6/rootfs-wpa-7_karo-414
/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source
make KDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source OUTPUT=/tftpboot/tx6/rootfs-wpa-7_karo-414 install_static

[root@vostro-og-ow]: ~/projects/yocto/rocko_rel-2018-04/wf111 #
echo $KBUILD_OUTPUT
/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/build
```

### configs
```
[user@vostro-og-ow]: ~/projects/yocto/rocko_rel-2018-04 $ lal wf111-devel/
total 1552
drwxr-xr-x 2 user users     140 2018-04-18 16:09:00 4.13-karo_yocto-rocko
drwxr-xr-x 2 user users     142 2018-04-18 11:05:17 4.14.24-karo_yocto-rocko
-rw-r--r-- 1 user users 1587640 2016-03-15 15:06:10 wf111-user_space_and_all-modules.tar.bz2
[user@vostro-og-ow]: ~/projects/yocto/rocko_rel-2018-04 $ cd wf111-devel/
[user@vostro-og-ow]: ~/projects/yocto/rocko_rel-2018-04/wf111-devel $ cd 4.13-karo_yocto-rocko/
[user@vostro-og-ow]: ~/projects/yocto/rocko_rel-2018-04/wf111-devel/4.13-karo_yocto-rocko $ lal
total 524
-rw-r--r-- 1 user users 106763 2018-04-18 15:00:46 .config
-rw-r--r-- 1 user users 105575 2018-04-17 16:48:53 .config.old
-rw-r--r-- 1 user users 104896 2018-04-17 16:07:50 .config.org
-rw-r--r-- 1 user users 105575 2018-04-17 16:48:53 .config.org-yocto_hostap
-rw-r--r-- 1 user users 105383 2018-04-17 16:18:28 .config.org-yocto-linux_karo_4.13-wireless_ext
[user@vostro-og-ow]: ~/projects/yocto/rocko_rel-2018-04/wf111-devel/4.13-karo_yocto-rocko $
```

###
/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/build

```
Location:
  -> Device Drivers
    -> Network device support (NETDEVICES [=y])
      -> Wireless LAN (WLAN [=y])
        -> Intersil devices (WLAN_VENDOR_INTERSIL [=y])
          -> IEEE 802.11 for Host AP (Prism2/2.5/3 and WEP/TKIP/CCMP) (HOSTAP [=n])
            -> Support downloading firmware images with Host AP driver (HOSTAP_FIRMWARE [=n])


~/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/build

~/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package/lib/modules/4.13.0-karo-tx6+g3d523ec
~/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package/
```

https://github.com/torvalds/linux/blob/master/Documentation/kbuild/modules.txt
```
=== 2. How to Build External Modules

To build external modules, you must have a prebuilt kernel available
that contains the configuration and header files used in the build.
Also, the kernel must have been built with modules enabled. If you are
using a distribution kernel, there will be a package for the kernel you
are running provided by your distribution.

An alternative is to use the "make" target "modules_prepare." This will
make sure the kernel contains the information required. The target
exists solely as a simple way to prepare a kernel source tree for
building external modules.

NOTE: "modules_prepare" will not build Module.symvers even if
CONFIG_MODVERSIONS is set; therefore, a full kernel build needs to be
executed to make module versioning work.

--- 2.1 Command Syntax

	The command to build an external module is:

		$ make -C <path_to_kernel_src> M=$PWD

	The kbuild system knows that an external module is being built
	due to the "M=<dir>" option given in the command.

	To build against the running kernel use:

		$ make -C /lib/modules/`uname -r`/build M=$PWD

	Then to install the module(s) just built, add the target
	"modules_install" to the command:

		$ make -C /lib/modules/`uname -r`/build M=$PWD modules_install

--- 2.2 Options

	($KDIR refers to the path of the kernel source directory.)

	make -C $KDIR M=$PWD

	-C $KDIR
		The directory where the kernel source is located.
		"make" will actually change to the specified directory
		when executing and will change back when finished.

	M=$PWD
		Informs kbuild that an external module is being built.
		The value given to "M" is the absolute path of the
		directory where the external module (kbuild file) is
		located.

--- 2.3 Targets

	When building an external module, only a subset of the "make"
	targets are available.

	make -C $KDIR M=$PWD [target]

	The default will build the module(s) located in the current
	directory, so a target does not need to be specified. All
	output files will also be generated in this directory. No
	attempts are made to update the kernel source, and it is a
	precondition that a successful "make" has been executed for the
	kernel.

	modules
		The default target for external modules. It has the
		same functionality as if no target was specified. See
		description above.

	modules_install
		Install the external module(s). The default location is
		/lib/modules/<kernel_release>/extra/, but a prefix may
		be added with INSTALL_MOD_PATH (discussed in section 5).

	clean
		Remove all generated files in the module directory only.

	help
		List the available targets for external modules.

--- 2.4 Building Separate Files

	It is possible to build single files that are part of a module.
	This works equally well for the kernel, a module, and even for
	external modules.

	Example (The module foo.ko, consist of bar.o and baz.o):
		make -C $KDIR M=$PWD bar.lst
		make -C $KDIR M=$PWD baz.o
		make -C $KDIR M=$PWD foo.ko
		make -C $KDIR M=$PWD /

=== 5. Module Installation

Modules which are included in the kernel are installed in the
directory:

	/lib/modules/$(KERNELRELEASE)/kernel/

And external modules are installed in:

	/lib/modules/$(KERNELRELEASE)/extra/

--- 5.1 INSTALL_MOD_PATH

	Above are the default directories but as always some level of
	customization is possible. A prefix can be added to the
	installation path using the variable INSTALL_MOD_PATH:

		$ make INSTALL_MOD_PATH=/frodo modules_install
		=> Install dir: /frodo/lib/modules/$(KERNELRELEASE)/kernel/

	INSTALL_MOD_PATH may be set as an ordinary shell variable or,
	as shown above, can be specified on the command line when
	calling "make." This has effect when installing both in-tree
	and out-of-tree modules.

--- 5.2 INSTALL_MOD_DIR

	External modules are by default installed to a directory under
	/lib/modules/$(KERNELRELEASE)/extra/, but you may wish to
	locate modules for a specific functionality in a separate
	directory. For this purpose, use INSTALL_MOD_DIR to specify an
	alternative name to "extra."

		$ make INSTALL_MOD_DIR=gandalf -C $KDIR \
		       M=$PWD modules_install
		=> Install dir: /lib/modules/$(KERNELRELEASE)/gandalf/

```


M=$HOME/projects/yocto/rocko_rel-2018-04/wf111/csr/os_linux/driver/Kbuild
INSTALL_MOD_PATH=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package

make modules_install

make modules_install INSTALL_MOD_PATH=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package

```
$KBUILD_OUTPUT/
ca $KBUILD_OUTPUT/modules.builtin $KBUILD_OUTPUT/modules.order $KBUILD_OUTPUT/Module.symvers .
# make -C $KDIR M=$PWD [target]
# make -C $KDIR M=$PWD
# make -C $KDIR M=$PWD install_static
```

make KDIR=~/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source OUTPUT=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package install_static

./crypto/Kconfig


make KDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source clean


make KDIR=/home/user/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/build

```
# LKM lay here (Kernel major versions in path!!):
# 4.13
$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package
```
```
# 4.14.24
$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/package

$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package install_static
```
install_static

# make modules
make prepare
make modules_prepare
make modules
make INSTALL_MOD_PATH=/frodo modules_install
### 4.13
```
export IMP=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package
make INSTALL_MOD_PATH=§IMP modules_install
```

### 4.14
```
export IMP=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/package
make INSTALL_MOD_PATH=$IMP modules_install
```

## All kernels

```
cp -ai $KBUILD_OUTPUT/Module.symvers .
make KDIR=~/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source OUTPUT=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package install_static
```

pud ~/projects/yocto/rocko_rel-2018-04/wf111

### Setup compile for the WF111
#### general
```
export KDIR=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work-shared/imx6ul-txul-nand/kernel-source
```

#### 4.13
```
export OUTPUT=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.13-r0/package
```

#### 4.14
```
export OUTPUT=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/work/imx6ul_txul_nand-poky-linux-gnueabi/linux-karo/4.14.24-r0/package
```

#### general
the fowlloing command needs "OUTPUT" to be defined otherwise will the
compile drop the created modules-firmware-userspace tools into the source

#### directory
```console
make OUTPUT=$OUTPUT install_static
cd $OUTPUT
```

# tar-ing
```console
tar -czvf MyBackup.tar.gz /home/user/public_html/ --exclude "/home/user/public_html/tmp"
# create module tar
```

```console
export DEPLOY=$HOME/projects/yocto/rocko_rel-2018-04/build-imx6ul-txul-nand/tmp/deploy/images/imx6ul-txul-nand
```
# 4.13
## modules--4.13-r0-imx6ul-txul-nand-20180425123754.tgz
```console
tar -czvf $DEPLOY/modules--4.13-r0-imx6ul-txul-nand-wf111_prepped-$(sdate).tgz . --exclude "boot" --exclude "build" --exclude "source"
tar -czvf $DEPLOY/modules--4.13-r0-imx6ul-txul-nand-wf111_installed-$(sdate).tgz . --exclude "boot" --exclude "build" --exclude "source"
```

# 4.14
```console
tar -czvf $DEPLOY/modules--4.14.24-r0-imx6ul-txul-nand-wf111_prepped-$(sdate).tgz . --exclude "boot" --exclude "build" --exclude "source"
tar -czvf $DEPLOY/modules--4.14.24-r0-imx6ul-txul-nand-wf111_installed-$(sdate).tgz . --exclude "boot" --exclude "build" --exclude "source"
```

## clean up
1) goto: wf111 source directory
2) do:
   $ git status -s
   [A]
3) check the above list does not include code changes files
4) do:
   $ git status -s > ../remove-files.list
5) edit created file "../remove-files.list" and remove git syntax, e.g.:
   from:
	?? csr/synergy/wifi/5.2.2/src/interfaces/sme/.csr_wifi_sme_free_downstream_contents.o.cmd
	?? csr/synergy/wifi/5.2.2/src/interfaces/sme/.csr_wifi_sme_free_upstream_contents.o.cmd
	?? csr/synergy/wifi/5.2.2/src/interfaces/sme/.csr_wifi_sme_serialize.o.cmd
   to:
	csr/synergy/wifi/5.2.2/src/interfaces/sme/.csr_wifi_sme_free_downstream_contents.o.cmd
	csr/synergy/wifi/5.2.2/src/interfaces/sme/.csr_wifi_sme_free_upstream_contents.o.cmd
	csr/synergy/wifi/5.2.2/src/interfaces/sme/.csr_wifi_sme_serialize.o.cmd
6) execute the following command:
   $ while read -r line; do rm "$line"; done < ../remove-files.list

After command at "6)" the drivers source directory will be clean again.


[A] This is a often used command. Often used commands a great candidates for
    aliasing. Create a git alias either editing your .gitconfig (global -
    prefered) or by executing follwoing command, of course the alias should
    defined for your workflow, here is an in-house example:
    ==  $ git config --global alias.sts 'status -s'
    ==> $ git status -s
    <=> $ git sts


### create a diff to the default .config
diff -Naru file_original file_updated > file.patch
patch -p1 --dry-run < dfile.patch


```
MACHINE=imx6q-tx6-emmc DISTRO=karo-x11 source ./setup-environment build-imx6q-tx6-**emmc**
bitbake karo-image-x11
```

---
## Footnotes & References

[1]: https://kernel.org

<a id="source"></a>
Source: <https://www.karo-electronics.de/1651.html>

<a name="pcn">PCN</a>:
Ka-Ro publishes changes to the TX COM in its PCN, which are available to the
users in the respective TX COM download area on the [Ka-Ro website][2]

[2]: https://www.karo-electronics.de
[3]: http://elinux.org/Bitbake_Cheat_Sheet
[4]: https://community.nxp.com/docs/DOC-94953
[5]: http://www.crashcourse.ca/wiki/index.php/BitBake_Tutorial

https://unix.stackexchange.com/questions/162131/is-this-a-good-way-to-create-a-patch


---
[Ka-Ro electronics GmbH](https://www.karo-electronics.de)
Contact support: support@karo-electronics.de
