# Welcome to Ka-Ro at Github
Welcome to the Ka-Ro software repositories on [Github][ghcom-karo]. Here we
offer the sources for the our Linux and Yocto solutions ... as we go along.


<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [Welcome to Ka-Ro at Github](#welcome-to-ka-ro-at-github)
    - [A short introduction](#a-short-introduction)
        - [This page](#this-page)
        - [TX standard](#tx-standard)
        - [Ka-Ro TX6 Series](#ka-ro-tx6-series)
        - [_Bootloader: Das U-Boot_](#bootloader-das-u-boot)
        - [_Mainline Linux Kernel_](#mainline-linux-kernel)
        - [Yocto](#yocto)
    - [What sources](#what-sources)
    - [Devicetree](#devicetree)
    - [Footnotes, Appendix & Sources](#footnotes-appendix--sources)

<!-- markdown-toc end -->

## A short introduction
### This page

This page is to provide an introduction to the Ka-Ro Yocto BSP via  listing and
easy access to the documentation concerning the TXCOM product software. Which
include the solutions based of either the _Mainline Linux Kernel_ or _Yocto_
based one.

### TX standard
The _Computer On Module_ (COM) of Ka-Ro's general TX family COM ("**TXCOM**"
hereafter) are a series of **pin-compatible** COM, which follow the open and
freely available Ka-Ro [TX-Standard][karo-tx-std]. The standard allows for
integration of solutions, depending on the solutions scale or intended target,
thus making it easy to create a product platform with different features, like
performance or peripherals, and/or with a future upgrade path.

The documentation herein is primarily targeted onto the TXCOM series known as
TX6.

### Ka-Ro TX6 Series
The Ka-Ro TX series of COM (see [TX standard](# , or short TXCOM, and herein,
specifically the TX6 are a series of COM solutions comprising of a range of
**NXP's i.MX6** SOC family; e.g. including but not exclusively the SOC of
i.MX6Q and i.MX6UL.

Ka-Ro TX6 modules are designed and made in Germany for the highest possible
quality. Ka-Ro offers technical support directly from design engineers and
developers, and provides guaranteed long-term availability to ensure extended
product life-cycles.

Support for TX6 modules is available for Linux, Microsoft Windows Embedded
Compact, as well as is there partnered third-party support available for
Android and QNX.

### _Bootloader: Das U-Boot_
Ka-Ro TX6 COM use as the initial bootloader ["Das U-Boot"][uboot-denx-home]

### _Mainline Linux Kernel_
Ka-Ro is dedicated to development of the _Mainline Linux Kernel_, therefore
the Linux kernels primarily used for the Ka-Ro Yocto BSP are based upon the
sources [kernel.org][korg], a.k.a. upstream sources, either [directly][linux-tx-korg]
or via [Ka-Ro's own repository][linux-tx-karo].  

This commitment to the _Mainline Linux Kernel_ in turn means that Ka-Ro pushes
all changes upstream; primarily via [LKML][linux-lkml]([LKML?][linux-lkml-wiki])

### Yocto
The premise of Yocto is to offer the developer a framework to _create a
distribution_, which in turn means __reproducible builds__. In case of Ka-Ro
TXCOM this [manifest][yocto-karo-manifest] in that the same sources for
different TXCOM (e.g. TX6Q vs. TX6UL) create the same solution.  

[Would you like to know more?][yocto-readme]
[Take a look at the Ka-Ro BSP][yocto-karo-bsp-repo]


## What sources
Here on Github we provide access to these main areas:

* __Bootloader: Das U-Boot__  
    * The Bootloader '**Das U-Boot**' with integrated support for the TXCOM modules:  
    `karo-tx-uboot` -
    [[sources]](https://github.com/karo-electronics/karo-tx-uboot) -
    [[docu]](uboot/uboot_getting-started.md)  


* __Flattend Device Tree__  
    * see [Devicetree](#devicetree) below


* __OS Kernel: Linux__  
    * _Linux Kernel - Mainline_  
      Version: **v4.13**  
      Linux for TXCOM modules based on the _mainline_ release kernel  
      `karo-tx-linux` -
      [[sources]](https://github.com/karo-electronics/karo-tx-linux)  

    * _Linux Kernel - Mainline LTS_  
      Version: **v4.14.24**  
      Linux for TXCOM modules based on the _mainline longterm (LTS)_ release kernel  
      [`kernel.org`][korg] -
      [[sources]](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tag/?h=v4.14.24)

    * _Linux Kernel - NXP (Yocto)_  
      Version: **v4.9.88_2.0.0_ga**  
      Linux based upon NXP BSP kernel  
      this includes the proprietary driver blob to fully support hardware acceleration  
      `NXP - linux-2.6-imx.git` -
      [[sources @ NXP]](https://source.codeaurora.org/external/imx/linux-imx/tag/?h=rel_imx_4.9.88_2.0.0_ga)

* __Yocto__  
    * _Getting Started_  
      [[Getting started]](https://www.karo-electronics.de/1920.html)

    * _Ka-Ro Yocto BSP_  
      `karo-bsp` -
      [[source]](https://github.com/karo-electronics/karo-bsp) -
      [[README]](https://github.com/karo-electronics/karo-bsp#ka-ro-yocto-bsp) -
      [[wiki]](https://github.com/karo-electronics/fsl-community-bsp-platform/wiki)

    * _Yocto BSP layer for NXP's ARM based platforms_  
      `meta-karo` -
      [[source]](https://github.com/karo-electronics/meta-karo.git) -
      [[README]](https://github.com/karo-electronics/meta-karo#ka-ro-yocto-bsp)

    * _Sample images created with Yocto_  
      `karo-yocto-images` -
      [[samples]](https://github.com/karo-electronics/karo-yocto-images#sample-images-created-with-yocto)

    * _Poky fork of the official yoctoproject.org poky repository_  
      This fork includes some fixes.  
      `poky` - [[source]](https://github.com/karo-electronics/poky)


## Devicetree
Find documentation and more resources concerning the Devicetree (DT) here:

* __Documentation__  
    * _Device Tree Documentation_  
      [[Device Tree Documentation]][dt-dt_home]


---
## Footnotes, Appendix & Sources

[dt-dt_home]: /dts/dt_home.md

[ghcom-karo]: https://github.com/karo-electronics

[karo-tx-std]: https://www.karo-electronics.com/tx-standard.html

[korg]: https://kernel.org
[korg-mainline-1]: https://www.linux.com/blog/learn/2018/2/which-linux-kernel-version-stable
[korg-mainline-2]: https://linux-sunxi.org/Mainline_Kernel_Howto
[korg-mainline-3]: https://askubuntu.com/questions/162616/should-i-upgrade-to-the-mainline-kernels
[korg-mainline-5]: localhost
[korg-mainline-6]: localhost

[linux-lkml]: https://lkml.org/
[linux-lkml-wiki]: https://en.wikipedia.org/wiki/Linux_kernel_mailing_list

[linux-tx-karo]: https://github.com/karo-electronics/karo-tx-linux
[linux-tx-korg]: https://github.com/karo-electronics/meta-karo/blob/rocko/recipes-kernel/linux/linux-karo_4.14.24.bb

[pdf-uboot]: https://github.com/karo-electronics/welcome/blob/master/uboot/TX6_U-Boot.pdf
[pdf-fdt_qref]: https://github.com/karo-electronics/welcome/blob/master/dts/FDT-Quickreference.pdf

[uboot-denx-home]: https://www.denx.de/wiki/U-Boot
[uboot-denx-docu]: https://www.denx.de/wiki/U-Boot/Documentation

[yocto-karo-manifest]: https://github.com/karo-electronics/karo-bsp/blob/rocko/default.xml
[yocto-karo-bsp-repo]: https://github.com/karo-electronics/karo-bsp
[yocto-readme]: /yocto/README.yocto.md)

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
