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
Renaming paths because the meanings have shifted can cause problems.
Programs get written using one name and then can't find files because
someone just had to have a better label. So it's important to at least
hear how things happened, to understand how we got here. If one is then
truly compelled to change a name then at least sym-link old to new,
or new to old. (Which is common practice.)

It's both humorous and sad, <br/>
"This is Unix. You just gotta know!"

Note: Linux got where it is by leveraging Unix history, Unix lessons,
and Unix people. It's no slam against Linux to describe it as a
variant of Unix. True, Linux has gone in its own direction ... a lot.
But in this document, we're talking about general Unix concepts.
Where Linux varies, we go with Unix.

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

"bin" seems to be widely recognized. Good!

## /usr

As Unix was being developed, `/usr` was first used for holding user
home directories on a separate disk from the root filesystem. But in the
early days disk space was expensive. The inventors of Unix borrowed from
the users to serve the system. As the system grew, some things got moved
from the root over to `/usr`.

Eventually (since `/usr` might be on a different disk even now) it came
to hold system files and programs which are not essential during the
boot and start-up stages. For example, commands which are crucial before
other filesystems are mounted must be find in `/bin` (or in `/sbin`). 

Many system engineers make `/bin` is a sym-link to `/usr/bin` and
other supposed simplifications. These are sometimes useful but come with
subtle costs. (Obviously if `/usr` is on a different disk then start-up
gets tricky.)

## /etc

`/etc` stands for et cetera. At first it held files that seemed to have
no other place to go. Now it holds the majority of system configuration
files. (I guess they just had no where else to go?) `/etc` defines the
personality of the system.

Theyse days `/etc` also holds much non-system configuration also.

## /var

`/var` stands for variable.

Consider spool files (e.g., for email or for printing).
Originally there was `/usr/spool`. But `/usr` evolved to mean
"operating system stuff" and might even be read-only, so `spool` was
moved. and now `/var/spool` is now spool files go, and `/var` has other
variable content.

## /opt

`/opt` stands for optional.

Question: What is optional? <br/>
Answer: Everything! (almost)

Any software package that is not part of the core operating system can,
and should, be placed under `/opt` or a variant such as `/local/opt`.
The exact definition of "core operating system" varies, but many packages
are now found under `/opt`.

The recommended naming for third party packages is:

        /opt/vendor/package

As an example, the Chrome web broswer from Google would go in:

        /opt/google/chrome

Packages have their own hierarchy. Commands and libraries go into
`bin` and `lib` respectively. So expanding on the naming:

        /opt/vendor/package/bin
        /opt/vendor/package/lib

## Putting it all Together

When bundling up a software package, don't comingle your files
with OS files. Leave the operating system pristine.

        /opt/vendor/package
    /etc/opt/vendor/package
    /var/opt/vendor/package

If the package is to have per-user configuration or per-user content
those files should go under the individual user's home directory.

## Family Argument

The above file paths are not universally agreed upon.
In particular, in many parts of the industry, people prefer to have
configuration varying files *after* the package prefix instead of
before it. It sounds convenient, and it simplifies initial deployment.
But it grossly complicates package management and future updates.

## Harmony

Sym-linkery might help.

        /opt/vendor/package/etc -> /etc/opt/vendor/package
        /opt/vendor/package/var -> /var/opt/vendor/package

It's just a suggestion. I don't recommend it. Maybe do it at first
like training wheels, but in the end too many sym-links are just clutter.
Also, the simplification does nothing for user-owned files.

Harmony can be achieved. We need to consider content classification
and dig deep enough to cope with real-world requirements.

## References

https://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html

https://unix.stackexchange.com/questions/5915/difference-between-bin-and-usr-bin ?

http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/basic/node32.html

https://en.wikipedia.org/wiki/Unix_filesystem

https://en.wikipedia.org/wiki/Spooling


