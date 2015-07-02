This repository contains the files required to build and package Git for [Cygwin][].

Building and packaging the 32-bit Git needs to be done on a 32-bit Cygwin installation; likewise for the 64-bit version.  The builds use Cygport, so from a copy of this repository, the following command will download and build Git, run the test suite, package the compiled results into separate packages, and (provided the key for upload access is `~/.ssh/id_rsa`) upload the results.

    cygport git.cygport download prep compile test install package upload

Wherever the test suite encounters problems that don't exist upstream, these are tracked in the [GitHub issue system][GHIssues].  Except as noted below, all tests that fail are patched in the repository to be expected to fail.

There is a [known issue with certain tests on 64-bit Cygwin that causes them to hang occasionally][GHI7].  Running the test suite in the presence of this problem requires spotting these hangs, killing `git.exe` processes via Process Explorer or similar, then re-running the tests.  Or, better, debugging and fixing the problem.

[Cygwin]: http://www.cygwin.com
[GHIssues]: https://github.com/me-and/Cygwin-Git/issues
[GHI7]: https://github.com/me-and/Cygwin-Git/issues/7
