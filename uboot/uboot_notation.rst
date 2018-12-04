.. role:: raw-html-m2r(raw)
   :format: html


.. code-block::

               U-Boot
           Notation and Shorthand


The notation used in this documents is based upon the daily usage of
developers and, of course, the U-Boot command set, as shown under
:U-Boot commands:

Therefore you will see for it to include commands which may seem
obscure, not available or in other ways strange or confusing.

These might look like these examples:

:txt:
fdt pr display

save

set boot_mode jffs2
:txt:

But these are essentially just the use of the U-Boot abilities like:


* abbreviation of commands
* TAB completion

thus making out of above given example commands these 'fullfledge'
U-Boot commands:

:txt:
fdt print display

saveenv

setenv boot_mode jffs2
:txt:

As usage of 'shorthand', be it general abbreviations or scripts defined
as variables in our environments, for our common tasks is all but second
nature to us we encourage their use.

Though for clarity we try to keep our usage in examplary logs to a
minimum. That said we might happen to miss the one or the other
and would like to apologize beforehand for any inconvinence caused.

----

Footnotes & Appendix
--------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
