# FAQ
## Where is the code?
> > The documentation says that there is something under
> > 'arm-linux/Documentation/spi' could you let me have this?
>
First and foremost this references the general publicly available
documentation as given in the kernel source directory.

This part of _our_ documentation is based on our 'small footprint' Linux -
i.e. not Yocto -, in which we use '`arm-linux`' as one of the default
directories used, and specifically, the directory where the Linux kernel
source is located.

Therefore the meaning of 'arm-linux' is synonymous with:

"path-to-linux-kernel-source"

Consequently, there under the directory named 'Documentation' is the document
you are looking for.

In general, we encourage the use of freely available information about the
handling of Yocto, such as the following, to familiarize yourself with the
framework:

https://community.nxp.com/docs/DOC-94953  
https://elinux.org/Bitbake_Cheat_Sheet  
https://www.openembedded.org/wiki/Bitbake_cheat_sheet  

The commands given there, will make your life easier and will be of every day
use in the devel process.

Short introduction to Yocto:

Yocto does that differently than a kernel developer or LFS would do Yocto is a
framework to create a _Distribution_ _not_ a *Devel-Framework* [1]. Therefore,
the following has only limited general validity:

For Yocto, X is under (! Commands see below!):

---
* Active kernel sources (i.e. work directory):  
  `$HOME/<yocto-project-dir>/<build-dir>/tmp/work-shared/<yocto-'MACHINE='-value>/kernel-source`


* Local copies of all the sources  
  respectively the sources for the whole project as they are downloaded into local
  git repositories:

  general example:  
  `$HOME/<yocto-project-dir>/downloads/git2/<[hostname.]domain.tld>.<directory>.<git-repository>`

  Example:  
  `$HOME/<yocto-project-dir>/downloads/git2/github.com.karo-electronics.karo-tx-linux`

Note:  
Wobei im Fall unseres Kernel der git-repository path aus der unter ".repo"
enthalten 'Manifest.xml' (welche das ['repo' tool](1) nutzt) hervorgeht.

The above given *cheat sheets* include commands that allows to jump right into
the __*work directory*__ from inside the Yocto framework - of course __after__
setup of the environment via the `setup-environment` script. A general example:

`$ bitbake <package> -c <task>`

Example:  
`$ bitbake linux-karo -c devshell`

will open a shell (XTerm) in the source directory _**`<package>`**_ (here:
`linux-karo`) directory. Where the _**`<package>`**_ name is implied by the
`.bb` file, as follows:

```console
sources/meta-freescale-3rdparty/recipes-kernel/linux/linux-karo_4.4.15.bb
                                                     ^^^^^^^^^^ ^^^^^^
                                                        [1]       [2]
```
where there is:  
`[1] Package name`  
`[2] Package version`  

Bevor Sie nun aber diesen Weg beschreiten:

Korrekterweise würden Sie Ihre Änderungen in ein bei Ihnen im LAN erreichbares
git repository [2] legen, welches ein Klon (git clone [--bare]) des
betreffenden Paketes (<package>) ist das Sie bearbeiten wollen, dieses wiederum
klonen ('git clone') sie auf ein den lokalen Computer - um beim Kernel zu
bleiben - dort bearbeiten Sie den Kernel und - zum testen - kompilieren [3]
diesen wie benötigt und per TFTP und NFS RFS testen (i.e. ohne schreiben ins
NAND oder eMMC) und dann die gemachten Änderungen in Ihr LAN git repo
(zurück-)legen und die 'Manifest.xml' anpassen um dieses dann in Zukunft zu
nutzen.

Von dem LAN repo aus würden Sie dann die Änderungen - ganz nach GPLv2 - an die
Community zurückgeben.

Vorteil dieser Vorgehensweise, da Yocto Verzeichnisse dazu tendieren groß zu
werden, können sie da säubern ohne das Ihrer Änderungen verloren gehen. Plus
das Ihrer Änderungen transferierbar (Im LAN? An die Kollegen? Github?) sind.

---

But before you take this path:

To be strictly correct changes would be commited to a git repository in your
LAN [2], which is a clone (git clone [--bare]) of the package (`<package>`) you want to
edit, this in turn clone ('`git clone`') them on a local machine - to access the
kernel stay there - edit the kernel and - test it - compile [3] Test it as
needed and via TFTP and NFS RFS (i.e. without writing to NAND or eMMC) and then
made the changes in your LAN git repo (back) and customize the '`Manifest.xml`'
to this in the future use.

From the LAN repo then you would the changes - according to GPLv2 - to the
Return community.

Advantage of this approach, since Yocto directories tend to be big:

_**You can clean them without losing your changes. plus that of your changes are
transferable (in the LAN? to colleagues? Github?).**_

---
## Footnotes & Appendix
[1]: https://gerrit.googlesource.com/git-repo/

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
