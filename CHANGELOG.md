# Unbiased changelog

Public release notes for customer-facing changes across Unbiased products.

## Unreleased

Use this section for reviewed entries that are approved but not yet tied to a dated public release.

### App

### CLI

### Platform

### Connectors

### Routing

### Security / Compliance

## 2026-09-04

### API

#### Added

- Added server-side tool support for Messages and Responses-compatible API traffic, including web search, image generation, patch application, and tool discovery.
- Added Anthropic-compatible `tool_search` handling so clients can discover supported tools through the Messages API adapter.
- Added non-streaming support for server tools: a `/v1/responses` or `/v1/messages` request that declares a server tool without `stream: true` now receives one JSON response body — the same object a streaming client receives in its final event — instead of the previous `server_tools_streaming_only` error, which is retired.

#### Changed

- Server tools are now enabled by default for eligible API traffic.
- Improved personal-plan admission checks so plan limits are applied consistently across API keys and workloads.
- Non-streaming server-tool requests run under a 300-second wall-clock budget: when less than 120 seconds remain the model is asked for its final answer, and a request still running at 300 seconds returns `504` with the message "Server-tool loop exceeded its wall-clock budget". Streaming requests are not affected.
- Mid-request failures on non-streaming server-tool requests return HTTP statuses instead of in-band stream events: `502` for an upstream failure, `500` for a billing settlement failure, `402` when prepaid credit runs out between tool turns, `503` during a deploy drain. Completed tool turns are billed as before.

#### Fixed

- Improved server-tool replay and tool-call handling across supported providers.
- Clarified low-balance and invalid-key API guidance.

## 2026-09-02

### Routing

#### Added

- Added persisted backend failure metrics so operators can troubleshoot routing health over time.

### Platform

#### Changed

- Required platform changelog changes to declare whether they should publish immediately, be held for gated availability, or remain changelog-only housekeeping.

### Connectors

#### Changed

- Required the `release` label whenever connector changelog entries are changed, so approved release notes are automatically tagged and promoted to the public changelog workflow after merge.
- Added an explicit `changelog-housekeeping` path for changelog-only maintenance edits that should not publish a release note.
- Removed the unused `Unreleased` staging section so connector release notes cannot be merged without a dated release section.

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

### Platform

- Fixed ...

### Connectors

- Added ...

### Routing

- Improved ...

### Security / Compliance

- Updated ...
```
