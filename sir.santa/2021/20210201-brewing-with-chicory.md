# Brewing with Chicory

This is inspired by my friend Roberto.
He indulged me, listening to me ramble a bit about Chicory.

Chicory is easy: easy to build for, easy to deploy with.
But Chicory is hard to explain. So I tried with Roberto.

## The Centerpiece

The centerpiece of Chicory is a common directory,
a prefix under which Chicory-enabled packages are found.

The usual prefix directory for Chicory is `/usr/opt`.
Keeping the story short, if that particular path presents problems
(like that it's under `/opt` for one thing), there are ways around it.

Create the `/usr/opt` directory and make sure it's writable
by anyone who will need to use it.

## A Real Example

It helps, when explaining, to use a real-life example.
Such a thing presented itself last week.

I've got a new virtual server running FreeBSD. It doesn't have `pico`
(lately `nano`), my usual text editor. No problem. I'll just build it.

I've got "wrapper" makefiles for older versions of Nano, most recently
4.9.2. Turns out that the current version is Nano 5.5. Fine: copy the
makefile from the `nano-4.9.2` directory into the `nano-5.5` directory,
change it to reflect the new version, and proceed with the build.

This wrapper makefile has the following targets that for any platform:

* `make source` -- downloads the source if needed, explodes the tarball

* `make verify` -- checks the signature if the source tarball is PGP-signed

* `make config` -- does a `./configure` in the real source directory, one level down

* `make` -- drives a 'make' in the real source directory

* `make install` -- arranges Chicory re-direction, then drives a `make install` in the real source

* `make distclean` -- deletes that "real source" sub-dir, but leaves any per-platform artifacts

I don't drive all of these targets every time.

## Nano 5.5

These wrapper makefiles vary slightly from release to release. You can
find the current wrapper makefile for Nano 5.5, as well as the source
tarball and its signature, here:

    http://nico.casita.net/pub/nano/nano-5.5.mak

If you wanted to build your own Nano 5.5 ala Chicory, create a directory
called "nano-5.5" (and a couple of support directories I'm skipping for now),
then copy ...

    http://nico.casita.net/pub/nano/nano-5.5.mak  as  "makefile"
    http://nico.casita.net/pub/opt.setup.sh  as  "setup"

 ... and then do (at least) the following

    make source
    make config
    make
    make install

If you don't have a writable `/usr/opt` then the "make install" step will fail.
The `/usr/opt` directory is the core of the Chicory scheme. I usually create it
as root and `chmod 1777` so that unprivileged users can play too. 

If the Nano build worked, then you can ...

    make distclean
    ./setup

 ... and then find `nano` at `/usr/opt/nano/bin/nano`.

If the `setup` script were run with privileges,
you'd also find `nano` at `/usr/local/bin/nano`.

2021-02-01 Monday


