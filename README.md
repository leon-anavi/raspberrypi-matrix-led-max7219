# raspberrypi-matrix-led-max7219
Sample applications for LED 8x16 Matrix Module For Raspberry Pi based on MAX7219 driving two LED 8x8 modules (8x16)

# Hardware

Tested with "Led Matrix LED Red Matrix Module Driver Board Lattice Led For Raspberry Pi" from icstation.com:
http://www.icstation.com/matrix-matrix-module-driver-board-lattice-raspberry-p-7274.html

# Installation

* Plug LED red matrix module on Raspberrry Pi and turn on the boards
* Enable SPI, easiest way on Raspbian is using raspi-config: https://www.raspberrypi.org/documentation/configuration/raspi-config.md
* Verify that SPI has been enabled
* Ensure that the SPI kernel driver is enabled:
```
$ dmesg | grep spi
[    3.769841] bcm2708_spi bcm2708_spi.0: master is unqueued, this is deprecated
[    3.793364] bcm2708_spi bcm2708_spi.0: SPI Controller at 0x20204000 (irq 80)
```
* Verify that devices are successfully installed in /dev:
```
$ ls -l /dev/spi*
crw------- 1 root root 153, 0 Jan  1  1970 /dev/spidev0.0
crw------- 1 root root 153, 1 Jan  1  1970 /dev/spidev0.1
```

#### Python

Follow the steps below to run the Python example:

* Install https://github.com/rm-hull/max7219
* Run Python script as root:
```
sudo python python/matrix-cpu.py
```

#### C

Follow the steps below to build and run the C example:

* Install C library for Broadcom BCM 2835 as used in Raspberry Pi: http://www.airspayce.com/mikem/bcm2835/
* Build and run the example:
```
cd c
make 
sudo ./led-max7219-text hello
```
