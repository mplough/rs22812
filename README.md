# rs22812

This is a Python script that will talk over a serial
port to a Radio Shack RS22812 digital multimeter.

If you want to monitor a measured electrical parameter (voltage,
current, resistance, etc.) over a period of time, this Python program
can talk to a Radio Shack 22-812 digital multimeter over the serial
port and print out its readings.

Besides needing the multimeter and a serial cable to connect to the
meter, you'll need to download the `PySerial` module:
http://pyserial.sourceforge.net.  If you don't have Python, you can
get it at http://www.python.org/.  My last few PCs didn't come with
serial ports; if you're in the same boat, you can purchase a
USB-to-serial adapter for $10-$15 that will do the job.

The meter costs about $70 from Radio Shack.  It can measure AC and DC
voltage (0.1 mV to 1000 V), AC and DC current (0.1 uA to 10 A), and
resistance (0.1 ohm to 40 Mohm).  It will also measure capacitance (1
pF to 40 uF), frequency (10 Hz to 4 MHz), duty cycle, pulse width, AC
voltage in dBm (1 mW), diode voltage drop, logic high and low levels,
and the DC gain of small bipolar transistors (0 to 1000).  In
conjunction with an optional thermocouple module, it will also measure
temperature.  It can auto range or manual range, measure minimum and
maximum values, and it has a relative measurement mode which subtracts
the reading shown when the REL button is pressed from subsequent
readings.  Depending on the measurements, measurement accuracy is in
the 0.5% to 1% range.

The Python code provided has an RS22812 object that you create by
specifying the COM port that the meter is connected to (e.g., a number
for Windows or a device for Linux).  Then you call the `GetReading()`
method of this object.  You'll be returned a tuple of three things:
the measured value, the meter's mode, and any annunciator flags that
are on.  Or, you can run the provided code as a stand-alone script and
it will print the timestamped meter readings to stdout.  Here's an
example:

```
16Aug2009-16:42:21 [1] ('129.7 mV', 'DC V', ('Auto',))
16Aug2009-16:42:23 [2] ('129.7 mV', 'DC V', ('Auto',))
16Aug2009-16:42:24 [3] ('129.7 mV', 'DC V', ('Auto',))
16Aug2009-16:42:26 [4] ('2.4 mV~', 'AC V', ('Auto',))
16Aug2009-16:42:28 [5] ('0.0 mV~', 'AC V', ('Auto',))
16Aug2009-16:42:30 [6] ('0.0 mV~', 'AC V', ('Auto',))
16Aug2009-16:42:32 [7] ('0.0 mV~', 'AC V', ('Auto',))
```

The meter first started reading the DC voltage of a power supply, then
I switched the meter to measure AC voltage.  The '~' appended to the
SI unit designates an AC measurement.

The RS22812 object's code is pretty simple, so you can easily
customize the output to your tastes.

As seen in the above example, the minimum time between readings is
about 1.5 seconds.  The manual states the battery life should be
around 100 hours.  I would imagine the battery life would be less when
RS-232 communications are turned on, but you still likely would be
able to get 100,000 or more readings on one battery.  If you need
more, it would not be difficult to power the meter from a power supply
such as a 9 volt wall wart (or use a lithium battery).

The zip file for the release also includes a [http://www.wxpython.org/
wxPython] program that provides a simple GUI.

## (Old) updates

**22 Jun 2014**:  I don't use this meter or software anymore, but other
people apparently still do, so I'll leave it on Google Code.  I
deprecated the files in the Downloads area and moved things to the
Mercurial repository.  If you want to get the files, install Mercurial
on your system and use the command given under the Source link at the
top of this page.

**17 Apr 2012**:  A user named J. Muczynski mentioned in an email
that the following changes were needed for use with python 3.1:

  * add () for the print statements
  * remove ord() calls because the code is using integers, not
    characters
  * use PySerial version 2.6 when using Python 3.1

**8 Sep 2011**:  I've included a PNG file of some plotted data; the
measurement was the thermocouple temperature of our GE kitchen oven.
This oven was installed with our house, which was built in 1971.
Interestingly, it is identical to the oven my mother had installed in
a house my parents built in 1970; my wife has never seen another oven
like it and wouldn't trade it for any other oven.

**9 Mar 2010**:  a user named chursch submitted a file with some
changes to make it easier to use on Linux.  This is the file
rs22812_linux.py in the zip file.
