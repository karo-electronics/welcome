# Example: `printenv`

```console
TX6DL U-Boot > pr
autoload=no
autostart=no
baseboard=stk5-v5
baudrate=115200
boot_mode=nand
bootargs_jffs2=run default_bootargs;setenv bootargs ${bootargs} root=/dev/mtdblock3 rootfstype=jffs2
bootargs_mmc=run default_bootargs;setenv bootargs ${bootargs} root=/dev/mmcblk0p2 rootwait
bootargs_nfs=run default_bootargs;setenv bootargs ${bootargs} root=/dev/nfs nfsroot=${nfs_server}:${nfsroot},nolock ip=dhcp
bootargs_ubifs=run default_bootargs;setenv bootargs ${bootargs} ubi.mtd=rootfs root=ubi0:rootfs rootfstype=ubifs
bootcmd=run bootcmd_${boot_mode} bootm_cmd
bootcmd_jffs2=setenv autostart no;run bootargs_jffs2;nboot linux
bootcmd_mmc=setenv autostart no;run bootargs_mmc;fatload mmc 0 ${loadaddr} uImage
bootcmd_nand=setenv autostart no;run bootargs_ubifs;nboot linux
bootcmd_net=setenv autoload y;setenv autostart n;run bootargs_nfs;dhcp
bootdelay=-1
bootfile=uImage
bootm_cmd=bootm ${loadaddr} - ${fdtaddr}
cpu_clk=792
date=2016-07-04
default_bootargs=setenv bootargs init=/linuxrc console=ttymxc0,115200 ro debug panic=1 ${append_bootargs}
ethact=FEC
ethaddr=00:0c:c6:7a:39:60
fdtaddr=11000000
fdtsave=fdt resize;nand erase.part dtb;nand write ${fdtaddr} dtb ${fdtsize}
fdtsize=a000
lcd_rotation=2
loadaddr=18000000
mtddevname=u-boot
mtddevnum=0
mtdids=nand0=gpmi-nand
mtdparts=mtdparts=gpmi-nand:1024k@0x20000(u-boot),384k(env),6m(linux),32m(rootfs),89600k(logo.bmp),512k@0x7f00000(dtb),512k@0x7f80000(bbt)ro
nfsroot=/tftpboot/rootfs
otg_mode=none
partition=nand0,0
splashimage=18000000
stderr=serial
stdin=serial
stdout=serial
touchpanel=edt-ft5x06
tx6_variant=tx6u-80x0
u=setenv autoload y;run uboot_file;bootp;romupdate
uboot_file=setenv bootfile 192.168.1.225:imx6q/u-boot-${tx6_variant}-${date}.bin
ver=U-Boot 2015.10-rc2-04954-g13a3e2e (Jul 04 2016 - 15:02:00 +0200)
video_mode=ET0700

Environment size: 1873/131068 bytes
```

---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
