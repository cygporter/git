This repository contains the files required to build and package Git for [Cygwin][].

Building and packaging the 32-bit Git needs to be done on a 32-bit Cygwin installation; likewise for the 64-bit version.  The builds use Cygport, so from a copy of this repository, the following command will download and build Git, run the test suite, package the compiled results into separate packages, and (provided `lftp` can find the key for upload access, <i>i.e.</i> it's `~/.ssh/id_rsa` or has been added to `ssh-agent`) upload the results.

    cygport git.cygport download prep compile test install package upload

## Test failures

**When investigating test failures, remember to check you're looking at something more interesting than a [fork failure][].  If you spend hours digging into something that turns out to be a common fork failure, you'll be righteously annoyed with yourself.  Here speaks the voice of painful experience.**

The below tests were all spotted in the v2.6.2 build or later; comparison with earlier releases is to check whether the tests have been made any worse.  I suspect a significant proportion of the failures are [BLODA][], <i>i.e.</i> something running in Windows and outside Cygwin causing undefined unpredictable behaviour.  At some point I'll probably investigate them, but intermittent failures are tedious to debug, and nobody's complained about anything related to them on the Cygwin mailing lists (and I don't see problems despite regularly using Cygwin Git), so it's not a priority.

Percentages are rough failure rates on the Cygport build.  Blanks mean I haven't tried yet, or I tried then forgot the result.

Test  | v2.5.3 32b | v2.5.3 64b | v2.6.2 32b | v2.6.2 64b | v2.6.3 32b | v2.6.3 64b | v2.8.0 32b | v2.8.0 64b | Issue   | Notes
------|------------|------------|------------|------------|------------|------------|------------|------------| --------|-------
t0025 |            | 3.7%       | 1.5%       | 3.8%       |            |            |            |            | [#12][] |
t7008 | 0%         | 0%         | 0%         | 0%         |            |            | 0%         | 0%         | [#8][]  | Should be failing!
t9128 |            |            |            |            | 2%         | 5%         |            |            | [#16][] |
t9167 |            | 14%        | 5%         | 4%         |            | 6%         |            |            | [#13][] |

[Cygwin]: http://www.cygwin.com
[fork failure]: https://cygwin.com/faq.html#faq.using.fixing-fork-failures
[BLODA]: https://cygwin.com/acronyms/#BLODA
[#8]: https://github.com/me-and/Cygwin-Git/issues/8
[#12]: https://github.com/me-and/Cygwin-Git/issues/12
[#13]: https://github.com/me-and/Cygwin-Git/issues/13
[#16]: https://github.com/me-and/Cygwin-Git/issues/16
