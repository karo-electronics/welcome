# Command Listing

This list of available commands in U-Boot, is comprised from **all** TX COM
variants and thus can include commands that are either specific to a modules of:

* The same SOC family: i.MX50 -> i.MX51 & i.MX53
* The same COM variant: NAND or eMMC

and hence are not applicable to all TX COM. Please use the command `help` to
see the list appropriate to the used TX COM.

|   Command    | Description                                                  |
|:------------:|:-------------------------------------------------------------|
| `?`	         | alias for `help`
| `base`       | print or set address offset
| `bdinfo`     | print Board Info structure
| `bmp`	       | manipulate BMP image data
| `boot`       | boot default, i.e., `run 'bootcmd'`
| `bootce`     | Boot a Windows CE image from memory
| `bootd`      | boot default, i.e., `run 'bootcmd'`
| `bootm`      | boot application image from memory
| `bootp`      | boot image via network using BOOTP/TFTP protocol
| `ceconnect`  | Set up a connection to the CE host PC over TCP/IP and download the run-time image
| `chpart`     | change active partition
| `clocks`*    | display clocks
| `cls`	       | clear screen
| `cmp`	       | memory compare
| `coninfo`    | print console devices and information
| `cp`	       | memory copy
| `crc32`      | checksum calculation
| `dcache`     | enable or disable data cache
| `dhcp`       | boot image via network using DHCP/TFTP protocol
| `echo`       | echo args to console
| `editenv`    | edit environment variable
| `env`	       | environment handling commands
| `ext2load`   | load binary file from a ext2 filesystem
| `ext2ls`     | list files in a directory (default `/`)
| `fatinfo`    | print information about filesystem
| `fatload`    | load binary file from a dos filesystem
| `fatls`      | list files in a directory (default `/`)
| `fbdump`     | dump framebuffer contents to flash
| `fdt`	       | flattened device tree utility commands
| `go`	       | start application at address `addr`
| `help`       | print command description/usage
| `icache`     | enable or disable instruction cache
| `iim`*       | IIM sub system
| `iminfo`     | print header information for application image
| `imxtract`   | extract a part of a multi-image
| `itest`      | return true/false on integer compare
| `loadb`      | load binary file over serial line (kermit mode)
| `loads`      | load S-Record file over serial line
| `loady`      | load binary file over serial line (ymodem mode)
| `loop`       | infinite loop on address range
| `md`	       | memory display
| `mdio`*      | MDIO utility commands
| `mii`	       | MII utility commands
| `mm`	       | memory modify (auto-incrementing address)
| `mmc`	       | MMC sub system
| `mmcinfo`    | display MMC info
| `mtdparts`   | define flash/nand partitions
| `mtest`      | simple RAM read/write test
| `mw`	       | memory write (fill)
| `nand`       | NAND sub-system
| `nboot`      | boot from NAND device
| `nbootce`    | Boot a Windows CE image from NAND
| `nfs`	       | boot image via network using NFS protocol
| `nm`	       | memory modify (constant address)
| `ping`       | send ICMP ECHO_REQUEST to network host
| `printenv`   | print environment variables
| `reset`      | Perform RESET of the CPU
| `romupdate`* | Creates an FCB data structure and writes an U-Boot image to flash
| `run`	       | run commands in an environment variable
| `saveenv`    | save environment variables to persistent storage
| `setenv`     | set environment variables
| `sleep`      | delay execution for some time
| `source`     | run script from memory
| `tftpboot`   | boot image via network using TFTP protocol
| `time`       | run commands and summarize execution time
| `version`    | print monitor, compiler and linker version

# something something dark side
                    * Commands are not available on all TX Series CoM


7.2 Commands and explanations
* `?`
       ï° alias for 'help'
* `base`
       print or set address offset which is used for all memory commands
       base                       - print address offset for memory commands
       base off                   - set address offset for memory commands to 'off'

* `bdinfo`
       print Board Info structure
       bdinfo                     - prints the information that U-Boot passes about the board such as
                                  memory addresses and sizes, clock frequencies, MAC address, etc.

* `bmp`
       manipulate BMP image data
       bmp info <imageAddr>
                                  - display image info bmp display <imageAddr> [x y]
                                  - display image at x,y

* `boot`
       the same as bootd; boot default, i.e., run 'bootcmd'

* `bootce`
       bootce - Boot a Windows CE image from memory
       bootce [args..]
                                  addr           - boot image from address 'addr'

* `bootd`
       bootd - boot default, i.e., run 'bootcmd'

* `bootm`
       boot application image from memory
       boot default, i.e., run 'bootcmd'
       bootm [addr [arg ...]]     - boot application image stored in memory
                                  passing arguments 'arg ...'; when booting a Linux kernel,
                                  'arg' can be the address of an initrd image

* `bootp`
       boot image via network using BOOTP/TFTP protocol
       bootp [loadAddress] [[hostIPaddr:]bootfilename]

* `ceconnect`
       Set up a connection to the CE host PC over TCP/IP and download the run-time image
       ceconnect [-v] [-t <timeout>]
                                 -v          verbose operation
                                 -t <timeout>
                                             - max wait time (#sec) for the connection

* `chpart`
       change active partition

* `clocks`*      (only: TX51, TX53)
       display clocks

* `cls`
       clear screen

* `cmp`
       memory compare
       cmp [.b, .w, .l] addr1 addr2 count
                                 compare memory
                                 .b          - access memory in size byte ( 8 bit)
                                 .w          - access memory in size word (16 bit)
                                 .l          - access memory in size long (32 bit)
                                 addr1       - address of memory area 1
                                 addr2       - address of memory area 2
                                 count       - number of elements (byte, word, long) to compare

* `coninfo`
       print console devices and information

* `cp`
       memory copy
       cp [.b, .w, .l] source target count
                                 copy memory
                                 .b            - access memory in size byte ( 8 bit)
                                 .w            - access memory in size word (16 bit)
                                 .l            - access memory in size long (32 bit)
                                 source        - source address of the data
                                 target        - target address of the data
                                 count         - number of elements (byte, word, long) to copy

* `crc32`
       checksum calculation
       crc32 addr1 count [addr2]
                                 calculate checksum of data starting at address addr1 for length count
                                 and (if given) store the result at address addr2
                                 addr1         - start address of data
                                 count         - number of memory addresses of the data
                                 addr2         - storage address for the result of the calculation

* `dcache`
       enable or disable data cache
       dcache [on, off, flush]
                                 enable, disable, or flush data (writethrough) cache

* `dhcp`  
       invoke DHCP client to obtain IP/boot params and load ${bootfile} via TFTP if the
           environment variable 'autoload' is set to 'yes'

* `echo`  
       echo args to console
       echo [args]               - echo args to console; \c suppresses newline

* `editenv`  
       edit environment variable
       editenv name              - edit environment variable 'name'

* `env`  
  environment handling commands<br>
        env default [-f] -a                   - [forcibly] reset default environment
        env default [-f] var [...]            - [forcibly] reset variable(s) to their default values
        env delete [-f] var [...]             - [forcibly] delete variable(s)
        env edit name                         - edit environment variable
        env export [-t | -b | -c] [-s         size] addr [var ...]
                                              - export environment
        env import [-d] [-t | -b | -c] addr [size]
                                              - import environment
        env print [-a | name ...]             - print environment
        env run var [...]                       - run commands in an environment variable
        env save                              - save environment
        env set [-f] name [arg ...]           - [forcibly] set environment variable

* `ext2load`  
        load binary file from a Ext2 filesystem<br>
        ext2load <interface> <dev[:part]>           [addr] [filename] [bytes]
                                     load binary file 'filename' from 'dev' on 'interface' to
                                     address 'addr' from ext2 filesystem

* `ext2ls`  
        list files in a directory (default /)<br>
        ext2ls <interface> <dev[:part]> [directory]
                                     list files from 'dev' on 'interface' in a 'directory'

* `fatinfo`  
        print information about filesystem<br>
        fatinfo <interface> <dev[:part]>
                                     print information about filesystem from 'dev' on 'interface'

* `fatload`  
        load binary file from a dos filesystem<br>
        fatload <interface> <dev[:part]> <addr> <filename> [bytes]
                                     load binary file 'filename' from 'dev' on 'interface'
                                     to address 'addr' from DOS filesystem

* `fatls`  
        list files in a directory (default /)<br>
        fatls <interface> <dev[:part]> [directory]
                                     list files from 'dev' on 'interface' in a 'directory'

* `fbdump`  
       dump framebuffer contents to flash
       fbdump [partition name]
                                 default partition name: 'logo'

* `fdt`  
  flattened device tree utility commands
       fdt addr    <addr> [<length>] - Set the fdt location to <addr>
       fdt boardsetup                    - Do board-specific set up
       fdt move    <fdt> <newaddr> <length>
                                         - Copy the fdt to <addr> and make it active
       fdt  resize                       - Resize fdt to size + padding to 4k addr
       fdt  print <path> [<prop>]        - Recursive print starting at <path>
       fdt  list   <path> [<prop>]              - Print one level starting at <path>
       fdt  set    <path> <prop> [<val>]
                                         - Set <property> [to <val>]
       fdt  mknode <path> <node>         - Create a new node after <path>
       fdt  rm     <path> [<prop>]       - Delete the node or <property>
       fdt  header                       - Display header info
       fdt  bootcpu <id>                 - Set boot cpuid
       fdt  memory <addr> <size>         - Add/Update memory node
       fdt  rsvmem print                 - Show current mem reserves
       fdt  rsvmem add <addr> <size>     - Add a mem reserve
       fdt  rsvmem delete <index>        - Delete a mem reserves
       fdt  chosen [<start> <end>]       - Add/update the /chosen branch in the tree
                                         <start>/<end> - initrd start/end addr

_Note:<br>
Dereference aliases by omitting the leading `/`, e.g. `fdt print ethernet0`._


* `go`  
  start application at address `addr`

  `go addr [arg ...]` - start application at address `addr` passing `arg` as arguments

* `help`  
  print online help
  <br>(alias: `?`)

  `help [command ...]` - show help information (for `command`)

  `help` prints online help for the monitor commands. Without arguments, it
   prints a short usage message for all commands. To get detailed help information
   for specific commands you can type `help` with one or more command names as
   arguments.

* `icache`  
       enable or disable instruction cache
       icache [on, off, flush]
                                  enable, disable, or flush instruction cache


* `iim`  
 (only: TX51, TX53)
       IIM sub system
       iim Warning: all numbers in parameter are in hex format!
       iim read <bank> <row>      - Read some fuses
       iim read fecmac            - Read FEC Mac address
       iim blow <bank> <row> <value>
                                  - Blow some fuses
       iim blow fecmac <0x##:0x##:0x##:0x##:0x##:0x##>
                                  - Blow FEC Mac address


* `iminfo`  
       print header information for application image
       iminfo addr [addr â¦]       - print header information for application image starting at
                                  address 'addr' in memory; this includes verification of the
                                  image contents (magic number, header and payload checksums)

* `imxtract`  
       extract a part of a multi-image
       imxtract addr part [dest]
                                  extract <part> from legacy image at <addr> and copy to <dest>

* `itest`  
       return true/false on integer compare
       itest [.b, .w, .l, .s] [*]value1 <op> [*]value2
                                  .b            - access memory in size        byte ( 8 bit)
                                  .w            - access memory in size        word (16 bit)
                                  .l            - access memory in size        long (32 bit)

* `loadb`  
       load binary file over serial line (kermit mode)
       loadb [ off ] [ baud ]     - load binary file over serial line with offset 'off' and baudrate
                                  'baud'

* `loads`  
       load S-Record file over serial line
       loads [ off ]              - load S-Record file over serial line with offset 'off'


* `loady`  
      load binary file over serial line (ymodem mode)
      loady [ off ] [ baud ]    - load binary file over serial line with offset 'off' and baudrate
                                'baud'

* `loop`  
      infinite loop on address range
      loop [.b, .w, .l] address count
                                loop on a set of addresses
                                .b             - access memory in size byte ( 8 bit)
                                .w             - access memory in size word (16 bit)
                                .l             - access memory in size long (32 bit)
                                address        - start address of the loop
                                count          - number of objects to read
                                This command can only be terminated by resetting the board!

* `md`  
      memory display, used to display memory contents both as hexadecimal and ASCII data.
      md [.b, .w, .l] address [count]
                                memory display
                                .b             - access memory in size       byte ( 8 bit)
                                .w             - access memory in size       word (16 bit)
                                .l             - access memory in size       long (32 bit)
                                address        - start address
                                count          - number of objects to be    displayed

* `mdio`  
  (only: TX51, TX53)
      MDIO utility commands
      mdio list                 - List MDIO   buses
      mdio read <phydev> [<devad>.]<reg>
                                - read PHY's register at <devad>.<reg>
      mdio write <phydev> [<devad>.]<reg> <data>
                                - write PHY's register at <devad>.<reg>
      <phydev> may be:
                                <busname> <addr>
                                <addr>
                                <eth name>
      <addr> <devad>, and <reg> may be ranges, e.g. 1-5.4-0x1f.

* `mii`  
     MII utility commands
     mii device                - list available devices
     mii device  <devname>     - set current device
     mii info    <addr>        - display MII PHY info
     mii read    <addr> <reg> -  read MII PHY <addr> register <reg>
     mii write   <addr> <reg> <data>
                               - write MII PHY <addr> register <reg>
     mii dump    <addr> <reg> - pretty-print <addr> <reg> (0-5 only)
                               <addr> and/or <reg> may be ranges, e.g. 2-7.

* `mm`  
     memory modify (auto-incrementing); displays the memory address and current content and
         prompts for hexadecimal user input as desired new content for this address; the address is
         automatically incremented each time
     mm[.b, .w, .l] address
                               .b              - access memory in size byte ( 8 bit)
                               .w              - access memory in size word (16 bit)
                               .l              - access memory in size long (32 bit)
                               address         - start address for modification

* `mmc`  
     MMC sub system
     mmc read addr blk# cnt
     mmc write addr blk# cnt
     mmc erase blk# cnt
     mmc rescan
     mmc part                  - lists available partition on current mmc device
     mmc dev [dev] [part]      - show or set current mmc device [partition]
     mmc list                  - lists available devices

* `mmcinfo`  
     display MMC info
     mmcinfo                   - device number of the device to dislay info of

* `mtdparts`  
      define flash/nand partitions
      mtdparts                   - list partition table
      mtdparts delall            - delete all partitions
      mtdparts del part-id       - delete partition (e.g. part-id = nand0,1)
      mtdparts default           - reset partition table to defaults
      mtdparts add <mtd-dev> <size>[@<offset>] [<name>] [ro]
                                 - add partition
      the command uses three environment variables:
      partition                  - keeps current partition identifier
                                 partition        := <part-id>
                                 <part-id>        := <dev-id>,part_num
      mtdids                     - linux kernel mtd device id <-> u-boot device id mapping
                                 mtdids            = <idmap>[,<idmap>,...]
                                 <idmap>          := <dev-id>=<mtd-id>
                                 <dev-id>         := [nand | nor]<dev-num>
                                 <dev-num>        := mtd device number, 0
                                 <mtd-id>         := unique device tag used by linux kernel to find
                                 mtd device (mtd->name)
      mtdparts                   - partition list
                                 mtdparts          = mtdparts=<mtd-def>[;<mtd-def>...]
                                 <mtd-def>        := <mtd-id>:<part-def>[,<part-def>...]
                                 <mtd-id>         := unique device tag used by linux kernel to find
                                 mtd device (mtd->name)
                                 <part-def> := <size>[@<offset>][<name>][<ro-flag>]
                                 <size>           := standard linux memsize OR '-' to denote all
                                 remaining space
                                 <offset>         := partition start offset within the device
                                 <name>           := '(' NAME ')'
                                 <ro-flag>        := when set to 'ro' makes partition read-only (not
                                 used, passed to kernel)

* `mtest`  
      simple RAM test
      mtest [start [end [pattern [iterations]]]]
                                 simple RAM read/write test
                                 start            - start address of the RAM test area
                                 end              - end address of the RAM test area
                                 pattern          - pattern, that is applied to the RAM for testing
                                                    Note:
      This test changes the contents of the RAM and may therefore cause crashing of the system
         if the memory area, where this test is applied to, is needed for the system operation.

* `mw`  
     memory write (fill)
     mw [.b, .w, .l] address value [count]
                             write memory
                             .b             - access memory in size byte ( 8 bit)
                             .w             - access memory in size word (16 bit)
                             .l             - access memory in size long (32 bit)
                             address        - start address to write to
                             value          - value to write to the address(es)
                             count          - number of addresses to which "value" is written

* `nand`  
     NAND sub-system
     `nand info`               - show available NAND devices
     nand device [dev]       - show or set current device
     nand read               - addr off|partition size
     nand write              - addr off|partition size
                             read/write 'size' bytes starting at offset 'off'
                             to/from memory address 'addr', skipping bad blocks.
     nand read.raw           - addr off|partition
     nand write.raw          - addr off|partition
                             Use read.raw/write.raw to avoid ECC and access the page as-is.
     nand erase[.spread] [clean] off size
                             - erase 'size' bytes from offset 'off'
                             With '.spread', erase enough for given file size, otherwise, 'size'
                             includes skipped bad blocks.
     nand erase.part [clean] partition
                             - erase entire mtd partition'
     nand erase.chip [clean] - erase entire chip'
     nand bad                - show bad blocks
     nand dump[.oob] off     - dump page
     nand scrub [-y] off size | scrub.part partition | scrub.chip
                             - really clean NAND erasing bad blocks (UNSAFE)
     nand markbad off [...]    - mark bad block(s) at offset (UNSAFE)
     nand biterr off         - make a bit error at offset (UNSAFE)

* `nboot`  
       boot from NAND device
       nboot [partition] | [[[loadAddr] dev] offset]

* `nbootce`  
       Boot a Windows CE image from NAND
       nbootce [off|partitition]
                                 off            - flash offset (hex)
                                 partition      - partition name

* `nfs`  
       boot image via network using NFS protocol
       nfs [loadAddress] [host ip addr:bootfilename]

* `nm`  
       memory modify (constant address â non-incrementing); displays the memory address and
           current content and prompts for hexadecimal user input as desired new content for this
           address
       nm [.b, .w, .l] address
                                 memory modify, read and keep address
                                 .b             - access memory in size byte ( 8 bit)
                                 .w             - access memory in size word (16 bit)
                                 .l             - access memory in size long (32 bit)
                                 address        - address for modification

* `ping`  
       send ICMP ECHO_REQUEST to network host
       ping pingAddress

* `printenv`  
  print environment variables  
  ```console
       printenv                  - print values of all environment variables
       printenv name             - print value of environment variable 'name'
  ```

* `reset`  
  Perform RESET of the CPU

* `romupdate`  
  Creates an FCB data structure and writes an U-Boot image to flash  
  ```console
  romupdate [-b #] [-n #] [-f #] [-r [#]] [<address>] [<length>]
             -b #       - first FCB block number (default 0)
             -n #       - total number of FCB blocks (default 1)
             -f #       - write bootloader image at block #
             -r         - write redundant bootloader image at next free block after first image
             -r #       - write redundant bootloader image at block #
             -e #       - specify number of redundant blocks per boot loader image

             <address>  - RAM address of bootloader image (default: ${fileaddr})

             <length>   - length of bootloader image in RAM (default: ${filesize})
  ```

* `run`  
  run commands in an environment variable; environment variables can also store sequences
           of commands; run can be called with several variables as arguments

       `run var [...]`              - run the commands in the environment variable(s) 'var'
                                  If a variable contains several commands and the execution of one
                                  command fails, the remaining commands are executed anyway!
                                  If a call of run contains several variables and the execution of one
                                  command fails, the execution of run is terminated and the remaining
                                  variables are NOT executed!

* `saveenv`  
  save environment variables to persistent storage (all unsaved changes to the
  environment variables will be lost when the system is rebooted next time)

* `setenv`  
  set environment variables  
  ```console
       setenv name value ...      - set environment variable 'name' to 'value ...'
       setenv name                - delete environment variable 'name'
                                  Remember that name and value have to be separated by space and/or
                                  tab characters!
  ```

* `sleep`  
  delay execution for some time
  ```console
  sleep N                    - delay execution for N seconds (N is decimal!)
  ```

* `source`  
  run script from memory  
  ```console
  source [addr]         - run script starting at addr
                        - A valid image header must be present
  ```
* `tftpboot`  
  boot image via network using TFTP protocol  
  ```console
  tftpboot [loadAddress] [bootfilename]
  ```

* `time`  
  run commands and summarize execution time  
  ```console
  time command [args...]
  ```
* `version`  
  print monitor version (prints version and build date of currently running U-Boot)

---

[Ka-Ro electronics GmbH](http://www.karo-electronics.de)

Contact support: support@karo-electronics.de
