# Security policy

This is the AsmFoundation's default policy. GitHub shows it for every
repository that has no `SECURITY.md` of its own. A repository's own policy
takes precedence: [KvAsm's](https://github.com/AsmFoundation/KvAsm/blob/main/SECURITY.md),
for example, adds its threat model.

## Supported versions

AsmFoundation projects are pre-1.0. Security fixes go into the latest minor
release of the affected project, and ship as a new patch version.

## Reporting a vulnerability

**Do not open a public issue for a vulnerability.** Report it privately:

1. Use GitHub's private reporting form: the affected repository's
   **Security** tab, then **Report a vulnerability**. Only the maintainers can
   read the report. Every AsmFoundation repository has private reporting
   turned on.
2. Include:
   - the project and its version (or commit, package version or image
     digest);
   - the configuration;
   - the relevant log lines;
   - a reproduction. For parser and protocol bugs, the raw input bytes are
     ideal.

**What to expect:**

- We aim to acknowledge a report within 7 days, and to have a fix or a
  mitigation plan within 30 days of the acknowledgement.
- The projects are maintained by a small team, so a release can take longer.
  We will tell you if it does.
- We will agree on a disclosure date with you, and credit you in the advisory
  unless you prefer not to be named.

## What we treat as vulnerabilities

Every project parses untrusted input in hand-written assembly, so we take
these seriously:

- **Memory safety:**
  - out-of-bounds reads or writes;
  - crashes or hangs caused by input;
  - returning data that belongs to another request or key.
- **Resource exhaustion beyond a project's configured limits.**
- **Supply chain:** a published package, image or toolchain that differs
  from what its pinned, verified sources would produce.

Attacks that need access to the host, or denial of service within limits a
deployment set too generously, are out of scope. Report bugs in test or
benchmark tooling as regular issues.
