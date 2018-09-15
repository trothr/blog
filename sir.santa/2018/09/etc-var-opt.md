# /etc, /var, and /opt

If you use Unix or Linux,
you will probably encounter one or all of the directories
`etc`, `var`, and `opt` in the root directory of the system.

What are they? What purpose do they serve?

## Tribal Knowledge

A colleague said that he just didn't know what the Unix path names
meant. Is `/opt` for "optional". (Yes, but it evolved.) Why do they
call it `/etc`? (It's historical.)

Knowing the story behind each path provides context.
Changing paths because the meanings have shifted can cause problems,
so it's important to at least hear how things happened.
(If one is then truly compelled to change a name then at least
sym-link old to new, or new to old.)

It's both humorous and sad, <br/>
"This is Unix. You just gotta know!"

Note: Linux got where it is by leveraging Unix history, Unix lessons,
and Unix people. It's no slam against Linux to describe it as a
variant of Unix. True, Linux has gone in its own direction ... a lot.
But in this document, we're talking about general Unix concepts.

## Classifying Content

Best practice with any computing system is to differentiate
kinds of data and where they reside. There are at least these:

* operating system, core code
* packages, optional code
* local configuration
* per-user configuration
* system data (e.g., logs, databases, varying content)
* user data, where distinct from system data

Throughout the industry are examples of packages,
even whole systems, which fail to distinguish these classes.
Eventualy someone gets bitten.

## Why /bin?

It may be common knowledge that Unix commands are found in the
`bin` directory. But why is it "bin" instead of perhaps "cmd"?

Presumably the rationale for "bin" is that most commands are
compiled executables. They're machine code. Their content is *binary*
rather than textual.

Let's move on.

## /usr

As Unix was being developed, /usr was first used to hold
user home directories. It was a separate disk from the root filesystem.
But in the early days disk space was expensive. As the system grew,
some things got moved from the root over to `/usr`. Eventually, since
`/usr` might be on a different disk, it came to hold system files
and programs which are not essential early in the boot stage.

`/bin` is often a sym-link to `/usr/bin`. That's sometimes useful
but comes with subtle costs. Further discussion is beyond our scope.

## /etc

`/etc` stands for et cetera.
At first it held files that seemed to have no other place to go.
Now it holds the majority of system configuration files.
`/etc` defines the personaly of the system.

As of this writing, /etc also holds non-system configuration too.

## /var

`/var` stands for variable.

Consider spool files (e.g., for email or for printing).
Originally there was `/usr/spool`. But `/usr` is really "operating
system stuff" and might even be read-only, so `spool` was moved.
`/var/spool` is now where spool files go, and `/var` has other
variable content.

## /opt

`/opt` stands for optional.

Question: What is optional? <br/>
Answer: Everything! (almost)

Anything that is not part of the core operating system can,
and should, be placed under `/opt`. The exact definition of
"core operating system" varies, but many packages are now found
under `/opt`.

The recommended naming for third party packages is:

        /opt/vendor/package

As an example, the Chrome web broswer from Google would to in:

        /opt/google//chrome

## Putting it all Together

When packaging your package, don't comingle your files with OS files.
Leave the operating system pristine.

        /opt/vendor/package
    /etc/opt/vendor/package
    /var/opt/vendor/package

If the package is to have per-user configuration or per-user content
that should go under `$HOME`.

## References

https://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html

https://unix.stackexchange.com/questions/5915/difference-between-bin-and-usr-bin ?

http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/basic/node32.html

https://en.wikipedia.org/wiki/Unix_filesystem


