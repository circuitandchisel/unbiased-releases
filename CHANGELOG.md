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

## 2026-08-31

### Connectors

#### Added

- Published the signed connector catalogue used by Unbiased clients to discover supported integrations at runtime.
- Added the lightweight connector catalogue used by terminal clients that do not need icon assets.
- Added detached signatures for each published connector catalogue payload.
- Added `publishedAt` metadata to the signed catalogue so clients and auditors can identify the exact published version.
- Added the hosted `connectors.unbiased.ai` publishing path for the catalogue.
- Added Slack to the connector catalogue as coming soon.

#### Changed

- Documented GitHub raw as the temporary serving host while the dedicated connector domain is staged.

#### Security / Compliance

- Added signature verification as the trust boundary for connector catalogue payloads.
- Kept connector signing keys outside the repository and CI environment.

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
