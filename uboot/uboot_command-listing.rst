.. role:: raw-html-m2r(raw)
   :format: html


U-Boot commands
===============

List of commands available in U-Boot.


.. raw:: html

   <!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
   **Table of Contents**

   - [U-Boot commands](#u-boot-commands)
       - [List](#list)
       - [Commands and explanations](#commands-and-explanations)
       - [Footnotes, Appendix & Sources](#footnotes-appendix--sources)

   <!-- markdown-toc end -->



As this list of commands available in U-Boot, is comprised from **all** TXCOM
variants and thus can include commands that are either specific to a modules
of:


* The variants of the same COM:

  * NAND vs.
  * eMMC

* The same SOC family, e.g.:

  * i.MX6\ :raw-html-m2r:`<br>`
    => i.MX6 -> S  -> DL  -> Q -> QP\ :raw-html-m2r:`<br>`
    => i.MX6 -> UL -> ULL  

and will generally applicable over all TXCOM might not be valid for specific
TXCOM. To check:

Please use the command ``help`` (or ``?``\ )to see the list appropriate to the used TXCOM.

Some commands use memory addresses, which are abstracted as predefined
variables in the U-Boot default environment of each TXCOM series, e.g.
``loadaddr``. For more see `here </uboot/uboot_environment-variables.md>`_

List
----

.. list-table::
   :header-rows: 1

   * - Command
     - Description
   * - `\ ``?`` <#?>`_
     - alias for `\ ``help`` <#help>`_
   * - `\ ``base`` <#base>`_
     - print or set address offset
   * - `\ ``bdinfo`` <#bdinfo>`_
     - print Board Info structure
   * - `\ ``bmp`` <#bmp>`_
     - manipulate BMP image data
   * - `\ ``boot`` <#boot>`_
     - boot default, i.e., ``run 'bootcmd'``
   * - `\ ``bootce`` <#bootce>`_
     - Boot a Windows CE image from memory
   * - `\ ``bootd`` <#bootp>`_
     - boot default, i.e., ``run 'bootcmd'``
   * - `\ ``bootm`` <#bootm>`_
     - boot application image from memory
   * - `\ ``bootp`` <#bootp>`_
     - boot image via network using BOOTP/TFTP protocol
   * - `\ ``ceconnect`` <#ceconnect>`_
     - Set up a connection to the CE host PC over TCP/IP and download the run-time image
   * - `\ ``chpart`` <#chpart>`_
     - change active partition
   * - `\ ``clocks`` <#clocks>`_
     - display clocks
   * - `\ ``cls`` <#cls>`_
     - clear screen
   * - `\ ``cmp`` <#cmp>`_
     - memory compare
   * - `\ ``coninfo`` <#coninfo>`_
     - print console devices and information
   * - `\ ``cp`` <#cp>`_
     - memory copy
   * - `\ ``crc32`` <#carc32>`_
     - checksum calculation
   * - `\ ``dcache`` <#dcache>`_
     - enable or disable data cache
   * - `\ ``dhcp`` <#dhcp>`_
     - boot image via network using DHCP/TFTP protocol
   * - `\ ``echo`` <#echo>`_
     - echo args to console
   * - `\ ``editenv`` <#editenv>`_
     - edit environment variable
   * - `\ ``env`` <#env>`_
     - environment handling commands
   * - `\ ``ext2load`` <#ext2load>`_
     - load binary file from a ext2 filesystem
   * - `\ ``ext2ls`` <#ext2ls>`_
     - list files in a directory (default ``/``\ )
   * - `\ ``fatinfo`` <#fatinfo>`_
     - print information about filesystem
   * - `\ ``fatload`` <#fatload>`_
     - load binary file from a dos filesystem
   * - `\ ``fatls`` <#fatls>`_
     - list files in a directory (default ``/``\ )
   * - `\ ``fdt`` <#fdt>`_
     - flattened device tree utility commands
   * - `\ ``go`` <#go>`_
     - start application at address ``addr``
   * - `\ ``help`` <#help>`_
     - print command description/usage
   * - `\ ``icache`` <#icache>`_
     - enable or disable instruction cache
   * - `\ ``iminfo`` <#iminfo>`_
     - print header information for application image
   * - `\ ``imxtract`` <#imxtract>`_
     - extract a part of a multi-image
   * - `\ ``itest`` <#itest>`_
     - return true/false on integer compare
   * - `\ ``loadb`` <#loadb>`_
     - load binary file over serial line (kermit mode)
   * - `\ ``loads`` <#loads>`_
     - load S-Record file over serial line
   * - `\ ``loady`` <#loady>`_
     - load binary file over serial line (ymodem mode)
   * - `\ ``loop`` <#loop>`_
     - infinite loop on address range
   * - `\ ``md`` <#md>`_
     - memory display
   * - `\ ``mdio`` <#mdio>`_
     - MDIO utility commands
   * - `\ ``mii`` <#mii>`_
     - MII utility commands
   * - `\ ``mm`` <#mm>`_
     - memory modify (auto-incrementing address)
   * - `\ ``mmc`` <#mmc>`_
     - MMC sub system
   * - `\ ``mmcinfo`` <#mmcinfo>`_
     - display MMC info
   * - `\ ``mtdparts`` <#mtdparts>`_
     - define flash/nand partitions
   * - `\ ``mtest`` <#mtest>`_
     - simple RAM read/write test
   * - `\ ``mw`` <#mw>`_
     - memory write (fill)
   * - `\ ``nand`` <#nand>`_
     - NAND sub-system
   * - `\ ``nboot`` <#nboot>`_
     - boot from NAND device
   * - `\ ``nbootce`` <#nbootce>`_
     - Boot a Windows CE image from NAND
   * - `\ ``nfs`` <#nfs>`_
     - boot image via network using NFS protocol
   * - `\ ``nm`` <#nm>`_
     - memory modify (constant address)
   * - `\ ``ping`` <#print>`_
     - send ICMP ECHO_REQUEST to network host
   * - `\ ``printenv`` <#printenv>`_
     - print environment variables
   * - `\ ``reset`` <#reset>`_
     - Perform RESET of the CPU
   * - `\ ``romupdate`` <#romupdate>`_
     - Creates an FCB data structure and writes an U-Boot image to flash
   * - `\ ``run`` <#run>`_
     - run commands in an environment variable
   * - `\ ``saveenv`` <#saveenv>`_
     - save environment variables to persistent storage
   * - `\ ``setenv`` <#setenv>`_
     - set environment variables
   * - `\ ``sleep`` <#sleep>`_
     - delay execution for some time
   * - `\ ``source`` <#source>`_
     - run script from memory
   * - `\ ``tftpboot`` <#tftpboot>`_
     - boot image via network using TFTP protocol
   * - `\ ``time`` <#time>`_
     - run commands and summarize execution time
   * - `\ ``version`` <#version>`_
     - print monitor, compiler and linker version


Commands and explanations
-------------------------


* 
  ``?``\ :raw-html-m2r:`<a id="?"></a>`\ :raw-html-m2r:`<br>`
  alias for 'help'

* 
  ``base``\ :raw-html-m2r:`<a id="base"></a>`  

  .. code-block::

      print or set address offset which is used for all memory commands

  .. code-block:: console

     base                       - print address offset for memory commands
     base off                   - set address offset for memory commands to 'off'

* 
  ``bdinfo``\ :raw-html-m2r:`<a id="bdinfo"></a>`\ :raw-html-m2r:`<br>`
  print Board Info structure

  .. code-block:: console

     bdinfo                     - prints the information that U-Boot passes about
                                  the board such as memory addresses and sizes,
                                  clock frequencies, MAC address, etc.

* 
  ``bmp``\ :raw-html-m2r:`<a id="bmp"></a>`\ :raw-html-m2r:`<br>`
  manipulate BMP image data

  .. code-block:: console

     bmp info <imageAddr>              - display image info
     bmp display <imageAddr> [x y]     - display image at x,y

* 
  ``boot``\ :raw-html-m2r:`<a id="boot"></a>`\ :raw-html-m2r:`<br>`
  the same as bootd;

  .. code-block:: console

     boot                       - boot default, i.e., run 'bootcmd'

* 
  ``bootce``\ :raw-html-m2r:`<a id="bootce"></a>`\ :raw-html-m2r:`<br>`
  bootce - Boot a Windows CE image from memory

  .. code-block:: console

     bootce [addr]
             addr            boot image from address 'addr' (default '${fileaddr}')
     or
             -i              initialize the WinCE globals data structure (before loading a .nb0 image)

* 
  ``bootd``\ :raw-html-m2r:`<a id="bootd"></a>`\ :raw-html-m2r:`<br>`
  bootd - boot default, i.e., run 'bootcmd'

* 
  ``bootm``\ :raw-html-m2r:`<a id="bootm"></a>`\ :raw-html-m2r:`<br>`
  boot application image from memory
  boot default, i.e., run 'bootcmd'

  .. code-block:: console

     bootm [addr [arg ...]]
                                - boot application image stored in memory
                                  passing arguments 'arg ...'; when booting a Linux
                                  kernel, 'arg' can be the address of an initrd image

                                  When booting a Linux kernel which requires a flat
                                  device-tree a third argument is required which is
                                  the address of the device-tree blob. To boot that
                                  kernel without an initrd image, use a '-' for the
                                  second argument. If you do not pass a third a
                                  bd_info struct will be passed instead

     Sub-commands to do part of the bootm sequence.  The sub-commands must be
     issued in the order below (it's ok to not issue all sub-commands):

     bootm [subcmd [addr [arg ...]]]
            start [addr [arg ...]]
            loados  - load OS image
            ramdisk - relocate initrd, set env initrd_start/initrd_end
            fdt     - relocate flat device tree
            cmdline - OS specific command line processing/setup
            bdt     - OS specific bd_t processing
            prep    - OS specific prep before relocation or go
            go      - start OS

* 
  ``bootp``\ :raw-html-m2r:`<a id="bootp"></a>`\ :raw-html-m2r:`<br>`
  boot image via network using BOOTP/TFTP protocol

  .. code-block:: console

     bootp [loadAddress] [[hostIPaddr:]bootfilename]

  **\ *Note:*\ **\ :raw-html-m2r:`<br>`
  Invoke BOOTP/DHCP client to obtain IP/boot parameters and - if the environment
  variable ``autoload`` is set to ``yes`` - load ``${bootfile}`` via TFTP to ``${loadaddr}``.\ :raw-html-m2r:`<br>`
  For more see `here </uboot/uboot_environment-variables.md>`_

* 
  ``ceconnect``\ :raw-html-m2r:`<a id="ceconnect"></a>`\ :raw-html-m2r:`<br>`
  Set up a connection to the CE host PC over TCP/IP and download the run-time image

  .. code-block:: console

     ceconnect [-v] [-t <timeout>] [-h host]
                -v            - verbose operation
                -t <timeout>  - max wait time (#sec) for the connection
                -h <host>     - send BOOTME requests to <host>
                                (default: broadcast address 255.255.255.255)

* 
  ``chpart``\ :raw-html-m2r:`<a id="chpart"></a>`\ :raw-html-m2r:`<br>`
  change active partition

* 
  ``clocks``\ :raw-html-m2r:`<a id="clocks"></a>`\ :raw-html-m2r:`<br>`
  display clocks

* 
  ``cls``\ :raw-html-m2r:`<a id="cls"></a>`\ :raw-html-m2r:`<br>`
  clear screen

* 
  ``cmp``\ :raw-html-m2r:`<a id="cmp"></a>`\ :raw-html-m2r:`<br>`
  memory compare

  .. code-block:: console

     cmp [.b, .w, .l] addr1 addr2 count

          .b                  - access memory in size byte ( 8 bit)
          .w                  - access memory in size word (16 bit)
          .l                  - access memory in size long (32 bit)
          addr1               - address of memory area 1
          addr2               - address of memory area 2
          count               - number of elements (byte, word, long) to compare

* 
  ``coninfo``\ :raw-html-m2r:`<a id="coninfo"></a>`\ :raw-html-m2r:`<br>`
  print console devices and information

* 
  ``cp``\ :raw-html-m2r:`<a id="cp"></a>`\ :raw-html-m2r:`<br>`
  memory copy

  .. code-block:: console

     cp [.b, .w, .l] source target count

         .b                   - access memory in size byte ( 8 bit)
         .w                   - access memory in size word (16 bit)
         .l                   - access memory in size long (32 bit)
         source               - source address of the data
         target               - target address of the data
         count                - number of elements (byte, word, long) to copy

* 
  ``crc32``\ :raw-html-m2r:`<a id="crc32"></a>`\ :raw-html-m2r:`<br>`
  checksum calculation

  .. code-block:: console

     crc32 addr1 count [addr2]

                         - compute CRC32 checksum [save at addr]
                           calculate checksum of data starting at address 'addr1'
                           for length 'count' and (if given) store the result at
                           address 'addr2'

           addr1         - start address of data
           count         - number of memory addresses of the data
           addr2         - storage address for the result of the calculation

* 
  ``dcache``\ :raw-html-m2r:`<a id="dcache"></a>`\ :raw-html-m2r:`<br>`
  enable or disable data cache

  .. code-block:: console

     dcache [on, off, flush]
                                - enable, disable, or flush data (writethrough) cache

* 
  ``dhcp``\ :raw-html-m2r:`<a id="dhcp"></a>`\ :raw-html-m2r:`<br>`
  boot image via network using DHCP/TFTP protocol  

  .. code-block:: console

     dhcp [loadAddress] [[hostIPaddr:]bootfilename]

  **\ *Note:*\ **\ :raw-html-m2r:`<br>`
  Invoke BOOTP/DHCP client to obtain IP/boot parameters and - if the environment
  variable ``autoload`` is set to ``yes`` - load ``${bootfile}`` via TFTP to ``${loadaddr}``.\ :raw-html-m2r:`<br>`
  For more see `here </uboot/uboot_environment-variables.md>`_

* 
  ``dm``\ :raw-html-m2r:`<a id="dm"></a>`\ :raw-html-m2r:`<br>`
  Driver model low level access

  .. code-block:: console

     dm tree                    - Dump driver model tree ('*' = activated)
     dm uclass                  - Dump list of instances for each uclass
     dm devres                  - Dump list of device resources for each device

* 
  ``echo``\ :raw-html-m2r:`<a id="echo"></a>`\ :raw-html-m2r:`<br>`
  echo args to console

  .. code-block:: console

     echo [args]                - echo args to console; \c suppresses newline

* 
  ``editenv``\ :raw-html-m2r:`<a id="editenv"></a>`\ :raw-html-m2r:`<br>`
  edit environment variable

  .. code-block:: console

     editenv name               - edit environment variable 'name'

* 
  ``env``\ :raw-html-m2r:`<a id="env"></a>`\ :raw-html-m2r:`<br>`
  environment handling commands

  .. code-block:: console

     env default [-f] -a                   - [forcibly] reset default environment
     env default [-f] var [...]            - [forcibly] reset variable(s) to their default values
     env delete [-f] var [...]             - [forcibly] delete variable(s)
     env edit name                         - edit environment variable
     env export [-t | -b | -c] [-s size] addr [var ...]
                                           - export environment
     env import [-d] [-t | -b | -c] addr [size]
                                           - import environment
     env print [-a | name ...]             - print environment
     env run var [...]                     - run commands in an environment variable
     env save                              - save environment
     env set [-f] name [arg ...]           - [forcibly] set environment variable

* 
  ``ext2load``\ :raw-html-m2r:`<a id="ext2load"></a>`\ :raw-html-m2r:`<br>`
  load binary file from a ext2 filesystem  

  .. code-block:: console

     ext2load <interface> <dev[:part]> [addr [filename [bytes [pos]]]]]

                                - load binary file 'filename' from 'dev' on 'interface'
                                  to address 'addr' from ext2 filesystem.

* 
  ``ext2ls``\ :raw-html-m2r:`<a id="ext2ls"></a>`\ :raw-html-m2r:`<br>`
  list files in a directory (default /)

  .. code-block:: console

     ext2ls <interface> <dev[:part]> [directory]

                                - list files from 'dev' on 'interface' in a 'directory'

* 
  ``fatinfo``\ :raw-html-m2r:`<a id="fatinfo"></a>`\ :raw-html-m2r:`<br>`
  print information about filesystem

  .. code-block:: console

     fatinfo <interface> [<dev[:part]>]

                                - print information about filesystem from 'dev' on 'interface'

* 
  ``fatload``\ :raw-html-m2r:`<a id="fatload"></a>`\ :raw-html-m2r:`<br>`
  load binary file from a dos filesystem

  .. code-block:: console

     fatload <interface> [<dev[:part]> [<addr> [<filename> [bytes [pos]]]]]

                                - Load binary file 'filename' from 'dev' on 'interface'
                                  to address 'addr' from dos filesystem.
                                  'pos' gives the file position to start loading from.
                                  If 'pos' is omitted, 0 is used. 'pos' requires 'bytes'.
                                  'bytes' gives the size to load. If 'bytes' is 0 or omitted,
                                  the load stops on end of file.
                                  If either 'pos' or 'bytes' are not aligned to
                                  ARCH_DMA_MINALIGN then a misaligned buffer warning will
                                  be printed and performance will suffer for the load.

* 
  ``fatls``\ :raw-html-m2r:`<a id="fatls"></a>`\ :raw-html-m2r:`<br>`
  list files in a directory (default /)

  .. code-block:: console

     fatls <interface> [<dev[:part]>] [directory]

                                - list files from 'dev' on 'interface' in a 'directory'

* 
  ``fdt``\ :raw-html-m2r:`<a id="fdt"></a>`\ :raw-html-m2r:`<br>`
  flattened device tree utility commands

  .. code-block:: console

     fdt addr [-c]  <addr> [<length>]    - Set the [control] fdt location to <addr>
     fdt boardsetup                      - Do board-specific set up
     fdt move   <fdt> <newaddr> <length> - Copy the fdt to <addr> and make it active
     fdt resize                          - Resize fdt to size + padding to 4k addr
     fdt print  <path> [<prop>]          - Recursive print starting at <path>
     fdt list   <path> [<prop>]          - Print one level starting at <path>
     fdt get value <var> <path> <prop>   - Get <property> and store in <var>
     fdt get name <var> <path> <index>   - Get name of node <index> and store in <var>
     fdt get addr <var> <path> <prop>    - Get start address of <property> and store in <var>
     fdt get size <var> <path> [<prop>]  - Get size of [<property>] or num nodes and store in <var>
     fdt set    <path> <prop> [<val>]    - Set <property> [to <val>]
     fdt mknode <path> <node>            - Create a new node after <path>
     fdt rm     <path> [<prop>]          - Delete the node or <property>
     fdt header                          - Display header info
     fdt bootcpu <id>                    - Set boot cpuid
     fdt memory <addr> <size>            - Add/Update memory node
     fdt rsvmem print                    - Show current mem reserves
     fdt rsvmem add <addr> <size>        - Add a mem reserve
     fdt rsvmem delete <index>           - Delete a mem reserves
     fdt chosen [<start> <end>]          - Add/update the /chosen branch in the tree
                                           <start>/<end> - initrd start/end addr

  **Note:**\ :raw-html-m2r:`<br>`
  Dereference aliases by omitting the leading '/', e.g. ``fdt print ethernet0``.

* 
  ``fuse``\ :raw-html-m2r:`<a id="fuse"></a>`\ :raw-html-m2r:`<br>`
  Fuse sub-system

  .. code-block:: console

     fuse read <bank> <word> [<cnt>]
                                  - read 1 or 'cnt' fuse words, starting at 'word'
     fuse sense <bank> <word> [<cnt>]
                                  - sense 1 or 'cnt' fuse words, starting at 'word'
     fuse prog [-y] <bank> <word> <hexval> [<hexval>...]
                                  - program 1 or several fuse words, starting at 'word' (PERMANENT)
     fuse override <bank> <word> <hexval> [<hexval>...]
                                  - override 1 or several fuse words, starting at 'word'

* 
  ``go``\ :raw-html-m2r:`<a id="go"></a>`\ :raw-html-m2r:`<br>`
  start application at address ``addr``

  .. code-block:: console

     go addr [arg ...]                 - start application at address 'addr' passing
                                         'arg' as arguments

* 
  ``help``\ :raw-html-m2r:`<a id="help"></a>`\ :raw-html-m2r:`<br>`
  print online help\ :raw-html-m2r:`<br>`
  (alias: ``?``\ )

  .. code-block:: console

     help [command ...]               - show help information (for 'command')

     - 'help' prints online help for the monitor commands. Without arguments, it
        prints a short usage message for all commands. To get detailed help information
        for specific commands you can type 'help' with one or more command names as
        arguments.

* 
  ``i2c``\ :raw-html-m2r:`<a id="i2c"></a>`\ :raw-html-m2r:`<br>`
  I2C sub-system

  .. code-block:: console

     Usage:
     i2c bus [muxtype:muxaddr:muxchannel] - show I2C bus info
     crc32 chip address[.0, .1, .2] count - compute CRC32 checksum
     i2c dev [dev]                        - show or set current I2C bus
     i2c loop chip address[.0, .1, .2] [# of objects]
                                          - looping read of device
     i2c md chip address[.0, .1, .2] [# of objects]
                                          - read from I2C device
     i2c mm chip address[.0, .1, .2]      - write to I2C device (auto-incrementing)
     i2c mw chip address[.0, .1, .2] value [count]
                                          - write to I2C device (fill)
     i2c nm chip address[.0, .1, .2]      - write to I2C device (constant address)
     i2c probe [address]                  - test for and show device(s) on the I2C bus
     i2c read chip address[.0, .1, .2] length memaddress
                                          - read to memory
     i2c write memaddress chip address[.0, .1, .2] length [-s]
                                          - write memory to I2C; the -s option
                                            selects bulk write in a single transaction
     i2c reset                            - re-init the I2C Controller
     i2c speed [speed]                    - show or set I2C bus speed

* 
  ``icache``\ :raw-html-m2r:`<a id="icache"></a>`\ :raw-html-m2r:`<br>`
  enable or disable instruction cache

  .. code-block:: console

     icache [on, off, flush]
                                - enable, disable, or flush instruction cache

* 
  ``iminfo``\ :raw-html-m2r:`<a id="iminfo"></a>`\ :raw-html-m2r:`<br>`
  print header information for application image

  .. code-block:: console

     iminfo addr [addr ...]     - print header information for application image starting at
                                  address 'addr' in memory; this includes verification of the
                                  image contents (magic number, header and payload checksums)

* 
  ``imxtract``\ :raw-html-m2r:`<a id="imxtract"></a>`\ :raw-html-m2r:`<br>`
  extract a part of a multi-image

  .. code-block:: console

     imxtract addr part [dest]
                                - extract 'part' from legacy image at 'addr' and copy to 'dest'

* 
  ``itest``\ :raw-html-m2r:`<a id="itest"></a>`\ :raw-html-m2r:`<br>`
  return true/false on integer compare

  .. code-block:: console

     itest [.b, .w, .l, .s] [*]value1 <op> [*]value2
            .b                  - access memory in size byte ( 8 bit)
            .w                  - access memory in size word (16 bit)
            .l                  - access memory in size long (32 bit)

* 
  ``loadb``\ :raw-html-m2r:`<a id="loadb"></a>`\ :raw-html-m2r:`<br>`
  load binary file over serial line (kermit mode)

  .. code-block:: console

     loadb [ off ] [ baud ]     - load binary file over serial line with offset 'off' and baudrate
                                  'baud'

* 
  ``loads``\ :raw-html-m2r:`<a id="loads"></a>`\ :raw-html-m2r:`<br>`
  load S-Record file over serial line

  .. code-block:: console

     loads [ off ]              - load S-Record file over serial line with offset 'off'

* 
  ``loady``\ :raw-html-m2r:`<a id="loady"></a>`\ :raw-html-m2r:`<br>`
  load binary file over serial line (ymodem mode)

  .. code-block:: console

     loady [ off ] [ baud ]     - load binary file over serial line with offset 'off' and baudrate
                                  'baud'

* 
  ``loop``\ :raw-html-m2r:`<a id="loop"></a>`\ :raw-html-m2r:`<br>`
  infinite loop on address range

  .. code-block:: console

     loop [.b, .w, .l] address count
                          - loop on a set of addresses

           .b             - access memory in size byte ( 8 bit)
           .w             - access memory in size word (16 bit)
           .l             - access memory in size long (32 bit)
           address        - start address of the loop
           count          - number of objects to read
           This command can only be terminated by resetting the board!

* 
  ``md``\ :raw-html-m2r:`<a id="md"></a>`  

  .. code-block::

     memory display, used to display memory contents both as hexadecimal and ASCII data.

  .. code-block:: console

     md [.b, .w, .l] address [count]
                            - memory display

         .b               - access memory in size byte ( 8 bit)
         .w               - access memory in size word (16 bit)
         .l               - access memory in size long (32 bit)
         address          - start address
         count            - number of objects to be displayed

* 
  ``mdio``\ :raw-html-m2r:`<a id="mdio"></a>`\ :raw-html-m2r:`<br>`
  MDIO utility commands

  .. code-block:: console

     mdio list                  - List MDIO buses
     mdio read <phydev> [<devad>.]<reg>
                                - read PHY's register at <devad>.<reg>
     mdio write <phydev> [<devad>.]<reg> <data>
                                - write PHY's register at <devad>.<reg>
     mdio rx <phydev> [<devad>.]<reg>
                                - read PHY's extended register at <devad>.<reg>
     mdio wx <phydev> [<devad>.]<reg> <data>
                                - write PHY's extended register at <devad>.<reg>

     <phydev> may be:
        <busname> <addr>
        <addr>
        <eth name>
     <addr> <devad>, and <reg> may be ranges, e.g. 1-5.4-0x1f.

* 
  ``mii``\ :raw-html-m2r:`<a id="mii"></a>`\ :raw-html-m2r:`<br>`
     MII utility commands

  .. code-block:: console

     mii device                - list available devices
     mii device  <devname>     - set current device
     mii info    <addr>        - display MII PHY info
     mii read    <addr> <reg> -  read MII PHY <addr> register <reg>
     mii write   <addr> <reg> <data>
                               - write MII PHY <addr> register <reg>
     mii dump    <addr> <reg> - pretty-print <addr> <reg> (0-5 only)
                               <addr> and/or <reg> may be ranges, e.g. 2-7.

* 
  ``mm``\ :raw-html-m2r:`<a id="mm"></a>`\ :raw-html-m2r:`<br>`
  memory modify (auto-incrementing); displays the memory address and current
  content and prompts for hexadecimal user input as desired new content for this
  address; the address is automatically incremented each time

  .. code-block:: console

     mm[.b, .w, .l] address
        .b                - access memory in size byte ( 8 bit)
        .w                - access memory in size word (16 bit)
        .l                - access memory in size long (32 bit)
        address           - start address for modification

* 
  ``mmc``\ :raw-html-m2r:`<a id="mmc"></a>`\ :raw-html-m2r:`<br>`
  MMC sub system

  .. code-block:: console

     mmc info                   - display info of the current MMC device
     mmc read addr blk# cnt
     mmc write addr blk# cnt
     mmc erase blk# cnt
     mmc rescan
     mmc part                   - lists available partition on current mmc device
     mmc dev [dev] [part]       - show or set current mmc device [partition]
     mmc list                   - lists available devices
     mmc hwpartition [args...]  - does hardware partitioning

       arguments (sizes in 512-byte blocks):
         [user [enh start cnt] [wrrel {on|off}]]
                                - sets user data area attributes
         [gp1|gp2|gp3|gp4 cnt [enh] [wrrel {on|off}]]
                                - general purpose partition
         [check|set|complete]   - mode, complete set partitioning completed

       WARNING: Partitioning is a write-once setting once it is set to complete.

       Power cycling is required to initialize partitions after set to complete.

     mmc setdsr <value>         - set DSR register value

* 
  ``mmcinfo``\ :raw-html-m2r:`<a id="mmcinfo"></a>`\ :raw-html-m2r:`<br>`
  display MMC info

  .. code-block:: console

     mmcinfo                    - device number of the device to dislay info of

* 
  ``mtdparts``\ :raw-html-m2r:`<a id="mtdparts"></a>`\ :raw-html-m2r:`<br>`
  define flash/nand partitions

  .. code-block:: console

     mtdparts                     - list partition table
     mtdparts delall              - delete all partitions
     mtdparts del part-id         - delete partition (e.g. part-id = nand0,1)
     mtdparts add <mtd-dev> <size>[@<offset>] [<name>] [ro]
                                  - add partition
     mtdparts default             - reset partition table to defaults

     -----
     this command uses three environment variables:

     'partition' - keeps current partition identifier

       partition  := <part-id>
       <part-id>  := <dev-id>,part_num

     'mtdids' - linux kernel mtd device id <-> u-boot device id mapping

       mtdids=<idmap>[,<idmap>,...]

       <idmap>    := <dev-id>=<mtd-id>
       <dev-id>   := 'nand'|'nor'|'onenand'<dev-num>
       <dev-num>  := mtd device number, 0...
       <mtd-id>   := unique device tag used by linux kernel to find mtd device (mtd->name)

     'mtdparts' - partition list

        mtdparts=mtdparts=<mtd-def>[;<mtd-def>...]

        <mtd-def>  := <mtd-id>:<part-def>[,<part-def>...]
        <mtd-id>   := unique device tag used by linux kernel to find mtd device (mtd->name)
        <part-def> := <size>[@<offset>][<name>][<ro-flag>]
        <size>     := standard linux memsize OR '-' to denote all remaining space
        <offset>   := partition start offset within the device
        <name>     := '(' NAME ')'
        <ro-flag>  := when set to 'ro' makes partition read-only (not used, passed to kernel)

* 
  ``mtest``\ :raw-html-m2r:`<a id="mtest"></a>`\ :raw-html-m2r:`<br>`
  simple RAM read/write test

  .. code-block:: console

     mtest [start [end [pattern [iterations]]]]

            start         - start address of the RAM test area
            end           - end address of the RAM test area
            pattern       - pattern, that is applied to the RAM for testing

  **\ *Note:*\ **\ :raw-html-m2r:`<br>`
  This test changes the contents of the RAM and may therefore cause crashing of
  the system if the memory area, where this test is applied to, is needed for
  the system operation.

* 
  ``mw``\ :raw-html-m2r:`<a id="mw"></a>`\ :raw-html-m2r:`<br>`
  memory write (fill)

  .. code-block:: console

     mw [.b, .w, .l] address value [count]

         .b               - access memory in size byte ( 8 bit)
         .w               - access memory in size word (16 bit)
         .l               - access memory in size long (32 bit)
         address          - start address to write to
         value            - value to write to the address(es)
         count            - number of addresses to which "value" is written

* 
  ``nand``\ :raw-html-m2r:`<a id="nand"></a>`\ :raw-html-m2r:`<br>`
  NAND sub-system

  .. code-block:: console

     nand info                  - show available NAND devices
     nand device [dev]          - show or set current device
     nand read                  - addr off|partition size
     nand write                 - addr off|partition size
                                  read/write 'size' bytes starting at offset 'off'
                                  to/from memory address 'addr', skipping bad blocks.
     nand read.raw              - addr off|partition
     nand write.raw             - addr off|partition
                                  Use read.raw/write.raw to avoid ECC and access
                                  the page as-is.
     nand erase[.spread] [clean] off size
                                - erase 'size' bytes from offset 'off'
                                  With '.spread', erase enough for given file
                                  size, otherwise, 'size' includes skipped bad
                                  blocks.
     nand erase.part [clean] partition
                                - erase entire mtd partition'
     nand erase.chip [clean]    - erase entire chip'
     nand bad                   - show bad blocks
     nand dump[.oob] off        - dump page
     nand scrub [-y] off size
        | scrub.part partition
        | scrub.chip
                                - really clean NAND erasing bad blocks (UNSAFE)
     nand markbad off [...]     - mark bad block(s) at offset (UNSAFE)
     nand biterr off            - make a bit error at offset (UNSAFE)

* 
  ``nboot``\ :raw-html-m2r:`<a id="nboot"></a>`\ :raw-html-m2r:`<br>`
  boot from NAND device

  .. code-block:: console

     nboot [partition] | [[[loadAddr] dev] offset]

* 
  ``nbootce``\ :raw-html-m2r:`<a id="nbootce"></a>`\ :raw-html-m2r:`<br>`
  Boot a Windows CE image from NAND

  .. code-block:: console

     nbootce [off|partitition]
              off               - flash offset (hex)
              partition         - partition name

* 
  ``nfs``\ :raw-html-m2r:`<a id="nfs"></a>`\ :raw-html-m2r:`<br>`
  boot image via network using NFS protocol  

  .. code-block:: console

     nfs [loadAddress] [[hostIPaddr:]bootfilename]

* 
  ``nm``\ :raw-html-m2r:`<a id="nm"></a>`\ :raw-html-m2r:`<br>`
  memory modify (constant address - non-incrementing); displays the memory
  address and current content and prompts for hexadecimal user input as desired
  new content for this address  

  .. code-block:: console

     nm [.b, .w, .l] address

         .b               - access memory in size byte ( 8 bit)
         .w               - access memory in size word (16 bit)
         .l               - access memory in size long (32 bit)
         address          - address for modification

* 
  ``ping``\ :raw-html-m2r:`<a id="ping"></a>`\ :raw-html-m2r:`<br>`
  send ICMP ECHO_REQUEST to network host  

  .. code-block:: console

     ping pingAddress

* 
  ``printenv``\ :raw-html-m2r:`<a id="printenv"></a>`\ :raw-html-m2r:`<br>`
  print environment variables  

  .. code-block:: console

     printenv [-a]              - print [all] values of all environment variables
     printenv name ...          - print value of environment variable 'name'

* 
  ``reset``\ :raw-html-m2r:`<a id="reset"></a>`\ :raw-html-m2r:`<br>`
  Perform RESET of the CPU

* 
  ``romupdate``\ :raw-html-m2r:`<a id="romupdate"></a>`\ :raw-html-m2r:`<br>`
  Creates an FCB data structure and writes an U-Boot image to flash  

  .. code-block:: console

     romupdate [-f {<part>|block#}] [-r [{<part>|block#}]] [-e #] [<address>] [<length>]
                -f <part>       write bootloader image to partition <part>
                -f #  write bootloader image at block # (decimal)
                -r  write redundant bootloader image at next free block after first image
                -r <part>       write redundant bootloader image to partition <part>
                -r #  write redundant bootloader image at block # (decimal)
                -e #  specify number of redundant blocks per boot loader image
                  (only valid if -f or -r specify a flash address rather than a partition name)
                -n  show what would be done without actually updating the flash
                <address>       RAM address of bootloader image (default: ${fileaddr})
                <length>        length of bootloader image in RAM (default: ${filesize})

* 
  ``run``\ :raw-html-m2r:`<a id="run"></a>`\ :raw-html-m2r:`<br>`
  run commands in an environment variable; environment variables can also
  store sequences of commands; run can be called with several variables as
  arguments  

  .. code-block:: console

     run var [...]                - run the commands in the environment
                                    variable(s) 'var'.

                                    If a variable contains several commands and
                                    the execution of one command fails, the
                                    remaining commands are executed anyway!

                                    If a call of run contains several variables
                                    and the execution of one command fails, the
                                    execution of run is terminated and the
                                    remaining variables are NOT executed!

* 
  ``saveenv``\ :raw-html-m2r:`<a id="saveenv"></a>`\ :raw-html-m2r:`<br>`
  save environment variables to persistent storage  

  **\ *Note:*\ **\ :raw-html-m2r:`<br>`
  All unsaved changes to the environment, like edited variables, will be lost
  when the system is rebooted next time.  

  **\ *Note:*\ **\ :raw-html-m2r:`<br>`
  Using this command **after** commands like `\ ``bootp`` <#bootp>`_ **will** save the IP
  settings (IP, gateway, serverip, etc.) into the environment!

* 
  ``setenv``\ :raw-html-m2r:`<a id="setenv"></a>`\ :raw-html-m2r:`<br>`
  set environment variables  

  .. code-block:: console

     setenv name value ...        - set environment variable 'name' to 'value ...'
     setenv name                  - delete environment variable 'name'
                                    Remember that name and value have to be separated
                                    by space and/or tab characters!

* 
  ``sleep``\ :raw-html-m2r:`<a id="sleep"></a>`\ :raw-html-m2r:`<br>`
  delay execution for some time

  .. code-block:: console

     sleep N                      - delay execution for N seconds (N is decimal!)

* 
  ``source``\ :raw-html-m2r:`<a id="source"></a>`\ :raw-html-m2r:`<br>`
  run script from memory  

  .. code-block:: console

     source [addr]                - run script starting at 'addr'
                                  - A valid image header must be present

* 
  ``tftpboot``\ :raw-html-m2r:`<a id="tftpboot"></a>`\ :raw-html-m2r:`<br>`
  boot image via network using TFTP protocol  

  .. code-block:: console

     tftpboot [loadAddress] [bootfilename]

  **\ *Note:*\ **\ :raw-html-m2r:`<br>`
  The default environment includes a variable of the name ``loadaddr`` which is
  used by default, and references using ``${loadaddr}``. Please *always* use
  variables, *not* addresses. For more see `here </uboot/uboot_environment-variables.md>`_

* 
  ``time``\ :raw-html-m2r:`<a id="time"></a>`\ :raw-html-m2r:`<br>`
  run commands and summarize execution time  

  .. code-block:: console

     time command [args...]

* 
  ``version``\ :raw-html-m2r:`<a id="version"></a>`\ :raw-html-m2r:`<br>`
  print monitor, compiler and linker version

----

Footnotes, Appendix & Sources
-----------------------------

Special thanks to:\ :raw-html-m2r:`<br>`
U-Boot Prompt\ :raw-html-m2r:`<br>`
U-Boot command "help"\ :raw-html-m2r:`<br>`
U-Boot command "help + command"  

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
