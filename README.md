# Programming the ATTINY85
The ATTINY85 is a great processor for when you need a simple, small, arduino-friendly form factor.  

## Differences from Uno
There is no "software serial" support, so you don't get the serial monitor.  Because of this, sometimes it's better to develop and debug on an Uno, then transfer your code to the Tiny.

Memory is constrained...you only get 8k flash for program space (as opposed to 32k on the Uno, and there's only 512 BYTES of RAM (instead of 2kbytes), so your program needs to be small.

## Pins
The TINY85 comes in a DIP-8 package  (DIP == Dual Inline Package).  DIP packages have a notch at the top, and are typically numbered with 1 on the top-left, running down the left side, and then switching over to the right and back up to the top right.   This means for the tiny, the DIP pin numbers are as such:
```
   +-\/-+
  1|    |8  
  2|    |7  
  3|    |6  
  4|    |5  
   +----+
```

