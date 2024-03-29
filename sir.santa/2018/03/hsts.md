# HSTS: Please Stop

This post is an open letter to internet luminaries,
especially those who support grass roots and hobbyist efforts.
*Please defend what remains of cleartext infrastructure.*

## Please Stop de-facto HSTS

The genesis of this rant was 2018 February 10th, a Saturday, 
while watching events in Pyeongchang, I was multi-tasking. 
I was vetting PGP keys at Henk Penning's path finder site,
https://pgp.cs.uu.nl/. From the browser I didn't notice the 
re-direct. But I was also scripting, and then noticed.

I collect direct-from-author source packages. No intermediate 
distributor. Most of these are signed by those authors. Home grown 
automation checks those signatures. PGP provides both assurance that 
source archives are intact and have not been tampered with. The PGP Web 
of Trust works without the need for other cryptographic infrastructure. 
FTP and plain HTTP are amply able to carry archives, signatures, and 
trust keys.

As more and more FOSS sites switch-on HSTS in their web servers, we're 
seeing more and more re-direct from HTTP to HTTPS. While HTTPS is 
preferred for most things, there are cases where one might need plain 
HTTP. The problem HSTS introduces is that one can no longer explicitly 
choose plain HTTP. You'll get a 301 "Moved Permanently" and then you 
must re-try with HTTPS.

Key pinning, one of the efatures of HSTS, is a good idea. The astute 
reader will note that vetting of PGP keys is exactly that (though in a 
different key space).

## Wither Volunteerism

Disabling cleartext is a bad idea. It increases the cost of every 
transaction. It requires pre-established trust, or that the client 
explicitly switch-on "insecure" mode of what is supposed to be a secure 
handshake. Even where it works, PKI is a useless hurdle to things like 
the Web of Trust.

Broader adoption of HTTPS and cryptographic data security is a good 
thing. It is presumably the primary motivation of the HSTS authors.

But some have said that PKI is a train wreck. Not the tech, but the 
business, the mis-management of fundamental trust by people with too 
little understanding of the impact and too little incentive to get it 
right. If PKI is a train wreck, then HSTS is an added locomotive 
bringing up the rear and pushing more cars into the ditch.

There are many places where HTTPS is unavailable. In my world, the pain 
point is "embryonic trust store" which has yet to be pre-loaded with 
root certificates from the major certificate authorities. Until the root 
certificates are added to the local trust store, the client has to 
proceed blindly with "--insecure" or "--no-check-certificate".

## It's All About Trust

It's all about trust: PKI breaches are overwhelmingly due to compromized 
or mis-managed certificate authorities. (Remember DigiNotar? Remember 
StartCom and WoSign?) Certificate authorities are trust brokers. 
Delegating trust is often a necessity. For consumers, it's the norm.

There are alternatives to cryptographic certificates
for establishing trust. In fact, PKI is now turning toward
statistical assurance rather than single-root chaining,
a model well established in the PGP world. A statistically heavy
body of cleartext outweighs a singular cryptographic proof.

This is what we had, a robust internetwork run by trusted carriers.
This is how we got the web we now enjoy, originally HTTP but now
increasingly HTTPS. Good! This is what we need going forward:
infrastructure which supports strong crypto but works even when
the crypto breaks.

There are many places where HTTPS is disallowed.  I'm a ham radio 
operator deeply interested in digital modes. As of this writing, 
encrypted traffic is not permitted on the ham bands. (WE DO hope that 
will change, and soon.) In any case, cleartext is not inherently bad.

## Crypto Breaks

Crypto breaks?

Yep.

Cryptography depends on the limits of computing technology
to be viable. When machines advance in capability, any crypto
falls to brute force.

Cryptography is a moving target. As algorithms enjoy broad
deployment, they become victims of analysis. Mathematicians
and cryptologists look for weaknesses, even while inventing
newer and better algorithms.

Cryptography demands obsolescence.
Certificates expire (even before their algorithms get cracked).

## I Love Crypto!

This post surely sounds like a slam.
I expect I come across as opposing cryptography.
The opposite is true.

My day job is all about datasec.
My salary is funded by cryptography.
My paycheck depends on business which depends on TLS.

Cryptography is simply not a silver bullet.
It's not the band-aid to apply to every wound.

We need crypto.
It gives us confidentiality and confirmation.
We need cleartext.
It works even when cryptography fails.

So stop with the HSTS already.
Use HTTPS. Promote HTTPS and SSL and TLS and PGP.
But allow, support, and nurture an internet which will
continue to work in spite of the cryptography.

-- R; <><


