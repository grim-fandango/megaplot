MEGAPLOT
========

This MEGA65 program runs from BASIC and adds text mode plot and line drawing features, 
similar to that found on the ZX81, so that users can remain in text mode and draw
graphics without having to have a raster screen split.  Text and graphics are easily
mixed - PRINT, CURSOR and other screen text commands can all be used alongside a 
160x50 resolution plot area.  

MEGAPLOT uses the PETSCII 'Battenburg' characters to provide each characters space 
with a 4-pixel plot area.

USAGE
-----

In your own programs, put the MEGAPLOT.PRG file on your disk and initialise it using: 

    10 BANK 0:BLOAD "MEGAPLOT"

MEGAPLOT will load at the top of BASIC at $7E00.  The switch to BANK 0 to is required  
to make it visible to BASIC.

The format of the command is:

SYS $7E00,X,Y,C 

...where X and Y are the co-ordinates of the point to plot where X is between 0-159 
in 80 column mode and 0-79 in 40 column mode.  Y is between 0-49 in both modes.

C is the index of the colour that you want to plot, i.e. 0=black, 1=white, 3=red 
etc.

Overplotting an existing point will not clear it, i.e. there is no XOR feature.  The 
point will be plotted again in the new colour specified.

Negative values and values over 255 will raise an ILLEGAL QUANTITY error.

Available calls are:

- __init_and_plot__:
  - SYS $7E00,X,Y,C
  - a = x-coord, x = y-coord, y = colour
  - (equivalent to original program's behaviour)
- __init__:
  - SYS $7E03
  - a 'one-time' init, so that future draw calls don't need to repeatedly init
- __plot__:
  - SYS $7E06,X,Y,C
  - a = x-coord, x = y-coord, y = colour
- __line__:
  - SYS $7E09,X1,Y1,X2,Y2
  - a = x1, x = y1, y = x2, z = y2
- __set_colour__:
  - SYS $7E0C,C
  - a = colour
  - (use this call to set the colour of your next line)

PI DEMO
-------

The Pi demo has an interesting heritage.  It was originally written by W TAGG (we think
this is Bill Tagg, Head of Maths from Hatfield School in the UK) in November 1979, then 
converted to an obscure teletext-compatible computer called the ABC800 in November 
1980 by A Wallis.  In the late 70s and early 80s, Brighton Polytechnic were running
an experimental telesoftware service on the UK teletext services CEEFAX and ORACLE.
Telesoftware is a method of distributing software to users over broadcast teletext.
Those early Brighton experiments used the ABC800 computer to receive off-air 
broadcasts containing software.

On 22nd February 1981, someone was recording the Charlton Heston film 'Khartoum' 
on BBC1.  The tape survived the intervening 40 years, and the teletext was recovered 
from that Betamax recording by sampling the video and processing the teletext data dots
recorded alongside the film.  The teletext pages, including telesoftware, can be 
reconstructed from these data, and this program can be seen in its original teletext
format here:  https://twitter.com/grim_fandango/status/1496234608656007171

The telesoftware was extracted from the teletext page and converted to ASCII.  From 
here it was adapted to the MEGA65 using MEGAPLOT to draw the required graphics.

4x SYMMETRY DEMO
----------------

This was adapted from the book 'The Art of Programming the 1k ZX81' by M James and 
M. Gee.

SINE OF THE TIMES DEMO
----------------------

This is something I knocked up in 10 minutes.

PETLINE
-------
The 'petline.prg' file features several examples that make use of the line drawing
capabilities of MEGAPLOT.
