# pmeter
RF power meter (AD8307 based) -- software to run on Raspberry Pi.

The power meter has a separate module with the sensor, and the plan is
to use an ADS1115, attached to a Raspberry Pi pico by i2c to sense the
voltage emitted (which will be more or less an affine function of the
power applied at the sensor. According to the [Analog Devices
datasheet](http://www.analog.com/media/en/technical-documentation/data-sheets/AD8307.pdf)
it should be possible to get decent performance from -75dBm to +17dBm
in the range from DC to 500MHz, but -70 to +10 dBm from DC to 150 MHz should
be achievable. There is a ADS1115 micropython library here: https://github.com/robert-hh/ads1x15

I want a controller housing with ports for two sensor heads. The sensor heads
will be built into aluminium diecast enclosure with RF connectors on one end and
a 4-wire cable to the controller unit: 1) power, 2) GND, 3) output voltage from
sensor, and 4) a voltage that signals which sensor head this is to the controller.

I want a raspberry pi pico with a wiznet 5500 ethernet controller, such that I
can use a REST interface to fetch readings if I like to. I also want an
interactive use. For interactive use I need to 1) be able to set the frequency
(calibrarion constants), offsets, and maybe the display units (from dBm to
Volts?). A rotary controller with a  button should be enough to step through
four modes: Channel A frequency, A offset, A units, B frequency, B offset, B
units. Then a display: Two lines of a 16x2 LCD display should in principle be
enough. Alternative: One 0.96 inch display for each channel (these are i2c). I
probably also should be able to display the ip-address of the controller (if
any).
