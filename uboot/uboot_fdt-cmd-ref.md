### Commands and explanations

`fdt`  
flattened device tree utility commands

```console
fdt addr [-c]  <addr> [<length>]`   - Set the fdt location to <addr>
fdt boardsetup`                     - Do board-specific set up
fdt move <fdt> <newaddr> <length>   - Copy the fdt to <addr> and make it active
fdt resize                          - Resize fdt to size + padding to 4k addr
fdt print <path> [<prop>]           - Recursive print starting at `<path>`
fdt list <path> [<prop>]            - Print one level starting at `<path>`
fdt get value <var> <path> <prop>`  - Get `<property>` and store in `<var>`
fdt get name <var> <path> <index>`  - Get name of node `<index>` and store in `<var>`
fdt get addr <var> <path> <prop>`   - Get start address of `<property>` and store in `<var>`
fdt get size <var> <path> [<prop>]` - Get size of [`<property>`] or num nodes and store in `<var>`
fdt set <path> <prop> [<val>]`      - Set `<property>` [to `<val>`]
fdt mknode <path> <node>`           - Create a new node after `<path>`
fdt rm <path> [<prop>]`             - Delete the node or `<property>`
fdt header`                         - Display header info
fdt bootcpu <id>`                   - Set boot cpuid
fdt memory <addr> <size>`           - Add/Update memory node
fdt rsvmem print`                   - Show current mem reserves
fdt rsvmem add <addr> <size>`       - Add a mem reserve
fdt rsvmem delete <index>`          - Delete a mem reserves
```

**NOTE**  
Dereference aliases by omitting the leading `'/'`, e.g. `fdt     print ethernet0`

`fdt chosen [<start> <end>]` - Add/update the /chosen branch in the tree
 `<start>`/`<end>` - initrd start/end addr

## FDT paths
A printout of the whole FDT as can be shown by using the U‑Boot command:

`fdt print`

Any specific nodes can be shown by:

`fdt print <alias|/path/to/node> [<property>]`

e.g. (aliases are dereferenced by omitting the leading `'/'`):

```console
fdt print display
fdt print /ahb@80080000/usb@80080000
```
* Linux  
  users and Linux users can (while running) see the Device Tree under
  (*rootfs*):

  `/proc/device-tree`  

  or:  

  `/sys/firmware/devicetree/base`

The Linux kernel has to be compiled with the option `"CONFIG_PROC_DEVICETREE"`
set **true**.

Refer to 'Linux/TX##-Driver.pdf' for a list of the device paths and aliases
provided and used on the StarterKit & TX-CoM assembly.

---
## Footnotes & Appendix

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
