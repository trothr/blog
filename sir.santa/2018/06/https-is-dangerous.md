# HTTPS is Dangerous

Lunduke says HTTPS is dangerous and Lawrence takes issue.

## HTTPS is Dangerous

Bryan Lunduke says HTTPS is Dangerous.

https://www.youtube.com/watch?v=ZmlQoeEycPc

I like Lunduke.
His delivery is a little unpolished, but casual.
He's also too apologetic. AAAaaannnddd... he's a click-bait master.
But he's usually on-point in one way or another.
Plus there's no accounting for taste; I like him.

## HTTPS is Good Stuff

Tom Lawrence really reacted to Lunduke's video.

https://www.youtube.com/watch?v=VCvyIB4L-E8

Interestingly, Lawrence spends a lot of time on "Extended Random",
making it sound like he and Lunduke are in violent agreement on something.

Lawrence missed the gem in Lunduke's rant.

## What Problem are we Trying to Solve?

The problem with HTTPS is that people see it as the fix for all of our
internet security woes. That, or they recognize the challenge is way
bigger but see HTTPS as the cornerstone.

## Lunduke Nails Jell-o

If builders built buildings the way programmers write programs,
then the first woodpecker to come along would knock down the whole
of human development.

The problem is inflexible and centralized infrastructure.
Contrast PKI infrastructure with the original design of the internet.
In the begining, the internet was designed to continue operating
even while in tatters. It came from the height of the Cold War.
US engineers were tasked with creating a network that could survive
a nuclear strike.

Bryan kinda danced around this point. Not sure he actually saw it.
Everything else he said hinted at it. Dependence on HTTPS and PKI
renders a lot of essential underpinings non-starters. THAT sucks.

## HSTS is More Dangerous

I would have agreed that HTTPS is dangerous,
like guns and cars and residential electrification are dangerous.
Never thought about it until HSTS.

First site I noticed the new behaviour was OpenSSL.org.
I was running some automation which fetches sources and re-builds
my system. This automation starts with an embryonic trust store.
It uses HTTP rather than HTTPS and verifies the sources apart from
PKI infrastructure. It confirms that the sources are valid using
PGP keys, if possible, and not using the keys and certificates
which make up the HTTPS world.

What I was was this: If I connected to OpenSSL.org via HTTP,
I'd get a 302 re-direct to the same URL via HTTPS. That's ironic.
I can't get SSL until I have working SSL. Thought it was maybe
something stupid in the configuration of their web site.
Turned out to be a new standard and they were the first site
(that I happened to hit) conforming to that new standard.
The new standard is HSTS.

But ... isn't that ironic? ... and ... doesn't it bother you
that one can't fetch the latest SSL unless you already have
a working SSL stack? Also, you'll now get an error if your
trust store is out of date (or simply incomplete).

## No Silver Bullet

I was talking with my wife this morning and realized that
some members of our family are still looking for silver bullets.
It's human nature: we want to find a thing which will fix a certain
problem. We're willing to put all kinds of effort behind that thing.
But relief is usually only found in a multi-faceted approach.

There's only one situation in life where One True Way applies.
This ain't it.

In every area of life, there's just no blue pill to make you forget,
put you back into the pod, and leave you in mind numbing bliss.
There's no silver bullet to slay the enemy, make and end of our problems.
(Corporate executives *really* like the idea. But it's a fantasy.)

As a data security professional, I hate the phrase "security is
a process", but it's true. You can't button-up and assume that's
the end of the effort. Lots of security people sleep better with HSTS.
I can't force them to take the red pill. Life would then be difficult
all over again.

So today ... one guy with an audience challenges HTTPS
and the rest of us react knee-jerk. Slow it down. Think it through.
The man has a point.



