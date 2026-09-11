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

## 2026-09-10

### Platform

#### Added

- The billing step of the workload setup wizard now has a "Skip for now" option, so you can finish setup and buy credits later. Organizations without credits are warned that requests will be refused until credits are purchased.
- New reminder email, sent a day after an account is ready, to organizations that have not sent a request yet. It includes your balance, or current rates if you have no credits, and the base URL and model string needed to point an OpenAI-compatible client at Pareto.

## 2026-09-04

### API

#### Added

- Added server-side tool support for Messages and Responses-compatible API traffic, including web search, image generation, patch application, and tool discovery.
- Added Anthropic-compatible `tool_search` handling so clients can discover supported tools through the Messages API adapter.
- Added non-streaming support for server tools: a `/v1/responses` or `/v1/messages` request that declares a server tool without `stream: true` now receives one JSON response body (the same object a streaming client receives in its final event) instead of the previous `server_tools_streaming_only` error, which is retired.

#### Changed

- Server tools are now enabled by default for eligible API traffic.
- Non-streaming server-tool requests run under a 300-second wall-clock budget: when less than 120 seconds remain the model is asked for its final answer, and a request still running at 300 seconds returns `504` with the message "Server-tool loop exceeded its wall-clock budget". Streaming requests are not affected.
- Mid-request failures on non-streaming server-tool requests return HTTP statuses instead of in-band stream events: `502` for an upstream failure, `500` for a billing settlement failure, `402` when prepaid credit runs out between tool turns, `503` during maintenance. Completed tool turns are billed as before.

## 2026-09-01

### Connectors

#### Added

- Connector catalogue changes now require human review and are published signed.
- Added CI checks that verify the generated connector catalogue and signatures stay in sync with the source manifests.
- Added automated SAST scanning and Dependabot validation for the connector catalogue repository.

#### Security / Compliance

- Classified connector publishing buckets for compliance inventory and replication controls.

## 2026-08-31

### Connectors

#### Added

- Published the signed connector catalogue used by Unbiased clients to discover supported integrations at runtime.
- Added the lightweight connector catalogue used by terminal clients that do not need icon assets.
- Added detached signatures for each published connector catalogue payload.
- Added `publishedAt` metadata to the signed catalogue so clients and auditors can identify the exact published version.
- Added the hosted `connectors.unbiased.ai` publishing path for the catalogue.

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
