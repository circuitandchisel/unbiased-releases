# Contributing release notes

This repository is for public, customer-facing release notes only.

## When to add an entry

Add a changelog entry when a shipped change affects what customers, admins, developers, auditors, or support teams can see, use, configure, rely on, secure, pay for, integrate with, or troubleshoot.

Examples:

- App, CLI, dashboard, API, connector, or routing behavior changed.
- A feature was added, removed, renamed, deprecated, or made generally available.
- Authentication, permissions, billing, limits, privacy, security, or compliance behavior changed.
- Customer-visible reliability, availability, latency, errors, diagnostics, or support workflows changed.
- Public documentation changed in a way that affects setup or supported behavior.

## When not to add an entry

Do not add entries for internal-only changes:

- Refactors with no behavior change.
- Test-only changes.
- Routine CI/build cleanup.
- Dependency updates with no customer-visible, security, or compliance impact.
- Internal logging, dashboards, benchmark harnesses, or infrastructure maintenance.

## Writing style

- Write for customers, not for the implementation team.
- Prefer product names and behavior over repository names.
- Mention customer action when action is required.
- Keep entries short, factual, and specific.
- Do not include secrets, customer names, private incident details, or internal-only system names.

Good:

```md
- Added signed connector catalogue verification for the desktop app and CLI.
```

Avoid:

```md
- Refactored catalogue signing script and changed dist generation.
```
