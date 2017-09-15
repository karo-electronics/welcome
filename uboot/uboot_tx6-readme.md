U-Boot for TX6
==============

Building U-Boot
---------------

**Note:**  

There are currently 14 variants of the TX6 module, that require slightly
different U-Boot configurations. They are distinguished through the _`TX6`_
suffix _`Q`_, _`QP`_, _`U`_, _`S`_ or _`UL`_ and the numerical suffix of the
module name. Replace the '?' in the following description with the corresponding
digits from your TX6 module.


E.g. TX6Q-1010 => 'make tx6q-10x0_config'

Furthermore you can build an U-Boot image for use with the MfGTool by inserting
`_mfg` between the module number suffix and the `_config`: `make
tx6q-10x0_mfg_defconfig`

The 'x' in the module number suffix is a wildcard for a digit (currently '1' or
'3') denoting the HW revision of the module PCB. The 'tx6q-11x0_mfg_config' is
valid for the TX6Q-1110 and TX6Q-1130 modules. When chosing the right config for
your module you should make sure to select the closest matching config file.
E.g. for the TX6Q-1020 module the exact match 'tx6q-1020_defconfig' applies
rather than the wildcard match 'tx6q-11x0_defconfig'.


Unpacking the source
--------------------
mkdir u-boot
cd u-boot
tar -xjf /cdrom/U-Boot/TX6/sources/u-boot-src.tar.bz2

Alternatively you can access the current source via the git repository:
git://git.karo-electronics.de/karo-tx-uboot.git master


Compiling U-Boot
----------------

```console
export ARCH=arm
export CROSS_COMPILE=arm-cortexa9-linux-gnueabi-
make tx6q-1036_defconfig
make
```

**Note:**  
Replace the shown `make` command _`option`_ (`tx6q-1036_defconfig`) with the
appropriate TXCOM in question.  
If the TXCOM is known but not the default config, execute the following command
in the linux source directory:

`find . -type f -name \*tx6\*config`

to a result list similar to the following (shortend) result list:

```console
$ find . -type f -name \*tx6\*config
./configs/tx6q-1036_defconfig
./configs/tx6q-1036_mfg_defconfig
[...]
./configs/tx6qp-8037_defconfig
./configs/tx6qp-8037_mfg_defconfig
[...]
./configs/tx6s-8034_defconfig
./configs/tx6s-8034_mfg_defconfig
[...]
./configs/tx6u-8012_defconfig
./configs/tx6u-8012_mfg_defconfig
[...]
./configs/tx6ul-0010_defconfig
./configs/tx6ul-0010_mfg_defconfig
[...]
./configs/tx6ul-5012_sec_defconfig
```

Where the filename without path is the value for the `make` _`option`_.

Flashing U-Boot Image
---------------------
* NAND
* eMMC

For all TX6 modules equipped with NAND flash

If you want to replace a working U-Boot with a new version, you can
load the new U-Boot image via TFTP or SD-Card and write it to flash
with the 'romupdate' command.

If you want to revive a bricked module, U-Boot can be downloaded via
USB with the 'sbloader' tool in recovery boot mode (Bootmode jumper ST3
on Starterkit-5 baseboard closed). See TX6_U-Boot.pdf for details.

e.g.: /cdrom/Flashtools/Linux/sbloader/sbloader-x86_32 -m -s /cdrom/U-Boot/TX6/target/u-boot-tx6q-10x0.bin
(This command can be used from within the ARMSK-VM)


For modules equipped with eMMC
(TX6Q-1020, TX6Q-1036, TX6S-8x35, TX6U-8x33, TXUL-5011):
--------------------------------------------------------
The bootloader, U-Boot environment and DTB is stored in the first boot
partition of the eMMC device. The command sequence to update the
bootloader is (e.g. for TX6Q-1020):
TX6Q U-Boot > setenv autostart n
TX6Q U-Boot > tftp u-boot-tx6q-1020.bin
TX6Q U-Boot > mmc partconf 0 ${emmc_boot_ack} ${emmc_boot_part} ${emmc_boot_part}
TX6Q U-Boot > mmc write ${fileaddr} 0 400
TX6Q U-Boot > mmc partconf 0 ${emmc_boot_ack} ${emmc_boot_part} 0

You may also store an alternate boot image/FDT in the second boot
partition and switch between both images with the 'mmc partconf'
command:
    mmc partconf 0 ${emmc_boot_ack} 1 0
will boot from the first boot partition

    mmc partconf 0 ${emmc_boot_ack} 2 0
will boot from the second boot partition

For further information on the 'mmc partconf' command refer to
U-Boot/TX6_U-Boot.pdf on the Starterkit CD.


MfgTool
-------
For Windows users the application MfgTool allows the (re-)flashing of
U-Boot, environment and/or operating system. For more information
either see:

\U-Boot\TX6\TX6Q_U-Boot.pdf
\STK5_TX6Q_Quickstart_Guide.pdf
\Flashtools\Windows\Mfgtools-TX6...


U-Boot Features
---------------

Environment variables:
baseboard     {stk5-v3|stk5-v5} selects type of baseboard
	      'stk5-v5' setting disables USB Host mode on USBOTG port
	      and redefines the LCD0 pin as CAN transceiver control pin.
	      Strings not starting in 'stk5' prevent the STK5 specific
	      pad initialization to be done.

boot_mode     selects which boot script will be used by 'bootcmd' to
	      boot the application (Linux)
	      supported values:
	      nand: (default) load kernel from NAND partition 'linux'
			      and mount rootfs (fstype UBIFS)
			      from partition 'rootfs'.
	      mmc:	      load kernel from file 'uImage' on first
	      		      partition (FAT) on (first) SD/MMC card
			      and mount rootfs (fstype autodetected)
			      from second partition.
	      net:	      load kernel image via tftp (file uImage)
	      		      and mount rootfs via NFS. This requires
			      the additional variables 'nfsroot'
			      (path to rootfs on NFS server) and
			      'nfs_server' (hostname or IP address of
			      NFS server) to be set.
	      jffs2: (legacy) load kernel from NAND partition 'linux'
			      and mount rootfs (fstype JFFS2)
			      from partition 'rootfs'.

cpu_clk       <CPU freq [MHz]> CPU clock frequency set after boot.

otg_mode      [host|device|none] operation mode of the USBOTG port

splashimage   either: memory address (e.g. ${loadaddr}) of a BMP file
	      to be displayed instead of the built-in logo. Since NAND
	      flash is not accessible in a memory mapped fashion,
	      U-Boot will try to load the contents of the flash
	      partition 'logo.bmp' to the address given with
	      'splashimage'.

	      or: the name of an MTD partition, that contains a raw
	      dump of the frame buffer contents which will be loaded
	      to the framebuffer.

splashpos     (when 'splashimage' contains a memory address) the
	      position ('x,y') on the screen at which the BMP image
	      will be displayed.
	      Setting splashpos to 'm,m' will center the image on the
	      screen.

touchpanel    {tsc2007|edt-ft5x06|egalax_ts} type of touchpanel.
	      No touchpanel will be enabled when unset.

video_mode    <one of the display names from the Glyn Family Concept or
	      a video mode as understood by Linux fb_find_mode() function
              (e.g.: 640x480MR-24@60)>
	      LCD interface will be disabled when unset.

Note: Some variables (like 'cpu_clk' or 'splashimage') may render the
      board unbootable if incorrectly set. Therefore these variables
      will not be evaluated in case the board has been reset through a
      watchdog reset or <CTRL-C> is detected on the serial console
      during startup to give the user a chance to recover from this
      situation. You should press and hold <CTRL-C> before applying
      power to the module, for this to work.


The following variables are automatically created by U-Boot under
certain circumstances (these are unset otherwise and won't be created
from the saved environment upon boot):

safeboot=1    signifies, that <CTRL-C> has been detected early during
	      boot and the above noted safety measures have been
	      taken.

wdreset=1     signifies, that the module has been booted due to a
	      watchdog reset. This can be used to change the booting
	      behaviour depending on the reset source.

	      You can use these variables in boot scripts e.g. to
	      select a fallback boot script when a watchdog reset
	      occured:
setenv bootcmd 'run run bootcmd_${boot_mode}${wdreset} bootm_cmd'
With the default setting of 'boot_mode=nand' this will run either the
commands stored in 'bootcmd_nand' if no watchdog reset happened or
'bootcmd_nand1' when a watchdog reset was detected.

Note: If a watchdog reset occured, a soft reset should be performed
before booting the actual OS, to make sure that the board is correctly
configured (PMIC, cpu_clk, splash image).

The following variables are automatically removed from the
environment upon boot, since they are automagically set by certain
U-Boot commands and have only transient meaning:
bootargs     set up by the standard boot scripts

fileaddr     set by 'tftp', 'bootp' to the specified RAM address
	     ('${loadaddr} by default)

filesize     set by 'tftp', 'bootp' to the actual amount of data
	     loaded to RAM.

---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de