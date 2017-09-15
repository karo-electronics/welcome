
```console

Environment size: 1873/131068 bytes
TX6DL U-Boot > bootp
BOOTP broadcast 1
BOOTP broadcast 2
BOOTP broadcast 3
DHCP client bound to address 192.168.100.215 (851 ms)
TX6DL U-Boot > fdt rm /
TX6DL U-Boot > tftp ${fdtaddr} Starterkit-5-1_36/imx6dl-tx6u-801x.dtb
Using FEC device
TFTP from server 192.168.100.1; our IP address is 192.168.100.215
Filename 'Starterkit-5-1_36/imx6dl-tx6u-801x.dtb'.
Load address: 0x11000000
Loading: ###
  1000 KiB/s
done
Bytes transferred = 38929 (9811 hex)
TX6DL U-Boot > setenv boot_mode net
TX6DL U-Boot > setenv bootfile Starterkit-5-1_36/uImage_tx6
TX6DL U-Boot > setenv nfs_server 192.168.1.96
TX6DL U-Boot > setenv nfsroot /tftpboot/Starterkit-5-1_36/rootfs-tx6
```

---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de