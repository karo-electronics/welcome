From: Tony Jirasupakorn <Tony.Jirasupakorn@thinkom.com>
To: "Support@KARO-electronics.de" <Support@KARO-electronics.de>
CC: Michael Vyskocil <mv@karo-electronics.de>, Matt Littles  <Matt.Littles@Thinkom.com>, Olaf Pernitt <Olaf.Pernitt@Thinkom.com>, "Ian  McClelland" <Ian.McClelland@thinkom.com>, Chimdi Azubuike  <Chimdi.Azubuike@thinkom.com>
Subject: RE: ThinKom U-Boot Corrupted Environment and NAND
Date: 2018-07-11 00:15:05 CEST

Thank you Lothar for your prompt response.

- Do you have the detailed timing of "saveenv" command?

> saveenv first erases the flash blocks where the environment resides.  
- Where is the environment reside?

> After that it programs the environment from SDRAM to flash.  
- Where does it write the new Checksum?

Best regards,
Tony

-----Original Message-----
From: Lothar Waßmann <LW@KARO-electronics.de> 
Sent: Tuesday, July 10, 2018 1:17 AM
To: Tony Jirasupakorn <Tony.Jirasupakorn@thinkom.com>
Cc: Michael Vyskocil <mv@karo-electronics.de>; Support@KARO-electronics.de; Matt Littles <Matt.Littles@Thinkom.com>; Olaf Pernitt <Olaf.Pernitt@Thinkom.com>; Ian McClelland <Ian.McClelland@thinkom.com>; Chimdi Azubuike <Chimdi.Azubuike@thinkom.com>
Subject: Re: ThinKom U-Boot Corrupted Environment and NAND

Hi,

> We would like you to shed more light on the followings.
> 
>   * Can you please send us the exact sequence (i.e. timing and processes)
>     during "saveenv" so we can have a better understanding?
>
saveenv first erases the flash blocks where the environment resides.
After that it programs the environment from SDRAM to flash.

Obviously a power cut or reset after or during the first step will leave the
env partition erased.

The same holds for your update script or any means of overwriting the env
partition. As you cannot overwrite a programmed flash without erasing it
first, the process will always be a two step procedure with the potential
being interrupted in between.

You can only circumvent this by enabling 'CONFIG_ENV_OFFSET_REDUND' in the
U-Boot config.

This will giye you two identical env partitions, so that you can write to one
of them while leaving the other intact. If U-Boot does not find a valid
environment on the first partition, it will use the env from the second one.

>   * Can you please review our python script during software upgrade to see
>     if there is any potential for corruption?
>
As mentioned above the potential for corruption is inherent in the NAND
erase/write process. There is NO WAY AROUND that, except using the above
mentioned method.

>   * Can you please review the unit logs below (Good vs Bad) and confirm if
>     this could be the result of corruption during "saveenv"?
>
As the environment is initialised to a compiled-in default when the CRC
checksum of the loaded environment is not correct, there is little use in the
'Bad' logs.

You can easily check whether the env partition is erased with the following
command:

    nand dump 00120000
	
If the result is all 0xff, the partition is erased.


Lothar Waßmann
--
___________________________________________________________

Ka-Ro electronics GmbH | Pascalstraße 22 | D - 52076 Aachen
Phone: +49 2408 1402-0 | Fax: +49 2408 1402-10
Geschäftsführer: Matthias Kaussen
Handelsregistereintrag: Amtsgericht Aachen, HRB 4996

www.karo-electronics.de | info@karo-electronics.de
___________________________________________________________
