# What is Chicory?

Chicory is the key ingredient in a special blend,
traditionally of coffee.

The chicory root is often roasted for use as an additive
in many brews, even some stouts. The plant is common in Europe,
both wild and cultivated.

## But what really is Chicory?

Chicory is a software packaging scheme.
Think brew, as in home-brew. Think brew, as in coffee and chicory.
So it's a pun. Cute, eh?

When I worked in academia,
I was exposed to the idea of Free and Open Source Software.
In those days we didn't yet have the acronyms FOSS or FLOSS
but they are (it is) the inspiration for Chicory.

In those days, one could get the VMS compiler from DEC, but many
would opt for GCC. "It's a better compiler." Open Source Software was
not just an interesting alternative, it was often the superior option.

Chicory restores the volunteerism and variety of old school
open source software. As FOSS has gained mainstream acceptance,
with complete systems based on it, package management has turned
monolithic. Chicory provides a compatible alternative to the
vendor and per-distro packaging methods without breaking anything.

## Outside the Mainstream

How does one install Open Source Software?
For that matter, how does one install any third party software package?

As open source use grew, the practice of throwing all third party
and/or open source programs under /usr/local grew too. This is
accepted practice even today and /usr/local/bin is the normal
location for commands and custom scripts.

/usr/local works great as a reference for things outside of
what the OS vendor provides. But it doesn't scale for managing
the packages. It provides no inventory. That's where Chicory
adds the needed flavor.

## /usr/opt

Software packages in the Chicory collection recognize /usr/opt
as a master prefix. Compare /usr/opt to similar master prefixes
from vendors, such as /usr/lpp defined by IBM. For many years
there was no name for the method of using /usr/opt for package
reference.

Chicory is the name we use instead of "the /usr/opt scheme".
Under /usr/opt are symbolic links to various third party
software packages. Unlike /opt, the /usr/opt path is a place
where packages come-and-go, with versioning, conditionally available
to users. (If the admin allows, then users can "install" Chicory
packages without special privileges.)

Chicory enabes multiple releases of any package simultaneously.
Someone might need both OpenSSL 1.0.2o and OpenSSL 0.9.8zh.
No problem! Those can happily coexist:

    /usr/opt/openssl-0.9.8zh
    /usr/opt/openssl-1.0.2o

All Chicory packages are versioned, and one will typically be
the default. Obviously only one can be the default at any time:

    /usr/opt/openssl -> openssl-1.0.2o

## Find Yourself

Chicory packages should be compiled (or configured) to find their
supporting components under their unique /usr/opt prefixed paths.
OpenSSL 1.0.2o should find its parts in /usr/opt/openssl-1.0.2o,
for example. This is the magic that allows any number of versions
to reside alongside each other. It also allows for easy re-location
of package residence.

Users should find package parts via the default path.
For OpenSSL that's:

    /usr/opt/openssl

With the usual sub-directories:

    /usr/opt/openssl/bin
    /usr/opt/openssl/lib
    /usr/opt/openssl/include

Whichever release of OpenSSL is default, it will still look for
supporting parts via the longer, fully-qualified path.

## Home is where the Files Are

Chicory packages can reside anywhere:
a local filesystem, a remote filesystem (via NFS or SMB),
a shared virtual disk, SAN, removable media (such as USB),
immutable media (such as DVD). The Chicory path for each package
simply points to where the files actually reside.

## Brewer's Collection

Over time, more than 100 packages have been built or configured
for Chicory. It is proven to work on more than two dozen different
operating systems.

Having a collection of software ready for service on-demand
is a huge benefit from using Chicory.

## What is Chicory?

Chicory ...

* is a software packaging method and prefix
* allows multiple versions of a package at the same time
* allows arbitrary [re]location of package residence
* optionally does not require admin rights
* can be coordinated with official package manager







