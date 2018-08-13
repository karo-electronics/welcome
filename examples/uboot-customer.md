# Examples

## How not to do things
To show an example what people do wrong, because of either not reading or not
actually understanding what they do wrong, hereafter an anonymised example
of an U-Boot environment of an actual customer:

```
U-Boot 2015.10-rc2 (Nov 14 2017 - 14:48:35 +0100)

CPU:   Freescale i.MX6Q rev1.2 at 792 MHz
Reset cause: POR
I2C:   ready
DRAM:  1 GiB
Board: Ka-Ro TX6Q-1110
VDDCORE set to 1421mV
VDDSOC  set to 1421mV
VDDIO   set to 3307mV
NAND:  128 MiB
MMC:   FSL_SDHC: 0, FSL_SDHC: 1
IPU HW Rev: 4
Temperature:   25 C, calibration data 0x5744e569
CPU clock set to 792.000 MHz
Baseboard: stk5-v3
MAC addr from fuse: <customer-id>
Net:   FEC
Hit any key to stop autoboot:  0
TX6Q U-Boot >
TX6Q U-Boot > printenv
autoload=no
autostart=no
baseboard=stk5-v3
baudrate=115200
bootFrom=nand
boot_mode=nand
bootargs_jffs2=run default_bootargs;set bootargs ${bootargs} root=/dev/mtdblock3 rootfstype=jffs2
bootargs_mmc=setenv bootargs ${bootargs} noinitrd rootfstype=ext4 root=/dev/mmcblk0p2 rw rootwait ${mtdparts} ip=off
bootargs_nand=setenv bootargs ${bootargs} noinitrd ubi.mtd=rootfs root=ubi0:rootfs rootfstype=ubifs rw ${mtdparts} gpmi_debug_init ip=off
bootargs_net=setenv bootargs ${bootargs} noinitrd root=${root} ip=${ip} nfsroot=${nfsroot}
bootargs_nfs=run default_bootargs;set bootargs ${bootargs} root=/dev/nfs nfsroot=${nfs_server}:${nfsroot},nolock ip=dhcp
bootargs_ubifs=run default_bootargs;set bootargs ${bootargs} ubi.mtd=rootfs root=ubi0:rootfs rootfstype=ubifs
bootcmd=run setup_env; run bootcmd_${bootFrom} bootm_cmd
bootcmd_jffs2=set autostart no;run bootargs_jffs2;nboot linux
bootcmd_mmc=run bootargs_mmc; ext2load mmc 0:1 ${loadaddr} uImage; ext2load mmc 0:1 ${fdtaddr} devicetree.dtb
bootcmd_nand=run bootargs_nand; setenv fdtaddr 11000000; nboot linux
bootcmd_net=run bootargs_net; tftp ${loadaddr} ${kernel}; bootm ${loadaddr}
bootdelay=0
bootedFrom=nand
bootfile=uImage
bootm_cmd=bootm
cpu_clk=800
default_bootargs=set bootargs init=/linuxrc console=ttymxc0,115200 ro debug panic=1 ${append_bootargs}
device_id=1010
dtbpath=<customer-id>/bootloader/imx6q-tx6q-11x0.dtb
ethact=FEC
ethaddr=<customer-id>
fdtaddr=11000000
fdtsave=fdt resize;nand erase.part dtb;nand write ${fdtaddr} dtb ${fdtsize}
fdtsize=a38a
hw_version=1.0
ip=192.168.23.103:192.168.100.1:192.168.100.1:255.255.0.0:<customer-id>:eth0:off
ipaddr=10.14.18.248
kernel=<customer-id>/uImage
kernelpath=<customer-id>/uImage
loadaddr=18000000
logopath=<customer-id>/bootloader/bootlogo<customer-id>.bmp
mtddevname=u-boot
mtddevnum=0
mtdids=nand0=gpmi-nand
mtdparts=mtdparts=gpmi-nand:1m@128k(u-boot),384k(env),6m(linux),119m(rootfs),896k(logo.bmp),128k(dtb),512k(bbt)ro
netmask=255.255.0.0
nfsroot=192.168.100.1:/tftpboot/<customer-id>/rootfs.net,nolock,nfsvers=3
otg_mode=device
partition=nand0,0
promptstr=<customer-id>
rfspathNand=<customer-id>/rootfs.nand
rfspathNet=/tftpboot/<customer-id>/rootfs.net
root=/dev/nfs rw
serverip=10.14.18.138
set_bootargs=setenv bootargs init=/sbin/init no_console_suspend=1 vt.global_cursor_default=0 consoleblank=0 console=ttymxc0,${baudrate} ro debug panic=1 video=${video_mode_kernel}
set_ip=setenv ip ${ipaddr}:${serverip}:${serverip}:${netmask}:${promptstr}:eth0:off
set_kernel=setenv kernel ${kernelpath}
set_nfsroot=setenv nfsroot ${serverip}:${rfspathNet},nolock,nfsvers=3
set_root=setenv root /dev/nfs rw
setup_env=run set_bootargs; run set_kernel; run set_root; run set_nfsroot; run set_ip
splashimage=18000000
splashpos=m,m
stderr=serial
stdin=serial
stdout=serial
touchpanel=tsc2007
ubootpath=<customer-id>/bootloader/u-boot-tx6q-11x0.bin
updateState=inactive
ver=U-Boot 2015.10-rc2 (Nov 14 2017 - 14:48:35 +0100)
video_mode=800x600MR-16@60
video_mode_kernel=mxcfb0:dev=ldb,LDB-VGA,if=RGB24

Environment size: 3049/131068 bytes
TX6Q U-Boot >
```

The above example is "as-is" with exception of everything marked ```<customer-id>```
, which removes the customers sepcifics as well as the unique MAC number of the
TX COM. The multiple IP used, are Class A and Class C networks.



## What did go wrong here?

### Baseboard
```
Baseboard: stk5-v3
MAC addr from fuse: 00:0c:c6:7a:41:f0
Net:   FEC
Hit any key to stop autoboot:  0
TX6Q U-Boot >
```

```
baseboard=stk5-v3
```


### Bootmode

Customer:
```
bootFrom=nand
```

Default:

```
boot_mode=nand
```


```
boot_mode=nand
bootargs_jffs2=run default_bootargs;set bootargs ${bootargs} root=/dev/mtdblock3 rootfstype=jffs2
bootargs_mmc=setenv bootargs ${bootargs} noinitrd rootfstype=ext4 root=/dev/mmcblk0p2 rw rootwait ${mtdparts} ip=off
bootargs_nand=setenv bootargs ${bootargs} noinitrd ubi.mtd=rootfs root=ubi0:rootfs rootfstype=ubifs rw ${mtdparts} gpmi_debug_init ip=off
bootargs_net=setenv bootargs ${bootargs} noinitrd root=${root} ip=${ip} nfsroot=${nfsroot}
bootargs_nfs=run default_bootargs;set bootargs ${bootargs} root=/dev/nfs nfsroot=${nfs_server}:${nfsroot},nolock ip=dhcp
bootargs_ubifs=run default_bootargs;set bootargs ${bootargs} ubi.mtd=rootfs root=ubi0:rootfs rootfstype=ubifs
bootcmd=run setup_env; run bootcmd_${bootFrom} bootm_cmd
bootcmd_jffs2=set autostart no;run bootargs_jffs2;nboot linux
bootcmd_mmc=run bootargs_mmc; ext2load mmc 0:1 ${loadaddr} uImage; ext2load mmc 0:1 ${fdtaddr} devicetree.dtb
```
# env default bootcmd_nand ### bootcmd_nand=run bootargs_nand; setenv fdtaddr 11000000; nboot linux

```
bootcmd_net=run bootargs_net; tftp ${loadaddr} ${kernel}; bootm ${loadaddr}
bootdelay=0
bootfile=uImage
bootm_cmd=bootm
```

see this:
```
default_bootargs=set bootargs init=/linuxrc console=ttymxc0,115200 ro debug panic=1 ${append_bootargs}
```

therein included ```${append_bootargs}```


### FDT handling
```
bootcmd_nand=run bootargs_nand; setenv fdtaddr 11000000; nboot linux
```

```
fdtaddr=11000000
fdtsave=fdt resize;nand erase.part dtb;nand write ${fdtaddr} dtb ${fdtsize}
```

Automagically created:
```
fdtsize=a38a
```


### NFS root
```
nfsroot=192.168.100.1:/tftpboot/<customer-id>/rootfs.net,nolock,nfsvers=3
```

```
root=/dev/nfs rw
```


```
rfspathNand=<customer-id>/rootfs.nand
rfspathNet=/tftpboot/<customer-id>/rootfs.net
```

### Network setup

```
ip=192.168.23.103:192.168.100.1:192.168.100.1:255.255.0.0:<customer-id>:eth0:off
ipaddr=10.14.18.248
```

### Setup

```
set_bootargs=setenv bootargs init=/sbin/init no_console_suspend=1 vt.global_cursor_default=0 consoleblank=0 console=ttymxc0,${baudrate} ro debug panic=1 video=${video_mode_kernel}
set_ip=setenv ip ${ipaddr}:${serverip}:${serverip}:${netmask}:${promptstr}:eth0:off
set_kernel=setenv kernel ${kernelpath}
set_nfsroot=setenv nfsroot ${serverip}:${rfspathNet},nolock,nfsvers=3
set_root=setenv root /dev/nfs rw
setup_env=run set_bootargs; run set_kernel; run set_root; run set_nfsroot; run set_ip
```

### Saving the environment after getting a IP
```
serverip=10.14.18.138
```


## Conclusion
The conclusion of this is best described in the fowllowing meme:

"We can explain it to you, ...

 but we can't understand it for you"

https://media.makeameme.org/created/i-can-explain-72g8po.jpg
