# Log

1. A full and complete bootlog:

```console
U-Boot 2015.10-rc2-04955-g9619f9d (Jul 05 2016 - 14:46:12 +0200)

CPU:   Freescale i.MX6UL rev1.1 at 396 MHz
Temperature: Industrial grade (-40C to 105C) at 42C - calibration data 0x5754e269
Reset cause: POR
I2C:   ready
DRAM:  256 MiB
Board: Ka-Ro TXUL-5010
PMIC: RN5T567
VDDCORE set to 1300mV
NAND:  128 MiB
MMC:   deferred ...
Video: 640x480x24
CPU clock set to 528.000 MHz
Baseboard: stk5-v3
MMC:   FSL_SDHC: 0
Net:   MAC addr from fuse: 00:0c:c6:7f:38:81
FEC0
Hit any key to stop autoboot:  0

Loading from nand0, offset 0x180000
   Image Name:   Linux-4.4.0-00118-g26d6b51
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    4476464 Bytes = 4.3 MiB
   Load Address: 80008000
   Entry Point:  80008000
## Booting kernel from Legacy Image at 82000000 ...
   Image Name:   Linux-4.4.0-00118-g26d6b51
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    4476464 Bytes = 4.3 MiB
   Load Address: 80008000
   Entry Point:  80008000
   Verifying Checksum ... OK
## Flattened Device Tree blob at 81000000
   Booting using the fdt blob at 0x81000000
   Loading Kernel Image ... OK
   reserving fdt memory region: addr=81000000 size=9000
   Loading Device Tree to 8e71e000, end 8e729fff ... OK

Starting kernel ...

Uncompressing Linux... done, booting the kernel.
Booting Linux on physical CPU 0x0
Linux version 4.4.0-00118-g26d6b51 (armsdk@armsdk) (gcc version 4.9.1 (GCC) ) #1 SMP PREEMPT Wed May 11 11:42:41 CEST 2016
CPU: ARMv7 Processor [410fc075] revision 5 (ARMv7), cr=10c5387d
CPU: PIPT / VIPT nonaliasing data cache, VIPT aliasing instruction cache
Machine model: Ka-Ro electronics TXUL-0010 Module
cma: Failed to reserve 320 MiB
Memory policy: Data cache writealloc
On node 0 totalpages: 65536
free_area_init_node: node 0, pgdat 80881600, node_mem_map 8fdf8000
  Normal zone: 512 pages used for memmap
  Normal zone: 0 pages reserved
  Normal zone: 65536 pages, LIFO batch:15
PERCPU: Embedded 12 pages/cpu @8fdd4000 s18112 r8192 d22848 u49152
pcpu-alloc: s18112 r8192 d22848 u49152 alloc=12*4096
pcpu-alloc: [0] 0
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 65024
Kernel command line: init=/linuxrc console=ttymxc0,115200 ro debug panic=1 ubi.mtd=rootfs root=ubi0:rootfs rootfstype=ubifs
PID hash table entries: 1024 (order: 0, 4096 bytes)
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 250516K/262144K available (6078K kernel code, 193K rwdata, 2128K rodata, 280K init, 436K bss, 11628K reserved, 0K cma-reserved, 0K highmem)
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xffc00000 - 0xfff00000   (3072 kB)
    vmalloc : 0x90800000 - 0xff800000   (1776 MB)
    lowmem  : 0x80000000 - 0x90000000   ( 256 MB)
    pkmap   : 0x7fe00000 - 0x80000000   (   2 MB)
    modules : 0x7f000000 - 0x7fe00000   (  14 MB)
      .text : 0x80008000 - 0x8080bd28   (8208 kB)
      .init : 0x8080c000 - 0x80852000   ( 280 kB)
      .data : 0x80852000 - 0x808827a0   ( 194 kB)
       .bss : 0x808827a0 - 0x808ef91c   ( 437 kB)
SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Preemptible hierarchical RCU implementation.
	Build-time adjustment of leaf fanout to 32.
	RCU restricting CPUs from NR_CPUS=4 to nr_cpu_ids=1.
RCU: Adjusting geometry for rcu_fanout_leaf=32, nr_cpu_ids=1
NR_IRQS:16 nr_irqs:16 16
Switching to timer-based delay loop, resolution 41ns
sched_clock: 32 bits at 24MHz, resolution 41ns, wraps every 89478484971ns
clocksource: mxc_timer1: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635851949 ns
Console: colour dummy device 80x30
Calibrating delay loop (skipped), value calculated using timer frequency.. 48.00 BogoMIPS (lpj=240000)
pid_max: default: 32768 minimum: 301
Mount-cache hash table entries: 1024 (order: 0, 4096 bytes)
Mountpoint-cache hash table entries: 1024 (order: 0, 4096 bytes)
CPU: Testing write buffer coherency: ok
/cpus/cpu@0 missing clock-frequency property
CPU0: thread -1, cpu 0, socket 0, mpidr 80000000
Setting up static identity map for 0x800082c0 - 0x80008318
Brought up 1 CPUs
SMP: Total of 1 processors activated (48.00 BogoMIPS).
CPU: All CPU(s) started in SVC mode.
devtmpfs: initialized
VFP support v0.3: implementor 41 architecture 2 part 30 variant 7 rev 5
clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 19112604462750000 ns
pinctrl core: initialized pinctrl subsystem
NET: Registered protocol family 16
DMA: preallocated 256 KiB pool for atomic coherent allocations
cpuidle: using governor ladder
cpuidle: using governor menu
imx6ul-pinctrl 20e0000.iomuxc: no fsl,pins property in node /soc/aips-bus@02000000/iomuxc@020e0000/hoggrp
imx6ul-pinctrl 20e0000.iomuxc: initialized IMX pinctrl driver
mxs-dma 1804000.dma-apbh: initialized
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
i2c-gpio i2c-gpio: using pins 129 (SDA) and 128 (SCL)
i2c i2c-0: IMX I2C adapter registered
i2c i2c-0: can't use DMA
Linux video capture interface: v2.00
pps_core: LinuxPPS API ver. 1 registered
pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
PTP clock support registered
Advanced Linux Sound Architecture Driver Initialized.
clocksource: Switched to clocksource mxc_timer1
NET: Registered protocol family 2
TCP established hash table entries: 2048 (order: 1, 8192 bytes)
TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
TCP: Hash tables configured (established 2048 bind 2048)
UDP hash table entries: 256 (order: 1, 8192 bytes)
UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
NET: Registered protocol family 1
RPC: Registered named UNIX socket transport module.
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
futex hash table entries: 256 (order: 2, 16384 bytes)
NFS: Registering the id_resolver key type
Key type id_resolver registered
Key type id_legacy registered
fuse init (API version 7.23)
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
Console: switching to colour frame buffer device 80x30
mxsfb 21c8000.lcdif: initialized
imx-sdma 20ec000.sdma: Direct firmware load for imx/sdma/sdma-imx6q.bin failed with error -2
imx-sdma 20ec000.sdma: Falling back to user helper
2020000.serial: ttymxc0 at MMIO 0x2020000 (irq = 19, base_baud = 5000000) is a IMX
console [ttymxc0] enabled
21e8000.serial: ttymxc1 at MMIO 0x21e8000 (irq = 218, base_baud = 5000000) is a IMX
[drm] Initialized drm 1.1.0 20060810
brd: module loaded
loop: module loaded
nand: device found, Manufacturer ID: 0x2c, Chip ID: 0xf1
nand: Micron MT29F1G08ABAEAWP
nand: 128 MiB, SLC, erase size: 128 KiB, page size: 2048, OOB size: 64
gpmi-nand 1806000.gpmi-nand: enable the asynchronous EDO mode 5
Bad block table found at page 65472, version 0x01
Bad block table found at page 65408, version 0x01
8 ofpart partitions found on MTD device gpmi-nand
Creating 8 MTD partitions on "gpmi-nand":
0x000000020000-0x000000120000 : "u-boot"
0x000000120000-0x000000180000 : "env"
0x000000180000-0x000000780000 : "linux"
0x000000780000-0x000002780000 : "rootfs"
0x000001560000-0x000007c60000 : "userfs"
0x000006180000-0x000006280000 : "logo.bmp"
0x000007f00000-0x000007f80000 : "dtb"
0x000007f80000-0x000008000000 : "bbt"
gpmi-nand 1806000.gpmi-nand: driver registered.
vcan: Virtual CAN interface driver
CAN device driver interface
2090000.flexcan supply xceiver not found, using dummy regulator
flexcan 2090000.flexcan: device registered (reg_base=90a00000, irq=21)
2094000.flexcan supply xceiver not found, using dummy regulator
flexcan 2094000.flexcan: device registered (reg_base=90a08000, irq=22)
pps pps0: new PPS source ptp0
libphy: fec_enet_mii_bus: probed
fec 2188000.ethernet eth0: registered PHC device 0
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
usbcore: registered new interface driver usb-storage
usbcore: registered new interface driver ums-datafab
usbcore: registered new interface driver ums-realtek
usbcore: registered new interface driver ums-sddr09
usbcore: registered new interface driver ums-sddr55
ci_hdrc ci_hdrc.1: EHCI Host Controller
ci_hdrc ci_hdrc.1: new USB bus registered, assigned bus number 1
ci_hdrc ci_hdrc.1: USB 2.0 started, EHCI 1.00
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: EHCI Host Controller
usb usb1: Manufacturer: Linux 4.4.0-00118-g26d6b51 ehci_hcd
usb usb1: SerialNumber: ci_hdrc.1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
input: 20b8000.kpp as /devices/platform/soc/2000000.aips-bus/20b8000.kpp/input/input0
edt_ft5x06 0-0038: touchscreen probe failed
usbcore: registered new interface driver usbtouchscreen
snvs_rtc 20cc000.snvs:snvs-rtc-lp: rtc core: registered 20cc000.snvs:snvs-r as rtc0
i2c /dev entries driver
imx2-wdt 20bc000.wdog: timeout 60 sec (nowayout=0)
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sdhci-pltfm: SDHCI platform and OF driver helper
/soc/aips-bus@02100000/usdhc@02190000: voltage-ranges unspecified
sdhci-esdhc-imx 2190000.usdhc: Got CD GPIO
sdhci-esdhc-imx 2190000.usdhc: No vmmc regulator found
sdhci-esdhc-imx 2190000.usdhc: No vqmmc regulator found
mmc0: SDHCI controller on 2190000.usdhc [2190000.usdhc] using ADMA
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
sgtl5000 0-000a: sgtl5000 revision 0x11
NET: Registered protocol family 17
can: controller area network core (rev 20120528 abi 9)
NET: Registered protocol family 29
can: raw protocol (rev 20120528)
can: broadcast manager protocol (rev 20120528 t)
lib80211: common routines for IEEE802.11 drivers
lib80211_crypt: registered algorithm 'NULL'
lib80211_crypt: registered algorithm 'WEP'
lib80211_crypt: registered algorithm 'CCMP'
lib80211_crypt: registered algorithm 'TKIP'
Key type dns_resolver registered
cpu cpu0: dev_pm_opp_get_opp_count: device OPP not found (-19)
Registering SWP/SWPB emulation handler
sgtl5000 0-000a: Using internal LDO instead of VDDD
asoc-simple-card sound: sgtl5000 <-> 202c000.sai mapping ok
ubi0: default fastmap pool size: 10
ubi0: default fastmap WL pool size: 5
ubi0: attaching mtd3
ubi0: scanning is finished
ubi0: attached mtd3 (name "rootfs", size 32 MiB)
ubi0: PEB size: 131072 bytes (128 KiB), LEB size: 126976 bytes
ubi0: min./max. I/O unit sizes: 2048/2048, sub-page size 2048
ubi0: VID header offset: 2048 (aligned 2048), data offset: 4096
ubi0: good PEBs: 256, bad PEBs: 0, corrupted PEBs: 0
ubi0: user volume: 1, internal volumes: 1, max. volumes count: 128
ubi0: max/mean erase counter: 2/1, WL threshold: 4096, image sequence number: 3389832359
ubi0: available PEBs: 0, total reserved PEBs: 256, PEBs reserved for bad PEB handling: 20
ubi0: background thread "ubi_bgt0d" started, PID 112
snvs_rtc 20cc000.snvs:snvs-rtc-lp: setting system clock to 1970-01-01 00:10:33 UTC (633)
vdd3p0: disabling
ALSA device list:
  #0: imx6ul-tx6ul-sgtl5000-audio
UBIFS (ubi0:0): UBIFS: mounted UBI device 0, volume 0, name "rootfs", R/O mode
UBIFS (ubi0:0): LEB size: 126976 bytes (124 KiB), min./max. I/O unit sizes: 2048 bytes/2048 bytes
UBIFS (ubi0:0): FS size: 27934720 bytes (26 MiB, 220 LEBs), journal size 1396736 bytes (1 MiB, 11 LEBs)
UBIFS (ubi0:0): reserved for root: 1319425 bytes (1288 KiB)
UBIFS (ubi0:0): media format: w4/r0 (latest is w4/r0), UUID AE415342-EBDD-4668-BF5D-C4F91AAAC3F7, small LPT model
VFS: Mounted root (ubifs filesystem) readonly on device 0:13.
devtmpfs: mounted
Freeing unused kernel memory: 280K (8080c000 - 80852000)
Executing /sbin/init
random: nonblocking pool is initialized
INIT: version 2.88 booting
Activating swap...done.
Initializing /var... Done.
Setting the system clock.
Loading kernel modules...done.
Activating lvm and md swap...done.
Checking file systems...imx-sdma 20ec000.sdma: loaded firmware 3.1
fsck from util-linux-ng 2.16
done.
Mounting local filesystems...done.
Activating swapfile swap...done.
Cleaning up temporary files....
Cleaning up temporary files....
Setting the system clock.
UBIFS (ubi0:0): background thread "ubifs_bgt0_0" started, PID 459
UBIFS (ubi0:0): background thread "ubifs_bgt0_0" stops
INIT: Entering runlevel: 2
Starting internet superserver: inetd done.
Configuring network interfaces: fec 2188000.ethernet eth0: Freescale FEC PHY driver [SMSC LAN8710/LAN8720] (mii_bus:phy_addr=2188000.ethernet:00, irq=166)
err, eth0: timed out
err, eth0: lease information file `/var/lib/dhcpcd/dhcpcd-eth0.info' does not exist
warn, eth0: using IPV4LL address 169.254.107.78
done.
Starting telnetd...
Setting sysfs variables....

GNU/Linux 4.4.0-00118-g26d6b51 on triton1(armv7l) /dev/ttymxc0:
All your base are belong to us
triton1 login: root
Password:
You are logged in on the Triton Starterkit System
root@triton1:~#
```

---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
