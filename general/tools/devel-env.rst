.. role:: raw-html-m2r(raw)
   :format: html


Setup of development environment
================================

Software development, be it the basic BSP or the Ka-Ro's Yocto based BSP, or
customer applications to be integrated in for all Ka-Ro products' software development

All (essentially) hereafter is blatantly stolen from:\ :raw-html-m2r:`<br>`
`Devuan.org's documentation source <https://devuan.org/os/documentation/install>`_

Devuan installation instructions
--------------------------------

There are no instructions concerning installation of a Linux (Devuan) here; 'cause:


#. 
   there are references to virtualmachines following this, and  

#. 
   this should be either done with ease, or  

#. 
   ask your admin.  

The one important thing is that the VM after install needs to be brought to an
uptodate state (use ``aptitude``\ ) and some tools, like ``sudo`` and
``build-essential``\ , etc.; where among others the latter is in turn needed for the
VM's LKML and DKMS infrastructure, which is required for Virtualbox's "Guest
Additions" to be installed.

Further on the Yocto framework will require to have packages installed, if not
directly referencing in error output (like: ``please install chrpath``\ ) then at it
will tell so least indirectly (\ ``couldn't run command X``\ ) which packages are
missing. This should be of no problem and solved with ease with minimal
understanding of the Debian/Devuan package management and the therein given
search functions. `Debian ``apt`` cheat
sheets <https://duckduckgo.com/?q=debian+apt+cheat+sheet>`_

The basic understanding of handling the problem above will give skills valueable
for handling the problems of the Linux created by the Yocto framework and fall
in anyway under "Basic Linux Skills". See also footnote: `Basic Linux Support <#basic-support>`_

Downloads
---------

Download section:\ :raw-html-m2r:`<br>`
https://files.devuan.org/?ref=/os/download

Download section, directly for ASCII:\ :raw-html-m2r:`<br>`
https://files.devuan.org/devuan_ascii/

Virtual Disk
------------

The virtual disks fro Devuan's ASCII release are available here:  

https://files.devuan.org/devuan_ascii/virtual/

The directory's entries are as follow:

.. code-block:: console

   ../
   README.txt                                         06-Jun-2018 15:14     646
   SHA256SUMS                                         06-Jun-2018 15:14     311
   SHA256SUMS.asc                                     06-Jun-2018 15:14    1528
   Vagrantfile                                        06-Jun-2018 15:14     288
   devuan_ascii_2.0.0_amd64_qemu.qcow2.xz             06-Jun-2018 15:14    532M
   devuan_ascii_2.0.0_amd64_vagrant.box               06-Jun-2018 15:14    707M
   devuan_ascii_2.0.0_amd64_vbox.vdi.xz               06-Jun-2018 15:14    533M

Each of the virtualization solutions have their own disk image which can directly
used with the respective solution's machine description. An extensive example for
that is given below in the section for `Vagrant <#vagrant>`_.

Virtual machines
----------------

We distribute virtual machine base images, ready to use on various virtualization platforms. They are all available in the downloads section.

The VM images are made using our `vm-sdk <https://git.devuan.org/sdk/vm-sdk>`_ on top of the `devuan-sdk <https://git.devuan.org/sdk>`_.

Qemu
^^^^

Qemu images are built ready for deployment, customization or conversion to other formats. They are available from the stable release directory in `files.devuan.org <https.//files.devuan.org>`_.

The scripts used to bake the image are all included in the `devuan-SDK <https://git.devuan.org/sdk>`_.

The .qcow2 image we `distribute <#qcow2-images>`_ is ready to boot with kvm.

Find the ASCII images `here <https://files.devuan.org/devuan_ascii/virtual/devuan_ascii_2.0.0_amd64_qemu.qcow2.xz>`_.

Download the Qemu image, then boot it with, for example:  

.. code-block::

   $ qemu-system-x86_64 --enable-kvm -hda devuan_jessie_1.0.0_amd64.qcow2

Images are also available for the i386 architecture (see Devuan's download section, `here <https://files.devuan.org/?ref=/os/download>`_\ ). The Qemu format is a gateway to the conversion to more formats, for more information refer to the documentation of the ``qemu-img`` convert command.

Vagrant
^^^^^^^

To quickly deploy a new Vagrant image based on Devuan, just copy the following file in your HOME directory and run ``vagrant up``.

.. code-block:: console

   $ mkdir devuan-vagrant && cd $_ && cat << EOF > Vagrantfile
   Vagrant.configure(2) do |config|
     config.vm.box = "https://files.devuan.org/devuan_ascii/virtual/devuan_ascii_2.0.0_amd64_vagrant.box"
     config.ssh.username = "root"
     config.ssh.password = "toor"
     config.vm.guest = :debian
     config.vm.synced_folder ".", "/vagrant", disabled: true
   end
   EOF
   $ vagrant up
   $ vagrant ssh

A pre-created file is available and can be downloaded from `here <https://files.devuan.org/devuan_ascii/virtual/Vagrantfile>`_.

Services offering Devuan
^^^^^^^^^^^^^^^^^^^^^^^^

Data Center Light: Gives back to the Devuan community by organising Devuan hackatons and has had special offers on Devuan VMs: https://devuanhosting.com

OpenNebula: Offers Devuan ASCII guest images off their marketplace and and also for free: http://marketplace.opennebula.org

----

Sources
=======

https://devuan.org/os/documentation/install

:raw-html-m2r:`<a id="qcow2-images">Devuan qcow2 images:</a>`\ :raw-html-m2r:`<br>`
https://files.devuan.org/devuan_ascii/virtual
https://files.devuan.org/devuan_jessie/virtual

----

Footnotes & Appendix
--------------------

:raw-html-m2r:`<a id="basic-support">Basic Linux support:</a>`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Ka-Ro includes in the sale of each development kit a "installation support"
package, which is not to be confused with a "Linux Basics & More Support"
package.

Customers that require the kind of help beyond what DuckDuckGo, etc. offer,
concerning "Linux Basics & More Support", please feel free to contact our
sales department at:

sales@karo-electronics.de

for a quote.

----

`Ka-Ro electronics GmbH <https://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
