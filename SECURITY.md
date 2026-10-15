# Security policy

## Reporting a vulnerability

Please **don't** open a public issue for security problems.

Report it privately: **[Security → Report a vulnerability](https://github.com/d1same/cordon/security/advisories/new)**. Only the maintainers can see it.

Helpful details:
- Cordon version (Settings → About) and Windows version
- what an attacker could do, and the steps to reproduce
- no real client data, passwords or tokens

We aim to reply within 3 business days. Critical issues get a fix and a signed update as fast as possible, and installed copies update themselves.

## Supported versions

Only the latest release gets security fixes. Cordon updates itself, so most people are always on it.

## Verifying releases

Every installer is signed with Cordon's offline release key (fingerprint `f985ce6f6a50a969`). The built-in updater refuses anything that isn't. See the README for how to check a download yourself.
