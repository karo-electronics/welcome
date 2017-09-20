# TXCOM Feature set
This release supports the machines as in the below given table. The user needs
to assign *one* of the following values in the `MACHINE=` column to the shell
variable of the same name by choosing the appropriate value, matching the
respective TX COM module.

* [TX6S](#tx6s)
* [TX6DL](#tx6dl)
* [TX6Q & TX6QP](#tx6q-tx6qp)
* [TX6UL](#tx6ul)

## TX6S
**TX6S** are based upon the i.MX6S

| `MACHINE=`  |   Number  |   Name                            |
|:-----------:|:---------:|:----------------------------------|
| `tx6s-8034` | TX6S-8034 | TX6S/800/256S/128F/I              |
| `tx6s-8035` | TX6S-8035 | TX6S/800/512S/4GF/E85             |
| `tx6s-8134` | TX6S-8134 | TX6S/800/256S/128F/LVDS/I         |
| `tx6s-8135` | TX6S-8135 | TX6S/800/512S/4GF/LVDS/E85        |

_Note: see here for [PCN](#pcn)_

## TX6DL
**TX6DL** are based upon the i.MX6DL

Also: **TX6DL** are marked with _TX6U_

| `MACHINE=`  |  Number   |   Name                            |
|:-----------:|:---------:|:----------------------------------|
| `tx6u-8030` | TX6U-8030 | TX6DL/800/1024S/128F/I            |
|             | TX6U-8010 | *legacy see PCN for more*         |
| `tx6u-8033` | TX6U-8033 | TX6DL/800/1024S/4GF/E85           |
| `tx6u-8130` | TX6U-8130 | TX6DL/800/1024S/128F/I/LVDS       |
|             | TX6U-8110 | *legacy see PCN for more*         |
| `tx6u-8133` | TX6U-8133 | TX6DL/800/1024S/4GF/LVDS/E85      |

_Note: see here for [PCN](#pcn)_

## TX6Q & TX6QP
**TX6Q** and **TX6QP** are based upon the i.MX6Q/QP

| `MACHINE=`  |  Number   |   Name                            |
|:-----------:|:---------:|:----------------------------------|
| `tx6q-1030` | TX6Q-1030 | TX6Q/1000/1024S/128F              |
|             | TX6Q-1010 | *legacy see PCN for more*         |
| `tx6q-1036` | TX6Q-1036 | TX6Q/1000/1024S/8GF               |
| `tx6q-8037` | TX6Q-8037 | TX6QP/800/2GS/4GF/I               |
| `tx6q-1130` | TX6Q-1130 | TX6Q/1000/1024S/128F/LVDS         |
|             | TX6Q-1110 | *legacy see PCN for more*         |

_Note: see here for [PCN](#pcn)_

## TX6UL
**TX6UL** are based upon the i.MX6UL

| `MACHINE=`  |  Number   |   Name                            |
|:-----------:|:---------:|:----------------------------------|
| `txul-5010` | TXUL-5010 | TX6UL/528/256S/128F/I             |
|             | TXUL-0010 | *legacy see PCN for more*         |
| `txul-5011` | TXUL-5011 | TX6UL/528/256S/4GF/E85            |
|             | TXUL-0011 | *legacy see PCN for more*         |

_Note: see here for [PCN](#pcn)_

# Commands
Set one of the above given values, respective to the TX COM used, in the machine
configuration variable:

`MACHINE=<name_from_list_above>`

## Set up the environment
To setup the the Yocto environment insert a value, fitting the desired target,
from the above table, looking like so:

`MACHINE=tx6u-8030 source setup-environment build`

### Choosing an image target
Choose an image target to build, e.g.:

`core-image-minimal`

**Note:**<br>
To find out what other _`images`_ can be build, these aptly named, cheat sheets
are available:

* [Bitbake Cheat Sheet][3]
* [Useful bitbake commands][4]
* [Crashcourse's BitBake Tutorial][5]

This builds a minimal image consisting of:

1. Bootloader
2. Kernel
3. RFS

The RFS (a.k.a: _rootfs_, id est: _root file system_) in this instance is a
low key file system generally intended for either first steps and/or headless
systems. It includes all the general standard tools of a GNU/Linux
distribution, but missing features like a X11 server, etc.; other _`images`_ chosen
create different RFS.

Additional packages can be added to images as long as there is a recipe
provided for that package.

### Building an image target

`bitbake <image|recipe>`

_**Example:**_

For building core-image-minimal:

`bitbake core-image-minimal`

For building _U-Boot_ _recipe_ **only**:

`bitbake u-boot-karo`

For building _Linux kernel_ **and** _kernel modules_ _recipes_ **only**:

`bitbake linux-karo`

The latter examples are especially in development circumstances a common occurrence
but can be used in a normal procedure as well.


## Re-Setup of build environment
To initialize the build environment when the session has been exited, run the
following command in the directory above the build directory:

`setup-environment <build directory>`

### Image Deployment
After a build is complete, the created image resides in the "`tmp/deploy/images`"
sub-directory. An image is, for the most part, specific to the machine set in
the environment setup. Each image build creates a:

* Bootloader (i.e.: U-Boot)
* Kernel
* RFS

Where the type of the image is based on the `IMAGE_FSTYPES` defined in the
machine configuration file.

The following files are created for Ka-Ro TX modules:

---
# Footnotes & References
Source: https://www.karo-electronics.de/1651.html

<a name="pcn"></a>
[1]: Ka-Ro publishes changes to the TX COM in its PCN, which are available to
     the users in the respective TX COM download area on the [Ka-Ro website][2]

[2]: http://www.karo-electronics.de
[3]: http://elinux.org/Bitbake_Cheat_Sheet
[4]: https://community.nxp.com/docs/DOC-94953
[5]: http://www.crashcourse.ca/wiki/index.php/BitBake_Tutorial

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de