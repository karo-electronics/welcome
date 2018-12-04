.. role:: raw-html-m2r(raw)
   :format: html


..

   In der Doku steht dass es dazu unter arm-linux/Documentation/spi was gibt,
   könnten Sie mir das vll noch zu kommen lassen?
   :raw-html-m2r:`<br>`
   Dieser Teil der Doku basiert auf unserem 'small footprint' Linux; dort ist
   'arm-linux' eines der Verzeichnisse die wir als Standard verwenden; und im
   Besonderen, das Verzeichnis wo der Linux-Kernel source liegt.


Das heißt also 'arm-linux' ist synonym zu:

"path-to-linux-kernel-source"

Folglich: Dort unter 'Dokumentation' liegt das von Ihnen gesuchte.

Allgemein empfehlen wir Ihnen bei der Nutzung von Yocto sich mit Informationen
wie den folgenden vertraut zu machen:

https://community.nxp.com/docs/DOC-94953
http://elinux.org/Bitbake_Cheat_Sheet
http://www.openembedded.org/wiki/Bitbake_cheat_sheet

Die dort gegebenen Befehle erleichtern Ihnen das Leben und Sie werden diese
tagtäglich nutzen in Ihrem Devel-Prozess.

Kurze Einführung in Yocto:

Yocto macht das anders als ein Kernel developer oder LFS machen würde, bedenken
Sie Yocto ist ein Framework um eine *Distribution* zu erstellen *nicht* eine
*Devel-Framework* [1]. Daher ist das nachfolgende nur beschränkt allgemein
Gültig:

Bei Yocto ist X unter (!Befehle dazu siehe unten!):


* Active kernel sources (i.e. work directory):
  $HOME/\ :raw-html-m2r:`<yocto-project-dir>`\ /\ :raw-html-m2r:`<build-dir>`\ /tmp/work-shared/<yocto-'MACHINE='-value>/kernel-source


* 
  Local copies of all the sources\ :raw-html-m2r:`<br>`
  respectively the sources for the whole project as they are downloaded into local
  git repositories:

  general example:
  $HOME/\ :raw-html-m2r:`<yocto-project-dir>`\ /downloads/git2/<[hostname.]domain.tld>.\ :raw-html-m2r:`<directory>`.\ :raw-html-m2r:`<git-repository>`

  Example:
  $HOME/\ :raw-html-m2r:`<yocto-project-dir>`\ /downloads/git2/github.com.karo-electronics.karo-tx-linux

Anmrk.:
Wobei im Fall unseres Kernel der git-repository path aus der unter ".repo"
enthalten 'Manifest.xml' (welche das 'repo' tool nutzt) hervorgeht.

In the above given 'cheat sheets' are commands included that allows to jump right into the
"work directory" from inside the Yocto framework - of course **after** setup
of the environment via the ``setup-enviornment`` script.

general example:
$ bitbake :raw-html-m2r:`<package>` -c :raw-html-m2r:`<task>`

Example:
$ bitbake linux-karo -c devshell

opens a shell/XTerm in the :raw-html-m2r:`<package>` (here: 'linux-karo' [A]) directory.

[A]
Der :raw-html-m2r:`<package>` Name ergibt sich aus dem Namen der '.bb' Datei:

.. code-block:: console

   sources/meta-freescale-3rdparty/recipes-kernel/linux/linux-karo_4.4.15.bb
                                                        ^^^^^^^^^^
                                               Yocto zurecht.

German
^^^^^^

Bevor Sie nun aber diesen Weg beschreiten:

Korrekterweise würden Sie Ihre Änderungen in ein bei Ihnen im LAN erreichbares
git repository [2] legen, welches ein Klon (git clone [--bare]) des
betreffenden Paketes (\ :raw-html-m2r:`<package>`\ ) ist das Sie bearbeiten wollen, dieses wiederum
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

English
^^^^^^^

But before you take this path:   

Generally speaking that means:\ :raw-html-m2r:`<br>`
To apply one's own changes to a package, like the kernel, busybox, eudev, etc.

One would clone (cmd: git clone) the package's original repository setup 

Correctly, your changes would be committed to a ``git`` repository [2] in your LAN -
usually a NFS share, to preserve Unix file permissions, but ``git`` isn't
pernickety about that as long as the target FS supports links.

This repository is a clone (git clone [--bare]) of the package's (e.g. busybox)
public repository changes are , this in turn clone ('git clone') them on a local machine - to
access the kernel stay there - edit the kernel and - test it - compile [3] Test
it as needed and via TFTP and NFS RFS (ie without writing to NAND or eMMC) and
then made the changes in your LAN git repo (back) and customize the
'Manifest.xml' to this in the future use.

From the LAN repo then you would the changes - according to GPLv2 - to the
Return community.

Advantage of this approach, since yocto directories tend to be big
You can clean them without losing your changes. plus

that of your changes are transferable (in the LAN? to colleagues? Github?)
--------------------------------------------------------------------------

Footnotes & Appendix
--------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
