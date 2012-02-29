(c) Copyright 2008, 2011, Steven T. Snyder, All Rights Reserved

====================================
  Tenica P-101 Disassembly Project
====================================

Project folders:
/util -- Utility scripts and software
/dis  -- The raw disassembly code, and the code I have commented
/ref  -- Reference material such as datasheets and code manuals
/bin  -- Binary PROM dump

The binary program data was read from the the PROM using a Moates BURN1.

I don't remember which software was used to create the disassembly, but it was
either OhsonSoft's Z80 Simulator IDE [1] or the freely available dZ80 [2]

[1] - http://www.oshonsoft.com/z80.html
[2] - http://www.inkland.org.uk/dz80/

========================
       Background
========================

There are a few Z80 dissassemblers available including Z80 Simulator IDE
(Commercial), and dZ80 (Freeware).

The Tenica P101 is a scrolling LED marquee marketed in the early 90′s. It
consists of a Z80 microcontroller running a massive bank of multiplexers to
control a 95×7 LED array made up of nineteen 5×7 LED “tiles”. It is capable
of displaying a-z, A-Z, 0-9, and various special characters. A series of
character lines are programmed in by the user and are then displayed in a loop.
The style of animation for each line and the transition between lines is
programmable by the user.

I found a couple of these units in storage and pulled them out to see if I
could get them to function. One started up and displayed “CONTENTS LOST”, but
after programming some lines into it the device seemed to be working properly.
After being shut off and turned back on, it would again display the error
message. I figured it must be using volatile memory and the onboard battery has
gone dead (remember, these things are over 10 years old by now!). The backup
battery turned out to be a pack of four 1.2V NiCad batteries. I replaced them
in an attempt to fix the memory loss problem, but this didn’t work.

While tracing the power circuit to find another solution, I noticed that the
PROM next to the microcontroller looked an awful lot like the ones used in
the GM fuel-injection engine computers I’m familiar with. This certainly
wouldn’t help me with the memory problem, but I figured I could make some use
of the display for some other project if I could figure out how it works. Sure
enough, my Moates.net PROM reader/writer was able to extract the program data
from the PROM. I successfully disassembled the binary PROM data using one of
the Z80 disassemblers available online (see the links above) and began
a project to comment and understand the code. So far I have determined the
storage format for characters as well as the startup routine and some of the
display routine.

