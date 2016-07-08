My arduino clone.

##How to put code on the 328PB
1. Flash the U2:
  Running the first command was not enough for me. It may be that the fuses need to be set before flash can be written
  1. ```sudo avrdude -p m16u2 -c usbtiny -U flash:w:~/.arduino15/packages/arduino/hardware/avr/1.6.11/firmwares/atmegaxxu2/arduino-usbserial/Arduino-usbserial-atmega16u2-Uno-Rev3.hex -U lfuse:w:0xFF:m -U hfuse:w:0xD9:m -U efuse:w:0xF4:m -U lock:w:0x0F:m -v```
  2. ```sudo avrdude -p m16u2 -c usbtiny -U flash:w:/home/paul/.arduino15/packages/arduino/hardware/avr/1.6.11/firmwares/atmegaxxu2/arduino-usbserial/Arduino-usbserial-atmega16u2-Uno-Rev3.hex```

2. As of right now, the 328pb is not supported by avrdude. To fix this, put [this](https://savannah.nongnu.org/bugs/?48237) snippet in your `/etc/avrdude.conf` file. there is a copy of the fixed file this repo. If you trust me, run `sudo cp avrdude.conf /etc/avrdude.conf` in the root of this repo.


##TODO
#### Schematic
* ~~Make schematic symbol for ESD protection~~
* ~~Place 5v regulator + caps~~
* ~~Place barel jack~~
* ~~Place 22res on D+-~~
* ~~Update 328P to 328PB~~
* ~~Create fp for bus switch~~
* ~~Separate Tn and Ram/bus switch power off of 3.3V rail~~
* ~~Add second tiny~~

#### BOM
* ~~Fix part numbers~~
* ~~Fix Datasheets~~
* ~~Find passives~~
