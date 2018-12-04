.. role:: raw-html-m2r(raw)
   :format: html


Welcome to Ka-Ro at Github
==========================

Welcome to the Ka-Ro software repositories on `Github <https://github.com/karo-electronics>`_. Here we
offer the sources for the our Linux and Yocto solutions ... as we go along.


.. raw:: html

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



A short introduction
--------------------

This page
^^^^^^^^^

This page is to provide an introduction to the Ka-Ro Yocto BSP via  listing and
easy access to the documentation concerning the TXCOM product software. Which
include the solutions based of either the *Mainline Linux Kernel* or *Yocto*
based one.

TX standard
^^^^^^^^^^^

The *Computer On Module* (COM) of Ka-Ro's general TX family COM ("\ **TXCOM**\ "
hereafter) are a series of **pin-compatible** COM, which follow the open and
freely available Ka-Ro `TX-Standard <https://www.karo-electronics.com/tx-standard.html>`_. The standard allows for
integration of solutions, depending on the solutions scale or intended target,
thus making it easy to create a product platform with different features, like
performance or peripherals, and/or with a future upgrade path.

The documentation herein is primarily targeted onto the TXCOM series known as
TX6.

Ka-Ro TX6 Series
^^^^^^^^^^^^^^^^

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

*Bootloader: Das U-Boot*
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Ka-Ro TX6 COM use as the initial bootloader `"Das U-Boot" <https://www.denx.de/wiki/U-Boot>`_

*Mainline Linux Kernel*
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Ka-Ro is dedicated to development of the *Mainline Linux Kernel*\ , therefore
the Linux kernels primarily used for the Ka-Ro Yocto BSP are based upon the
sources `kernel.org <https://kernel.org>`_\ , a.k.a. upstream sources, either `directly <https://github.com/karo-electronics/meta-karo/blob/rocko/recipes-kernel/linux/linux-karo_4.14.24.bb>`_
or via `Ka-Ro's own repository <https://github.com/karo-electronics/karo-tx-linux>`_.  

This commitment to the *Mainline Linux Kernel* in turn means that Ka-Ro pushes
all changes upstream; primarily via `LKML <https://lkml.org/>`_\ (\ `LKML? <https://en.wikipedia.org/wiki/Linux_kernel_mailing_list>`_\ )

Yocto
^^^^^

The premise of Yocto is to offer the developer a framework to *create a
distribution*\ , which in turn means **reproducible builds**. In case of Ka-Ro
TXCOM this `manifest <https://github.com/karo-electronics/karo-bsp/blob/rocko/default.xml>`_ in that the same sources for
different TXCOM (e.g. TX6Q vs. TX6UL) create the same solution.  

`Would you like to know more? </yocto/README.yocto.md)>`_
`Take a look at the Ka-Ro BSP <https://github.com/karo-electronics/karo-bsp>`_

What sources
------------

Here on Github we provide access to these main areas:


* **Bootloader: Das U-Boot**  

  * The Bootloader '\ **Das U-Boot**\ ' with integrated support for the TXCOM modules:\ :raw-html-m2r:`<br>`
    ``karo-tx-uboot`` -
    `[sources] <https://github.com/karo-electronics/karo-tx-uboot>`_ -
    `[docu] <uboot/uboot_getting-started.md>`_  


* **Flattend Device Tree**  

  * see `Devicetree <#devicetree>`_ below


* 
  **OS Kernel: Linux**  


  * 
    *Linux Kernel - Mainline*\ :raw-html-m2r:`<br>`
    Version: **v4.13**\ :raw-html-m2r:`<br>`
    Linux for TXCOM modules based on the *mainline* release kernel\ :raw-html-m2r:`<br>`
    ``karo-tx-linux`` -
    `[sources] <https://github.com/karo-electronics/karo-tx-linux>`_  

  * 
    *Linux Kernel - Mainline LTS*\ :raw-html-m2r:`<br>`
    Version: **v4.14.24**\ :raw-html-m2r:`<br>`
    Linux for TXCOM modules based on the *mainline longterm (LTS)* release kernel\ :raw-html-m2r:`<br>`
    `\ ``kernel.org`` <https://kernel.org>`_ -
    `[sources] <https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tag/?h=v4.14.24>`_

  * 
    *Linux Kernel - NXP (Yocto)*\ :raw-html-m2r:`<br>`
    Version: **v4.9.88_2.0.0_ga**\ :raw-html-m2r:`<br>`
    Linux based upon NXP BSP kernel\ :raw-html-m2r:`<br>`
    this includes the proprietary driver blob to fully support hardware acceleration\ :raw-html-m2r:`<br>`
    ``NXP - linux-2.6-imx.git`` -
    `[sources @ NXP] <https://source.codeaurora.org/external/imx/linux-imx/tag/?h=rel_imx_4.9.88_2.0.0_ga>`_

* 
  **Yocto**  


  * 
    *Getting Started*\ :raw-html-m2r:`<br>`
    `[Getting started] <https://www.karo-electronics.de/1920.html>`_

  * 
    *Ka-Ro Yocto BSP*\ :raw-html-m2r:`<br>`
    ``karo-bsp`` -
    `[source] <https://github.com/karo-electronics/karo-bsp>`_ -
    `[README] <https://github.com/karo-electronics/karo-bsp#ka-ro-yocto-bsp>`_ -
    `[wiki] <https://github.com/karo-electronics/fsl-community-bsp-platform/wiki>`_

  * 
    *Yocto BSP layer for NXP's ARM based platforms*\ :raw-html-m2r:`<br>`
    ``meta-karo`` -
    `[source] <https://github.com/karo-electronics/meta-karo.git>`_ -
    `[README] <https://github.com/karo-electronics/meta-karo#ka-ro-yocto-bsp>`_

  * 
    *Sample images created with Yocto*\ :raw-html-m2r:`<br>`
    ``karo-yocto-images`` -
    `[samples] <https://github.com/karo-electronics/karo-yocto-images#sample-images-created-with-yocto>`_

  * 
    *Poky fork of the official yoctoproject.org poky repository*\ :raw-html-m2r:`<br>`
    This fork includes some fixes.\ :raw-html-m2r:`<br>`
    ``poky`` - `[source] <https://github.com/karo-electronics/poky>`_

Devicetree
----------

Find documentation and more resources concerning the Devicetree (DT) here:


* **Documentation**  

  * *Device Tree Documentation*\ :raw-html-m2r:`<br>`
    `[Device Tree Documentation] </dts/dt_home.md>`_

----

Footnotes, Appendix & Sources
-----------------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
