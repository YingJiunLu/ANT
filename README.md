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

with the following content (all one one line):<br>

>SUBSYSTEM=="usb", ATTRS{idVendor}=="0fcf", ATTRS{idProduct}=="1008", RUN+="/sbin/modprobe usbserial vendor=0x0fcf product=0x1008", MODE="0666", OWNER="pi", GROUP="root"<br>

4.Next reinsert the receiver. Now you should have a /dev/ttyUSB0 node:<br>
>$ ls /dev/ttyUSB0<br>
>/dev/ttyUSB0<br>


Software
-
1.I’m using Python-Ant to read the heart rate. First clone python-ant <br>
>$ git clone https://github.com/baderj/python-ant.git <br>

2.Next install python-setuptools and with that python-ant: <br>
>$ sudo apt-get install -y python-setuptools <br>
>$ cd python-ant/ <br>
>$ sudo python setup.py install <br>

