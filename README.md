# ATTINY85 Guide
The ATTINY85 is a great processor for when you need a simple, small, arduino-friendly form factor.  It'll run on 5v, or a 3.3v coin cell, or a 9v battery...so powering it is a breeze! 

## Differences from Uno
There is no "software serial" support, so you don't get the serial monitor.  Because of this, sometimes it's better to develop and debug on an Uno, then transfer your code to the Tiny.

Memory is constrained...you only get 8k flash for program space (as opposed to 32k on the Uno, and there's only 512 BYTES of RAM (instead of 2kbytes), so your program needs to be small.

## Pins
The TINY85 comes in a DIP-8 package  (DIP == Dual Inline Package).  DIP packages have a notch at the top, and are typically numbered with 1 on the top-left, running down the left side, and then switching over to the right and back up to the top right.   This means for the tiny, the physical DIP pin numbers are as such:
```
      +-\/-+
     1|    |8  VCC
     2|    |7  
     3|    |6  
GND  4|    |5  
      +----+
```
Note that pin 8 is power (top right) and pin 4 is ground (bottom left).  

All 6 of the other pins can be Digial I/O pins.  But, here's the tricky bit:  their numbering in arduino doesn't match the physical pin number!!!  Their layout is shown below:
```
        +-\/-+
(D 5)  1|    |8  VCC
(D 4)  2|    |7  (D 2)
(D 3)  3|    |6  (D 1)
  GND  4|    |5  (D 0)
        +----+
```
Meaning if you refer to pin 5 in arduino, you are really talking about the pin that's top-left on the chip. 

In addition, 4 of these pins can be configured as Analog inputs.  Once again, their numbering is confusing....not only doesn't it match the physical pin number, it also doesn't match the digital pin number!!!  Here are the analog pins:
```
        +-\/-+
(A0)  1|    |8  VCC
(A3)  2|    |7  (A1)
(A2)  3|    |6  
 GND  4|    |5  
       +----+
```
## Programming Setup
The first thing you need to do is to add the tiny board manager package under "preferences".  Paste the following text into the "Additional Boards Managers URLS" field...if you've got a bunch, you'll need to add a comma separator.
```
https://raw.githubusercontent.com/damellis/attiny/ide-1.6.x-boards-manager/package_damellis_attiny_index.json
```

Next, install the board manager package by selecting:  "Tools->Board->Boards Manager" and type attiny.  It should find the 
tiny package by David Mellis.

We now need to setup the UNO as a programmer.  Download the built-in example #11 (ArduinoISP) and program it onto your UNO.

Next, we need to hook up the tiny to the Uno for programming.  Here are the connections:

| tiny physical pin | arduino pin |
|-----------|-------------|
| 1 | 10 |
| 4 | GND |
| 5 | 11 |
| 6 | 12 |
| 7 | 13 |
| 8 | +5v |

You'll also want a 10 uF cap running across the arduino's reset pin to gnd.

Now you need to burn in the bootloader to the tiny.  Change your board settings as follows:
```
Board -> ATtiny25/24/85
Processor -> ATtiny85
Clock -> Internal 8 MHz
Programmer -> Arduino as ISP
```

Then click "burn bootloader".  This should only need to be done once per chip....and now your tiny is ready for sketches!

From this point on, you can download sketches like you normally would....just make sure the board settings match above.
