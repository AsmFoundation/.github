# Contributing to AsmFoundation projects

Thank you for helping. This is the organization's default guide. GitHub shows
it for every repository that has no `CONTRIBUTING.md` of its own. A
repository's own guide takes precedence and lists its exact build and test
commands ([KvAsm's](https://github.com/AsmFoundation/KvAsm/blob/main/CONTRIBUTING.md),
for example).

Assembly has no type system, no bounds checks and no sanitizers, so every
project relies on two habits:

- **Correctness comes from independent checks:** conformance suites,
  differential tests against reference implementations, fuzzing, and
  end-to-end tests against the real binary. One author's understanding of a
  protocol is not a check.
- **Performance comes from measurement.** A change that is supposed to be
  faster ships with a paired measurement that shows it: the same workload,
  old and new builds, interleaved on the same machine. An argument is not a
  measurement.

## Before you start

- **For anything beyond a small fix, open an issue first.** Describe the
  problem and the change you have in mind, so the design can be agreed
  before the work is done.
- **Report vulnerabilities privately**, never in an issue:
  [SECURITY.md](SECURITY.md).

## What a pull request needs

1. **CI passes.** Every repository runs its full test suite on every push and
   pull request; run it locally first. The repository's README and its own
   CONTRIBUTING guide have the commands.
2. **Tests for the change.**
   - A bug fix comes with the test that failed before it.
   - New behavior comes with tests at the level where it is observable, for
     a server usually the end-to-end suite.
3. **Documentation in the same pull request.**
   - Code comments that explain *why* (in assembly: registers, invariants,
     what each routine clobbers).
   - The docs a user reads, and the `CHANGELOG.md` entry.
4. **Evidence for any performance claim**, in the pull request description,
   and in the project's claims ledger if the claim goes public.

## License

Contributions are accepted under the repository's license, Apache-2.0, as
section 5 of the license says.
