# Building Yocto

To initiate the building of a deployable Yocto image the user has to setup the
build environment for Yocto, which requires choosing a `MACHINE=` value
appropriate to the used TXCOM. This value can be found in the following
[machine table](yocto_machine-table.md).

Here a listing of the `MACHINE=` values for the different TXCOM.

* [TX6S](yocto_machine-table.md#tx6s)
* [TX6DL](yocto_machine-table.md#tx6dl)
* [TX6Q & TX6QP](yocto_machine-table.md#tx6q-tx6qp)
* [TX6UL](yocto_machine-table.md#tx6ul)

## Set up the environment
### Commands
For this purpose the user needs to assign *one* of the following values in
the `MACHINE` column to the shell variable of the same name.
See __"[Commands](#Commands)"__ below.

Set one of the above given values, respective to the TXCOM used, in the machine
configuration variable:

`MACHINE=<name_from_machine_table>`

## Set up the environment
Set one of the above given values, respective to the TXCOM used, in the machine
configuration variable:

`MACHINE=<name_from_machine_table>`

To setup the the Yocto environment insert a value, fitting the desired target,
from the above table, looking like so:

`MACHINE=tx6u-8030 source setup-environment build`

### Choosing an image target
Choose an image target to build, e.g.:

`core-image-minimal`

**Note:**  
To find out what other _`images`_ can be build, these aptly named, cheat sheets
are available:

* [Bitbake Cheat Sheet][3]
* [Useful bitbake commands][4]
* [Crashcourse's BitBake Tutorial][5]

This builds a minimal image consisting of:

1. Bootloader
2. Kernel
3. RFS

The RFS (a.k.a: _rootfs_, i.e.: _root file system_) in this instance is a
low key file system generally intended for either first steps and/or headless
systems. It includes all the general standard tools of a GNU/Linux
distribution, but missing features like a X11 server, etc.; other _`images`_
chosen create different RFS.

Additional packages can be added to images as long as there is a recipe
provided for that package.

### Building an image target

`bitbake <image|recipe>`

_**Example:**_

For building image (e.g. _core-image-minimal_):

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
## Footnotes & References
<a id="source"></a>  
Source: <https://www.karo-electronics.de/1651.html>

<a name="pcn">PCN</a>:  
Ka-Ro publishes changes to the TX COM in its PCN, which are available to the
users in the respective TX COM download area on the [Ka-Ro website][2]

[2]: http://www.karo-electronics.de
[3]: http://elinux.org/Bitbake_Cheat_Sheet
[4]: https://community.nxp.com/docs/DOC-94953
[5]: http://www.crashcourse.ca/wiki/index.php/BitBake_Tutorial

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
