##Install instruction：
```shell
#git clone https://github.com/Pillar1989/mraa_and_upm
#sudo su
#cd mraa_and_upm/deb
#dpkg -i mraa_0.0.2_arm64.deb upm_0.0.1_arm64.deb
```
##Where can we find the demo?
[https://software.intel.com/en-us/iot/hardware/sensors](https://software.intel.com/en-us/iot/hardware/sensors)

##Knows bug
*mraa serial cannt be used. if you still want to use serial, you need modify the kernel device tree.

on arch/arm64/boot/dts/qcom/apq8016-sbc.dtsi

change

stdout-path= "serial0" to stdout-path= "serial1"

then you need install python-serial
```shell
#sudo apt-get install python-serial
```
example:
```python
import serial

port = serial.Serial("/dev/ttyMSM1", baudrate=115200, timeout=3.0)

while True:
    port.write("\r\nSay something:")
    rcv = port.read(10)
    port.write("\r\nYou sent:" + repr(rcv))
```
##Note:
This software tested on http://builds.96boards.org/releases/dragonboard410c/linaro/debian/15.11/
