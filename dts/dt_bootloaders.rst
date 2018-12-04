.. role:: raw-html-m2r(raw)
   :format: html


[TX53]/Linux/README.RedBoot

|From version 3.4 onwards the Linux kernel is built with devicetree
|(DT) support (see Documentation/devicetree/*).
|Therefore the devices supported by the kernel are no longer registered
|by individual platform initialization code, but by generic code that
|interprets the devicetree configuration data.
|
|The configuration data for TX53 can be found in the following files:

|   arch/arm/boot/dts/imx53.dtsi             CPU/SoC specific configuration
|   arch/arm/boot/dts/imx53-tx53.dtsi        platform specific device setup
|   arch/arm/boot/dts/imx53-tx53-x03x.dtsi   module specific setup for TX53-8030 & TX53-1030
|   arch/arm/boot/dts/imx53-tx53-x13x.dtsi   module specific setup for TX53-8130 & TX53-1331
|
|The first file provides an abstract description of the available
|hardware and should not normally need to be changed, while the second
|file selects those devices that are used on the particular platform.
|If you want to enable/disable devices, you should adapt the
|appropriate imx53-tx53-x?3x.dts file.
|
|The DT configuration data needs to be converted to a binary blob and
|programmed into the U-Boot partition 'dtb' or appended to the kernel
|zImage (when using RedBoot):
|Note, that in the latter case the Kconfig option CONFIG_ARM_APPENDED_DTB needs
|to be set when compiling the kernel!
|1. Compile the kernel including modules and DT data (for use with RedBoot):
|  make ARCH=arm CROSS_COMPILE=arm-cortexa8-linux-gnueabi- zImage dtbs modules
|2. Concatenate the kernel with the generated DT blob:
|  cat arch/arm/boot/zImage arch/arm/boot/tx53-tx53-x?3x.dtb > arch/arm/boot/zImage_tx53-v3_amd_rx_vega_64_at_675_each

----

Footnotes & Appendix
--------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
