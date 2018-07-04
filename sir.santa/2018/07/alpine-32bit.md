# Alpine - Thank You for Thirty Two

Alpine Linux is still available for 32-bit I386.

## Linux and 32-bit Support

I run a lot of surplus hardware.
Systems which don't need contemporary processor speed
or greater than 4G of memory don't strictly need a 64-bit CPU.
And they work. And they're cheap.

My current favorite Linux distribution is OpenSUSE Leap.
I'm running it on my primary desktop and on my work laptop.
I'm also running Leap on the virtualization server.
Leap is great!

There are two things I dislike about Leap.
First is SystemD, which gets in the way of so many things.
But SystemD is not a show stopper. I can still *use* the system.
The other dislike is lack of 32-bit support. I can't blame SUSE.
Their focus is business Linux, enterprise systems,
the latest and greatest hardware (S390X, ARM, POWER).
But it's frustrating from where I sit.

One particular surplus system is an aging machine that I got
from a family member. It's current enough to have USB and SATA,
but not a 64-bit CPU. It serves as a sometime-remote backup server.
The OS was out of maintenance, its repositories no longer available.
When I tried to manually drop-in bits and pieces from NORD,
I rendered it mostly inoperative. (The OS in question had SystemD.
Gee, what a surprise.)

So this old beater needed a new OS.
But clearly I could not use Leap.
What to do?

## Along Comes Alpine

There are many excellent Linux distributions,
some which are focused on small systems, embedded systems,
or edge cases or experimentation. Alpine is an up-and-coming
distribution designed for tight environments. It leans heavily on
BusyBox and uses Musl libc. 

Alpine runs on several contemporary hardware platforms
(S390X, ARM, POWER). Alpine also runs on I386. Yay!
I wondered if Alpine would fill the need, burned a CD and booted
the installer. Worked like a charm!

A big THANK YOU to the Alpine team for continuing to ship
a viable 32-bit operating system.

The machine is humming along again.
Now it's just a matter of working around BusyBox quirks
and avoiding executables which can't live in a Musl world.
No problem.

## Why not NORD?

It's fair to ask why I didn't install my own home-grown OS.
The reason is easy: NORD lacks good LVM support. NORD mostly lacks
UDEV support. (The MD driver is part of the kernel and the LVM tools
are trivial. But we'd need UDEV to get logical volumes to "show up"
correctly.)


