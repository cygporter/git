This repository contains the files required to build and package Git for [Cygwin][].

Building and packaging the 32-bit Git needs to be done on a 32-bit Cygwin installation; likewise for the 64-bit version.  The builds use Cygport, so from a copy of this repository, the following command will download and build Git, run the test suite, package the compiled results into separate packages, and (provided `lftp` can find the key for upload access, <i>i.e.</i> it's `~/.ssh/id_rsa` or has been added to `ssh-agent`) upload the results.

    cygport git.cygport download prep compile test install package upload

[Cygwin]: http://www.cygwin.com
