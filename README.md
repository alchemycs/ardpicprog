
Arduino-based PIC programmer
============================

This distribution contains an Arduino-based solution for programming
PIC microcontrollers from Microchip Technology Inc, such as the
PIC16F628A and friends.  The solution has three parts:

* Circuit that is built on one or more prototyping shields to interface
  to the PIC and provide the 13V programming voltage.
* Sketch called ProgramPIC that is loaded into an Arduino to directly
  interface with the PIC during programming.  The sketch implements a
  simple serial protocol for interfacing with the host.
* Host program called ardpicprog; a drop-in replacement for
  [picprog](http://hyvatti.iki.fi/~jaakko/pic/picprog.html) that
  implements the serial protocol and controls the PIC programming
  process on the computer side.

See the [documentation](http://rweather.github.com/ardpicprog/)
for more information on the project.

## Obtaining ardpicprog

The sources for `ardpicprog` are available from the project
[git repository](https://github.com/rweather/ardpicprog).  Then read the
[installation instructions](http://rweather.github.com/ardpicprog/installation.html).

## Support for 16F877 added by [@Alchemycs](https://github.com/alchemycs/ardpicprog)
Support added for 16F877 with info from http://ww1.microchip.com/downloads/en/DeviceDoc/39025f.pdf and some
poking around in [picprog](http://hyvatti.iki.fi/~jaakko/pic/picprog.html)

The 16F877 is a 40pin device so you must use the ICSP to program it

**WARNING** The power supplied for Vdd by pin D2 doesn't supply enough current for the 16F877 to work. 
I found simply not using the Vdd supplied by the `ardpicprog` and using a bench supply worked fine if you
use the following sequence:

* Power off all supplies and unplug the `ardpicprog` from your computer
* Connect the `ardpicprog` ICSP to the 16F877
* Ensure the `ardpicprog` and bench supply to the 16F877 share common GND
* Apply bench power to the 16F877
* Apply power/plugin the `ardpicprog` to your computer
* Program your 16F877
* Remove power from the `ardpicprog`
* Remove power from the bench supply to the 16F877
* Remove the ICSP connection from the 16F877

Once you apply power back to your 16F877 (make sure you have your ~MCLR reset circuit wired correctly) all should be fine.


## Contact

For more information on Ardpicprog, to report bugs, or to suggest
improvements, please contact the author Rhys Weatherley via
[email](mailto:rhys.weatherley@gmail.com).  Patches to support new
device types are very welcome.
