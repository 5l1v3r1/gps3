# README #

gps3 is a python3 interface for gpsd.

gpsd (http://www.catb.org/gpsd/) is a fabulous application that deserves a Python3 interface.

The goal is to deliver a package to the Cheese Shop (https://pypi.python.org/pypi/gps3/0.1a1) that equals the quality of the source and craftsmanship behind it.

It is a match made in heaven.
![GPSD-OBJECTS.png](https://bitbucket.org/repo/nGqxd8/images/3787208142-GPSD-OBJECTS.png)
### How do I get set up? ###

* Summary of set up
The gpsd source can be found at http://download.savannah.gnu.org/releases/gpsd/

If you're hardcore you can build it by following the instructions.  It uses scons and such.  If you gather your tools, it should not be a problem.  [All the installation info](http://www.catb.org/gpsd/installation.html) is here: http://www.catb.org/gpsd/installation.html

If you're like most of humanity **sudo apt-get install gpsd python-gps**

This gives you the daemon, library, and the python fun-pack.  If you use a different package system you are obviously smart enough to figure out how to make yours go.

* Configuration

Setup of the gpsd is straight forward.  Autostart is your choice.  We tend to flag *-n -b -G* in /etc/default/gpsd, to cut down on problems with a spectrum of gps devices and applications.  Default setting the rest of the way.  Generally, there are no surprises.

```
#!bash

usage: gpsd [-b] [-n] [-N] [-D n] [-F sockfile] [-G] [-P pidfile] [-S port] [-h] device...
  Options include:
  -b		     	    = bluetooth-safe: open data sources read-only
  -n			    = don't wait for client connects to poll GPS
  -N			    = don't go into background
  -F sockfile		    = specify control socket location
  -G         		    = make gpsd listen on INADDR_ANY
  -P pidfile	      	    = set file to record process ID
  -D integer (default 0)    = set debug level
  -S integer (default 2947) = set port for daemon
  -h		     	    = help message
  -V			    = emit version and exit.
A device may be a local serial device for GPS input, or a URL of the form:
     {dgpsip|ntrip}://[user:passwd@]host[:port][/stream]
     gpsd://host[:port][/device][?protocol]
in which case it specifies an input source for GPSD, DGPS or ntrip data.

```
### gps3.py from the terminal ###
```
#!bash
me@work:~/SyPy_projects/gps3$ python3 gps3.py --help
usage: gps3.py [-h] [-human] [-host HOST] [-port PORT] [-metric] [-verbose]
               [-device DEVICEPATH] [-json] [-nautical] [-imperial] [-nmea]
               [-rare] [-raw] [-scaled] [-timimg] [-split24] [-pps]

optional arguments:
  -h, --help          show this help message and exit
  -human              DEFAULT Human Friendly
  -host HOST          DEFAULT "127.0.0.1"
  -port PORT          DEFAULT 2947
  -metric             DEFAULT METRIC units
  -verbose            increases verbosity, but not that much
  -device DEVICEPATH  alternate devicepath e.g.,"/dev/ttyUSB0"
  -json               /* output as JSON objects */
  -nautical           /* output in NAUTICAL units */
  -imperial           /* output in IMPERIAL units */
  -nmea               /* output in NMEA */
  -rare               /* output of packets in hex */
  -raw                /* output of raw packets */
  -scaled             /* scale output to floats */
  -timimg             /* timing information */
  -split24            /* split AIS Type 24s */
  -pps                /* enable PPS JSON */
me@work:~/SyPy_projects/gps3$ 
```

Currently not all options are implemented or fully  functional.
Commandline execution without options is the same as using the DEFAULT option flags.

Don't have a gps to experiment?  Try
```
#!bash
python3 gps3.py -host sypy.ddns.net
```
It's not that exciting, as it's not moving, but you will have the gps jitter. 