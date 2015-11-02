This repository contains the files required to build and package Git for [Cygwin][].

Building and packaging the 32-bit Git needs to be done on a 32-bit Cygwin installation; likewise for the 64-bit version.  The builds use Cygport, so from a copy of this repository, the following command will download and build Git, run the test suite, package the compiled results into separate packages, and (provided the key for upload access is `~/.ssh/id_rsa`) upload the results.

    cygport git.cygport download prep compile test install package upload

## Test failures

Test  | v2.5.3 32b | v2.5.3 64b | v2.6.2 32b | v2.6.2 64b | Issue   | Notes
------|------------|------------|------------|------------|---------|-------
t5813 |            |            |            |            |         |
t7008 | 100%       | 100%       | 100%       | 100%       | [#8][]  | Should be failing!
t7063 |            |            |            |            |         |

[Cygwin]: http://www.cygwin.com
[#8]: https://github.com/me-and/Cygwin-Git/issues/8
