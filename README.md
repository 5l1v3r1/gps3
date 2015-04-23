# README #
[![Coverage Status](https://coveralls.io/repos/wadda/gps3/badge.svg)](https://coveralls.io/r/wadda/gps3)

gps3 is a Python3 interface for gpsd.  It is backwards compatable with Python2.7

gpsd (http://www.catb.org/gpsd/) is a fabulous application/daemon for many geo-location devices.

The goal is to deliver a Python package to the Cheese Shop (https://pypi.python.org/pypi/gps3/0.1a)

![GPSD-OBJECTS.png](http://wadda.org/dropbag/gps3proof.png)

### gps3.py from the terminal ###
```
#!bash
me@work:~/projects/gps3$ python3 gps3.py --help
usage: gps3.py [-h] [-human] [-host HOST] [-port PORT] [-metric] [-verbose]
               [-device DEVICEPATH] [-json] [-nautical] [-imperial] [-nmea]
               [-rare] [-raw] [-scaled] [-timimg] [-split24] [-pps]

optional arguments:
  -h, --help          show this help message and exit
  -human              DEFAULT Human Friendlier
  -host HOST          DEFAULT "127.0.0.1"
  -port PORT          DEFAULT 2947
  -metric             DEFAULT METRIC units
  -verbose            increases verbosity, but not that much
  -device DEVICEPATH  alternate devicepath e.g.,"/dev/ttyUSB0"
  -json               /* output as JSON objects */
  -nautical (WIP)     /* output in NAUTICAL units */
  -imperial (WIP)     /* output in IMPERIAL units */
  -nmea               /* output in NMEA */
  -rare               /* output of packets in hex */
  -raw                /* output of raw packets */
  -scaled             /* scale output to floats */
  -timing             /* timing information */
  -split24 (WIP)      /* split AIS Type 24s */
  -pps                /* enable PPS JSON */
me@work:~/projects/gps3$
```
Currently not all options are implemented or fully  functional.
Commandline execution without options is the same as using the DEFAULT option flags.

Don't have a gps to experiment?   Try
```
#!bash
python3 gps3.py -host wadda.ddns.net  # python gps3.py -host wadda.ddns.net
```
See if the gps server is running.  While it's not moving, you will have the gps jitter.

A trivial demonstration of functionality found in
```
#!bash
python3 demo_gegps3.py  # python demo_gegps3.py
```
Presently, when placed in same directory as gps3.py, creates a keyhole (.kml) file for Google Earth (GE defaults 4 second refreshing) with age < 1 sec from refresh.
Open the generated file (/tmp/gps3_live.kml) with Google Earth and watch the jitter and track scratch that way, all day.

Similarly ***gpex3.py*** in the same directory as gps3.py creates a gpx log file at /tmp/gpx3.gpx.
```
#!bash
python3 gpex3.py
```

However, it is not currently Python2 compliant.




