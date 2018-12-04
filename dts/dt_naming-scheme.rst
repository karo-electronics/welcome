.. role:: raw-html-m2r(raw)
   :format: html


.. code-block::

   regulators {
       /* label  */: /*node name*/
       reg_lcd0_pwr: regulator-lcd0-power {
           compatible = "regulator-fixed";
           regulator-name = "LCD0 RESET";
           regulator-min-microvolt = <3300000>;
           regulator-max-microvolt = <3300000>;
           pinctrl-names = "default";
           pinctrl-0 = <&pinctrl_lcd0_pwr>;
           gpio = <TX_GPIO_PIN150 GPIO_ACTIVE_HIGH>;
           enable-active-high;
           regulator-boot-on;
           regulator-always-on;
       };


   /* label  */:
   Only for compiler to handle/know what is referenced - will not be in the DTB
   There are no '-' allowed (as it is a arithmetic operant)

   /*node name*/
   Reference that is actually the DT name for this node - nay, device.


   device-node-name {
       label : node-name {
       compatible = "regulator-fixed";
       property-string-valued = "string";
       property-numerical-valued = <decimal-or-hexadecimal>;
       peroperty = <&referenced-device-node>;
       property;
       }
       reg_lcd0_pwr: regulator-lcd0-power {
           compatible = "regulator-fixed";
           regulator-name = "LCD0 RESET";
           regulator-min-microvolt = <3300000>;
           regulator-max-microvolt = <3300000>;
           pinctrl-names = "default";
           pinctrl-0 = <&pinctrl_lcd0_pwr>;
           gpio = <TX_GPIO_PIN150 GPIO_ACTIVE_HIGH>;
           enable-active-high;
           regulator-boot-on;
           regulator-always-on;
       };



#
^

.. code-block::

   &pwm2 {
       pinctrl-names = "default";
       pinctrl-0 = <&pinctrl_pwm2>;
       #pwm-cells = <3>;
       status = "disabled";
   };


This is a text

.. code-block::

   backlight0: backlight0 {
       compatible = "pwm-backlight";
       pwms = <TX_PWM 0 500000>;
   [...]


This is a text

'''This is another text'''

'''
    /*

.. code-block::

   #pwm-cells = <3>;

   defines the amount of values ("cells") - <3> -  allowed in the PWM:

   pwms = <TX_PWM 0 500000 0>;
             0    1   2    3
                      ^
           1st 2nd 3rd 4th

'''

default value for ``PWM_POLARITY_INVERTED`` in a Kernel without support for
polarity inversion is ``'2'``\ , e.g. ``#pwm-cells = <2>;``. The removal of the
property (\ ``#pwm-cells``\ ) resets to the default.

----

Footnotes & Appendix
--------------------

----

`Ka-Ro electronics GmbH <http://www.karo-electronics.de>`_\ :raw-html-m2r:`<br>`
Contact support: support@karo-electronics.de
