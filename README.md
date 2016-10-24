# Arch Linux Testing Repository Test Scripts

Arch Linux testers test software packages for obvious bad behavior before the
packages are introduced to Arch users. From [the wiki][1]:

> Testing a package can range from a simple "does it start/run?" test to more
> complex ones. Normally checking if the software still works for some simple
> example (for example, "does the new linux kernel still boot" or "does perl
> still run some perl script I have?") is sufficient. The main goal is to catch
> very badly broken packages before they can hit a large number of users.

[1]: https://wiki.archlinux.org/index.php/DeveloperWiki:CoreSignoffs

This repository contains the scripts I use to test packages in [testing] and
[community-testing]. I maintain these scripts as part of my responsibilities as
an Arch Linux tester. Patches are welcome.

**Testing scripts are not a replacement for a couple minutes of quality
fiddling and mishandling to test for breakages.** The scripts **can** help
determine whether your fiddling and mishandling broke the package.

Just running the script and signing off when it succeeds is **not** testing.

# Workflow

    paclist testing
    paclist community-testing

Produces the list of currently installed testing packages.

    ./depson <package>

Lists packages that depend on `<package>`. These can often be used to test
`<package>` indirectly if `<package>` does not provide a testable binary.

    ./newtest <package>
    $EDITOR tests/<package>

Registers a test file for `<package>` as `tests/<package>`, where you can then
append your test invocation.

    tests/<package>

Runs test-command for `<package>`. Errors if no testing command has been
registered.
