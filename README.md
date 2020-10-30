ANT+
=
Hardware
-

1.Log in to the Raspberry Pi, then insert the ANT+ receiver. Check that the receiver is recognized by running <br>
>$ dmesg | tail <br>

2.You should see entries for the receiver and the corresponding vendor id and product id. For the receiver they should always be: <br>
>idVendor: 0fcf<br>
>idProduct: 1008<br>
<br>
3.  To get the usb serial kernel driver to create a node for our  receiver we need to create an udev rule. First unplug the receiver then create the following file:

>$ sudo vi /etc/udev/rules.d/garmin-ant2.rules<br>
<br>
with the following content (all one one line):
>SUBSYSTEM=="usb", ATTRS{idVendor}=="0fcf", ATTRS{idProduct}=="1008", RUN+="/sbin/modprobe usbserial vendor=0x0fcf product=0x1008", MODE="0666", OWNER="pi", GROUP="root"<br>


Software
-
