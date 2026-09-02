# Unbiased releases

This repository is the public source of truth for customer-facing release notes across Unbiased products.

Development happens in private repositories. Only customer-facing or customer-relevant changes are recorded here, including changes to the desktop app, CLI, platform/API, connectors, routing behavior, security, privacy, compliance, and documented product behavior.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for the public release history.

## Scope

Release notes should describe shipped behavior in language a customer, administrator, developer, auditor, or support person can understand.

Include changes such as:

- New product features or workflows.
- Meaningful behavior changes in the app, CLI, platform, API, connectors, or routing.
- Security, privacy, compliance, authentication, billing, limit, or permission changes.
- Breaking changes, deprecations, migrations, or changes that require customer action.
- Material reliability, availability, latency, or troubleshooting improvements.
- Public documentation changes that alter supported behavior or setup guidance.

Do not include purely internal changes such as refactors, test-only changes, routine CI cleanup, internal logging, or infrastructure changes with no customer-visible effect.

## Process

Each changelog entry should be reviewed before it is published here. Source repositories may enforce their own release-note gates to decide whether a customer-facing change requires an entry.
