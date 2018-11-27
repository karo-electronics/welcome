# TX6 Setup for Yocto Project 2.0 - codename Jethro

For the newer guide based on version 2.1 - Krogoth, click [[https://www.karo-electronics.de/yocto.html?&L=1,|here]]. For the older guide based on version 1.8 - Fido, click [[https://www.karo-electronics.de/1691.html?&L=1,|here]].

## References

This guide is based on the// NXP/Freescale Yocto Project User's Guide// (IMXLXYOCTOUG)

 The instructions for setting up and building Linux in the Yocto Project were adopted to our products and the ARMSDK environment.

Documentation is available online at nxp.com.[[http://www.nxp.com/products/arm-processors/i.mx-applications-processors-based-on-arm-cores/i.mx-software-and-tools:IMXSW_HOME|
i.MX Software and Development Tools]]

A list of helpful bitbake commands can be found here:[[https://community.freescale.com/docs/DOC-94953|
NXP/Freescale - Useful bitbake commands]]

A cheat sheet for bitbake:
[[http://elinux.org/Bitbake_Cheat_Sheet|Bitbake Cheat Sheet]]

The FSL Community BSP is also available at github:[[http://freescale.github.io/|
FSL Community BSP]]

## Requirements

For Yocto a Linux Host Machine is needed. For this purpose Ka-Ro offers a Virtual Appliance, called [[https://www.karo-electronics.de/428.html?&L=1,|ARMSDK VM]]. This Virtual Appliance offers the comprehensive capabilities to use the tool-chain supplied by Ka-Ro either in it's pre-compiled version or from the source. Allowing the user to compile all packages offered by Ka-Ro, including but not limited to U-Boot. Although it is possible to use all Linux distributions, because of diversity and versatility of Linux distributions the offered ARMSDK VM Virtual Appliance is the only means supported by Ka-Ro for cross compilation. For further information concerning the ARMSDK VM please refer to the there enclosed documentation.

An important consideration is the hard disk space required for the virtual appliance. It is recommended that at least 120 GB is provided.

## Host packages

A NXP/Freescale Yocto Project Community BSP build requires that some packages be installed for the build that are documented under the Yocto Project.

You can go to [[http://www.yoctoproject.org/docs/current/ref-manual/ref-manual.html|Yocto Project Quick Start]] and check for the packages that must be installed for your build machine.

First of all update your local repository:

sudo apt-get update

Install essential Yocto Project host packages:

sudo apt-get install gawk wget git-core diffstat unzip \
texinfo gcc-multilib build-essential chrpath socat

i.MX layers host packages:

sudo apt-get install libsdl1.2-dev xterm sed cvs \
subversion coreutils texi2html docbook-utils \
python-pysqlite2 help2man make gcc g++ desktop-file-utils \
libgl1-mesa-dev libglu1-mesa-dev mercurial autoconf \
automake groff curl lzop asciidoc u-boot-tools

## Setting up the repo utility

Repo is a tool built on top of Git that makes it easier to manage projects that contain multiple repositories, which do not need to be on the same server. Repo complements very well the layered nature of the Yocto Project, making it easier for customers to add their own layers to the BSP.

To install the “repo” utility, perform these steps:
```console
 curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
 chmod a+x ~/bin/repo
 ```

## Yocto Project Setup

First make sure that git is setup properly with the commands below.

```console
 git config --global user.name "Your Name"
 git config --global user.email "Your Email"
 git config --list
 ```

The NXP/Freescale Yocto Project BSP Release directory contains a "sources" directory, which contains the recipes used to build, one or more build directories, and a set of scripts used to set up the environment. The recipes used to build the project come from both the community and NXP/Freescale. The Yocto Project layers are downloaded to the sources directory. This sets up the recipes that are used to build the project. The following example shows how to download the NXP/Freescale Yocto Project Community BSP recipe layers. For this example, a directory called fsl-release-bsp is created for the project.

Use the stable branch "jethro":

```console
 mkdir yocto-karo-fcb && cd yocto-karo-fcb
 repo init -u https://github.com/karo-electronics/fsl-community-bsp-platform -b jethro
 repo sync
```

When this process is completed, the source code is checked out into the
directory "sources" under the working directory, which is in the example above
"fsl-community-bsp".

You can update the source code of all by performing a repo synchronization,
with the command "repo sync". User should update to the latest codebase
periodically. But at least after a prolonged timespan an update is strongly
recommended.

If errors occur during repo initialization, try deleting the .repo directory
and running the repo initialization command again.

## Ka-Ro patches

The patches needed for compiling the Ka-Ro flavoured Yocto are already included
in the source tree.

* Download the karo archive
```console
  wget https://www.karo-electronics.de/fileadmin/download/yocto/fsl-community-bsp-jethro-karo-2016-03-16.tgz
```
* Extract files onto the FSL Community BSP tree
```console
 tar xzf fsl-community-bsp-jethro-karo-2016-03-16.tgz
```
## Choosing a machine

This release supports the following machines. Choose the machine configuration
that matches your TXCOM module.

### Ka-Ro TX CoM to Yocto Machine

Available Machines table
{|
| Table Name
|}


Set the above given as value in the machine configuration variable:
```console
MACHINE=<name-from-list-above>
```
## Set up the environment

The command to setup of the Yocto environment in it's general form looks like
the following:

 MACHINE=<MACHINE> source setup-environment <build-directory>

Where the user has to insert a value, fitting the desired target, from the
above table, and choose a name for the build directory to be created by the
"setup-environment" script, to look like such:

 MACHINE=tx6u-80x0 source setup-environment it-shall-be-named-appropriately

## Choosing an image target

Choose an image target to build, e.g.:

 core-image-minimal

This builds a minimal image consisting of:

	1. Kernel
	2. Bootloader
	3. RFS

The RFS (or: rootfs, or: root file system) in this instance is a low key file
system generally intended for either first steps and/or headless systems. It
includes all the general standard tools of a GNU/Linux distribution, but
missing features like a X11 server, etc.

Additional packages can be added to images as long as there is a recipe
provided for that package. A comprehensive listing of available layers can be
found for example here:

[[https://layers.openembedded.org/|https://layers.openembedded.org]]

## Building an image target

`bitbake <image>`

Examples:

* For building U-Boot only:

  `bitbake u-boot-karo`

* For building Linux kernel and kernel modules only:

  `bitbake linux-karo`

* For building core-image-minimal:

  `bitbake core-image-minimal`

To initialize the build environment when the session exits, run the following
command in the directory above the build directory:

`setup-environment <build directory>`

## Image Deployment

After a build is complete, the created image resides in the "tmp/deploy/images"
sub-directory. An image is, for the most part, specific to the machine set in
the environment setup. Each image build creates a U-Boot, a kernel, and an
image type based on the IMAGE_FSTYPES defined in the machine configuration
file.

The following files are created for Ka-Ro TX modules:

| Filename | Content |
| ---------| :-----: |
| `u-boot.bin` | U-Boot binary
| `uImage` | Kernel image
| `modules-<machine>.tgz` | Kernel modules
| `<image>-<machine>.tar.bz2` | RFS

Add 'init=/sbin/init' to the standard U-Boot kernel command line, e.g.:

`setenv append_bootargs 'init=/sbin/init'`

(the single qoutes, e.g. 'string', guarantee that U-Boot will not interpret
commands entered a variable values are not executed but taken "as-is."

The variable 'append_bootargs' is integrated into the U-Boot startup scripts by
default, allowing users to integrate variables without disturbing the default
behaviour by changes in the default settings.

Also will variable 'append_bootargs' mitigate the problem that the U-Boot
variables as saved in the environment are subject to a maxium string lenght.


Check [[https://www.karo-electronics.de/1277.html?&L=1,|MfgTool / Custom Files]] for
easy programming of deployed images!


---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](https://www.karo-electronics.de)  
Contact support: support@karo-electronics.de