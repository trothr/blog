# Somebody please Make it Stop

Somebody please make it stop!

This is about SystemD. <br/>
I would very much like to *not* hate SystemD,
and it's not so much that I dislike SystemD as that it forces out alternatives.

## SystemD

If it were just about INIT replacement it might not be so bad.
It would involve a learning curve, but I'm okay with that.

Call it SD for shorthand in this post.

The evil of SD is that it assumes more and more system tasks.
The damage there is two-fold: For one thing, it renders otherwise
perfectly acceptable packages redundant. But worse, it clearly
violates the Unix rule of "do one thing and do it well".
Whether you consider SD as "doing it well" or not,
you really cannot argue that it is doing more (WAY more) than one thing.

What was wrong with SYSLOG? (One of the victims.)
Thankfully, there are still some places where "normal" SYSLOG
implementations still survive.

## Spreading like Cancer

In the medical world, something which spreads as widely
and as rapidly as SD looks a lot like the dreaded C word: cancer.

Observe the disease and learn.
Growth of unhealthy cells outpaces healthy, robbing the healthy
of vital nutrients. Sounds a lot like SD.

What is it that feeds cancer?
What is it that feeds SD?

## Whither SUDO

And now there's this:

https://news.itsfoss.com/systemd-run0/

Seriously? <br/>
This comes back around to one of my main objections:
SD breaks interoperability. SUDO is and has been the primary way
of securely performing privileged or sensitive operations.
It has the controls needed for controlling scope. It logs by default.
It can even drive keystroke logging. (Talk about the ultimate audit.)
But no. It's not good enough for the authors of SD.

## Against the Current

I'm fighting for non-SystemD environments as much as I can.
Obviously too many people *like* SystemD.
Maybe that's just an outgrowth of the SysV Init haters.
(I agree that SysV Init is ugly, but I like it, and it works.)

There must be a large number of Linux users who like SD.
Many Linux users in my circle simply accept it as a given.
A few truly object to it (but lack the critical mass to fight it).

I have tried Devuan, a Debian spin without SD.
But it's a small subset. I also am less familiar with Debian/Devuan
than with other Linux distros. (And I was never fond of Debian INIT.)

This isn't supposed to be a bitch-and-moan session.
I'd like to know where to turn.
BSD?

<!--                                                                 -->

2024-07-17 Wednesday


