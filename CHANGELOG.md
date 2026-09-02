# Unbiased changelog

Public release notes for customer-facing changes across Unbiased products.

## Unreleased

Use this section for reviewed entries that are approved but not yet tied to a dated public release.

### App

### CLI

### Platform / API

### Connectors

### Routing

### Security / Compliance

## 2026-09-01

### Connectors

#### Added

- Added security and review controls for connector catalogue changes, including human review ownership for connector manifests, signed payloads, icons, signing scripts, and publishing infrastructure.
- Added CI checks that verify the generated connector catalogue and signatures stay in sync with the source manifests.
- Added automated SAST scanning and Dependabot validation for the connector catalogue repository.
- Added automatic connector release tagging for merged PRs that carry the `release` label and include changelog entries.

#### Security / Compliance

- Classified connector publishing buckets for compliance inventory and replication controls.
- Set connector publishing build logs to retain evidence for one year.

## Entry Format

Copy this shape when publishing a dated release section:

```md
## YYYY-MM-DD

### App

- Added ...

### CLI

- Changed ...

### Platform / API

- Fixed ...

### Connectors

- Added ...

### Routing

- Improved ...

### Security / Compliance

- Updated ...
```
