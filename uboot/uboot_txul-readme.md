# U-Boot for TXUL

---
This is just the normal README, tweaked to be markdown.

---

## Building U-Boot

**Note:**  
There are currently 2 variants of the TXUL module, that require slightly
different U-Boot configurations. They are distinguished through the numerical
suffix of the module name. Replace the `?` in the following description with the
corresponding digits from your TXUL module:

TXUL-0010 => `make tx6ul-0010_config`  
TXUL-0011 => `make tx6ul-0011_config`  

Furthermore you can build an U-Boot image for use with the _MFGTool_ by
inserting `_mfg` between the module number suffix and the `_config`:

`make tx6ul-0010_mfg_config`

The first digit of the module name suffix may be `0` for the first batch of
engineering samples or `5` for the final production modules. The config file
names do not reflect this distinction, but always have a `0` in this place. Thus
`tx6ul-0010_defconfig` matches the (legacy) _TXUL-0010_ **and** the current
_TXUL-5010_ modules.


## Unpacking the source

```console
mkdir u-boot
cd u-boot
tar -xjf /cdrom/U-Boot/TXUL/sources/u-boot-src.tar.bz2
```

Alternatively you can access the current source via the git repository:

```console
git://git.karo-electronics.de/karo-tx-uboot.git master
```


## Compiling U-Boot

```console
export ARCH=arm
export CROSS_COMPILE=arm-cortexa7-linux-gnueabi-
make tx6ul-001?_config            (see above Note!)
make
```

## Flashing U-Boot Image

* For TXUL modules equipped with NAND flash (TXUL-0010, TXUL-5010):

  If you want to replace a working U-Boot with a new version, you can
  load the new U-Boot image via TFTP or SD-Card and write it to flash
  with the `romupdate` command.

  If you want to revive a bricked module, U-Boot can be downloaded via
  USB with the `sbloader` tool in recovery boot mode (Bootmode jumper `ST3`
  on Starterkit-5 baseboard closed). See TXUL_U-Boot.pdf for details.

  E.g.:  
  ``` console
  /cdrom/Flashtools/Linux/sbloader/sbloader-x86_32 -m -s /cdrom/U-Boot/TXUL/target/u-boot-tx6ul-0010.bin
  ```
  (This command can be used from within the ARMSK-VM)


* For modules equipped with eMMC (TXUL-0011, TXUL-5011):  

  The bootloader, U-Boot environment and DTB is stored in the first boot
  partition of the eMMC device. The command sequence to update the
  bootloader is:

  ```console
  TX6Q U-Boot > setenv autostart n
  TX6Q U-Boot > tftp u-boot-tx6ul-0011.bin
  TX6Q U-Boot > mmc partconf 0 ${emmc_boot_ack} ${emmc_boot_part} ${emmc_boot_part}
  TX6Q U-Boot > mmc write ${fileaddr} 0 400
  TX6Q U-Boot > mmc partconf 0 ${emmc_boot_ack} ${emmc_boot_part} 0
  ```

  You may also store an alternate boot image/FDT in the second boot
  partition and switch between both images with the ```mmc partconf```
  command:

      `mmc partconf 0 ${emmc_boot_ack} 1 0`

  will boot from the first boot partition

      `mmc partconf 0 ${emmc_boot_ack} 2 0`

  will boot from the second boot partition

  For further information on the `mmc partconf` command refer to
  U-Boot/TX6_U-Boot.pdf on the Starterkit CD.


## MfgTool

For Windows users the application MfgTool allows the (re-)flashing of
U-Boot, environment and/or operating system. For more information
either see:

```console
\U-Boot\TXUL\TXUL_U-Boot.pdf
\STK5_TXUL_Quickstart_Guide.pdf
\Flashtools\Windows\Mfgtools-TX6...
```

## U-Boot Features
### Environment variables:
* `baseboard`  
  `{stk5-v3|stk5-v5}` selects type of baseboard `stk5-v5` setting disables USB
  Host mode on USBOTG port and redefines the LCD0 pin as CAN transceiver control
  pin. Strings not starting in 'stk5' prevent the STK5 specific pad
  initialization to be done.

* `boot_mode`  
  selects which boot script will be used by 'bootcmd' to boot the application
  (Linux) supported values:

	* `nand`: (**default**) load kernel from NAND partition 'linux'
			      and mount rootfs (fstype UBIFS)
			      from partition 'rootfs'.
	      * `mmc`:	      load kernel from file 'uImage' on first
	      		      partition (FAT) on (first) SD/MMC card
			      and mount rootfs (fstype autodetected)
			      from second partition.
	      * `net`:	      load kernel image via tftp (file uImage)
	      		      and mount rootfs via NFS. This requires
			      the additional variables 'nfsroot'
			      (path to rootfs on NFS server) and
			      'nfs_server' (hostname or IP address of
			      NFS server) to be set.
	      * `jffs2`: (legacy) load kernel from NAND partition 'linux'
			      and mount rootfs (fstype JFFS2)
			      from partition 'rootfs'.

* `cpu_clk`       <CPU freq [MHz]> CPU clock frequency set after boot.

* `jtag_disable`  the i.MX6UL has the JTAG pins (TRST, TCK, TMS, TDI, TDO)
	      multiplexed with other pin functions (sound chip
	      interface on STK5). Operation of the JTAG interface
	      requires these pins to be configured
	      appropriately. U-Boot configures these pins as JTAG pins
	      unless the variable 'jtag_disable' is set to 'y'.

* `otg_mode`      [host|device|none] operation mode of the USBOTG port

* `splashimage`   either: memory address (e.g. ${loadaddr}) of a BMP file
	      to be displayed instead of the built-in logo. Since NAND
	      flash is not accessible in a memory mapped fashion,
	      U-Boot will try to load the contents of the flash
	      partition 'logo.bmp' to the address given with
	      'splashimage'.

	      or: the name of an MTD partition, that contains a raw
	      dump of the frame buffer contents which will be loaded
	      to the framebuffer.

* `splashpos`     (when 'splashimage' contains a memory address) the
	      position ('x,y') on the screen at which the BMP image
	      will be displayed.
	      Setting splashpos to 'm,m' will center the image on the
	      screen.

* `touchpanel`    {tsc2007|edt-ft5x06|egalax_ts} type of touchpanel.
	      No touchpanel will be enabled when unset.

* `video_mode`    <one of the display names from the Glyn Family Concept or
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