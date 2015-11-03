This repository contains the files required to build and package Git for [Cygwin][].

Building and packaging the 32-bit Git needs to be done on a 32-bit Cygwin installation; likewise for the 64-bit version.  The builds use Cygport, so from a copy of this repository, the following command will download and build Git, run the test suite, package the compiled results into separate packages, and (provided the key for upload access is `~/.ssh/id_rsa`) upload the results.

    cygport git.cygport download prep compile test install package upload

## Test failures

**When investigating test failures, remember to check you're looking at something more interesting than a [fork failure][].  If you spend hours digging into something that turns out to be a common fork failure, you'll be righteously annoyed with yourself.  Here speaks the voice of painful experience.**

The below test failures were all noted as part of building the v2.6.2 release for Cygwin.  Comparisons with the v2.5.3 release are to help distinguish whether releasing v2.6.2 will make anything any worse, and to help track down where bugs were introduced.

Percentages are rough failure rates on the Cygport build.  Blanks mean I haven't tried yet, or I tried then forgot the result.

Test  | v2.5.3 32b | v2.5.3 64b | v2.6.2 32b | v2.6.2 64b | Issue   | Notes
------|------------|------------|------------|------------|---------|-------
t0025 |            |            | 1.5%       |            |         |
t5813 | N/A        | N/A        | 100%       | 100%       | [#11][] | Added after v2.5.3, and appears to have been failing ever since.
t7008 | 0%         | 0%         | 0%         | 0%         | [#8][]  | Should be failing!
t7063 |            |            |            |            | [#10][] |
t9167 |            |            |            | 4%         |         |

[Cygwin]: http://www.cygwin.com
[fork failure]: https://cygwin.com/faq.html#faq.using.fixing-fork-failures
[#8]: https://github.com/me-and/Cygwin-Git/issues/8
[#10]: https://github.com/me-and/Cygwin-Git/issues/10
[#11]: https://github.com/me-and/Cygwin-Git/issues/11
