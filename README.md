# Programming the ATTINY85
The ATTINY85 is a great processor for when you need a simple, small, arduino-friendly form factor.  

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

