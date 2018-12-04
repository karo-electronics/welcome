.. role:: raw-html-m2r(raw)
   :format: html


Restoring the factory installation
==================================

Following are some basic instructions and data for setting up a TX53 CoM to
factory installation; please also refer to the
%%\ *%%%%*\ %%'U-Boot_Guide.pdf'%%\ *%%%%*\ %% for more. The TX53 CoM specific
'//Recovery Boot//' option are described in Ch. %%\ *%%%%*\ %%2.1.4%%\ *%%%%*\ %%
(%%\ *%%%%*\ %%Flash Program%%\ *%%%%*\ %%) and Ch. %%\ *%%%%*\ %%2.1.6%%\ *%%%%*\ %%
(%%\ *%%%%*\ %%Recovery Boot%%\ *%%%%*\ %%).

Requirements
============

Windows Host:%%\ *%%%%*\ %%Terminal Setup%%\ *%%%%*\ %%
%%\ *%%%%*\ %%TFTP Server Setup%%\ *%%%%*\ %%

Linux Host:%%\ *%%%%*\ %%Terminal Setup%%\ *%%%%*\ %%

Terminal Setup
==============

%%*%%Connect UART1 (Starterkit 5 ST9) to a COM port of your host PC

For the settings please refer to Chapter %%\ *%%%%*\ %%1.2%%\ *%%%%*\ %%
(%%\ *%%%%*\ %%Terminal connection%%\ *%%%%*\ %%).

TFTP Server Setup
=================

%%*%%Connect Ethernet (Starterkit 5 ST23) to your network

Software download via TFTP protocol is recommended, because download via
X/Y/ZModem protocols are slow. To do this, any Linux or Windows based TFTP
server software may be used. On the CD, enclosed in this StarterKit, you will
find a TFTP server evaluation software from Walusoft Ltd. (for Windows NT). This
unregistered evaluation version has the following restrictions:\ %%*%%Max 2
simultaneous clients

%%*%%Max 10 transfers before quitting

%%*%%No firewall support

%%*%%No Create Paths

%%*%%Fixed to port 69

%%\ *%%Server stops working after one hour and needs to be manually restarted
After installation you have to start the TFTP service to be able to configure it
from the control panel: %%*\ %%Choose Start, choose Settings and choose Control
Panel.

%%\ *%%Choose Services, select TFTPSrvc2001 from the list, and choose Start
Alternatives for the Walusoft Ltd. TFTP server, either OSS or Free Software,
are, e.g.:
%%*\ %%[[http://tftpd32.jounin.net/|TFTPD]][[http://tftpd32.jounin.net/|(x32 &
x64)]] (also includes a DHCP server)

%%*%%[[http://www.solarwinds.com/products/freetools/free_tftp_server.aspx|SolarWinds TFTP]]

Flashing U-Boot
===============

U-Boot can be reset to factory installation by either of three ways; TFTP, UART
or USB. While using TFTP is the fastest way it can only be done while U-Boot is
**functional**\ , while the USB and UART modes are mainly to be used in case
U-Boot is **not functional** any more, and are referred to as '//Recovery
Boot//' option. USB is the recommended

The TX53 Series CoM's '//Recovery Boot//' option is provided by the tool
'''flash_program''', which is available in the folder '''Flashtools''' folder on
the CD, either as Linux or Windows version (using Cygwin). For the more general
way of flashing over TFTP please consult the
%%\ *%%%%*\ %%'U-Boot_Guide.pdf'%%\ *%%%%*\ %%.

Flash Program
=============

%%\ *%%Connect USB (Starterkit 5 ST21) to a USB port of your host PC
%%*\ %%%%\ *%%[recommended]%%*\ %%%%*%%

**or**

%%\ *%%Connect UART%%*\ %%%%\ *%%2%%*\ %%%%\ *%% (Starterkit 5 %%*\ %%%%\ *%%ST5%%*\ %%%%\ *%%) to
a COM port of your host PC %%*\ %%%%\ *%%[requires: D-Sub adapter]%%*\ %%%%*%%

The '''flash_program''' tool is used to install an U-Boot image to the TX53
target platform; either via USB or UART. There are two versions included on the
StarterKit CD, a Linux or a Windows host (using Cygwin) version. Connect the
TX53-StarterKit 5 assembly as recommended over the //'//USB Mini-A/B (ST21) or
the UART2 (ST5) port, latter a D-Sub adapter is required, to the host PC.

The software has also interactive capabilities, as well as other commands and
options, to work with the TX CoM. Please also be aware that different variants
of the TX53 CoM only work if '''flash_program''' is called with the correct
defined option for processor type (''"-P")''. For more please refer to:

''"Flashtools/Linux/Flashprogram/README "''
Example output on a Linux host (TX53-8130, USB, programming U-Boot):

''$ ./flash_program -U -P mx53-v3 prog 0 u-boot-tx53-xx30.bin ''
''flash_program V1.1 for i386 built: Feb 23 2012 10:18:53 ''
''Programming file: 'u-boot-tx53-xx30.bin' at address 0x00000000 ''
''Bootstrap is running ''
''usb_bulk_read() returned -19 ''
''Failed to read USB data: -19 ''
''HAB Type: Development/Disable ''
''HAB Status: HAB_PASSED ''
''Reading silicon rev @ 63f98020 ''
''Initializing memory interface ''
''Sending 38912 byte 0 byte remaining ''
''Starting RKL at 70004000 ''
''USB comms init: Protocol error ''
''Programming flash from 0x00000000 to 0x00054e4b ''
''Flash Program successful!   ''
''BYE!''

ADSToolkit
==========

This tool-kit is a Windows only, GUI tool to upload U-Boot as well as Kernel
images onto the TX CoM, the users guide for it can be found (on CD) under:

``Flashtools/Windows/ADSToolkit/ATK_TX53_User_Guide.pdf``

Recovery Boot
=============

Make sure the BOOT_MODE jumper (ST3) is set and

no SD-Card is inserted Locate the ``u boot-tx53-xx3?.bin`` file (on
CD: ``U-Boot/u-boot-tx53-xx3?.bin``\ )

Note:\ :raw-html-m2r:`<br>`
The actual name of the ``.bin`` file depends on the TX53 CoM variant as
indented target. The last digit of the TXCOM number characterises the?

Connect the TX53 with either USB [recommended] or UART to the host
computer

Erase the entire NAND flash-memory:

``./flash_program -U -P mx53-v3 erase 0 0x8000000``

Program U-Boot on the TX53 with ``flash_program`` (either Linux or Windows
version):

``./flash_program -U -P mx53-v3 prog 0 /cdrom/U-Boot/u-boot-tx53-xx3?.bin``

Power down the module, make sure the BOOT_MODE jumper (ST3) is removed and
re-apply power to start from flash and hit any key to stop autoboot.

Note:\ :raw-html-m2r:`<br>`
Erasing the entire NAND Flash **will** cause this warning at startup:

.. code-block:: console

   Warning - bad CRC or NAND, using default environment

Save the defaults (environment, partitions table, etc.):
``saveenv``

The TX53 CoM is now in factory state and can be load the with Linux (or WinCE),
for this the usage of TFTP is recommended.

The setup and usage of TFTP is described in 'U-Boot_Guide.pdf' and
in 'Linux/README'

Note:\ :raw-html-m2r:`<br>`
Advanced users can simplify steps 4 and 5, combining them
or make use of the interactive mode.

Note:\ :raw-html-m2r:`<br>`
Non-factory resetting does **not** need to erase the NAND

Erase NAND memory partition
===========================

Before writing (again) a desired image file to the NAND memory, it is necessary
to erase the corresponding area. Use the command ``mtdparts`` to get a
list of the partitions, their names and their respective memory areas. Which
output should look similar to this, e.g.:

.. code-block:: console

   TX6DL U-Boot > mtdparts

   device nand0 <gpmi-nand>, # parts = 7
    #: name                size            offset          mask_flags
    0: u-boot              0x00100000      0x00020000      0
    1: env                 0x00060000      0x00120000      0
    2: linux               0x00600000      0x00180000      0
    3: rootfs              0x02000000      0x00780000      0
    4: userfs              0x05780000      0x02780000      0
    5: dtb                 0x00080000      0x07f00000      0
    6: bbt                 0x00080000      0x07f80000      1
   ECC stats for device nand0:
     corrected bit flips:     0
     uncorrectable errors:    0

   active partition: nand0,0 - (u-boot) 0x00100000 @ 0x00020000

   defaults:
   mtdids  : nand0=gpmi-nand
   mtdparts: mtdparts=gpmi-nand:1024k@0x20000(u-boot),384k(env),6m(linux),32m(rootfs),89600k(userfs),512k@0x7f00000(dtb),512k@0x7f80000(bbt)ro
   TX6DL U-Boot >

After choosing the target partition, using the command
``nand erase.part`` + ``<name>`` will erase the chosen partition; e.g. (rootfs):

.. code-block:: console

   TX6DL U-Boot > nand erase.part rootfs

   NAND erase.part: device 0 offset 0x780000, size 0x2000000
   Erasing at 0x2760000 -- 100% complete.
   OK

Configuring the network
^^^^^^^^^^^^^^^^^^^^^^^

To configure the network via `\ ``bootp`` <uboot/uboot_command-listing.md>`_\ , use the
following commands:

Prevent automatic loading of image files

.. code-block:: console

   setenv autoload no
   Configure network:
   bootp

After successful execution of the commands you should get messages like the
following:

.. code-block:: console

   TX6DL U-Boot > bootp
   BOOTP broadcast 1
   BOOTP broadcast 2
   BOOTP broadcast 3
   DHCP client bound to address 192.168.100.67 (937 ms)
   TX6DL U-Boot >

In case of ``autoload no`` not set, U-Boot will interpret the ``bootfile``
environment variable and try to load the file defined there, from the TFTP
server given in the variable ``serverip``\ , which by standard is set automatically
to the DHCP/BOOTP server by the ``bootp`` command (see above example).

For a manual configuration of the Ethernet you will need to set the following
environment variables to values fitting to your network:

.. code-block:: console

   # Set DNS IP
   set dnsip 192.168.0.1

   # Set the Gateway IP
   set gatewayip 192.168.0.2

   # Set the Host IP
   set ipaddr 192.168.0.21

   # Set the Netmask
   set netmask 255.255.255.0

   # Set TFTP server IP (TFTP Server == DHCP Server)
   set serverip 192.168.0.100

For more about configure the Ethernet manually and environment variables, please
see Chapter [[http://www.denx.de/wiki/view/DULG/UBootEnvVariables|5.10]] of the
U-Boot documentation:

`Chapter 5.10 <http://www.denx.de/wiki/view/DULG/UBootEnvVariables|http://www.denx.de/wiki/view/DULG/UBootEnvVariables>`_

Environment variables of factory installation
---------------------------------------------

The following list (subject to change) shows the status of the environment
variables after factory installation:

.. code-block:: console

   TX53 U-Boot > printenv
   autoload=no
   autostart=no
   baseboard=stk5-v3
   baudrate=115200
   bootargs=console=ttymxc0,115200 ro debug panic=1
   bootargs_mmc=run default_bootargs;set bootargs ${bootargs} root=/dev/mmcblk0p3 rootwait
   bootargs_nand=run default_bootargs;set bootargs ${bootargs} root=/dev/mtdblock3 rootfstype=jffs2
   bootargs_nfs=run default_bootargs;set bootargs ${bootargs} root=/dev/nfs ip=dhcp nfsroot=${serverip}:${nfsroot},nolock
   bootcmd=run bootcmd_nand
   bootcmd_mmc=set autostart no;run bootargs_mmc;mmc read ${loadaddr} 100 3000;run bootm_cmd
   bootcmd_nand=set autostart no;run bootargs_nand;nboot linux;run bootm_cmd
   bootcmd_net=set autostart no;run bootargs_nfs;dhcp;run bootm_cmd
   bootdelay=3
   bootfile=uImage
   bootm_cmd=fdt boardsetup;bootm ${loadaddr} - ${fdtaddr}
   cpu_clk=800
   default_bootargs=set bootargs console=ttymxc0,115200 ro debug panic=1 video=${video_mode} ${append_bootargs}
   ethact=FEC
   ethaddr=00:0c:c6:77:92:00
   fdtaddr=71000000
   fdtsize=00004be5
   loadaddr=78000000
   mtddevname=u-boot
   mtddevnum=0
   mtdids=nand0=mxc_nand
   mtdparts=mtdparts=mxc_nand:1m(u-boot),0x60000(env),4m(linux),16m(rootfs),256k(dtb),-(userfs)
   nfsroot=/tftpboot/rootfs
   otg_mode=device
   partition=nand0,0
   stderr=lcd
   stdin=serial
   stdout=lcd
   touchpanel=tsc2007
   ver=U-Boot 2012.04.01-10520-g7156867 (Nov 05 2012 - 15:42:14)
   video_mode=VGA-1:640x480MR-24@60
   Environment size: 1384/131068 bytes
   TX53 U-Boot >

Building U-Boot for TX53
========================

With the following commands U-Boot can be build successfully with the same
settings used for the respective release. For further information on building
U-Boot please refer to either *Building U-Boot* in U-Boot/README, or the general
README in the u-boot-src.tar.bz2 file.

Unpacking the source
--------------------

.. code-block:: console

   mkdir u-boot
   cd u-boot
   tar -xjf u-boot-src.tar.bz2

Compile U-Boot
==============

The following commands allow the user to compile U-Boot (with optional object
directory):

.. code-block:: console

   export ARCH=arm
   export CROSS_COMPILE=arm-cortexa8-linux-gnueabi-
   make tx53-xx3?_config [O=./build_u boot_tx##]
   make [O=./build_u boot_tx##]

** Important: **
The Command ``make tx53-xx3?_config`` is general example as there are currently
two variants of the TX53 module, which require slightly different U-Boot
configurations. They are distinguished through the last digit of the module
name. Replace the ** ``?`` ** in the given example with the corresponding number
from your TX CoM. E.g.:

TX53-8031 => ``make tx53-xx31_config``

Advanced users can also use the TAB auto-complete feature of Linux. The ARMSDK
VM offers some simplifications for the setup of a development environment, for
more please consult the documentation there.

When invoked correctly, these commands, either in the U-Boot source directory or
in the given object directory as defined by the option ``O=...``\ , will create the
relevant files for the TX53 CoM including following, e.g.:

.. code-block:: console

   u-boot
   u-boot.bin
   u-boot.lds
   u-boot.map
   u-boot.srec

The TX53 specific file ``u-boot.bin`` can then be started via ``flash_program`` or
installed in flash for NAND-boot.

**Note:**\ :raw-html-m2r:`<br>`
Ka Ro provided image files differ only by name, if compiled from unchanged
source, i.e. ``u-boot.bin`` => ``u-boot-tx53-xx3[0|1].bin``.

----

Footnotes & Appendix
--------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
