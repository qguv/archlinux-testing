# Archlinux `*testing` Package Test Scripts

These scripts serve as reproducible sanity checks for Arch Linux package
testing. From [the wiki][]:

> Testing a package can range from a simple "does it start/run?" test to more
> complex ones. Normally checking if the software still works for some simple
> example (for example, "does the new linux kernel still boot" or "does perl
> still run some perl script I have?") is sufficient. The main goal is to catch
> very badly broken packages before they can hit a large number of users.

[the wiki]: https://wiki.archlinux.org/index.php/DeveloperWiki:CoreSignoffs

I'm taking the second approach: for each program I've tested, I've written a
short script to test a basic use case that shouldn't change between versions.

# Usage

    paclist testing
    paclist community-testing

Produces a list of packages from [(community-)testing] that are currently
installed.

    ./depson <package>

Lists packages that depend on <package>. These can often be used to test
<package> indirectly if <package> does not provide a testable binary.

    ./newtest <package> <command> <args>...

Registers a test-command for <package> as tests/<package>, where you can further
edit the command manually.

    ./tests/<package>

Runs test-command for <package>. Errors if no testing command has been
registered.
