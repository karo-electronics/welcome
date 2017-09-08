> In der Doku steht dass es dazu unter arm-linux/Documentation/spi was gibt,
> könnten Sie mir das vll noch zu kommen lassen?
>   
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
Sie Yocto ist ein Framework um eine _Distribution_ zu erstellen _nicht_ eine
*Devel-Framework* [1]. Daher ist das nachfolgende nur beschränkt allgemein
Gültig:

Bei Yocto ist X unter (!Befehle dazu siehe unten!):

- Aktive compilierte Kernel sources (i.e. Work directory):
  $HOME/<yocto-project-dir>/<build-dir>/tmp/work-shared/<yocto-'MACHINE='-value>/kernel-source


- Aktive Kernel-Source git repository, bzw. lokale Kopien der benutzen und
  benötigten Quellen und/oder repositories:

  allg. Bsp.:
  $HOME/<yocto-project-dir>/downloads/git2/<[hostname.]domain.tld>.<directory>.<git-repository>

  Bsp.:
  $HOME/<yocto-project-dir>/downloads/git2/github.com.karo-electronics.karo-tx-linux

Anmrk.:
Wobei im Fall unseres Kernel der git-repository path aus der unter ".repo"
enthalten 'Manifest.xml' (welche das 'repo' tool nutzt) hervorgeht.

In den o.g. 'cheat sheets' sind Befehle enthalten die Sie nutzen können um das
besagte 'Work directory' aus Yocto zu erreichen (ofc, nach aufsetzen der
Umgebung via 'setup-environment' script):

allg. Bsp.:
$ bitbake <package> -c <task>

Bsp.:
$ bitbake linux-karo -c devshell

öffnet eine Shell/XTerm im <package> (hier 'linux-karo' [A]) Verzeichnis.

[A]
Der <package> Name ergibt sich aus dem Namen der '.bb' Datei:

sources/meta-freescale-3rdparty/recipes-kernel/linux/linux-karo_4.4.15.bb
                                                     ^^^^^^^^^^
                                            Das poppelt sich Yocto zurecht.

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
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)

Contact support: support@karo-electronics.de
