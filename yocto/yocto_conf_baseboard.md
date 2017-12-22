# Baseboard
The baseboards are the users way to adapt the TX CoM to their product.
Baseboards under the Linux kernel are created in the Device Tree structure.
While there are already basic support for baseboards available these boards are
primarily either pre-setup products or based upon the Ka-Ro developerkit series,
either Starterkit 5v3, 5v5 or Mainboard 7 (MB7).

The Device Tree structure of the Linux kernel allows users to take the SoC
specific pre-defined basic structure and to enable or disable devices as needed;
depending on the devices used in the final product.

The DT offers syntax to allow for the appropriate setting of devices.


## Structure
The DT structure for the baseboards of Ka-Ro electronics can be found in the
tree as follows:

```console
\-- meta-fsl-arm-extra
	+-- conf
	[...]
	+-- recipes-bsp
	[...]
	\-- recipes-kernel
		\-- linux
			+-- linux-karo-4.1.15
			[...]
			|   +-- tx6
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
				[...]
```
As one can see there are three type of files, first **\*.h** then **\*.dts** and
finally **\*.dtsi** files.

Example:

```console
				|   |   +-- imx6qdl-tx6.dtsi
				|   |   \-- imx6qdl-tx6-gpio.h
				|   \-- txbase
				|       +-- aclavis
				|       |   +-- imx6dl-tx6-emmc-aclavis.dts
```

## Files
The purpose of these files is to setup the structure from which to create a so
DTB file (Device Tree Blob), which is the binary format of the DT which is
supplied to the Linux kernel and from where it know what and how to setup the
devices.

The files provided by Ka-Ro in the Yocto layer (Linux kernel recipe) are
non-standard conform to the Linux mainline kernel sources in how they are
structured and their entity relationship. On the other hand this allows the
users of the Yocto development framework to work with DT structure on a
simplified, easier to access level.

While users coming from the [Linux mainline][1] will find that the structure and
relations are by and large if not similar then at least based onto proper
mainline DT, as know, while having changes that will need to be taken into
account when adjusted to the user hardware.

The files provided by Ka-Ro for the NXP Yocto Linux kernel fall into these
categories:

* Header files

    The provided **\*.h** file (`imx6qdl-tx6-gpio.h`) is a specific created
		by Ka-Ro for the Yocto setup of the DT. It creates and provides shortcuts
		and unified naming scheme for the GPIO available on the TX CoM.

    This allows users to setup pins and in turn devices with user specific - in
		contrast to the TX Standard as implemented by Ka-Ro - pinout with ease by
		offering an abstracted, crossreferenced way of a data set for the pins.

    Example:

```c++
     [...]
     #define TX_GPIO_PIN52   &gpio1 16
     #define TX_GPIO_PIN53   &gpio1 17
     [...]
```


* DTSI files

    The **\*.dtsi** **(Device Tree Syntax Include)** files are include files and
    as such define the most basic structure of the DT. These files
    `(imx6qdl-tx6.dtsi | txbase-mb7-lvds.dtsi)` are generally SoC centric and
    thus off-limits for user edited content.

    The provided **\*.dtsi** files diverge from the standard as given by the
    [Linux mainline][1] kernel, yet are for users of the *Ka-Ro Yocto extension*
    a valid target of editing.


* DTS files

    From the [official][2] [reference][3]: "A textual representation of a
		devicetree consumed by the DTC." (DTC: Device Tree Compiler)

    The provided **\*.dts** **(Device Tree Syntax)** are the basic files for
		users editing and represent the most common target for edting and adjusting
		of adaptation to the users hardware.


## Yocto setup
When working with Yocto the user has to setup these

```console
linux-karo-x.y.ab/txbase/myboard/imx6s-tx6-emmc-myboard.dts
linux-karo-x.y.ab/txbase/myboard/txbase-myboard.dtsi
```

Example:

```console
sources/meta-fsl-arm-extra/recipes-kernel/linux/linux-karo-4.1.15/txbase/myboard/imx6s-tx6-emmc-myboard.dts
sources/meta-fsl-arm-extra/recipes-kernel/linux/linux-karo-4.1.15/txbase/myboard/txbase-myboard.dtsi
```

### Machine config
To compile the Yocto for a specific target the users use the `MACHINE=` variable
on the command line. Like so:

```console
MACHINE=tx6u-8030 source setup-environment <image>
```

Find out what images can be made with [Yocto Cheatsheet][5]

What this does, is that it will search the source tree for a config file name,
fitting the value given by the `MACHINE=` variable, in the above given
example: `MACHINE=tx6u-8030`.

```console
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
[...]
```

For a list of target values for `MACHINE=` for TX CoM please see this [Yocto
Machine Table][4]

The file looks like the follwoing:


`sources/meta-fsl-arm-extra/conf/machine/tx6u-8030.conf`

```config
#@TYPE: Machine
#@NAME: Ka-Ro electronics i.MX6DL TX6DL Computer-On-Module
#@SOC: i.MX6DL
#@DESCRIPTION: Machine configuration for Ka-Ro electronics TX6DL Computer-On-Module
#@MAINTAINER: Oliver Wendt <ow@karo-electronics.com>

require include/tx6-karo-common.inc
SOC_FAMILY = "mx6:mx6dl:tx6"

KERNEL_DEVICETREE ?= "imx6dl-tx6u-801x.dtb"
UBOOT_MACHINE = "tx6u-80x0_config"

TXTYPE = "imx6dl-tx6"
TXNVM = "nand"
```

These available config files will setup the environment for bitbake fitting with
the therein set variables. Here is where Ka-Ro electronics made some changes
that diverge to the normal way, as to allow for the way a TX CoM hardware can
be setup in relation to the features on the TX CoM and the baseboard.

### Kernel recipe
The recipes for the Ka-Ro kernel can be found here.

`sources/meta-fsl-arm-extra/recipes-kernel/linux/linux-karo_4.1.15.bb`

```python
# Add baseboard dtsi file(s)
SRC_URI += "file://txbase-${TXBASE}.dtsi;subdir=git/arch/arm/boot/dts"

# Add TX6 (machine) specific DTS file(s)
SRC_URI += "file://${TXTYPE}-${TXNVM}-${TXBASE}.dts;subdir=git/arch/arm/boot/dts"

KERNEL_DEVICETREE = "${TXTYPE}-${TXNVM}-${TXBASE}.dtb"
DEFAULT_PREFERENCE = "1"
KERNEL_IMAGETYPE = "uImage"

COMPATIBLE_MACHINE  = "(tx6[qus]-.*)"

TXTYPE = "imx6dl-tx6"
TXNVM = "nand"

SRC_URI += "file://txbase-${TXBASE}.dtsi;subdir=git/arch/arm/boot/dts"
```

#### Ka-Ro specific recipe data

```python
TXTYPE = "imx6dl-tx6"
TXNVM = "nand"

SRC_URI += "file://txbase-${TXBASE}.dtsi;subdir=git/arch/arm/boot/dts"
```

### Add TX6 (machine) specific DTS file(s)

```python
SRC_URI += "file://${TXTYPE}-${TXNVM}-${TXBASE}.dts;subdir=git/arch/arm/boot/dts"

KERNEL_DEVICETREE = "${TXTYPE}-${TXNVM}-${TXBASE}.dtb"
DEFAULT_PREFERENCE = "1"
KERNEL_IMAGETYPE = "uImage"

COMPATIBLE_MACHINE  = "(tx6[qus]-.*)"
```

Inline code

I think you should use an
`<addr>` element here instead.

---
## Footnotes & Appendix

[1]: https://www.kernel.org
[2]: https://www.devicetree.org/specifications/
[3]: https://github.com/devicetree-org/devicetree-specification-released
[4]: yocto-machine-table.md
[5]: yocto-cheatsheet.md

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
