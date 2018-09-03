# Offsite Lives!

After some time flying without a net, we have offsite backup again.
Here's the story.

## Original Offsite

Our first offsite backup system was built from surplus.

Surplus is good.
Excellent gear is often available as surplus,
having served a particular lifecycle role and now replaced with better,
or at least newer, other hardware. The old stuff probably works fine and
usually goes for cheap, even free. Surplus is also typically free from
intrusions like AMT (see Links section).

With computing hardware, the demands of ever faster processing and
graphics overshadow the simpler requirements of point-of-presence
or simple data handling. So we took a spare PC and installed Linux-i386
with a couple of VPN methods in place for reachability. Cheap hardware
but ample for the task.

Our original offsite unit resided with a family member in another town.
But then the unit needed manual attention.
And then the family member relocated.
Between those two things, the machine came back to headquarters.
And then an OS upgrade went sideways.

That particular unit is running again (thanks to Alpine Linux),
but is so physically big as to be annoying. This is 2018 after all!
When it came time to re-deploy, we just could not install the beast
in its would-be remote home.

## Raspberry Pi to the Rescue

The Raspberry Pi is the new hobbyist hotness.

In conversation between the double-E and me, we talked about options.
What should we do for better offsite service? Clearly we needed low
maintenance (because it'd be kinda hard to get to), minimal intrusion
(to whoever would let us park it with them), quiet (few moving parts,
e.g., no fans), but flexible for home-spun configuration.

Raspberry Pi came to mind right away as the likely host platform.
I was thinking to build an *enclosure* with the RPi, some number of
external drives connected via USB, collected power supplies (and a
common power plug for sanity). The plan included disks which used their
own power so to avoid loading up the phantom power on the RPi USB ports.

## What Actually Happened

The enclosure idea kinda faded.
Otherwise, the project unfolded mostly as envisioned.

We got three RPis, one for this project and two more for experimentation,
and a 3TB *powered* USB external disk. The disk, with its own enclosure,
is physically large enough that I attached the RPi to its side using velcro.
That left two power supllies and a USB cable dangling, easily remedied
with zip ties and adhesive strain reliefs. Not fully "enclosed",
but reasonably contained.

After tinkering with the OS and defining a couple dozen logical
volumes, the new unit was ready to ship to another offsite relative.
"Just plug it in.", and it worked.

Success! Yay!

## Operating System

The hardware was easy once decided on.
The OS was another matter.

Raspbian won in the end.
We flashed Raspbian Stretch from 2018-June-27 onto an 8G micro SD card.
That booted straight away, auto-logged-on user `pi` with the Raspbian
desktop, and a half dozen configuration prompts. It was ready-to-run
less than 10 minutes after first boot. Nice!

I also tried OpenSUSE for ARM, Leap 42.3 with XFCE. It's the community
branch of an enterprise-grade distribution. OpenSUSE reportedly could be
installed (configured) via SSH, and we were running headless at first.
But we could not get the initial bootstrap rolling.

Raspbian turned out to be more oriented to the hobbyist (than OpenSUSE,
which I use heavily elsewhere), and yet a solid system. Since wrapping-up
the offsite project, I've been tinkering with one of the other RPis.
It has an appeal drawing me away from any fixation on XFCE (which itself
is a great alternative to the bloat of KDE or Gnome).

## Networking

This particular offsite location has WiFi access that we knew.
Easy enough to get that SSID and PSK punched in.

Wired ethernet would be preferred, but it's hard to fight the convenience
of wireless. Given the intended use of this thing as a backup storage server,
vulnerabilities related to radio are acceptably small, making placement
or relocation of the unit easier for offsite family is a win.

Now it's a matter of reviewing `cron` jobs to be sure we push
content to the remote server regularly. That's what backup is all about.

## Links

One reason for using surplus, no AMT.

https://en.wikipedia.org/wiki/Intel_Active_Management_Technology

I mention AMT knowing that the RaspberryPi is based on a Broadcom.


