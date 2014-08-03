This repository contains the files required to build and package Git for [Cygwin][].

Building and packaging the 32-bit Git needs to be done on a 32-bit Cygwin installation; likewise for the 64-bit version.  The builds use Cygport, so from a copy of this repository, the following command will download and build Git, and package it into separate packages.

    cygport git.cygport download prep compile install package

To run the test suite, you can either use `cygport git.cygport test`, or run `make` from the `build/t` directory after the compile stage has been completed.  Note that there are some tests that are known to fail in Cygwin but aren't disabled.  Any such tests should be [flagged with an issue in the Github repository][GHIssues], and can be disabled by setting the `GIT_SKIP_TESTS` environment variable (for example to `t3900 t4018`) when running `make`.  To have the output of the tests saved as well as printed to the terminal, set `GIT_TEST_OPTS=--tee`.

[Cygwin]: http://www.cygwin.com
[GHIssues]: https://github.com/me-and/Cygwin-Git/issues
