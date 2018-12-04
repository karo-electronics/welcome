.. role:: raw-html-m2r(raw)
   :format: html


Setup of eMMC
=============

The Ka-RO TXCOM are available with two types of NVM memory:


* `\ ``NAND`` <README.nand.md>`_
* `\ ``eMMC`` <https://en.wikipedia.org/wiki/MultiMediaCard#eMMC>`_

this document is only applicable to TXCOM with eMMC NVM.

About eMMC
----------

Quote `[1] <https://en.wikipedia.org/wiki/MultiMediaCard#eMMC>`_ (emphasis added):\ :raw-html-m2r:`<br>`
"The eMMC (embedded MMC) architecture puts the MMC components (flash memory plus
controller) into a small ball grid array (BGA) IC package for use in circuit
boards as an embedded non-volatile memory system. This is noticeably different
from other versions of MMC as this is **not a user-removable card**\ , but rather
a permanent attachment to the circuit board."

Factory
-------

While the Ka-Ro TXCOM have a factory setup that allows users to work with the
module OOTB, it might be necessary to recover modules from a event that
essentially bricks the module or otherwise stops the developer to take advantage
of the pre-installed and pre-setup environment.

There are two solutions to the aforementioned causes, which are as follows:


* Recovery Boot

  * State: **bricked**

    * Main cause: Bootloader (U-Boot) rendered inoperative  


* Empty NVM

  * State: **bootable**
  * Sub-State: **no OS boot**
    *

    * Main cause: Missing partition table

The hereafter described procedures assumes the following:  


* TXCOM placed in a development baseboard

  * Baseboards available:

    * StarterKit 5

      * StarterKit 5v3
      * StarterKit 5v5

    * MB7

      * Mainboard 7
      * Mainboard 7 SD

    * TXUL-Evalkit

Pre-requisites:  


* TFTP server

  * Linux (recommended): tftpd-hpa\ :raw-html-m2r:`<br>`
    (please consult the package management of your distribution for more)
  * Windows (recommended): ``tftpd32`` | ``tftpd64`` - `available here <http://tftpd32.jounin.net/>`_

Recommended:  


* Terminal programm

  * Linux (recommended): minicom\ :raw-html-m2r:`<br>`
    (please consult the package management of your distrobution for more)
  * Windows (recommended): `\ ``PuTTY`` <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>`_ | `\ ``TeraTerm`` <https://ttssh2.osdn.jp/index.html.en>`_

* NFS server

Recovery Boot
-------------

The *Recover Boot* procedure, while basically the same as the recovery procedure
of TXCOM  with NAND NVM, includes special commands handling the reapplication of
the bootloader to the TXCOM, thus "un-bricking" the module.


* 
  TXCOM state:  


  * State "\ **bricked**\ "

Note:\ :raw-html-m2r:`<br>`
The actual filename depends on the TX6 CoM variant in use, e.g.:\ :raw-html-m2r:`<br>`
*TX6Q-1010* (\ ``..._tx6q-1010.bin``\ ), *TX6U-8010* (\ ``..._tx6u-8010.bin``\ )

.. code-block::

       1.)  Set (close) BOOT_MODE jumper (ST3)
       2.)  Connect the STK5 debug UART
       3.)  Launch the terminal application
       4.)  Connect the STK5 per Ethernet to the network
       5.)  Setup a DHCP server
            (needed for 'bootp')
       6.)  Prepare the TFTP server:
            - Locate the U-Boot binary
              StarterKit CD under: U-Boot/target
            - Copy the file(s) into the TFTP server's data directory,
              usually: /tftpboot
       7.)  Connect the STK5 per USB
            - Power-up of the module
            - NO Power-up / Reset output will appear
       8.)  Start U-Boot on the TX6 with 'sbloader'
            ./sbloader-x86_32 -m -s /cdrom/U-Boot/target/u-boot.bin
       9.)  Abort autoboot (press any key)
            - Power-up / Reset output will appear
       10.) Recover the TX6 using following commands:
            Full factory recovery:
            Procedure: Set and load U-Boot image into memory → Write it to eMMC
                setenv autoload y
                setenv autostart n
                setenv uboot_file u-boot-tx6.bin
                bootp ${uboot_file}
                mmc partconf 0 ${emmc_boot_ack} ${emmc_boot_part} ${emmc_boot_part}
                mmc write ${fileaddr} 0 400
                mmc partconf 0 ${emmc_boot_ack} ${emmc_boot_part} 0
       11.) Power down the module
       12.) Remove (open) BOOT_MODE jumper (ST3)
       13.) Re-apply power to start from flash
            - Power-up / Reset output will appear (Ch. 1.3)
       14.) Abort autoboot (press any key)
       15.) Done.

Install of OS
-------------

Premise
^^^^^^^

The following information has been taken from the MFGTool's configuration and
procedure setup file `\ ``ucl2.xml`` <file://Mfgtools-TX6-2016-12a/Profiles/TX6/OS%20Firmware/ucl2.xml>`_.

The hereafter described procedures require either:


* NFS shares available with a RFS (a.k.a. "\ *NFS root*\ ")  

or  


* Files extracted from the MFGTool packed file  

Which of the solution is chosen is more a question of taste, and facility. As the
procedure is similar to procedures used in development the here preferred method
is the usage of *NFS root*. Further information about *NFS root* can be found
`here <#nfs-root>`_ or `here <#footnotes-appendix-sources>`_


* 
  TXCOM state:  


  * State:     **bootable**
  * Sub-State: **no OS boot**

All hard- and software is presumed to be factory issued.

Introduction
^^^^^^^^^^^^

In the moment the TXCOM is bootable, meaning that the TXCOM has a working
bootloader installed, there are multiple ways to get a working OS onto the module's NVM. The primary
solutions are:


* Manual
* Images - Disk Images

While disk images might seem as the superior solution, it has major
disadvantages, like - among other things - it's dependency to know the precise
storage capacity of the target device. And is therefore neither recommended, nor
explained here.

In this state is a TXCOM with an ``eMMC`` NVM solution, behaves similar to the
run-of-the-mill PC - DIY, non OEM/SI or their "no-OS" solutions - in the office
or at home. When it's fresh out of the box it has only a BIOS and nothing to
boot. It's up to the operator to get it running.

Yet, rather unlike a PC, there is no ready to use CD/USB stick to boot the
"Install Medium". The "Install Medium" is

----

.. code-block:: xml

   <!--U-Boot update and environment setup: -->
   body="Recovery" file="%_MFGUBOOT%" >Loading mfg U-Boot.

   file="%_MFGENV%"  address="%_ADDR_MFGENV%"  - Loading mfg U-Boot parameters.
   file="%_MFGKRNL%" address="%_ADDR_MFGKRNL%" - Loading mfg Linux kernel.
   file="%_MFGDTB%"  address="%_ADDR_MFGDTB%"  - Loading mfg dtb.
   file="%_RAMFS%"   address="%_ADDR_RAMFS%"   - Loading initramfs.
   file="%_UBOOT%"   address="%_ADDR_UBOOT%"   - Loading U-Boot image.
   file="%_ENV%"     address="%_ADDR_ENV%"     - Loading U-Boot environment.
   file="%_DTB%"     address="%_ADDR_DTB%"     - Loading dtb.

----

LINUX-MMC
^^^^^^^^^

.. code-block:: console

   Boot...

   # Select SD device
   $ cd /dev ; for d in `ls | sed '/mmcblk/!d;/p/d;/boot/d'` ; do [ -e ${d}rpmb ] && continue ; ln -s $d emmc ; break ; done

   # Select eMMC device if possible
   $ cd /dev ; for d in `ls | sed '/mmcblk/!d;/p/d;/boot/d'` ; do [ -e ${d}rpmb ] || continue ; ln -sf $d emmc ; break ; done

   # Partitioning
   $ [ -b /dev/emmc ] && (echo label-id:0x0cc66cc0; echo size=30720,type=c ; echo type=83) | sfdisk /dev/emmc

   # Format Linux partition
   $ [ -b /dev/$(readlink /dev/emmc)p1 ] && mkfs.vfat /dev/$(readlink /dev/emmc)p1

   # Format rootfs partition
   $ [ -b /dev/$(readlink /dev/emmc)p2 ] && mkfs.ext3 /dev/$(readlink /dev/emmc)p2

   $ mkdir -p /mnt/mmcblk0p1
   $ mount -t vfat /dev/$(readlink /dev/emmc)p1 /mnt/mmcblk0p1

   # Write kernel image
   $ cat - > /mnt/mmcblk0p1/uImage file="%_KRNL%"

   # Flush the memory
   $ sync

   # Write logo bitmap
   $ cat - > /mnt/mmcblk0p1/logo.bmp file="%_LOGO%"

   # Flush the memory
   $ sync

   $ umount /mnt/mmcblk0p1
   $ rmdir /mnt/mmcblk0p1

   $ mkdir -p /mnt/mmcblk0p2
   $ mount -t ext3 /dev/$(readlink /dev/emmc)p2 /mnt/mmcblk0p2

   # Sending and writing rootfs
   $ tar -x%_ROOTFS_TAROPT%v -C /mnt/mmcblk0p2" file="%_ROOTFS%"

   # Flush the memory
   $ sync

   # Write modules
   $ tar -C /mnt/mmcblk0p2 -x%_MODULES_TAROPT%vf - lib ./lib usr ./usr file="%_MODULES%"

   # Flush the memory
   $ sync

   $ umount /mnt/mmcblk0p2
   $ rmdir /mnt/mmcblk0p2

   # Done
   $ echo "Update Complete!"

----

LINUX-SD
^^^^^^^^

.. code-block:: console

   Boot...

   $ cd /dev ; for d in `ls | sed '/mmcblk/!d;/p/d;/boot/d'` ; do [ -e ${d}rpmb ] && continue ; ln -s $d emmc ; break ; done

   # Select SD device...
   # Partitioning...
   $ [ -b /dev/emmc ] && (echo size=30720,type=c ; echo type=83) | sfdisk /dev/emmc
   # Format Linux partition
   $ [ -b /dev/$(readlink /dev/emmc)p1 ] && mkfs.vfat /dev/$(readlink /dev/emmc)p1
   # Format rootfs partition
   $ [ -b /dev/$(readlink /dev/emmc)p2 ] && mkfs.ext3 /dev/$(readlink /dev/emmc)p2

   $ mkdir -p /mnt/mmcblk0p1
   $ mount -t vfat /dev/$(readlink /dev/emmc)p1 /mnt/mmcblk0p1

   # Write kernel image
   $ cat - > /mnt/mmcblk0p1/uImage file="%_KRNL%"

   # Flush the memory
   $ sync

   # Write logo bitmap
   $ cat - > /mnt/mmcblk0p1/logo.bmp file="%_LOGO%"

   # Flush the memory
   $ sync

   $ umount /mnt/mmcblk0p1
   $ rmdir /mnt/mmcblk0p1


   $ mkdir -p /mnt/mmcblk0p2
   $ mount -t ext3 /dev/$(readlink /dev/emmc)p2 /mnt/mmcblk0p2

   # Sending and writing rootfs
   $ tar -x%_ROOTFS_TAROPT%v -C /mnt/mmcblk0p2 file="%_ROOTFS%"

   # Flush the memory
   $ sync

   # Write modules
   $ tar -C /mnt/mmcblk0p2 -x%_MODULES_TAROPT%vf - lib ./lib usr ./usr file="%_MODULES%"

   # Flush the memory
   $ sync

   $ umount /mnt/mmcblk0p2
   $ rmdir /mnt/mmcblk0p2

   # Done
   $ echo "Update Complete!"

----

MMC-HIREL
^^^^^^^^^

.. code-block:: console

   Boot...

   # Select eMMC
   $ ln -s $(cd /dev;ls mmcblk*rpmb | sed s/rpmb//) /dev/emmc

   # Check if partitioning is possible
   $ [ $(mmc extcsd read /dev/emmc | sed '/PARTITION_SETTING_COMPLETED/!d;s/^.* //;s/[^0-9a-fx]*//gi') == 0x00 ]

   $ mmc enh_area set -y 0 $(( \
       $(mmc extcsd read /dev/emmc | sed '/MAX_ENH_SIZE_MULT/!d;s/^.* //') \
       * $(mmc extcsd read /dev/emmc | sed '/HC_WP_GRP_SIZE/!d;s/^.* //;s/[^0-9a-fx]*//gi') \
       * $(mmc extcsd read /dev/emmc | sed '/HC_ERASE_GRP_SIZE/!d;s/^.* //;s/[^0-9a-fx]*//gi') \
       * 512 )) /dev/emmc | \
       # Set enhanced eMMC area - power cycle needed...
       grep 'Device power cycle needed'

   # DONE - POWER CYCLE NEEDED
   $ echo "Update Complete!"

----

WINDOWS-NAND
^^^^^^^^^^^^

.. code-block:: console

   # Boot...

   # Flush the memory
   $ sync

   # Select NK partition
   $ cd /dev ; for d in `grep osimage1 /proc/mtd | sed 's/:.*//'` ; do ln -s $d mtdosimage1 ; break ; done

   # Write NK
   $ nandwrite -p /dev/mtdosimage1 file="%_KRNL%"

   # Flush the memory
   $ sync

   # Select logo partition
   $ cd /dev ; for d in `grep logo /proc/mtd | sed 's/:.*//'` null ; do ln -s $d mtdlogo ; break ; done

   # Write logo bitmap
   $ nandwrite -p /dev/mtdlogo

   # Flush the memory
   $ sync

   # Done
   $ echo "Update Complete!"

----

WINDOWS-MMC
^^^^^^^^^^^

.. code-block:: console

   # Boot...

   # Select eMMC
   $ ln -s $(cd /dev;ls mmcblk*rpmb | sed s/rpmb//) /dev/emmc

   # Partitioning
   $ [ -b /dev/emmc ] && (echo label-id:0x0cc66cc0; echo size=325632,type=c; echo type=c) | sfdisk /dev/emmc

   # Format Windows partition
   $ [ -b /dev/$(readlink /dev/emmc)p1 ] && mkfs.vfat /dev/$(readlink /dev/emmc)p1

   $ mkdir -p /mnt/emmcp1
   $ mount -t vfat /dev/$(readlink /dev/emmc)p1 /mnt/emmcp1

   # Write NK
   $ cat - > /mnt/emmcp1/nk file="%_NK%"

   # Flush the memory
   $ sync

   # Write logo bitmap
   $ cat - > /mnt/emmcp1/logo.bmp" file="%_LOGO%"

   # Flush the memory
   $ sync

   # Finish by cleanly un-mounting the filesystem
   $ umount /mnt/emmcp1
   $ rmdir /mnt/emmcp1

   # Done
   $ echo "Update Complete!"

----

Footnotes, Appendix & Sources
-----------------------------

:raw-html-m2r:`<a id="nfs-root">NFS root:</a>`\ :raw-html-m2r:`<br>`
http://elinux.org/TFTP_Boot_and_NFS_Root_Filesystems\ :raw-html-m2r:`<br>`
https://www.kernel.org/doc/Documentation/filesystems/nfs/nfsroot.txt\ :raw-html-m2r:`<br>`
https://wiki.archlinux.org/index.php/Diskless_system\ :raw-html-m2r:`<br>`
http://wiki.emacinc.com/wiki/Booting_with_an_NFS_Root_Filesystem\ :raw-html-m2r:`<br>`
https://fedoraproject.org/wiki/StatelessLinux/NFSRoot\ :raw-html-m2r:`<br>`
https://help.ubuntu.com/community/DisklessUbuntuHowto  

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
