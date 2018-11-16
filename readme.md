# Python-NEO-6M-GPS-Raspberry-Pi
Python script for the NEO-6M GPS module on the Raspberry Pi
## Connecting Schema
![Image of Yaktocat](https://raspberrytips.nl/wp-content/uploads/2016/12/UBOLX-NEO-6M-RPI-600x274.png)

## Getting Started
These instructions will get you a quick start with the script.
* look if the terminal output of the sensor works
```
cat /dev/ttyAMA0
```
* Run the script
```
cd Python-NEO-6M-GPS-Raspberry-Pi
sudo python Neo6mGPS.py
```

## Dependencies
* pip installed.
```
sudo apt-get install python-pip
```
* you will need pynmea2.
```
sudo pip install pynmea2
```

## Example Code
```
import serial
import pynmea2
def parseGPS(str):
    if str.find('GGA') > 0:
        msg = pynmea2.parse(str)
        print "Timestamp: %s -- Lat: %s %s -- Lon: %s %s -- Altitude:
%s %s" %
(msg.timestamp,msg.lat,msg.lat_dir,msg.lon,msg.lon_dir,msg.altitude,m
sg.altitude_units)
serialPort = serial.Serial("/dev/ttyAMA0", 9600, timeout=0.5)
while True:
    str = serialPort.readline()
    parseGPS(str)

```