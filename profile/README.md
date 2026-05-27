# Proofline

Proofline is an open-source project for encrypted incident capture and trusted evidence access.

The project is designed around preserving encrypted records of important incidents, including emergencies, safety checks, and non-emergency interactions where a durable private record may matter.

Proofline is experimental and not production-ready public infrastructure.

## Current status

The active implementation is:

| Repository | Status | Purpose |
|---|---|---|
| [`open-proofline/server`](https://github.com/open-proofline/server) | Active | Go backend for encrypted chunk ingest, incident metadata, token-scoped incident review, evidence bundles, deployment docs, and server release workflow. |

Planned future repositories:

| Repository | Purpose |
|---|---|
| `open-proofline/web-client` | Account portal, authorised incident review, trusted-contact access, and eventual replacement for the current token-only viewer. |
| `open-proofline/ios-client` | iOS incident capture, encrypted staging, upload, local account flows, and platform-specific recording behaviour. |
| `open-proofline/android-client` | Android incident capture, encrypted staging, upload, local account flows, and platform-specific recording behaviour. |
| `open-proofline/protocol` | Shared API specs, encryption envelope specs, bundle manifests, compatibility matrix, and conformance tests. |

These repositories will be created when their scope is ready. Until then, planning notes may live in the server repository.

## Project goals

Proofline aims to support:

- encrypted incident capture
- local-first media encryption before upload
- continuous upload of already-encrypted chunks
- evidence preservation if a device is lost, damaged, powered off, or taken
- trusted-contact and authorised review workflows
- clear separation between capture, escalation, sharing, and export
- careful documentation of security limits and deployment assumptions

## Current server boundaries

The current server backend:

- receives already-encrypted chunks
- stores metadata in SQLite
- stores encrypted blobs on local disk
- exposes private `/v1` API routes for write/admin-style operations
- exposes token-scoped read-only incident viewer routes
- produces encrypted ZIP evidence bundles with JSON manifests

The server does not currently provide:

- account management
- public `/v1` authentication
- push/SMS/Messenger notification workflows
- emergency-services integration
- backend decryption
- browser decryption
- raw server-held media keys
- key escrow
- playable media export
- production deployment hardening

## Security

Do not report security vulnerabilities through public GitHub issues.

For the current server implementation, follow the security policy in:

[`open-proofline/server/SECURITY.md`](https://github.com/open-proofline/server/blob/main/SECURITY.md)

Do not publish raw incident tokens, uploaded bytes, request bodies, private deployment details, plaintext, raw keys, exploit details, or user safety data.

## License

The current server implementation is licensed under the GNU Affero General Public License v3.0 only (`AGPL-3.0-only`).

Future repositories should declare their own licence explicitly.
