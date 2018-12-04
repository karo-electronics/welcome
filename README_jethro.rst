.. role:: raw-html-m2r(raw)
   :format: html


Welcome to Ka-Ro at Github
==========================

Welcome to the Ka-Ro software repositories on `Github <https://github.com/karo-electronics>`_. Here we offer
the sources for the our Linux and Yocto solutions ... as we go along.

A short introduction
--------------------

TX standard
^^^^^^^^^^^

The *Computer On Module* (COM) of Ka-Ro's general TX family COM ("\ **TXCOM**\ "
hereafter) are a series of **pin-compatible** COM, which follow the open and
freely available Ka-Ro `TX-Standard <https://www.karo-electronics.com/tx-standard.html>`_. The standard allows for integration
of solutions, depending on the solutions scale or intended target, thus making it
easy to create a product platform with different features, like performance or
peripherals, and/or with a future upgrade path.

The documentation herein is primarily targeted onto the TXCOM series known as
TX6.

Ka-Ro TX6 Series
^^^^^^^^^^^^^^^^

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

This page
---------

This page is to provide listing and easy access to the documentation concerning
the TXCOM product software. Which include the solutions based of either the
*Mainline Linux Kernel* or *Yocto* based one.

*Mainline Linux Kernel*
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Ka-Ro is dedicated to development of the *Mainline Linux Kernel*

Yocto
^^^^^

The premise of Yocto is to offer the developer a framework to *create a
distribution*\ , which in turn means **reproducible builds**. In case of Ka-Ro
TXCOM this manifests in that the same sources for different TXCOM (e.g. TX6Q vs.
TX6UL) create the same solution. `Would you like to know more? <yocto/README.yocto.md>`_

What sources
------------

Here on Github we provide access to these main areas:


* 
  **Bootloader (Das U-Boot)**


  * 
    The Bootloader '\ **Das U-Boot**\ ' with integrated support for the TXCOM modules:\ :raw-html-m2r:`<br>`
    ``karo-tx-uboot`` -
    `[sources] <https://github.com/karo-electronics/karo-tx-uboot>`_ -
    `[docu] <uboot/uboot_getting-started.md>`_ -
    `[PDF] <https://github.com/karo-electronics/welcome/blob/master/uboot/TX6_U-Boot.pdf>`_

  * 
    Flattend Device Tree\ :raw-html-m2r:`<br>`
    A short "How-to work with the Device Tree under U-Boot" can be found here: `[PDF] <https://github.com/karo-electronics/welcome/blob/master/dts/FDT-Quickreference.pdf>`_\ :raw-html-m2r:`<br>`
    For more comprehensive documentation please look here: `[docu] <dts/dt_home.md>`_

* 
  **Linux Kernel**


  * 
    *Linux Mainline Kernel*\ :raw-html-m2r:`<br>`
    Linux for TXCOM modules based on longterm release kernel, version 4.4\ :raw-html-m2r:`<br>`
    ``karo-tx-linux`` -
    `[sources] <https://github.com/karo-electronics/karo-tx-linux>`_ -
    `[wiki] <https://github.com/karo-electronics/karo-tx-linux/wiki>`_

  * 
    *Linux NXP Kernel (Yocto)*\ :raw-html-m2r:`<br>`
    Linux for TXCOM modules based NXP Yocto BSP kernel, version 4.1\ :raw-html-m2r:`<br>`
    which includes proprietary driver blob to fully support hardware acceleration\ :raw-html-m2r:`<br>`
    ``NXP - linux-2.6-imx.git`` - `[sources @ NXP] <http://git.freescale.com/git/cgit.cgi/imx/linux-2.6-imx.git/>`_

* 
  **Yocto**


  * 
    *Getting Started*\ :raw-html-m2r:`<br>`
    `[Getting started] <https://www.karo-electronics.com/1661.html?&L=1>`_

  * 
    *Ka-Ro flavoured FSL Community BSP*\ :raw-html-m2r:`<br>`
    ``fsl-community-bsp-platform`` -
    `[source] <https://github.com/karo-electronics/fsl-community-bsp-platform>`_ -
    `[README] <https://github.com/karo-electronics/fsl-community-bsp-platform>`_ -
    `[wiki] <https://github.com/karo-electronics/fsl-community-bsp-platform/wiki>`_

  * 
    *Yocto BSP layer for NXP's ARM based platforms*\ :raw-html-m2r:`<br>`
    ``meta-fsl-arm-extra`` - `[source] <https://github.com/karo-electronics/meta-fsl-arm-extra>`_

  * 
    *Sample images created with Yocto*\ :raw-html-m2r:`<br>`
    ``karo-yocto-images`` - `[samples] <https://github.com/karo-electronics/karo-yocto-images>`_

----

Footnotes & Appendix
--------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
