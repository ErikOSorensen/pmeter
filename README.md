# pmeter
RF power meter (AD8307 based) -- software to run on Raspberry Pi.

The power meter has a separate module with the sensor, and the plan is
to use an ADS1115, attached to a Raspberry Pi by i2c to sense the
voltage emitted (which will be more or less an affine function of the
power applied at the sensor. According to the [Analog Devices
datasheet](http://www.analog.com/media/en/technical-documentation/data-sheets/AD8307.pdf)
it should be possible to get decent performance from -75dBm to +17dBm
in the range from DC to 500MHz.

The reason I went for a Raspberry Pi for controlling the power meter
is that I want to attach the power meter to my LAN, and allow for
reading the power as part of automating testing procedures. But I also
want to be able to use it interactively. For this I attach two more
units to the Pi: 1) 7-segment LED displays for the power level (and
calibration frequency) and 2) A rotary encoder to interactively set
the calibration frequency (the intercept term of the AD8307 output
changes with frequency). In order to control the LED displays,
I want to use the [MAX7221 serial interface display driver](https://www.maximintegrated.com/en/products/power/display-power-control/MAX7221.html)).