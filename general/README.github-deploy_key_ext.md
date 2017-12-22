# GitHub Deploy Key

## Table of Contents


   * [GitHub Deploy Key](#github-deploy-key)
      * [Introduction](#introduction)
      * [What / Why](#what--why)
      * [Using Github Deploy Key](#using-github-deploy-key)
         * [How to: Generate a ssh key under Linux](#how-to-generate-a-ssh-key-under-linux)
         * [How to: Generate a ssh key under Windows](#how-to-generate-a-ssh-key-under-windows)
      * [SSH settings](#ssh-settings)
         * [Test functionality](#test-functionality)
      * [Deploy the Deploy Key](#deploy-the-deploy-key)
         * [Add the generated public ssh key](#add-the-generated-public-ssh-key)
      * [Reviewing your deploy keys](#reviewing-your-deploy-keys)
      * [Testing the Deploy Key](#testing-the-deploy-key)
      * [Footnotes & Appendix](#footnotes--appendix)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc)  
rev. 2017-09-26

## Introduction
In this document are short excerpts of the _What_, _Why_ and _How_ of access
to repositories on **GitHub** using a so called **Deploy Key**.

The sources of these excerpts are cited as "[`src`](http://example.com/)".

## What / Why
**Deploy key** is a SSH key set in your repo to grant client read-only (as well
as r/w, if you want) access to your repo.

As the name says, its primary function is to be used in the deploy process,
where only read access is needed. Therefore keep the repo safe from the attack,
in case the server side is fallen.


## Using Github Deploy Key
[`src`][gist-gh]  
[Winmerge][winmerge]  

Hereafter are some generalized step-by-step instructions.

### How to: Generate a ssh key under **Linux**

Under Linux you will need to run `ssh-keygen` to generate a (purpose bound)
key.  The commands look like the following:

``` console
    ssh-keygen -t rsa -b 4096 -C "{email}"
```

where `"{email}"` should be replaced with the appropriate valid value similar
to (incl. quotes):

`"example@example.com"`

`ssh-keygen` will ask for a name of the key, the user can there either:

``` console
Enter file in which to save the key (/home/example/.ssh/id_rsa):
```

If no filename is given the `ssh-keygen` will create files (secret and public
key) with the names `id_rsa` and `id_rsa.pub`.

**Note:**  
It is highly recommended to set a filename for the key pair to allow for
multiple keys in the system, and to respect purpose binding. Also any already
previously created keys with the default naming **will** be lost.

After the generation, file `id_rsa` and `id_rsa.pub` can be found under the
`$HOME/.ssh` folder.

---
**Trap for young players:**

* **File location:**  
  The ssh-keygen will ask the user for a filename:

  `Enter file in which to save the key (/home/example/.ssh/id_rsa): example-name_for_key`

  to not input a path - _like in the example above_ - in the above request will
  create the files in the **current** directory (usually `$HOME`). At the end of
  the process the created files can easily be moved to the appropriate location,
  just doing:

  `$ mv -i example-name_for_key* $HOME/.ssh/`

  see [Key created without proper path](#key-created-without-proper-path) for more.

* **Without passphrase:**  
  If you want the process to work keyboard-less the passphrase has to be left
  empty, when the `ssh-keygen` ask for an input:

  `Enter passphrase (empty for no passphrase):`

----
The whole process looks as follows:

``` console
$ ssh-keygen -t rsa -b 4096 -C "example@example.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/home/example/.ssh/id_rsa): example-name_for_key
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in example-name_for_key.
Your public key has been saved in example-name_for_key.pub.
The key fingerprint is:
f3:a3:a9:78:da:08:50:5d:2f:7b:c2:f1:b2:3c:06:4f example@example.com
The key's randomart image is:
+---[RSA 4096]----+
|      .          |
|   . . .         |
|  . . o .        |
| .   . =         |
|.   . E S        |
| .   = = o       |
|  .   *   o      |
|   . =.. o .     |
|    +oo.o        |
+-----------------+
```

If no filename is given the `ssh-keygen` will create files (secret and public
key) under the names `id_rsa` and `id_rsa.pub`.  
See [Key created without proper path](#key-created-without-proper-path) for more
about this.


### How to: Generate a ssh key under **Windows**
For this we use and describe the usage of [`PuTTY`][PuTTY] and the there
included `PuTTYgen` tools for gernating the ssh key. An alternative, similar,
program is `OpenSSH`.

**Note:**  
@PuTTY - To get the non-installer version, please scroll down to "_Alternative
binary files_"

----

* Introduction  
  `PuTTYgen` is an key generator tool for creating SSH keys for `PuTTY`. It is
  analogous to the `ssh-keygen` tool used in some other SSH implementations.

  The basic function is to create public and private key pairs. `PuTTY` stores
  keys in its own format in `.ppk` files. However, the tool can also convert
  keys to and from other formats.

  `PuTTYgen.exe` on Windows is a graphical tool. A command-line version is
  available for Linux.

  [`src`](https://www.ssh.com/ssh/putty/windows/puttygen)

* PuTTY Key Generator (a.k.a. `PuTTYgen`)  
  While `PuTTY` is a client program for SSH (in addition to Telnet and Rlogin),
  it is not a port of or otherwise based on OpenSSH. Consequently, PuTTY does
  not have native support for reading OpenSSH's SSH-2 private key files.
  However, PuTTY does have a companion named PuTTYgen (an RSA and DSA key
  generation utility), that can convert OpenSSH private key files into PuTTY's
  format; allowing you to connect to your cloud server from a Windows machine,
  with the added security that SSH keys provide.

  PuTTYgen is a (free) open-source utility and can be downloaded from the
  maintainer's website. PuTTYgen is what you will use to generate your SSH keys
  for use in PuTTY. To start, all you need to do is download the exectuable
  files (.exe) and save them on the computer that you'll use to connect to your
  VPS, e.g. on the desktop. You will not need to "install" PuTTYgen, because it
  is a standalone application.

  [`src`][putty-create-key]

* Generating OpenSSH-compatible Keys for Use with PuTTY
  To generate a set of RSA keys with PuTTYgen:

  * Start the PuTTYgen utility

  * Set **Type of key to generate** to: `RSA` (eq. to "SSH-2 RSA")

  * Set value in **Number of bits in a generated key field** to `4096`

  * Click the Generate button and follow the instructions then given:  

  	* Move your mouse pointer around in the blank area of the Key section,  
      below the progress bar (to generate some randomness) until the progress
  	  bar is full.<br><br>

  * A private/public key pair has now been generated

  * In the Key comment field, enter any comment you'd like, to help you identify
    this key pair

  * **Optional:** Type in a passphrase in the `Key passphrase` and
    `Confirm passphrase` fields, it's highly recommended to use password
    generators like [KeePassX] or [KeePass]

  * Click the **Save public key** button  
    choose whatever filename you'd like (some users create a folder in their  
    computer named my_keys)

  * Click the **Save private key** button & choose whatever filename you'd like
    (you can save it in the same location as the public key, but it should be a
    location that only you can access and that you will NOT lose! If you lose
    your keys and have disabled username/password logins, you will no longer be
    able log in!)

  * Right-click in the text field labeled Public key for pasting into OpenSSH
	authorized_keys file and choose **Select All**

  * Right-click again in the same text field and choose Copy.

**Note:**  
PuTTY and OpenSSH use different formats for public SSH keys. If the SSH Key you
copied starts with "`---- BEGIN SSH2 PUBLIC KEY ...`", it is in the wrong
format. Be sure to follow the instructions carefully. Your key should start with
"`ssh-rsa AAAA ....`"

[`src`][putty-create-key]

## SSH settings
Under _Linux_ the ssh client uses the directory `$HOME/.ssh` for keeping it's
user's configuration file. Further, in this config file, does the ssh client
allow for aliasing endpoints - i.e. the host (a.k.a. `HostName`).

``` console
$ man ssh_config
[...]
[...]
The possible keywords and their meanings are as follows (note that keywords
are case-insensitive and arguments are case-sensitive):

Host    Restricts the following declarations (up to the next Host or Match
        keyword) to be only for those hosts that match one of the patterns
        given after the keyword.  If more than one pattern is provided, they
        should be separated by whitespace.  A single ‘*’ as a pattern can be
        used to provide global defaults for all hosts.  The host is the
        hostname argument given on the command line (i.e. the name is not
        converted to a canonicalized host name before matching).

        A pattern entry may be negated by prefixing it with an exclamation
        mark (‘!’).  If a negated entry is matched, then the Host entry is
        ignored, regardless of whether any other patterns on the line match.
        Negated matches are therefore useful to provide exceptions for
        wildcard matches.

        See PATTERNS for more information on patterns.
```

Example:  
`~/.ssh/config`

``` console
# Setting for GitHub Deploy Key
Host github.com-deploy
   HostName github.com
   User git
   ForwardX11 no
   IdentityFile ~/.ssh/example-name_for_key
```

### Test functionality
**With** modified `.ssh/config` setting a 'Host'

``` console
ssh -T github.com-deploy
```

**W/o** modified `.ssh/config` setting a 'Host' (and no other keys in ssh)

``` console
ssh -T git@github.com
```

As can be seen with these two examples the setting `Host` allows to set task
specific usage of keys, while the setting of the keyword `User` allows to omit
providing the username.

Output example:

```console
$ ssh -T github.com-deploy
Enter passphrase for key '/home/user/.ssh/github-deploy':
Hi karo-electronics/TEST! You've successfully authenticated, but GitHub does not provide shell access.
```

---
## Deploy the _Deploy Key_ @ github
### Add the generated public ssh key
After having be generated the the public key file is to be added to the git
repositories  `Deploy keys`, which is found in the repo's `Settings`.

Adding the key(s) is done by going to the above mentioned `Settings` page and
simply opening it up the public key file (`*.pub`) via a text editor (`emacs`,
`notepad++`, etc.) and then _copy-and-paste'ing_ the contens of the
`.pub`-file into the there given and marked input field.

## Reviewing your deploy keys
[`src`][gh-review-keys]

Following an excerpt of above:

You should review deploy keys to ensure that there aren't any unauthorized
(or possibly compromised) keys. You can also approve existing deploy keys
that are valid.

* On GitHub, navigate to the main page of the repository.

* Under your repository name, click **`Settings`**.

* In the left sidebar, click **`Deploy keys`**.

* On the Deploy keys page, take note of the deploy keys associated with your
  account. For those that you don't recognize, or that are out-of-date,
  click **`Delete`**. If there are valid deploy keys you'd like to keep,
  click **`Approve`**.

---
## Key created without proper path
After generating the _Deploy Key_ and before setting up the ssh client, if the
user has created the ssh keys without an full path file name it will have been
created into the current directory (usually `$HOME`), while this "_all fine and
dandy_" for experienced users for purpose of  keeping things simple in this
documentation it **needs** to be moved; as follows:

```console
# below names appear when using tab completion in a command as following 'mv'
# and represent the key's file names:
# example-name_for_key
# example-name_for_key.pub

$ mv example-name_for_key* .ssh/
$ ls -Al .ssh
total 212
-rw-r--r-- 1	612 2012-02-01 16:38:19 authorized_keys
-rw-r--r-- 1   3315 2017-08-31 10:38:35 config
-rw------- 1   3326 2017-09-01 09:56:28 example-name_for_key
-rw-r--r-- 1	745 2017-09-01 09:56:28 example-name_for_key.pub
```

---
## Footnotes & Appendix
[KeePassX]: https://www.keepassx.org/
[KeePass]: http://keepass.info/
[PuTTY]: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
[Npp-web]: https://notepad-plus-plus.org/download/
[Npp-smb]: smb://net/server2003/install/Tools/Optional/Text-Editors/Notepad++
[putty-create-key]: https://www.digitalocean.com/community/tutorials/how-to-create-ssh-keys-with-putty-to-connect-to-a-vps
[gist-gh]: https://gist.github.com/zhujunsan/a0becf82ade50ed06115
[winmerge]: https://en.wikipedia.org/wiki/WinMerge
[gh-review-keys]: https://help.github.com/articles/reviewing-your-deploy-keys/

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de