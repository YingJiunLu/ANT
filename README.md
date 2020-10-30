ANT+
=
Hardware
-

1.Log in to the Raspberry Pi, then insert the ANT+ receiver. Check that the receiver is recognized by running <br>
  $ dmesg | tail <br>
2.You should see entries for the receiver and the corresponding vendor id and product id. For the receiver they should always be: <br>
>idVendor: 0fcf<br>
>idProduct: 1008<br>
3.  To get the usb serial kernel driver to create a node for our Movestick mini we need to create an udev rule. First unplug the Movestick then create the following file:<br>
Software
-
