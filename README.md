# gmake-proxy

`gmake-proxy` consists of a single `BSDmakefile` that can be dropped into any project
with an existing `Makefile` relying on syntax specific to GNU make. Instead of seeing
and endless wall of errors as bmake attempts (and fails) to parse the gmake-specific,
with this `BSDmakefile` in place, `make` will silently proxy all commands (and even
attempt to forward commandline options in a compatibile manner) to GNU make if `gmake`
is found.

If `gmake` is not installed, this makefile will emit the appropriate error message
informing the end user that `gmake` is required to compile the project in question.

## How this works

Since the split from the original AT&T `make`, both GNU's `make` and the BSD `make`
have adopted different syntax to improve and expand the makefile syntax. These
syntaxes changes are largely incompatible with one another. While the BSD makefile
syntax is typically seen as being cleaner and clearer (and `bmake` can handle paths
with spaces), the GNU variant of the makefile syntax is by far the more popular of
the two in random open source projects found around the web.

Fortunately, both GNU `make` and BSD `make` default to a different makefile name that,
if present, will be used instead of a file named `Makefile` in the project root. For
BSD `make`, that filename is `BSDmakefile`, while for GNU `make`, that name is is
`GNUmakefile`.

This project consists of a single `BSDmakefile` that can be dropped into any directory
containing either a `GNUmakefile` or (as is most common) a platform-agnostic `Makefile`
that incorrectly contains GNU-specific syntax/code. This `BSDmakefile` will attempt
to intercept the user's build command and forward it to a GNU `make` instance, relying
on the presence of GNU `make` installed under the name `gmake`.

## Copyright and authorship

`gmake-proxy` is written and developed by Mahmoud Al-Qudsi of NeoSmart Technologies.
This project is (aptly) released to the general public under the terms of the two-clause
BSD license (aka "the simplified BSD license" or "the FreeBSD license"). Please see the
`LICENSE` file for the full text of the license.

(Code licensed under the BSD license may be freely used in GPL projects, unfortunately
the converse is not true.)
