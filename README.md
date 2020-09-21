## Overview

Simple little project to control a limited number of LEDs using an 
ESP8266 device over WiFi using MQTT for communication and control.



## Setup

### ESP8266

Using the Lua NodeMcu firmware

#### Installing esptool

Creating a virtual environment

```
python3 -mvenv matrix
source ./matrix/bin/activate
```

Install esptool

```
pip install esptool
```

#### Flashing Firmware

Obtain the flash build and then run the following command

```
esptool.py --port /dev/ttyUSB0 write_flash -fm dio 0x0000 ~/nodemcu-master-10-modules-2020-05-27-13-09-01-integer.bin
```

This will generate output similar to this

```
Serial port /dev/ttyUSB0
Connecting....
Detecting chip type... ESP8266
Chip is ESP8266EX
Features: WiFi
Crystal is 26MHz
MAC: 80:7d:3a:75:e4:79
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Auto-detected Flash size: 4MB
Flash params set to 0x0240
Compressed 454656 bytes to 298751...
Wrote 454656 bytes (298751 compressed) at 0x00000000 in 26.6 seconds (effective 136.9 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...
```

#### Connecting to the lua interpreter

Running the following screen command should connect to and present the `>` command prompt

```
screen /dev/ttyUSB0 115200
```


#### Connecting to Wifi

Simple Lua code to connect to Wifi

```
wifi.setmode(wifi.STATION)
station_cfg = {}
station_cfg.ssid="wibble-2GHz"
station_cfg.pwd = "My password!"
station_cfg.save = false
wifi.sta.config(station_cfg)
```

Check the status with the following

```
print(wifi.sta.status())
```

5 is a good status as that means the device has managed to get an IP address

Print the IP address

```
print(wifi.sta.getip())
```



## References

### ESP8266

* [NodeMcu Lua firmware](https://github.com/nodemcu/nodemcu-firmware)
* [NodeMCU firmware builder](https://nodemcu-build.com)
* [ESPtool](https://github.com/espressif/esptool)
* [ESP Board](https://lastminuteengineers.com/esp8266-nodemcu-arduino-tutorial/)
* [NodeMCU docs](https://nodemcu.readthedocs.io/en/master/upload/)
* [Flashing firmware](https://nodemcu.readthedocs.io/en/master/flash/)
* [NodeMCU complete docs](https://nodemcu.readthedocs.io/en/master/)





