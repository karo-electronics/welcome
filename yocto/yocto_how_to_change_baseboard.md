# The first principle

It's not an embedded Linux distribution - it creates a custom one for you.

[!] stolen here: slideshare/yocto-something

## So, what is Yocto then?
_"The Yocto project is an open-source collaboration project. It provides
templates, tools and methods to help you create custom Linux-based systems for
embedded products regardless of hardware architecture."_

[!] stolen here: yocto/about

### Basics
Yocto - and _bitbake_ as its primary executive tool - can be used to, via the
recipes created, to essentially create everything, inclusive the kitchen
sink. ... But only if one knows what to tell _bitbake_ to do.

Users should have a basic understanding of what they do when they work with
_bitbake_ and other tools and structures of Yocto and thus it is strongly advised
to expose oneself to the simplest ways of creation of the part done. This will
allow for greater understanding of the matters at hand.

_Bitbake_ recipes are capable to extend, cut, enrich the creation process in many
shapes and forms, from either simple setting of variables what a recipe is in
it's most basic form to having your own framework within the Yocto framework.

It is therefore imperative that customers have the understanding of a simple
`make`, how to tweak `autoconf`, create `Makefile` files, or - on the other hand -
how to to chain commands, hand over of environment variables. This in turn means
that a healthy understanding of the standards, commands and requirements used to
set-up a GNU\Linux come in very handy.

The Yocto framework not only is "only available on" but also requires a
underlying GNU\Linux operating system to work.
We therefore strongly recommend to get acquainted with standards used in the
'* nix' world, like:

* FHS - File Hierarchy Standard
* make files
* Kernel Documentation
* grep
* find

The Yocto framework is "only available on" also requiring an underlying
GNU\Linux operating system (like the ARMSDK-VM) to work from.

### What does Ka-Ro's Yocto release do for you?

What Ka-Ro does with this Yocto release, is to give customers a basic, known to
work solution, having prepared a OOTB basis, 'cause as in the beginning simply
put:

Yocto is not an embedded Linux distribution - it creates a custom one for you.

You as a user need to setup up your distribution, that means you will need to
decide and setup what will be included in the distribution you create for
end-user.

As we, Ka-Ro electronics, as well only build upon - nay, tweak - the NXP
published sources for Yocto; there are some image presets available.


After you, the users, have installed and setup the Yocto you can use the data
offered by Ka-Ro electronics to setup an _initial_ development cycle. Giving
you a crystalisation point for further, more end-user/consumer market
orientated product development.

Which means you, our customers, having your own baseboard designed, be it
either with less, more or different devices to what is given by default on the
Ka-Ro development baseboard(s) (StarterKit 5v3, 5v5, 5v7 [a.k.a. MB7], Evalkit)
and can do drop-in adjustments to allow for your changes.

You can therefore rather quickly step up your development cycle to as with the
infrastructure created by Ka-Ro you can create a baseline software from which
all of your solutions can be derived.

Based upon the TX standard all customer baseboards can be drived from the data
files provided by Ka-Ro.

Be always aware:

It's not an Linux distribution - it creates a custom one for you.

#### How to create your own distribution

To create a distribution with Yocto Ka-Ro offers a basic setup that customers
can be used as a basis for the customer to edit and adapt to their own needs
and setup.

With the structure in the Yocto recipe for the kernel are a simplified and
compartemetalized base for the device configuration available to the customer.

The DT files as given by Ka-Ro are still following the simple syntax of the
Devicetree as outlined in the Kernel Documentation [1] or the offical DT
webpage [2][3].


### Understanding the tools used
The tools used in the development cycle are basic tools of any Linux
distribution:

VCS:
 `git`<br>
Editor:
 `emacs`

if they are not installed the integrated package system, which essentially all
majo Distributions have, will have it available to you on just a view commands.

---

_**Note:**  
Be aware that command line rulez, even when you get a GUI frontends, which are
usually just is a python/perl/tcl/json wrapper for the command line tools.
Experience shows that, while GUI frontends are good at common task and superb at
visualisation of relationships of commits and/or branches, it is preferable to
use the CLI tools as they generally offer more control._

---

More and/or other tools can be used, but are generally represent personal
preferences. Tools used can reach from simple CLI tools like 'nano' to the
full-fledge behemoths of resource hogs like e.g. Eclipse.

In this guide the editing and source management is done from the CLI and/or via
emacs editor, this will mitigate the problem of creating bad habits. Which is
kinda bad excuse when the software and hardware you build rams a 45 tonne truck
into the end of a traffic jam with full speed, or when your IOT devices become
the botnet of the day.

To put it into a internet meme: _Git Gud_.

### Commands
Hereafter commands you will need and which follow this simple structure:

`bitbake <package> <option> <parameter>`

```console
bitbake linux-karo -c cleansstate
bitbake linux-karo -c configure
bitbake linux-karo -c patch
bitbake linux-karo -c devshell
bitbake linux-karo -c menuconfig
```

show the environment:

`bitbake -e <package>`



### Structure
The structure of the files as given by Ka-Ro can be seen here, the relation-
ship between each are described further down.

```console
 .
 \-- meta-fsl-arm-extra
     +-- conf
     |   \-- machine
     |       +-- include
     |       |   +-- tx6-karo-common.inc
     |       |   \-- tx6ul-karo-common.inc
     |       +-- tx6q-1030.conf
     |       +-- tx6q-1036.conf
     |       +-- tx6q-1130.conf
     |       +-- tx6q-8037.conf
     |       +-- tx6s-8034.conf
     |       +-- tx6s-8035.conf
     |       +-- tx6s-8134.conf
     |       +-- tx6s-8135.conf
     |       +-- tx6u-8030.conf
     |       +-- tx6u-8033.conf
     |       +-- tx6u-8130.conf
     |       +-- tx6u-8133.conf
     |       +-- txul-5010.conf
     |       \-- txul-5011.conf
     +-- recipes-bsp
     |   \-- u-boot
     |       +-- u-boot-karo
     |       |   +-- mx6-clock-div.patch
     |       |   \-- mx6-soc-l2en.patch
     |       \-- u-boot-karo_git.bb
     \-- recipes-kernel
         \-- linux
             +-- linux-karo-4.1.15
             |   +-- imx
             |   |   +-- bcmhd_gcc6_indent_warning_error_fix.patch
             |   |   +-- gcc6_integrate_fix.patch
             |   |   +-- gpu-viv_gcc6_indent_warning_error_fix.patch
             |   |   +-- reset_ethernet_phy_whenever_the_enet_out_clock_is_being_enabled.patch
             |   |   \-- set-enet_ref_clk-to-50-mhz.patch
             |   +-- tx6
             |   |   +-- defconfig
             |   |   +-- imx6qdl-tx6.dtsi
             |   |   \-- imx6qdl-tx6-gpio.h
             |   \-- txbase
             |       +-- aclavis
             |       |   +-- imx6dl-tx6-emmc-aclavis.dts
             |       |   +-- imx6dl-tx6-nand-aclavis.dts
             |       |   +-- imx6q-tx6-emmc-aclavis.dts
             |       |   +-- imx6q-tx6-nand-aclavis.dts
             |       |   +-- imx6s-tx6-emmc-aclavis.dts
             |       |   +-- imx6s-tx6-nand-aclavis.dts
             |       |   \-- txbase-aclavis.dtsi
             |       +-- aclavis-lvds
             |       |   +-- imx6dl-tx6-emmc-aclavis-lvds.dts
             |       |   +-- imx6dl-tx6-nand-aclavis-lvds.dts
             |       |   +-- imx6q-tx6-emmc-aclavis-lvds.dts
             |       |   +-- imx6q-tx6-nand-aclavis-lvds.dts
             |       |   +-- imx6s-tx6-emmc-aclavis-lvds.dts
             |       |   +-- imx6s-tx6-nand-aclavis-lvds.dts
             |       |   \-- txbase-aclavis-lvds.dtsi
             |       +-- evalkit
             |       |   +-- imx6dl-tx6-emmc-evalkit.dts
             |       |   +-- imx6dl-tx6-nand-evalkit.dts
             |       |   +-- imx6q-tx6-emmc-evalkit.dts
             |       |   +-- imx6q-tx6-nand-evalkit.dts
             |       |   +-- imx6s-tx6-emmc-evalkit.dts
             |       |   +-- imx6s-tx6-nand-evalkit.dts
             |       |   \-- txbase-evalkit.dtsi
             |       +-- mb7
             |       |   +-- imx6dl-tx6-emmc-mb7.dts
             |       |   +-- imx6dl-tx6-nand-mb7.dts
             |       |   +-- imx6q-tx6-emmc-mb7.dts
             |       |   +-- imx6q-tx6-nand-mb7.dts
             |       |   +-- imx6s-tx6-emmc-mb7.dts
             |       |   +-- imx6s-tx6-nand-mb7.dts
             |       |   \-- txbase-mb7.dtsi
             |       +-- mb7-lvds
             |       |   +-- imx6dl-tx6-emmc-mb7-lvds.dts
             |       |   +-- imx6dl-tx6-nand-mb7-lvds.dts
             |       |   +-- imx6q-tx6-emmc-mb7-lvds.dts
             |       |   +-- imx6q-tx6-nand-mb7-lvds.dts
             |       |   +-- imx6s-tx6-emmc-mb7-lvds.dts
             |       |   +-- imx6s-tx6-nand-mb7-lvds.dts
             |       |   \-- txbase-mb7-lvds.dtsi
             |       \-- myboard
             |           +-- imx6s-tx6-emmc-myboard.dts
             |           \-- txbase-myboard.dtsi
             +-- linux-karo_4.1.15.bb
             +-- linux-karo-4.4.15
             |   +-- imx6dl-tx6s-8134.dts
             |   +-- imx6dl-tx6s-8135.dts
             |   +-- imx6dl-tx6u-8133.dts
             |   +-- tx6
             |   |   \-- defconfig
             |   \-- txul
             |       \-- defconfig
             \-- linux-karo_4.4.15.bb
```

### Changing the DT

```console
        \-- recipes-kernel
            \-- linux
                +-- linux-karo-4.1.15
                |   +-- imx
                |   |   +-- bcmhd_gcc6_indent_warning_error_fix.patch
                |   |   +-- gcc6_integrate_fix.patch
                |   |   +-- gpu-viv_gcc6_indent_warning_error_fix.patch
                |   |   +-- reset_ethernet_phy_whenever_the_enet_out_clock_is_being_enabled.patch
                |   |   \-- set-enet_ref_clk-to-50-mhz.patch
                |   +-- tx6
                |   |   +-- defconfig
                |   |   +-- imx6qdl-tx6.dtsi
                |   |   \-- imx6qdl-tx6-gpio.h
                |   \-- txbase
                |       +-- aclavis
                |       |   +-- imx6dl-tx6-emmc-aclavis.dts
                |       |   +-- imx6dl-tx6-nand-aclavis.dts
                |       |   +-- imx6q-tx6-emmc-aclavis.dts
                |       |   +-- imx6q-tx6-nand-aclavis.dts
                |       |   +-- imx6s-tx6-emmc-aclavis.dts
                |       |   +-- imx6s-tx6-nand-aclavis.dts
                |       |   \-- txbase-aclavis.dtsi
                |       +-- aclavis-lvds
                |       |   +-- imx6dl-tx6-emmc-aclavis-lvds.dts
                |       |   +-- imx6dl-tx6-nand-aclavis-lvds.dts
                |       |   +-- imx6q-tx6-emmc-aclavis-lvds.dts
                |       |   +-- imx6q-tx6-nand-aclavis-lvds.dts
                |       |   +-- imx6s-tx6-emmc-aclavis-lvds.dts
                |       |   +-- imx6s-tx6-nand-aclavis-lvds.dts
                |       |   \-- txbase-aclavis-lvds.dtsi
                |       +-- evalkit
                |       |   +-- imx6ul-tx6-emmc-evalkit.dts
                |       |   +-- imx6ul-tx6-nand-evalkit.dts
                |       |   \-- txbase-evalkit.dtsi
                |       +-- mb7
                |       |   +-- imx6dl-tx6-emmc-mb7.dts
                |       |   +-- imx6dl-tx6-nand-mb7.dts
                |       |   +-- imx6q-tx6-emmc-mb7.dts
                |       |   +-- imx6q-tx6-nand-mb7.dts
                |       |   +-- imx6s-tx6-emmc-mb7.dts
                |       |   +-- imx6s-tx6-nand-mb7.dts
                |       |   +-- imx6ul-tx6-emmc-mb7.dts
                |       |   +-- imx6ul-tx6-nand-mb7.dts
                |       |   \-- txbase-mb7.dtsi
                |       \-- mb7-lvds
                |           +-- imx6dl-tx6-emmc-mb7-lvds.dts
                |           +-- imx6dl-tx6-nand-mb7-lvds.dts
                |           +-- imx6q-tx6-emmc-mb7-lvds.dts
                |           +-- imx6q-tx6-nand-mb7-lvds.dts
                |           +-- imx6s-tx6-emmc-mb7-lvds.dts
                |           +-- imx6s-tx6-nand-mb7-lvds.dts
                |           \-- txbase-mb7-lvds.dtsi
                +-- linux-karo_4.1.15.bb
```

For more details about the device tree please see the following [1][3].

The base structure for the Ka-Ro extension to the FSL-Community-BSP can be seen
in the above diagram.

It follows rules that are as follows:

linux-karo_4.1.15.bb
	- Basic Recipe for the Linux 4.1

+-- tx6
	- this being the sub directory for modules in question

This directory includes the basic device listing and the

|   +-- defconfig
|   +-- imx6qdl-tx6.dtsi
|   \-- imx6qdl-tx6-gpio.h


\-- txbase
	- TX Baseboards

    \-- mb7-lvds
	- Base board

	+-- imx6dl-tx6-emmc-mb7-lvds.dts
	+-- imx6dl-tx6-nand-mb7-lvds.dts
	[...]

---
## Footnotes & References
[1] Kernel Source -> Folder: Documentation/bindings
[2] Devicetree.org
[3] devicetree.org
[4] git docu

In the first age, in the first battle, when the shadows first lengthened, one
stood. Burned by the embers of Armageddon, his soul blistered by the fires of
Hell and tainted beyond ascension, he chose the path of perpetual torment. In
his ravenous hatred he found no peace; and with boiling blood he scoured the
umbral plains seeking vengeance against the dark lords who had wronged him. He
wore the crown of the Night Sentinels, and those that tasted the bite of his
sword named him.. the Doom Slayer.

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
