# Proofline

Proofline is an experimental open-source safety and evidence-capture project.

It is maintained by one person, is not operated as a for-profit business, and is
not production-ready emergency infrastructure.

The project exists to explore tools that can help people preserve encrypted
records, share critical context with trusted contacts, and review incident
metadata when something goes wrong. It is still early, security-sensitive, and
under active design.

## Maintainer and funding reality

Proofline is currently a maintainer-led open-source project. There is no company,
large team, support department, or emergency response center behind it.

The official hosted server, if offered publicly, will likely require paid
subscriptions for cost recovery. That is intended to help cover hosting,
database, object storage, email delivery, monitoring, backup, maintenance, and
release costs. It is not intended as profit-maximizing SaaS branding.

Self-hosting remains part of the open-source direction. A future one-time
donation path for the main website may be added separately, but donations are
not part of the current implementation and are not an account-access substitute
unless a later design explicitly says so.

This project does not currently claim registered charity or nonprofit status.
Do not treat subscriptions or future donations as tax-deductible unless official
project documentation says that a legally reviewed structure exists.

## Current status

Proofline currently has two active repositories:

| Repository | Status | Purpose |
|---|---|---|
| [`server`](https://github.com/open-proofline/server) | Active, experimental | Go backend for the authenticated `/v1` API, private admin surfaces, read-only incident viewer, local account/session auth, encrypted chunk ingest, incident and stream metadata, contact public-key metadata, sharing grants, wrapped-key metadata, deletion/retention workflows, optional PostgreSQL/S3-compatible/Valkey backends, release workflow, and deployment documentation. |
| [`web-client`](https://github.com/open-proofline/web-client) | Active, experimental | React account portal and incident-review prototype. Current scope includes login/logout, registration and email-verification flows, conservative browser session handling, mock/live API modes, incident metadata views, contact/sharing/wrapped-key metadata views, Tailwind/Catalyst UI components, and frontend validation workflows. |

Planned future repositories:

| Repository | Purpose |
|---|---|
| `open-proofline/ios-client` | Native iOS incident capture, encrypted local staging, upload, account flows, and platform-specific recording behavior. |
| `open-proofline/android-client` | Native Android incident capture, encrypted local staging, upload, account flows, and platform-specific recording behavior. |
| `open-proofline/protocol` | Shared API specs, encryption envelope specs, bundle manifests, compatibility matrix, and conformance tests. |

Those future repositories will be created only when their scope is ready. Until
then, planning notes may live in the active repositories.

## What Proofline is trying to support

The long-term project direction includes:

- encrypted incident capture;
- local-first media encryption before upload;
- continuous upload of already-encrypted chunks;
- evidence preservation if a device is lost, damaged, powered off, or taken;
- trusted-contact and authorised review workflows;
- clear separation between capture, escalation, sharing, retention, and export;
- careful documentation of security limits, deployment assumptions, and recovery
  boundaries;
- hosted account access only after payment, abuse-control, deployment, and
  operational hardening work is ready.

The goal is not to pretend software can replace emergency services, legal
advice, a support network, or human judgment. It cannot. Annoying, but true.

## What exists today

The current server backend can:

- authenticate local username/password accounts;
- manage opaque server-side sessions;
- expose an authenticated `/v1` API listener;
- expose private admin-only surfaces;
- expose a token-gated, read-only incident viewer;
- receive already-encrypted chunks;
- verify complete encrypted chunk uploads with SHA-256;
- store metadata in SQLite by default, with optional PostgreSQL when configured;
- store encrypted blobs on local disk by default, with optional S3-compatible
  object storage when configured;
- use optional Valkey/Redis-compatible coordination for specific coordination
  and rate-limit paths;
- create encrypted ZIP evidence bundles with JSON manifests;
- support private deletion/retention workflows and safe operator maintenance
  tooling.

The current web client can:

- render an experimental React account portal prototype;
- provide login/logout, registration, and email-verification UI flows;
- keep browser session handling conservative and explicit;
- run in mock mode without a live backend;
- call live backend routes where the API contract is confirmed;
- display incident, stream, chunk, contact public-key, sharing-grant, and
  wrapped-key metadata;
- provide visible prototype and emergency-reliance warnings;
- run frontend validation with typecheck, lint, unit tests, build, and
  Playwright smoke tests.

## What does not exist yet

Proofline does not currently provide:

- production mobile recording clients;
- production public hosted accounts;
- production payment or billing flows;
- production account recovery;
- push, SMS, Messenger, or trusted-contact notification delivery;
- emergency-services integration;
- backend decryption;
- browser decryption;
- trusted-contact decryption;
- raw server-held media keys;
- key escrow;
- break-glass key access;
- playable media export;
- production deployment hardening.

Users and trusted contacts remain responsible for contacting emergency services.
Proofline must not be treated as an emergency dispatch system.

## Hosted service direction

A future official hosted Proofline service may support public account creation
once the required backend, web-client, payment, abuse-control, deployment,
security, monitoring, backup/restore, incident-response, and operational work is
implemented and reviewed.

Hosted subscriptions are planned as cost recovery for the official shared
server. They should be described plainly as funding infrastructure and
maintenance, not as proof that Proofline is production-ready or emergency-safe.

Until that work is complete, public account creation and hosted production use
remain out of scope.

## Mobile client concepts

Proofline is planned around native iOS and Android clients for private capture,
encrypted staging, upload, safety checks, trusted-contact alerts, and evidence
review.

Early mobile interface concepts exist in Figma. They are design concepts only;
native mobile clients, account/recovery flows, and production recording behavior
are not implemented yet.

- [iOS concepts](https://www.figma.com/design/C7ojEm3GNfZ7zfFP7jPK4z/Proofline-Android---iOS-Concepts?node-id=134-2&t=p79BbGYDVQKcMCCM-1)
- [Android concepts](https://www.figma.com/design/C7ojEm3GNfZ7zfFP7jPK4z/Proofline-Android---iOS-Concepts?node-id=135-2&t=p79BbGYDVQKcMCCM-1)

## Security

Do not report security vulnerabilities through public GitHub issues.

For the current server implementation, follow the security policy in:

[`open-proofline/server/SECURITY.md`](https://github.com/open-proofline/server/blob/main/SECURITY.md)

For the current web-client prototype, follow the security policy in:

[`open-proofline/web-client/SECURITY.md`](https://github.com/open-proofline/web-client/blob/develop/SECURITY.md)

Do not publish raw incident tokens, session tokens, secrets, uploaded bytes,
request bodies, Authorization headers, private deployment details, plaintext,
raw keys, raw media keys, contact private keys, wrapped-key ciphertext, exploit
details, object-store credentials, stored paths, object keys, or user safety
data.

## License

The current server implementation is licensed under the GNU Affero General
Public License v3.0 only (`AGPL-3.0-only`).

The current web-client prototype is also intended to use the project license
declared in its repository. Tailwind Catalyst/Tailwind Plus-derived component
source files, if present, remain governed by the Tailwind Plus license and are
used as part of the web-client application only. They must not be redistributed
as a standalone UI kit, template, starter, package, or design asset set.

Future repositories should declare their own licence explicitly.
