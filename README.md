# Welcome to Ka-Ro at Github
Welcome to the Ka-Ro software repositories on [Github][gh-com]. Here we offer
the sources for the our Linux and Yocto solutions ... as we go along.

## A short introduction
### TX standard
The _Computer On Module_ (COM) of Ka-Ro's general TX family COM ("**TXCOM**"
hereafter) are a series of **pin-compatible** COM, which follow the open and
freely available Ka-Ro [TX-Standard][tx-stand]. The standard allows for integration
of solutions, depending on the solutions scale or intended target, thus making it
easy to create a product platform with different features, like performance or
peripherals, and/or with a future upgrade path.

The documentation herein is primarily targeted onto the TXCOM series known as
TX6.

### Ka-Ro TX6 Series
The Ka-Ro TX6 series herein, specifically is a series of COM comprising of a
range of **NXP's i.MX6** SOC family; e.g. including but not exclusively the SOC
of i.MX6Q and i.MX6UL.

Ka-Ro TX6 modules are designed and made in Germany for the highest possible
quality. Ka-Ro offers technical support directly from design engineers and
developers, and provides guaranteed long-term availability to ensure extended
product life-cycles.

Support for TX6 modules is available for Linux, Microsoft Windows Embedded
Compact, as well as is there partnered third-party support available for
Android and QNX.

## This page

This page is to provide listing and easy access to the documentation concerning
the TXCOM product software. Which include the solutions based of either the
_Mainline Linux Kernel_ or _Yocto_ based one.

### _Mainline Linux Kernel_
Ka-Ro is dedicated to development of the _Mainline Linux Kernel_


### Yocto
The premise of Yocto is to offer the developer a framework to _create a
distribution_, which in turn means __reproducible builds__. In case of Ka-Ro
TXCOM this manifests in that the same sources for different TXCOM (e.g. TX6Q vs.
TX6UL) create the same solution. [Would you like to know more?](yocto/README.yocto.md)

## What sources
Here on Github we provide access to these main areas:

* __Bootloader (Das U-Boot)__

    * The Bootloader '**Das U-Boot**' with integrated support for the TXCOM modules:  
    `karo-tx-uboot` -
    [[sources]](https://github.com/karo-electronics/karo-tx-uboot) -
    [[docu]](uboot/uboot_getting-started.md) -
    [[PDF]][uboot-pdf]

    * Flattend Device Tree  
    A short "How-to work with the Device Tree under U-Boot" can be found here: [[PDF]][fdt-qref]  
    For more comprehensive documentation please look here: [[docu]](dts/dt_home.md)

* __Linux Kernel__
    * _Linux Mainline Kernel_  
    Linux for TXCOM modules based on longterm release kernel, version 4.4  
    `karo-tx-linux` -
    [[sources]](https://github.com/karo-electronics/karo-tx-linux) -
    [[wiki]](https://github.com/karo-electronics/karo-tx-linux/wiki)

    * _Linux NXP Kernel (Yocto)_  
    Linux for TXCOM modules based NXP Yocto BSP kernel, version 4.1  
    which includes proprietary driver blob to fully support hardware acceleration  
    `NXP - linux-2.6-imx.git` - [[sources @ NXP]](http://git.freescale.com/git/cgit.cgi/imx/linux-2.6-imx.git/)

* __Yocto__
    * _Getting Started_  
    [[Getting started]](https://www.karo-electronics.com/1661.html?&L=1)

    * _Ka-Ro flavoured FSL Community BSP_  
    `fsl-community-bsp-platform` -
    [[source]](https://github.com/karo-electronics/fsl-community-bsp-platform) -
    [[README]](https://github.com/karo-electronics/fsl-community-bsp-platform) -
    [[wiki]](https://github.com/karo-electronics/fsl-community-bsp-platform/wiki)

    * _Yocto BSP layer for NXP's ARM based platforms_  
    `meta-fsl-arm-extra` - [[source]](https://github.com/karo-electronics/meta-fsl-arm-extra)

    * _Sample images created with Yocto_  
    `karo-yocto-images` - [[samples]](https://github.com/karo-electronics/karo-yocto-images)

---
## Footnotes & Appendix
[gh-com]: https://github.com/karo-electronics
[tx-stand]: https://www.karo-electronics.com/tx-standard.html
[uboot-pdf]: https://github.com/karo-electronics/welcome/blob/master/uboot/TX6_U-Boot.pdf
[fdt-qref]: https://github.com/karo-electronics/welcome/blob/master/dts/FDT-Quickreference.pdf

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
