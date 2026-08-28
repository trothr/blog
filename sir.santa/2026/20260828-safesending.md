# The Safest Way to Send a File

As humans, we're all about communicating.

Sadly, though we have two ears and just one mouth,
we tend to speak more than listen. In tech terms,
we exercise "push" mode more often than "pull" mode.
And there are reasons for this, but they're mostly
beyond the scope of this journal entry, but some perhaps helpful.

## Sending and Going

Historically, we *go*. <br/>
While we welcome visitors (as long as they pass IFF muster)
we just as often (or more often) land on a cousin's doorstep
looking for a bed for the night (or week, or year).

This post is supposed to be about sending files electronically.
Thinking on that, push mode has been around longer than pull mode.
Starting from telegraphy, then radio telegraphy (eventually voice),
and teletype, followed by radio teletype (RTTY) ... we've been pushing
messages for decades.

I say all this about push versus pull
simply to emphasize that push is normal.
With the advent of the World Wide Web, pull became effective,
and operationally more common. But the two modes are complementary
rather than competitive.

## Data Big and Plentiful

We actually do use computers to make decisions for us.
Yet even in this time of pervasive processing there's LOTS of data.
The serious systems of old were recognized as "data movers".

I was a college student when the Internet became a consumer thing.
There were other networks in those days, with all kinds of odd
capabilities. The other networks were quickly overshadowed by the
novelty of "You've got Mail". As far as *sending* files, there was an
unconscious switch from push to pull. More than that, there was a loss
of general purpose push. In layman's terms: the way to SEND something
with typical consumer Internet is to attach the thing to email.

Now ... sending something along with a letter is not a bad thing,
but consider the implications: Should you deliver that shiny new
Samsung fridge via USPS or instead FedEx, UPS, or DHL? Ahhh... now we're
getting to the point of this rant.

## Enter UFT

UFT came into being in those days when consumer Internet was exploding
as a protocol to send files. The "U" stands for "unsolicited", which means
only that UFT is a push operation (versus pull, or "solicit"). Some have
called UFT "universal" file transfer, which is perhaps over attribution.

UFT is suitable for those large files, yet does not require the sender
to have any identity on the receiving end. You would not want the UPS guy
to drop off that refrigerator in your living room, would you? Other protocols
for sending bulk content (FTP, SCP, SFTP) mean that the sender must have a key.

Compare the operation of UFT with that of IBM's NJE protocol.
Traditional IBM mainframes interconnect with NJE and pass files regularly
as part of day-to-day operation. There is no sign-on required of the sender.
Networked peers are recognized (otherwise are not permitted to connect or send).
When a file is sent using UFT, it appears on the receiving end (at the figurative
front door or a a "delivery dock") and can be disposed of any way the recipient
desires.

## Points of Privacy and Protection

Some of the design points in UFT which facilitate safe sending include ...

* delivery does not require credentials on the target system
* the target user might not be a user, might be a queue or channel
* standard Unix/Linux/POSIX implementation for rapid deployment
* generic canonization of data (e.g., text versus binary)
* open-ended attributes or metadata
* all metadata is optional (file being sent might not have a name, for example)
* an AGENT function for added assurance of sending system veracity
* "chaffing" of the conversation with automatic "winnowing" of the payload

UFT protocol can, of course, be wrapped in security layers (SSL, TLS).
The extreme example of security layering is the Tor network.
Sending a file using UFT via the Tor network may be the safest way
to send a file. Such a transfer commonly requires just two things:
run the UFT client program with a Tor-capable proxy, and a "hidden service"
(a .onion address) UFT server/receiver. UFT can be compiled with anonymization
in mind, exposing less and minimizing fingerprinting.





## References

https://en.wikipedia.org/wiki/Chaffing_and_winnowing

https://en.wikipedia.org/wiki/Remote_job_entry#Network_Job_Entry

https://github.com/trothtech/uft/

https://en.wikipedia.org/wiki/Transport_Layer_Security

https://en.wikipedia.org/wiki/Tor_(network)




