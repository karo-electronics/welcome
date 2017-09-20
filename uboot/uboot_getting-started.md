# U-Boot
The TXCOM of the TX6 ([Bootloader](#bootloader)) series are delivered with
pre-installed U-Boot firmware/bootloader.

U-Boot supports several features like:

* low-level-debugging options
* file download via:
    * Ethernet
    * Serial
        * XModem
        * YModem
        * ZModem
* NVM
    * NAND
    * eMMC (internal)
    * SD-Card (external)

## Getting started with U-Boot
For a extensive documentation and a more encompassing view on U-Boot features,
please be referred to the official manual, as available
[here @Denx: *Das U-Boot Manual*][denx-man] (http://www.denx.de/wiki/view/DULG/Manual).

* [Commands](#u-boot-commands)
* [Environment](uboot/uboot_environment-variables.md)
    * [Enviroment Printout](uboot/uboot_environment-printout.md)


## Terminal connection
To connect TXCOM a terminal program like Windows `TeraTerm` or Unix based
`minicom`, must be running on the host PC and following communication
parameters been set:

```console
Baud rate:    115 200
Data bits:    8
Parity:       None
Stop bits:    1
Flow control: None (or: Xon/Xoff)
              (disable: RTS/CTS (hardware handshake))
```

**Note:**  
It's highly recommended to __turn on logging__ in the terminal program.

## Power-on Reset
After power up (a.k.a. POR) or reset, output of U-Boot will
appear resembling this e.g. (example output):

```console
U-Boot 2015.10-rc2-04959-g9c86706 (Jul 11 2016 - 12:39:17 +0200)

CPU:         Freescale i.MX6DL rev1.1 at 792 MHz
Temperature: Industrial grade (-40C to 105C) at 42C - calibration data 0x5b051f69
Reset cause: SOFT
I2C:   ready
DRAM:  1 GiB
Board: Ka-Ro TX6U-8010
PMIC: LTC3676
VDDCORE set to 1421mV
VDDSOC  set to 1421mV
VDDIO   set to 3307mV
NAND:  128 MiB
MMC:   FSL_SDHC: 0 (SD), FSL_SDHC: 1
IPU HW Rev: 4
Baseboard: stk5-v3
MAC addr from fuse: 00:0c:c6:7a:39:60
Net:   FEC
Hit any key to stop autoboot:  0
TX6DL U-Boot >
```

## U-Boot Commands
Subsequently are some of the most important commands of U-Boot being described.
Using the `help` (or `?`) command will print a list of all available commands
for the system, also `help` (or `?`) will show the specifics for each single
command.

All commands can be abbreviated to the shortest string that uniquely identifies
each command (e.g. `sa` == `saveenv`, `era` == `erase` or `re` == `reset`).

U-Boot will by pressing the `TAB` key auto-complete the commands. Respectively
it will complete to the least common denominator and show a list of commands,
while allowing to auto-complete step-by-step.

The features of U-Boot are configurable and can depend on the TXCOM basis, such
that some TXCOM might present the user different availability of commands. Ka-Ro
strives to configure U-Boot to the highest possible commonalities. Please also
use the `help` (or `?`) command to find out more about your configuration's
commands.

Also note that above described feature-set is subject to change and defined at
compile time.

All U-Boot commands (exceptions noted, see `help`) expect numbers to be entered
in hexadecimal input format; therefore a leading `0x` prefix is not required.

### Overview of Commands
[Find it here](uboot/uboot_command-listing.md)

---
## Footnotes & Appendix
<a id="bootloader">Bootloader:</a>  
"Das U-Boot" is, besides for the TX6 series, also available as bootloader for
the TXCOM: TX28, TX48, TX51, TX53, TXSD


[denx-man]: http://www.denx.de/wiki/view/DULG/Manual

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
