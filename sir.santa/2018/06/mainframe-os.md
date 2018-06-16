# Mainframe Operating Systems

I was sending a barrage of email to a friend
to prep him for an up-coming conference that I will miss.
One thought led to another, and then the following rambing gurgled out.

## Current Mainframe Operating Systems

For reference ... operating systems which can run on z/VM ...

* z/VM (unlimited nesting of the hypervisor "CP")
* CMS (comes with the z/VM product), presents the "Ready;" prompt
you see before you boot Linux at Marist
* z/OS, formerly OS/390, formerly MVS, originally OS/360
* z/VSE, formerly DOS or DOS/VS, with a subsystem called "POWER"
(not related to the chip, and much older)
* z/TPF, think airline reservation systems world-wide, banking too
* UTS, Unix, and *not* the "Unix Systems Services" (USS) subsystem
of z/OS, long before Linux or even AIX
* Linux

I am guessing that UTS is still around. Would love to get access
to a UTS system. It's a *great* Unix, AT&T base,
originally from Amdahl.
Long story.

## Historical Mainframe Operating Systems

The following are defunct, but might fill-in gaps ...

* AIX/370, a port of AIX for the PS/2 to S/370 (24-bit*) and S/390
(31-bit*) hardware
* AIX/ESA, a fresh port of AIX (not related to PS/2) to S/390 hardware
(no S/390, 24-bit*)
* Solaris (Neale will know, but prolly a painful topic for him,
or maybe just annoying)
* IX/370, a fiasco, attempt by IBM to compete with UTS, early 1980s

I notice those are all Unix variants. Thought there were some non-Unix
too but can't recall any now.

IBM failed time and again to product a decent Unix for the mainframe.
USS on z/OS is usable, but speaks EBCDIC (!) and is more akin to
CYGWIN or WSL, a POSIX layer on something else. AIX was better.
AIX/ESA was excellent, but flopped in the market. Amdahl got it right
and were more than a decade ahead.

There's also Wikipedia ...

    https://en.wikipedia.org/wiki/History_of_IBM_mainframe_operating_systems

\*24-bit and 31-bit are addressing modes. Integers on all mainframes
since the 1960s have been 32-bit, until they were alternatively 64-bit.

This is a stream-of-consciousness dump. Use it as you will.
I hope it helps.

-- R; \<\>\<


