## U-Boot Environment Variables
## Transient Variables
The following variables are automatically removed from the environment upon
boot, since they are automagically set by certain U-Boot commands and have
only transient meaning:

* `bootargs`  
  set up by the standard boot scripts

* `fileaddr`  
  set by `tftp`, `bootp` to the specified RAM address
  (default: [`${loadaddr}`](#loadaddr))

* `filesize`  
  set by '`tftp`', '`bootp`' to the actual amount of data loaded to RAM.


## Default Static Variables
The following variables are statically compiled into the default environment of
U-Boot and used application of commands:

* `loadaddr`  
  The address where commands like `tftp`, `bootp` or `boot` by default load their
  payload data, e.g.:

  `tftp ${loadaddr} [${bootfile}]`

* `fdtaddr`  
  Standard address whereto U-Boot at boot time will load the FDT; it can also be
  the target of manual loads, e.g.:

  `tftp ${fdtaddr} <dtb-file-on-tftp-server>`


## Configuration Variables
* `baseboard`  
  `[stk5-v3|stk5-v5]` selects type of baseboard `stk5-v5` setting disables USB
  Host mode on USBOTG port and redefines the LCD0 pin as CAN transceiver control
  pin. Strings not starting in 'stk5' prevent the STK5 specific pad
  initialization to be done.

* `boot_mode`  
  selects which boot script will be used by `bootcmd` to boot the application
  (Linux) supported values:

	* `nand` (_**NAND: default**_)  
      load kernel from NAND partition `linux` and mount rootfs (fstype UBIFS)
      from partition `rootfs`.

	* `mmc` (_**eMMC: default**_)  
      load kernel from file `uImage` on first partition (FAT) on (first) SD/MMC
      card and mount rootfs (fstype autodetected) from second partition.

	* `net`  
      load kernel image via tftp (file `uImage`) and mount rootfs via NFS. This
      requires the additional variables 'nfsroot' (path to rootfs on NFS server)
      and `nfs_server` (hostname or IP address of the NFS server) to be set.

	* `jffs2`  
      (_legacy_) load kernel from NAND partition 'linux' and mount
      rootfs (fstype JFFS2) from partition 'rootfs'.

* `cpu_clk`  
  `[CPU freq {MHz}]` CPU clock frequency set after boot.

* `jtag_disable`  
  the i.MX6UL has the JTAG pins (`TRST`, `TCK`, `TMS`, `TDI`, `TDO`) multiplexed
  with other pin functions (sound chip interface on STK5). Operation of the JTAG
  interface requires these pins to be configured appropriately. U-Boot
  configures these pins as JTAG pins unless the variable `jtag_disable` is set
  to `y`.

* `otg_mode`  
  `[host|device|none]` operation mode of the USBOTG port

* `splashimage`  
  * _either:_  
     memory address (e.g. `${loadaddr}`) of a BMP file to be displayed
     instead of the built-in logo. Since NAND flash is not accessible in a
     memory mapped fashion, U-Boot will try to load the contents of the flash
	 partition `logo.bmp` to the address given with `splashimage`.

  * _or:_  
     the name of an MTD partition, that contains a raw dump of the frame buffer
     contents which will be loaded to the framebuffer.

* `splashpos`  
  when `splashimage` contains a memory address - the position ('x,y') in pixel
  on the screen at which the BMP image will be displayed.  
  Setting splashpos to `m,m` will center the image on the screen.

* `touchpanel`  
  `[tsc2007|edt-ft5x06|egalax_ts]` type of touchpanel.  
  _**No**_ touchpanel will be enabled when _**unset**_.

* `video_mode`  
  one of the display names from the _**Glyn Family Concept**_ or a video mode as
  understood by Linux `fb_find_mode()` function, e.g.: `640x480MR-24@60` LCD
  interface will be disabled when unset.

**Note:**
Some variables (like `cpu_clk` or `splashimage`) may render the board unbootable
if incorrectly set. Therefore these variables will not be evaluated in case the
board has been reset through a watchdog reset or `CTRL-C` is detected on the
serial console during startup to give the user a chance to recover from this
situation.
You should **press and hold** `CTRL-C` **before** applying power to the module,
for this to work.

## Case based variables
The following variables are automatically created by U-Boot under
certain circumstances (these are unset otherwise and won't be created
from the saved environment upon boot):

* `safeboot=1`  
  signifies, that `CTRL-C` has been detected early during  boot and the above
  noted safety measures have been taken.

* `wdreset=1`  
  signifies, that the module has been booted due to a watchdog reset. This can be
  used to change the booting behaviour depending on the reset source.

You can use these variables in boot scripts e.g. to select a fallback boot
script when a watchdog reset occured:

`setenv bootcmd 'run run bootcmd_${boot_mode}${wdreset} bootm_cmd'`  

With the default setting of `boot_mode=nand` this will run either the commands
stored in `bootcmd_nand` if no watchdog reset happened or `bootcmd_nand1` when a
watchdog reset was detected.

**Note:**  
If a watchdog reset occured, a soft reset should be performed before booting the
actual OS, to make sure that the board is correctly configured (PMIC, cpu_clk,
splash image).

---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de