# Yocto Machine Table
This release supports the machines as in the below given table.

The user needs to assign *one* of the following values in the `MACHINE=` column
to the shell variable of the same name by choosing the appropriate value,
matching the respective TXCOM module to the commands as outlined
[here](yocto_building.md#commands).

* [TX6S](#tx6s)
* [TX6DL](#tx6dl)
* [TX6Q & TX6QP](#tx6q-tx6qp)
* [TX6UL](#tx6ul)

_Note: see here for a [legend](#legend)_

## TX6S
**TX6S** are based upon the i.MX6S

| `MACHINE=`  |   Number  |   Name                            |
|:-----------:|:---------:|:----------------------------------|
| `tx6s-8034` | TX6S-8034 | TX6S/800/256S/128F/I              |
| `tx6s-8035` | TX6S-8035 | TX6S/800/512S/4GF/E85             |
| `tx6s-8134` | TX6S-8134 | TX6S/800/256S/128F/LVDS/I         |
| `tx6s-8135` | TX6S-8135 | TX6S/800/512S/4GF/LVDS/E85        |

_Note: see here for [PCN](#pcn) and [legend](#legend)_

## TX6DL
**TX6DL** are based upon the i.MX6DL  
**TX6DL** are **also** marked with _**TX6U**_

| `MACHINE=`  |   Number    | Name                         |
|:-----------:|:-----------:|:---------------------------- |
| `tx6u-8030` |  TX6U-8030  | TX6DL/800/1024S/128F/I       |
|             | *TX6U-8010* | *legacy see PCN for more*    |
| `tx6u-8033` |  TX6U-8033  | TX6DL/800/1024S/4GF/E85      |
| `tx6u-8130` |  TX6U-8130  | TX6DL/800/1024S/128F/I/LVDS  |
|             | *TX6U-8110* | *legacy see PCN for more*    |
| `tx6u-8133` |  TX6U-8133  | TX6DL/800/1024S/4GF/LVDS/E85 |

_Note: see here for [PCN](#pcn) and [legend](#legend)_


## TX6Q & TX6QP
**TX6Q** and **TX6QP** are based upon the i.MX6Q/QP

| `MACHINE=`  |   Number    | Name                      |
|:-----------:|:-----------:|:------------------------- |
| `tx6q-1030` |  TX6Q-1030  | TX6Q/1000/1024S/128F      |
|             | *TX6Q-1010* | *legacy see PCN for more* |
| `tx6q-1036` |  TX6Q-1036  | TX6Q/1000/1024S/8GF       |
| `tx6q-8037` |  TX6Q-8037  | TX6QP/800/2GS/4GF/I       |
| `tx6q-1130` |  TX6Q-1130  | TX6Q/1000/1024S/128F/LVDS |
|             | *TX6Q-1110* | *legacy see PCN for more* |

_Note: see here for [PCN](#pcn) and [legend](#legend)_

## TX6UL
**TX6UL** are based upon the i.MX6UL

| `MACHINE=`  |   Number    | Name                      |
|:-----------:|:-----------:|:------------------------- |
| `txul-5010` |  TXUL-5010  | TX6UL/528/256S/128F/I     |
|             | *TXUL-0010* | *legacy see PCN for more* |
| `txul-5011` |  TXUL-5011  | TX6UL/528/256S/4GF/E85    |
|             | *TXUL-0011* | *legacy see PCN for more* |

_Note: see here for [PCN](#pcn) and [legend](#legend)_

## TX6ULL
**TX6ULL** are based upon the i.MX6ULL

| `MACHINE=`  |  Number   |   Name                            |
|:-----------:|:---------:|:----------------------------------|
| `txul-8013` | TXUL-8013 | TX6ULL/800/512S/4GF/E85           |

_Note: see here for [PCN](#pcn) and [legend](#legend)_

---
## Footnotes & References
<a id="pcn">PCN</a>:  
Ka-Ro publishes changes to the TXCOM in its PCN, which are available to the
users in the respective TXCOM download area on the [Ka-Ro website][2]

<a id="legend">Legend</a>:
```console
TX6ULL/800/512S/4GF/E85
TX6DL/800/1024S/128F/I/LVDS
 (1)  (2) (3)  (4)  (5) (6)
```

(1) TXCOM name (or: see above)  
(2) Clock frequency in `MHz`  
(3) RAM size  

| Indicator |            Description |
| ---------:| ----------------------:|
|    `512S` |             512 MiByte |
|   `1024S` | 1 GiByte / 1024 MiByte |
|     `2GS` | 2 GiByte / 2048 MiByte |

(4) NVM (a.k.a. Flash)  

| Indicator | Description  |       Size |
| ---------:|:------------:| ----------:|
|    `128F` |  NAND Flash  | 128 MiByte |
|     `4GF` | eMMC (Flash) |  4  GiByte |

(5) Operational temperature ranges  

| Indicator |    Description    | Temperature range |
| ---------:|:-----------------:|:-----------------:|
|       `I` |    Industrial     |   -40°C - 105°C   |
|     `E85` | Extended consumer |   -20°C - 105°C   |

(6) Display adapter  

| Indicator |            Description             |
| ---------:|:----------------------------------:|
|       N/A |         Parallel interface         |
|    `LVDS` | Low-voltage differential signaling |


[2]: http://www.karo-electronics.de

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
