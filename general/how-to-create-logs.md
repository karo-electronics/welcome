# How to create logs

## Introduction
For people that think screenshots are logs.

## About screenshots
Dear customer, screenshots are not logs nor are they expanding the information
content as needed by the support team.

It can be of interest for the support team to have a photo of screen output in
case the display is e.g. distorted.

### MFGTool
Usable information for the support team about problems in the programming
procedure are not logged by the MFGTool itself. To be able to provide said data
to the support team, that show the problems in it's functionality, user should
keep to the basics of the following list:

- Serial cable  
    Attach baseboard via serial port (RS-232), a.k.a. UART, to a host computer's
    serial interface (e.g.: /dev/ttyS0 | COM1).

- Terminal  
    Start a terminal program like 'minicom' [Linux] or 'PuTTY' [Windows] monitoring
    above mentioned serial port.
    Please be aware the Windows' "HyperTerm" _*cannot*_ be used.

- Log-To-File  
    Activate the terminal program's settings for it's "Log-To-File" feature.

    - Give the file a coherent and unique name. Following generalized examples
      of unique file names:  
        `minicom_2018-04-24_12-22-09.log`  
        `minicom_mfgtool_tx6q_bad--2018-04-24_12-22-09.log`  
        `minicom_mfgtool_tx6q_good.log`  

    - Please look up the correct naming and position in the configuration/preferences
      of that feature in the manual of the respective software used, or "google it".

    - Please be aware that Windows' "Hyperterm" _*will*_ create binary files, which
      are useless. Hence: _*Do Not Use HyperTerm!*_

- Apply power to the baseboard  
    by attaching the USB cabel used for programming by the MFGtool to the
    baseboard and host computer, the baseboard will be powered.

    **TX6Q users beware**:  
    User of the TX6Q COM should be aware that USB does not supply enough wattage
    to guarantee reliably running a i.MX6Q based TX COM. It is recommended to
    provide secondary power supply by also plugging in the 5V AC adapter, as in
    the usual normal operation mode.

- Start MFGTool  
    start the programming procedure of the MFGTool as known.

- Send the Log  
    Take the such create log file in an unedited, unabridged and uncompressed
    form (i.e. _**as-is**_) to the e-mail and use the _**Attach as file"**_ feature.
    Do **Not** copy and paste the log file into the e-mail.

    If you want to highlight something please use small excerpts. For more please
    see [here](hihlighting in emails)

### Linux


