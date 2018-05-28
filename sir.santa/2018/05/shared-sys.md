# From read-only-root to Containers

 ... or "shared op sys woulda been better".

A long, long time ago (but I can still remember),
we had this idea for shared operating systems among virtual machines.
Idea nuthin! It was reality! It was beautiful. It was flawed.

The basic idea was sound, remains sound, and is sound for the current
trends in virtualization (containers versus full machines).
Here's some rambling about that.

## Remembering Read-Only Root

Mike MacIsaac posted on the LINUX-390 list (and the IBMVM list) ...

    I stumbled onto the first "Read-only root" paper that the guys
    from Nationwide basically wrote. While on the Redbooks website,
    I was surprised to be asked if I wanted to chat about it. I said yes,
    and tried to be respectful. Below is the chat text, which in the
    Turing Test, I would vote yes, that was a live sapien (perhaps I failed?).

"The guys from Nationwide" being Steve and me, but Michael plays down
his part.

The R/O root "Redpaper" is old.
I was surprised to see my name on it. Had forgotten.
Mike and Steve did most of the work. It was hard work and a hard recipe.
Later, Kyle Black joined Steve and Mike on a longer piece.

The point of Mike's post was speculating "a bot or not a bot?".
But the subject line, and the reason Mike was chatting with the rep
in the first place, was all about read-only root years ago and now today.

    I look back and now reflect - are Containers and Docker the new
    "read-only root"? Is mainframe playing catch-up 10 years later?
    Can we somehow lead?

Can we somehow lead? Why would we NOT lead? ("We" being z geeks.)

Containers work fine on "z" hardware.
It's possible that containers work *better* on z.
Someone please gather hard numbers and share them.
(If you can't measure it ...)

There is, however, a gap.
In all the hype surrounding containers, I don't hear any mention
of shared content, shared filesystems, shared disk space.

Shared disk makes sense in any environment.
Shared disk makes sense with containers too.

## Read-only shared disks

z/VM and its forerunners have done dramatic disk sharing for decades.
It's a story VMers know all too well, but people from other background
have probably never heard, and when they do hear they wonder what's the
point.

CMS is the default environment on z/VM. It is a single-user system.
Sort of. See on z/VM a user is a virtual machine and a virtual machine
is a user, so "users" running CMS each get their own personal computer
which is naturally a single-user system.

CMS depends wholly on the z/VM host and gets more out of that relationship
than other guest operating systems. You gotta realize that CMS is all-in.
Decades ago it relinquished the ability to run native (to function apart
from the hypervisor), so it depends wholly on the z/VM host. With CMS,
the operating system is shared by all users on any single z/VM instance.

CMS shares the boot disk (190) and at least one supplemental disk (19E).
All CMS users get the same 190 disk, the same 19E disk, the same 19D disk
and others. The norm on VM/CMS is to install products to disks which
will be shared ... always ... and read-only.

There's nothing magical about CMS that makes it better at the sharing
game than other operating systems. It's just committed.

## Read-only Linux root

Prior to 1998, there was no other virtualization than VM/ESA (and VM/XA,
VM/HPO, VM/SP, and VM/370 before it). VMers understood the value of
guest operating systems.

Unix appealed to many. There were several Unix implementations for S/370,
XA, and S/390 hardware over the years. Some were quite good and all ran
well on VM. Then came Linux and it had mindshare. Linas Vepstas was the
first to publicly port Linux to S/370. A talented team at IBM was doing
the same, but such projects just can't be outted too soon. (Been there,
done that, I get it, and it sucks for the rest of us that we don't know.)
Later, the IBM port did become public, and the rest is history.

Linux for S/390 was an obvious candidate for virtualization.
Whether UTS or AIX or Linux, a Unix-like system hosted by z/VM was a
"gotta have it!" idea. VMers wanted to demonstrate the power of the
VM/ESA hypervisor. Naturally, we wanted to implement some of the tricks
we had learned from VM over in Linux land.

"You can share the whole operating system across dozens, hundreds,
even thousands of Linux virtual machines. Isn't that cool?!?!?"

So we did Linux the way we had done CMS:
put the operating system on a common disk, share that disk
across all virtual machines using that particular release,
and arrange the needed hacks to cope with the read-only thing.

It didn't have to be the root. We just didn't know that at the time.

Forcing the Linux guys to use a read-only root was a mistake.
It's just too foreign. It bothered them. But we VMers didn't see
the alternative soon enough:

* share the OS, not the root itself

The Linux side never fully got the value of the shared operating system.
For example, instead of upgrading on all 500 guests, do the upgrade just
once and eventually reboot the guests to use the new release. But that's not
how they did it on discrete systems. That's not how they did it on VMware.

Most observers thought the VMers were simply trying to save space.
Hardly. Storage is cheap (and bandwidth is cheaper). The real savings
was in having set-in-stone consistency, absolute defence against changes
(e.g., by a hacker or rogue program), and guaranteed availability of
specific software releases and bundles.

## Virtualization Beyond the Mainframe

VMware came on the scene about two years before Linux for S/390.

As time went on, VMware got increasingly robust. It also caught the
attention of businesses needing to reign-in costs. (Remember the
mainframe versus distributed war? Remember how the mainframe detractors
got bitten by the hidden costs in their cheaper-but-many model?)

And then we got other hypervisors. Xen was popular. At first Xen
required a virtual-aware guest. It was "paravirtualization".
Purists were put off, and Windows was a non-starter. Later Xen learned
how to do full virtualization. The chips got better too. And faster.

As of this writing, we have lots of virtualization options.
I myself use KVM heavily. (And I warmed up to Xen and para-virt,
so I used it too for a while.) VMware continues, though is further
from the reach of hobbyists and academics.

The newcomers are not so new. They've grown up, gotten stable.
But there's still a long way to go. TO THIS DAY z/VM is more efficient,
more reliable, more scalable, and generally better than any other hypervisor.

The noobs have a lot to learn.

## Containers - Old is New

In the never-ending push for bigger, faster, cheaper, we gotta cut
overhead. There's no getting around the overhead imposed by a hypervisor.
(Barely noticable with z/VM, but a measurable cost with the others.)
Add to that the inherent overhead of running multiple kernels,
one per virtual machine, many fully-autonomous guests.

Enter containers.

Wait, wait ... too fast ... first let's talk about `chroot`.
I used to say "chroot is the closest thing Unix has to a virtual macine."
That was then.

`chroot` first appeared in V7 Unix as far back as 1979, and in Berkeley
Unix two or three years later. It's awesome! Great for development,
teriffic for testing, even a boon to security. Everything in the `chroot`
padded cell is isolated from the parent environment. (Though it uses
the same kernel and has the same network presence.)

FreeBSD took things up a notch.
Around Y2K, the FreeBSD people gave us the "jail" concept.
Others followed.

A FreeBSD jail is chroot on steroids (even before Sun made that claim).
The environment in the jail is not only isolated to the `chroot`
sub-hierarchy but also has its own network presence and cannot "see"
things in the parent. (Things which are visible to an ordinary `chroot`.)

Linux followed suit.

Linux being Linux, and borrowing the best ideas from other systems,
picked up on the jail concept. Dunno if "jail" has some negative
connotation or if they just wanted to eschew all things BSD,
but the capability was called "containers" in Linux. Same concept.

The advantage of containers over full virtualization is the shared kernel.
The downside of containers versus full virtualization is the shared kernel.

When you share the kernel, you get more resource savings. That's good!
When you share the kernel, you're stuck on the same kernel (if it matters,
and sometimes it *does* matter).

## Shared Operating System

Containers are the new hotness, the current shiny thing. What does
all of this say about read-only root? (More accurately, what does
all of this say about shared op sys hierarchy, but you get the idea.)
Only that shared operating system hierarchies are an under-valued idea.

A container must share the host kernel. Full stop.
Within the container, the userland programs and libraries and files
can be anything that works with the host kernel. The container can have
as much or as little as you need. (SUSE has been pushing JeOS, Just
Enough Operating System to get the job done. Others too; common sense.)

A container can get its stuff from:

* a sub-directory of the host
* a dedicated disk or partition
* a mixture including shared content and R/O OS
* NFS or SMB
* even removable media

In the VM world, we learned it's better to share the core OS than to
necessarily share the root filesystem. `/bin`, `/lib`, `/usr` are what
need to be pinned down and made replaceable. This is just as true for
containers as it is for virtual machines.

## Point N Shoot

If containers are all about rapid deployment,
what could be faster than leveraging an existing copy of what you need?
Rather than copy or link or arrange, simply point the container at
a ready-to-run static copy of the core operating system and run it.

Don't stop there. Do the apps too. Remember CMS puts packages each
on their own disk. Neat trick. Very handy. So add in selected disks
with the packages needed. Core OS, supplemental packages, requisite
private R/W space, and go!

Mike asked, "Can we somehow lead?". Heck yeah!


