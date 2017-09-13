# Welcome to Ka-Ro at Github

## Ka-Ro TX6 Series for NXP i.MX6 SOC Processors

Ka-Ro TX6 modules are available for a complete range of NXP i.MX6 SOC
processors. All modules in the TX family are pin-compatible ([TX-Standard](#tx)),
making it easy to create a product platform with different features or upgrading
for more performance.

Ka-Ro TX6 modules are designed and made in Germany for the highest possible
quality. Ka-Ro offers technical support directly from design engineers and
developers, and provides guaranteed long-term availability to ensure extended
product lifecycles.

Support for TX6 modules is available for Linux, Microsoft Windows Embedded
Compact, as well as is there partnered third-party support available for
Android and QNX.


## This page

This page is for customers and interested to provide listing and easy access
to documentation.

Here on Github we provide access to these main areas:

* Bootloader - U-Boot
  * The Bootloader ' Das U-Boot' with integrated support for the TXCOM modules:  
    `karo-tx-uboot` -
    [[sources]](https://github.com/karo-electronics/karo-tx-uboot) -
    [[PDF]](uboot/TX6_U-Boot.pdf)

  * Flattend Device Tree  
    A short "How-to work with the Device Tree under U-Boot" can be found here:  
    [[PDF]](FDT-Quickreference.pdf)

    For more comprehensive documentation please look here:
    [[docu]](dts/dt_home.md)

* Linux Kernel
  * Linux Mainline Kernel  
      Linux for TXCOM modules based on longterm release kernel, version 4.4<br>
      `karo-tx-linux` -
      [[sources]](https://github.com/karo-electronics/karo-tx-linux) -
      [[wiki]](https://github.com/karo-electronics/karo-tx-linux/wiki)

  * Linux NXP Kernel (Yocto)  
      Linux for TXCOM modules based NXP Yocto BSP kernel, version 4.1<br>
      which includes proprietary driver blob to fully support hardware acceleration<br>
      `NXP - linux-2.6-imx.git` - [[sources @ NXP]](http://git.freescale.com/git/cgit.cgi/imx/linux-2.6-imx.git/)

* Yocto

    * Getting Started  
      [[Getting started]](https://www.karo-electronics.com/1661.html?&L=1)

    * Ka-Ro flavoured _FSL Community BSP_  
      `fsl-community-bsp-platform` -
      [[source]](https://github.com/karo-electronics/fsl-community-bsp-platform) -
      [[README]](https://github.com/karo-electronics/fsl-community-bsp-platform) -
      [[wiki]](https://github.com/karo-electronics/fsl-community-bsp-platform/wiki)

    * Yocto BSP layer for NXP's ARM based platforms  
      `meta-fsl-arm-extra` - [[source]](https://github.com/karo-electronics/meta-fsl-arm-extra)

    * Sample images created with Yocto  
      `karo-yocto-images` - [[samples]](https://github.com/karo-electronics/karo-yocto-images)

---
## Footnotes & Appendix
[tx]: See the [TX-Standard](https://www.karo-electronics.com/tx-standard.html) for more.

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de