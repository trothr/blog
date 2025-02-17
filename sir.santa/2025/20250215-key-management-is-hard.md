# Key Management is Hard

Crypto is easy.
Key management is hard. <br/>
It's true. Here's why and how.

The slogan itself I learned from Voltage Security when I worked there.
									.
The Voltage group (which was aquired by HP, then part of HPE, then Micro
Focus, and lately under Open Text) is focused on data protection. For them,
cryptography and key management make for a "been there / done that"
kind of thing. They know of what they speak.

## Crypto is Easy

Over the past two or three weeks
I have put in several hours taking inventory of cryptographic keys
used for code signing. It's tedious work. I was reflecting on that.

For better or worse, I (still) maintain a good sized body of software
acquired in source form. Whenever there is an update to one of these
packages, I snag the latest source code, explode the archive (in English,
I un-tar the TAR file), run the configurator, then `make`.
This is a terrible time sink, but is arguably justified, yet that
argument will have to wait for another time and another journal post.

I've been doing this for a long time.
What started as a hobby has persisted to this day.
I learned about "open source software" or what is often called FLOSS
(for free/libre open source software) when I worked in academia.
It was educational to review programs others had written and the
universities ate it up. Over time, more packages were added,
and more and more were improved, with the effect that a complete
viable operating system resulted. (But further discussion of *that*
is also for another journal post.)

I noticed several years ago that many of the package maintainers
began to sign the tarball (or zip file or whatever) using PGP.
Having been involved in the PGP ecosystem, I was happy to see this:
not only that those handling the code cared to perform signing of
their wares, but especially that they were using PGP (or GPG) where
the web of trust is based on individuals rather than on organizations
(as with PKI code signing).

When you download these sources, there is often now a second file
which is the "detached signature". (The deliverable remains the same.)
Download both files and confirming a signature is easy.
Suppose that you have the latest version of Musl Libc.
On any Linux system, and most Unix-like systems, you can easily use
GPG (GnuPG, the Gnu Privacy Guard)\*, like this:

    gpg --verify musl-1.2.5.tar.gz.asc

GPG takes the full filename as that of the detached signature,
then removes the final extension to derive the name of the signed file.
So it compares `musl-1.2.5.tar.gz` with signature `musl-1.2.5.tar.gz.asc`.
If the signature looks valid, GPG says so. If you have the matching
public key (in your "keyring"), GPG can confirm or deny authenticity.

I added logic a long time ago to my own build scripts to check signatures.
So now it's just a matter of acquiring and vetting the signing keys.

\* We're talking about the PGP ecosystem even though I use GPG to do
the work. There are (now) many implementations of PGP-compatible logic.
It's not that cryptography is easy as much as that the cryptography
has long since been distilled into software. (GPG being one of the
packages that I insist on building from source.)

## Always Sign Your Work

I wish more web pages had date stamps. <br/>
I also wish more web page authors would include their name or initials. <br/>
What artist does not sign his work? Maybe web artists lack pride in
their work. (Or maybe they're just clueless about art etiquette.
Or maybe they're just clueless about etiquette.)

When you're writing code, put your name on it. <br/>
When you share a package publicly, sign it (cryptographically).
This too is easy to do:

    gpg --detach-sign uftc4win.tar.gz

The above command will prompt you for your passphrase. That's all!
It then creates `uftc4win.tar.gz.sig`. The original payload remains as-is.
(And that's a good thing.) Alternatively, you can generate a safe-for-email
signature:

    gpg --armor --detach-sign uftc4win.tar.gz

That also prompts for passphrase but results in `uftc4win.tar.gz.asc`
which is "ASCII armored". Either form of signature is acceptable
for verification.

Lately I've taken to signing not only packages that I publish
but also email. For email, my preferred client program now invokes
PGP logic automagically. That makes it soooo much easier.
(Signing files is not egregious, but signing email used to be clumsy.)

# Key Management is Hard

To verify a package, you need the *public* key. <br/>
(To sign a package, you need your *private* key.)
Public keys are, as the name suggests, for public consumption.
They should be distributed far and wide. And so they are!

There are many viable channels for acquiring public keys.
There is the grand "web of trust" served by several independent
web sites. There are also a number of large collections of public keys.
The Debian project maintains a list of public PGP keys of contributors
and ships a number of keyrings with their distribution. Similarly,
the Gnu project also has a keyring of contributors. The Linux kernel
maintainers have a very sophisticated collection of contributor keys
broken out into individual public keys and hosted with Git.

The above paragraph makes it sound easy, and acquiring keys *is* easy.
The hard part is confirming which keys to accept, checking trust chains,
and handling keys as they expire. Note that an expired key might should
not be removed from the keyring. An expired key which signed a certain
archive (e.g., ZIP file or TAR file) certifies the authenticity of
that file long after its own expiration. The math (of the cryptographic
signature) doesn't change just because time has moved forward.

The story is the same with PKI, except that we talk about "certificates"
(which actually contain public keys). The added burden in the PKI model
is the ultimate authority is outsourced to your CA (Certificate Authority).

I remember the pain our customers endured when I was with Voltage Security.
While our product rendered their data safe, they still had to turn the crank
at intervals and follow the dictates of their CA. The appliance served
as a solid trust anchor, but it required one or more PKI keys for client
assurance, trust, security, and privacy. (Subsequent key management was
*vastly* easier thanks to the features and function of the appliance.)

For what it's worth, OpenSSL and LibreSSL are two packages that,
like GPG, I insist on building from source. I also have a home-grown CA.
But I think I'm getting off track; sorry.

## It's All About Trust

Key management is hard. <br/>
While the handling of keys is facilitated by excellent tools like
GnuPG or OpenSSL, there's no getting around the serious decisions needed
when choosing which keys or certificates to trust.

Even when some of the management is outsourced (to your CA of choice)
where there is a staff to do much of the work, the choice remains:
which root certs to include in the trust store? So while the PGP model
involves documented manual effort, the PKI model is not free of it.
(I'm not slamming PKI, though I often find myself defending PGP.)

Keys are cheap! Trust is where the value lies.
But electronic trust is wired to the keys. Many security professionals
endorse key rotation, and some CAs enforce it. Even so, can you bear
the cost of re-signing objects when your signing key gets changed?
Think about it. It may be more effective to generate more keys
and revoke instead of expiring.

Anyway ... I was reminded of all this as I sank several hours of my life
into (what seemed like) pointless extraction, reviewing, and verifying
of the keys which sign most of the source code that I care about.
I have a home-grown system with a high degree of trust in both the
running artifacts (binaries, executables) and the sources (old and new)
used for building it. It's work. I thought, "Why am I doing this?".
It's exhausting to have to choose for each key "do I trust this one?".
But I immediately remember that there is no easy way.

It's all about trust.

2025-Feb-15 Saturday


