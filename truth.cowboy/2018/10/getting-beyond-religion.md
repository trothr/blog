# Getting Beyond Religion

I'm not religious.
I just love the Lord!

That's how the lyrics go.
As a Christian, one most would call Evangelical,
when I heard the song on the Christian radio station,
I understood the lyrics: It's not about religion,
it's about relationship.

I'm *not* religious.
And where I am, I'm anxious to eliminate any ritual
or compulsion and focus on Christ, the Way, the Truth, the Life.

## Free Me from Religiousness

In English, "religion" has at least two meanings.
The most obvious meeting is belief in the supernatural
and how we relate to that in our lives. What's your religion?

The other meaning is of something one clings to with fervor,
sometimes irrationally. I know that the humanist will say that
belief in the supernatural is irrational, but lets set that aside
if only for the moment. Clearly there are things people believe in
without question. Often these are GOOD THINGS, but our faith in them
can lead to unintended consequences.

## Techno Religion

Lately I'm fustrated by techno religion.
No no ... not technological religious experience,
but rather the religion surrounding certain kinds of technology.
You know, when people are so enamored with a certain invention
or gadget or new science that they use it in ways that it's
not necessarily useful.

I find that I am contrarian.
I reject some newer implementatinos (particularly in software) which
complicate things. If they demonstate no improvement in the whole,
then why have them? Maybe they've got the coolness factor.
One of those is SELinux, and that's the reason for writing today.

SELinux should probably go under my other blog space.
It's more about technology than truth. But my objection to SELinux
is over the philosophy more than the tech itself. SELinux is nifty
idea that has been misapplied and now has become a litmus test for
"hardened systems".

SELinux is almost like Java, a problem looking for a solution.
Really though, SELinux does solve some unique problems.
But in Linux land we don't use it for that. We use it as a cop.

## It Works

There's no argument: SELinux can arrest misbehaving programs,
keep them from straying where they ought not. My argument is with
how and where SELinux is employed. My complaint is about the cost
of using SELinux when simpler mechanisms get the job done.

I once asked an SELinux proponent why he liked it.
He said he sleeps better. In other words, with SELinux blocking
certain programs from straying outside of their proper domain,
he had nothing to worry about. Nuthin. Nada.

What programs?
One example rogue program might be HTTPD (name your web server
of choice). The World-Wide Web brings people from all over the net
right into your system. A poorly configured web server is the poster
child for a system at risk. There are many ways to constrain
the web server. They all require effort. They all take work.
SELinux is probably the coolest way to reign-in the rogue,
and it gives that sense of, "you're not allowed!" feeling.

## Keep it Simple

There are several problems with SELinux.
They all relate to complexity, loss of simplicity.
Today I was helping a customer with a serious problem during
an upgrade. In his case, there is at least the learning curve.
But more than that, his upgrade is no longer just a matter of
dropping in the latest code. His system (which we sold him)
now must be properly labeled (in SELinux terms).

In this case, my customer has added SNMP to the mix. The modification
was working fine until SELinux was activated due to an upgrade.
(Being a security product, it's kinda hard to *not* have SELinux
activated. See below.) If the scripts driven by SNMPD are well-behaved
(and they are) then SELinux isn't needed. It only adds complexity.
But one can never know that some bad boy won't sneak in.

## Back to Religion

Here's why this post is about religion:
SELinux has become an auditor's check-box.
"Is SELinux enabled?", check, done. (Whether it is effective is
not a question. Whether it is overkill is not even considered.)

Adherents to SELinux have gotten religious about it.
It's difficult to get some to even consider that it might not be
the right tool for any particular job. And don't DARE suggest that
a hardened system would not use SELinux.

What SELinux is good at, classifying data, nobody uses.
(SELinux is not the only way to do that either. I'm into cryptography
which is harder to circumvent.) People instead use SELinux as the
night watchman, still on duty during prime time. (EVERY operation
has to go through the gate. It's like airport screening to the max.)

It does not hurt to have extra assurance. There's nothing wrong with
layers of protection. But SELinux is expensive, complicated,
and obviates other mechanisms. Worse, the SELinux movement
won't allow even the slightest objection.

Let's get beyond the religion of SELinux and think about
appropriate application.

-- R; <><

original draft 2018-Oct-19


