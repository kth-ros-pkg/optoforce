# Optoforce Driver
The current version of the library is built on the top of the official library of the manufacturer (see [here](http://optoforce.com/support/))

The access to the devices is done in 2 steps:

* all connected devices are first found.
* any connected devices an then be accessed to get the forces measured 

The class OptoforceApplication is proposed for applications looking for a basic recording of forces.

Examples of uses can be found in the directory [examples](examples).

Main developers so far: Asier Fernandez, Anthony Remazeilles


# Installation Instructions

## 1. Linux
- Add privileges for the user to "dialout" group
```bash
$ sudo usermod -a -G group_name user_name
```
- Change permission to usb port.
  * Create next file
```bash
$ sudo gedit /etc/udev/rules.d/72-OptoForce.rules
```
  * Copy his content
```bash
ATTR{idVendor}=="04d8", ATTR{idProduct}=="000a", MODE="0666", GROUP="dialout"
```

# Gnuplot Manual

- Set column separator

        set datafile separator ";"

- Set ranges
```bash
set autoscale                          # let gnuplot determine ranges (default)
set xrange [1:10]
set yrange [1:100]
```

- Set labels
```bash
set title 'Measured Force'                       # plot title
set xlabel 'Time'                              # x-axis label
set ylabel 'Force'                          # y-axis label
```

- Plot data. Only 1 Force axis
```bash
plot 'filename.csv' using 1:2 with lines
```

- Plot data. 3 Force axis
```bash
plot 'filename.csv' using 1:2 with lines title "Fx", 'filename.csv' using 1:3 with lines title "Fz", 'filename.csv' using 1:4 with lines title "Fz" 
```

# To do
Most of the aspects to improve are defined in the code using the flag todo.
Othe relevant aspect to consider:

* Miguel started a driver in which a dirct access to the devices was done through boost (ie without the optofrce driver)
* An optoforce library has been developed [there](https://github.com/ethz-asl/liboptoforce)
* Optoforce developed a ROS node that should be tested as well (see [here](http://optoforce.com/support/)).
