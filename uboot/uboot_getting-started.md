# U-Boot

The TX CoM of the TX6 series are delivered with pre-installed U-Boot
firmware/bootloader. U-Boot supports several low-level-debugging options,
while also offering features like:

- - -

file download via Ethernet or serial X/Y/ZModem. These files can additionally
be stored into the NVM, NAND or eMMC depending on the TX CoM outfitting, to be
started by command or power-on.


## Getting started with U-Boot

Please be referred, for a more extensive description and more encompassing
view on U-Boot, to the ==[@Denx: *Das U-Boot
Manual*](http://www.denx.de/wiki/view/DULG/Manual)==

## Terminal connection

To connect TX-CoM a terminal program like Windows ==TeraTerm== or Unix based
==minicom==, must be running on the host PC. The communication parameters used
are:

```console
## Terminal connection

To connect TX-CoM a terminal program like Windows 'TeraTerm' or Unix based
'minicom', must be running on the host PC. The communication parameters used
are:

Baud rate:    115 200
Data bits:    8
Parity:       None
Stop bits:    1
Flow control: None
              (or: Xon/Xoff - disable: RTS/CTS (hardware handshake))
```

==

Note:
It's highly recommended to __turn on logging__ in the terminal program. After
power up or reset, output of U-Boot will appear resembling this e.g.:

==

U-Boot startup/reset output

```console
U-Boot 2012.04.01-10520-g7156867 (Nov 05 2012 - 15:42:14)
CPU:   Freescale i.MX53 rev2.1 at 800 MHz
Reset cause: SOFT
Board: Ka-Ro TX53-xx30
DRAM:  512 MiB
NAND:  128 MiB
MMC:   FSL_SDHC: 0, FSL_SDHC: 1
No DTB in flash; using default DTB
Baseboard: stk5-v3
Net:   FEC
Hit any key to stop autoboot:  0
```
# U-Boot commands

Subsequently are some of the most important commands of U-Boot being
described. Using the ==`help`== (or ==`?`==) command will print a list of all
available commands for the system, also ==`help`== (or ==`?`==) will show the
specifics for each single command.

All commands can be abbreviated to the shortest string that uniquely
identifies each command (e.g. `sa` == `saveenv`, `era` == `erase` or `re` ==
`reset`.

U-Boot will auto-complete the commands by pressing the ==`TAB`==
key. Respectively it will complete to the least common denominator and show a
list of commands, while allowing to auto-complete step-by-step.

The features of U-Boot are configurable and can depend on the TX Series CoM
basis, such that some TX series CoM might present the user different
availability of commands. Ka-Ro strives to configure U-Boot to the highest
possible commonalities. In such a case please also refer to the TX Series CoM
specific U-Boot documentation under **please_insert_here**. Please also use
the `help` (or `?`) command to find out more about your configuration's
commands.

Also note that above described feature-set is subject to change and defined at
compile time. For a general introduction to possible changes and customization
please refer to **please_insert_here**, Chapter **please_insert_here**.

All U-Boot commands (exceptions noted) expect numbers to be entered in
hexadecimal input format; therefore a leading `0x` prefix is not required.


## Overview of commands
```console
?         - alias for 'help'
base      - print or set address offset
bdinfo    - print Board Info structure
bmp       - manipulate BMP image data
boot      - boot default, i.e., run 'bootcmd'
bootce    - Boot a Windows CE image from memory
bootd     - boot default, i.e., run 'bootcmd'
bootm     - boot application image from memory
bootp     - boot image via network using BOOTP/TFTP protocol
ceconnect - Set up a connection to the CE host PC over TCP/IP and download the run-time image
chpart    - change active partition
clocks    - display clocks
cls       - clear screen
cmp       - memory compare
coninfo   - print console devices and information
cp        - memory copy
crc32     - checksum calculation
dcache    - enable or disable data cache
dhcp      - boot image via network using DHCP/TFTP protocol
echo      - echo args to console
editenv   - edit environment variable
env       - environment handling commands
ext2load  -  load binary file from a Ext2 filesystem
ext2ls    - list files in a directory (default /)
fatinfo   - print information about filesystem
fatload   - load binary file from a dos filesystem
fatls     - list files in a directory (default /)
fbdump    - dump framebuffer contents to flash
fdt       - flattened device tree utility commands
go        - start application at address 'addr'
help      - print command description/usage
iim       - IIM sub system
icache    - enable or disable instruction cache
iminfo    - print header information for application image
imxtract  - extract a part of a multi-image
itest     - return true/false on integer compare
loadb     - load binary file over serial line (kermit mode)
loads     - load S-Record file over serial line
loady     - load binary file over serial line (ymodem mode)
loop      - infinite loop on address range
md        - memory display
mdio      - MDIO utility commands
mii       - MII utility commands
mm        - memory modify (auto-incrementing address)
mmc       - MMC sub system
mmcinfo   - display MMC info
mtdparts  - define flash/nand partitions
mtest     - simple RAM read/write test
mw        - memory write (fill)
nand      - NAND sub-system
nboot     - boot from NAND device
nfs       - boot image via network using NFS protocol
nm        - memory modify (constant address)
ping      - send ICMP ECHO_REQUEST to network host
printenv  - print environment variables
reset     - Perform RESET of the CPU
run       - run commands in an environment variable
saveenv   - save environment variables to persistent storage
setenv    - set environment variables
sleep     - delay execution for some time
source    - run script from memory
tftpboot  - boot image via network using TFTP protocol
time      - run commands and summarize execution time
version   - print monitor, compiler and linker version
```

### Commands and explanations
For a complete list of commands and their explanations please be referred to the official documentation, available here:

[@Denx: *Das U-Boot Manual*](http://www.denx.de/wiki/view/DULG/Manual)

---

[Ka-Ro electronics GmbH](http://www.karo-electronics.de)

Contact support: support@karo-electronics.de
