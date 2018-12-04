.. role:: raw-html-m2r(raw)
   :format: html


Yocto
=====

The premise of Yocto is to offer the developer a framework to *create a
distribution*\ , which in turn means **reproducible builds**. In case of Ka-Ro
TXCOM this manifests in that the same sources for different TXCOM (e.g. TX6Q vs.
TX6UL) create the same solution.

Supporting factors for this behaviour for Yocto are, e.g.:


#. 
   For this one of the main supporting factors for  this is Linux's unique
   feature of being one kernel for all devices.

#. 
   Another supporting factor is that all parts of the root filesystem (RFS), the
   GNU infrastructure like coreutils, bash, init, etc., are single parts. The
   solution doesn't require: a GUI, X11,

----

Footnotes, Appendix & Sources
-----------------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
