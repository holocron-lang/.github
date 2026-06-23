# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in any `holocron-lang` project,
please **do not** open a public issue. Instead, report it privately using
GitHub's [private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability).

To report:

1. Go to the affected repository (e.g. `holocron-lang/holocron`).
2. Click the **Security** tab.
3. Click **Report a vulnerability**.

We aim to acknowledge reports within **72 hours** and provide an initial
assessment within **7 days**. If the issue is confirmed, we'll coordinate
a fix and disclosure timeline with you.

## Supported Versions

We support the **most recent stable release** on crates.io. Older
versions may receive critical security fixes at our discretion but are
not guaranteed.

## Out of Scope

- Vulnerabilities in dependencies — please report those upstream first.
- Issues that require local access already privileged enough to modify
  the user's filesystem (the compiler is a build-time tool).