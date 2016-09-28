# The Ugolino
An Arduino compaible board based on the ATMEGA328PB that uses the secondary SPI
bus provided by the 328 to interface with 256k of SRAM. There are two aditional
AVRs on borad, both are ATTINY85 microcontrollers. The 85s share the SRAM with
the 328. The 85s' each have four GPIO pins broken out. In order to implement
this functionality, bus switches were used to multiplex the SPI bus and GPIO of
each 85.

An ATMEGA16u2 was used as a USB to serial tranceiver. Right now, support for the
328pb is limited, a patch for the pb is needed for avrdude, and the Arduino IDE
requires an extra board to be installed.

##Known Issues
* ~MISO and MOSI on the Tinys are labeled with respect to the host, where the
tiny is a slave.~(fixed)
* ~SS_328 is not connected to the SS line of the RAM.~ (fixed)
* The PCB does not yet reflect the changes marked fixed.
* Some footprint library dependencies are currently unavaliable but will be
corrected.

## How to put code on the 328PB

1. Flash the U2:
  Running the first command was not enough for me. It may be that the fuses need to be set before flash can be written
  1. ```sudo avrdude -p m16u2 -c usbtiny -U lfuse:w:0xFF:m -U hfuse:w:0xD9:m -U efuse:w:0xF4:m -U lock:w:0x0F:m -v```
  2. ```flash:w:/home/paul/.arduino15/packages/arduino/hardware/avr/1.6.11/firmwares/atmegaxxu2/arduino-usbserial/Arduino-usbserial-atmega16u2-Uno-Rev3.hex```

2. Right now, the 328pb is not supported by avrdude. To fix this, put
[this](https://savannah.nongnu.org/bugs/?48237) snippet in your
`/etc/avrdude.conf` file. A copy of the fixed file is included. If you trust
me, run `sudo cp avrdude.conf /etc/avrdude.conf` in the root of this repo.



The Ugolino was first created as an intern project while I was working at
[Thimble.io](http://thimble.io), and I have recieved permission to publish this
work publically.
