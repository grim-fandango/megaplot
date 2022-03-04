MEGAPLOT

This MEGA65 program runs from BASIC and adds a text mode plot feature, 
similar to that found on the ZX81, so that users can remain in text mode and draw
graphics without having to have a raster screen split.  Text and graphics are easily
mixed - CURSOR, PRINT and other screen text commands can all be used alongside a 
160x50 resolution plot area.  

MEGAPLOT uses the PETSCI 'Battenburg' characters to provide each characters space 
with a 4-pixel plot area.

USAGE

Load the PRG - it sits at the top of BASIC at $7E00.  Switch to BANK 0 first to 
make it visible to BASIC.

The format of the command is:

SYS $FE00,X,Y,C 

..where X and Y are the co-ordinates of the point to plot where X is between 0-159 
in 80 column mode and 0-79 in 40 column mode.  Y is between 0-49 in both modes.

C is the index of the colour that you want to plot, i.e. 0=black, 1=white, 3=red 
etc.

Overplotting an existing point will not clear it, i.e. there is no XOR feature.  The 
point will be plotted again in the new colour specified.