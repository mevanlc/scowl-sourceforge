This is the git repository for SCOWL (and friends).

SCOWL (Spell Checker Oriented Word Lists) is a database of English
words that can be used to create word lists suitable for use in spell
checkers of various sizes and dialects (America, British (both -ise
and -ize), Canadian and Australian). However, I am sure it will have
numerous other uses as well.

SCOWL is derived from many sources under a BSD compatible license.
The combined work is freely available under a
[MIT-like](https://raw.githubusercontent.com/kevina/wordlist/master/scowl/Copyright)
license.

To build simply type:

    make

The build uses GNU Make, Bash, Perl, a C++ compiler, and the usual Unix
utilities, including `tar`, `gzip`, and `unzip`. The build and release
scripts support the standard macOS/BSD and GNU/Linux utilities; GNU
versions of `find`, `grep`, `ls`, and `cp` are not required on macOS.
Compiler settings can be overridden with `CXX`, `CPPFLAGS`, `CXXFLAGS`,
`LDFLAGS`, and `LDLIBS`.

To build the aspell and hunspell dictionaries (you will need Aspell
0.60 installed):

    cd scowl/speller
    make aspell
    make hunspell

`make test` also requires `sqlite3`, `unix2dos`, and the Perl `DBI` and
`DBD::SQLite` modules. If multiple Perl installations are present, make
sure the `perl` on `PATH` has those modules as well as `/usr/bin/perl`,
which is used by the SQL command-line helpers.

To package the built SCOWL word lists as release archives (also requires
`zip`), run from a clean checkout:

    export SCOWL_VERSION=2026.11.06
    make
    cd scowl
    src/make-dist "$SCOWL_VERSION"

This creates `scowl-2026.11.06.tar.gz` and `scowl-2026.11.06.zip` in
`scowl/`. The version labels the current sources; it does not select a
historical release. Packaging cleans intermediate build files and
replaces any existing bundle with the same version. The tar archive
preserves symbolic links; the ZIP archive uses DOS/Windows line endings.
The broader maintainer release workflow is in `.misc/make-release.sh`.

For more information please see our homepage at <http://wordlist.aspell.net>.
