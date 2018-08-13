# Yocto Machine Table
The Rocko based release supports the machines as given in the table below.

The user needs to assign *one* of the following values in the `MACHINE=` column
to the shell variable of the same name by choosing the appropriate value,
matching the respective TXCOM module to the commands as outlined
[here](yocto_building.md#commands).

Cortex A9 solutions  
* [TX6S](#tx6s)
* [TX6DL](#tx6dl)
* [TX6Q](#tx6q)
* [TX6QP](#tx6qp)

Cortex A7 solutions  
* [TX6UL](#tx6ul)
* [TX6ULL](#tx6ull)

## A NeW

Choosing a machine

This release supports the following machines. Depending on the target to be
compiled choose the machine configuration that matches your TXCOM module.

The user has to differentiate between payload software, like the operating
system (GNU/Linux), and the bootloader (U-Boot), thus there are in above given
table two different settings for `MACHINE=`.

This is an effect for the BSP as the U-Boot bootloader requires a different
toolchain to be compiled with.

## TX6S
**TX6S** are based upon the i.MX6S  
_Note: see here for [PCN](#pcn)_

- **NAND Modules**

|    `MACHINE=`     | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name                |
|:-----------------:|:----------------------:|:------------ |:------------------------- |
| `imx6dl-tx6-nand` |      `tx6s-8034`       | TX6S-8034    | TX6S/800/256S/128F/I      |
|                   |      `tx6s-8134`       | TX6S-8134    | TX6S/800/256S/128F/I/LVDS |

- **eMMC Modules**

|    `MACHINE=`     | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name                 |
|:-----------------:|:----------------------:|:------------ |:-------------------------- |
| `imx6dl-tx6-emmc` |      `tx6s-8035`       | TX6S-8035    | TX6S/800/512S/4GF/E85      |
|                   |      `tx6s-8135`       | TX6S-8135    | TX6S/800/512S/4GF/E85/LVDS |

## TX6DL
**TX6DL** are based upon the i.MX6DL

_Note: **TX6DL** are marked with _**TX6U**_  
_Note: see here for [PCN](#pcn)_

- NAND Modules

|    `MACHINE=`     | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name                  |
|:-----------------:|:----------------------:|:------------ |:--------------------------- |
| `imx6dl-tx6-nand` |                        | _TX6U-8010_  | _(Legacy)_                  |
|                   |      `tx6u-8030`       | TX6U-8030    | TX6DL/800/1024S/128F/I      |
|                   |                        | _TX6U-8110_  | _(Legacy)_                  |
|                   |      `tx6u-8130`       | TX6U-8130    | TX6DL/800/1024S/128F/I/LVDS |

- eMMC Modules

|    `MACHINE=`     | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name                   |
|:-----------------:|:----------------------:|:------------ |:---------------------------- |
| `imx6dl-tx6-emmc` |      `tx6u-8033`       | TX6U-8033    | TX6DL/800/1024S/4GF/E85      |
|                   |      `tx6u-8133`       | TX6U-8133    | TX6DL/800/1024S/4GF/E85/LVDS |

## TX6Q
**TX6Q** are based upon the i.MX6Q  
_Note: see here for [PCN](#pcn)_

- **NAND Modules**

|    `MACHINE=`    | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name                |
|:----------------:|:----------------------:|:------------ |:------------------------- |
| `imx6q-tx6-nand` |                        | _TX6Q-1010_  | _(Legacy)_                |
|                  |      `tx6q-1030`       | TX6Q-1030    | TX6Q/1000/1024S/128F      |
|                  |                        | _TX6Q-1110_  | _(Legacy)_                |
|                  |      `tx6q-1130`       | TX6Q-1130    | TX6Q/1000/1024S/128F/LVDS |

- **eMMC Modules**

|    `MACHINE=`    | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name          |
|:----------------:|:----------------------:|:------------ |:------------------- |
| `imx6q-tx6-emmc` |      `tx6q-1036`       | TX6Q-1036    | TX6Q/1000/1024S/8GF |


## TX6QP
**TX6QP** are based upon the i.MX6QP  
_Note: see here for [PCN](#pcn)_

- **eMMC Modules**

|    `MACHINE=`     | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name             |
|:-----------------:|:----------------------:|:------------ |:---------------------- |
| `imx6qp-tx6-emmc` |      `tx6q-8037`       | TX6Q-8037    | TX6QP/800/1GS/8GF/I    |
|                   |      `tx6q-8137`       | TX6Q-8137    | TX6QP/800/1GS/8GF/LVDS |

## TX6-UL
**TX6UL** are based upon the i.MX6UL  
_Note: see here for [PCN](#pcn)_

- **NAND Modules**

|    `MACHINE=`     | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name            |
|:-----------------:|:----------------------:|:------------ |:--------------------- |
| `imx6ul-tx6-nand` |                        | _TXUL-0010_  | _(Legacy)_            |
|                   |      `txul-5010`       | TXUL-5010    | TX6UL/528/256S/128F/I |

- **eMMC Modules**

|    `MACHINE=`     | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name             |
|:-----------------:|:----------------------:|:------------ |:---------------------- |
| `imx6ul-tx6-emmc` |                        | _TXUL-0011_  | _(Legacy)_             |
|                   |      `txul-5011`       | TXUL-5011    | TX6UL/528/256S/4GF/E85 |

## TX6ULL
**TX6ULL** are based upon the i.MX6ULL  
_Note: see here for [PCN](#pcn)_

- **eMMC Modules**

|     `MACHINE=`      | U-Boot <br> `MACHINE=` | TXCOM number | TXCOM name              |
|:-------------------:|:----------------------:|:------------ |:----------------------- |
| `imx6ull-txul-emmc` |      `txul-8013`       | TXUL-8013    | TX6ULL/800/512S/4GF/E85 |


Set the above given, depending on your intended workload, as value in the
machine configuration variable:

`MACHINE=<name-from-list-above>`

Set up the environment

The command to setup of the Yocto environment in it's general form looks like
the following:

`MACHINE=<MACHINE> source ./setup-environment <build-directory>`

Where the user has to insert a value, fitting the desired target TXCOM and
software target, from the above table, and choose a name for the build directory
to be created by the "setup-environment" script, to look like such:

- GNU/Linux:

    `MACHINE=imx6dl-tx6-emmc source ./setup-environment build-gnulinux`

- U-Boot:

    `MACHINE=tx6u-8033 source ./setup-environment build-bootloader`

The user has to differentiate between payload software, like the operating
system (GNU/Linux), and the bootloader (U-Boot), thus there are in above given
table two different settings for `MACHINE=`.

This is an effect for the BSP as the U-Boot bootloader requires a different
toolchain to be compiled with.


---
## Footnotes & References
Source: <https://www.karo-electronics.de/1651.html>

<a id="pcn">PCN</a>:  
Ka-Ro publishes changes to the TXCOM in its PCN, which are available to the
users in the respective TXCOM download area on the [Ka-Ro website][2]

[2]: https://www.karo-electronics.de
[3]: http://elinux.org/Bitbake_Cheat_Sheet
[4]: https://community.nxp.com/docs/DOC-94953
[5]: http://www.crashcourse.ca/wiki/index.php/BitBake_Tutorial

---
[Ka-Ro electronics GmbH](https://www.karo-electronics.de)  
Contact support: support@karo-electronics.de