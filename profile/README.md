# Proofline

> Record the truth. Keep the keys.

Proofline is being built for moments when losing the record could matter. It helps preserve end-to-end encrypted evidence as events unfold, while giving trusted contacts controlled access when it matters.

Proofline is experimental open-source safety and evidence-capture infrastructure. It is maintained by one person, is not operated as a for-profit business, and is not production-ready emergency infrastructure.

Proofline must not be treated as emergency dispatch, emergency-services integration, a staffed response centre, or a guaranteed real-time safety system. Users and trusted contacts remain responsible for contacting emergency services when immediate help is needed.

## What Proofline is trying to support

The long-term project direction is to support:

- encrypted incident capture;
- timed safety checks;
- non-emergency interaction records;
- evidence notes;
- near-live encrypted upload of short audio, video, location, timestamp, and context chunks where clients support it;
- evidence preservation if a device is lost, damaged, powered off, destroyed, or taken;
- controlled trusted-contact access for authorised review;
- end-to-end encryption so Proofline itself is not meant to read sensitive material;
- clear separation between capture, escalation, sharing, retention, and export.

The goal is not to pretend software can replace emergency services, legal advice, a support network, or human judgment. It cannot.

## Current status

Proofline currently has three active repositories:

| Repository | Status | Purpose |
|---|---|---|
| [`server`](https://github.com/open-proofline/server) | Active, experimental | Go backend for authenticated `/v1` routes, private admin web/operator surfaces, read-only incident viewer routes, local account/session auth, email/TOTP/WebAuthn second-factor flows, encrypted chunk ingest, incident and stream metadata, contact public-key metadata, sharing grants, wrapped-key metadata, deletion/retention workflows, optional PostgreSQL/S3-compatible/Valkey backends, regional stream-ingress relay support, release workflow, and deployment documentation. |
| [`web-client`](https://github.com/open-proofline/web-client) | Active, experimental | React account portal and incident-review prototype. Current scope includes login/logout, registration and email-verification flows, conservative browser session handling, mock/live API modes, account and incident metadata views, contact/sharing/wrapped-key metadata views, Tailwind/Catalyst UI components, and frontend validation workflows. It is not a production recorder or emergency workflow. |
| [`website`](https://github.com/open-proofline/website) | Active, experimental | Static public website for user-facing project framing, current status, community services, support links, repository links, and safety boundaries. It is not a docs site, backend, client app, admin tool, or emergency system. |

Planned future repositories:

| Repository | Purpose |
|---|---|
| `open-proofline/ios-client` | Native iOS incident capture, encrypted local staging, upload, account flows, and platform-specific recording behavior. |
| `open-proofline/android-client` | Native Android incident capture, encrypted local staging, upload, account flows, and platform-specific recording behavior. |
| `open-proofline/protocol` | Shared API specs, encryption envelope specs, bundle manifests, compatibility matrix, and conformance tests. |

Those future repositories will be created only when their scope is ready. Until then, planning notes may live in the active repositories.

## What exists today

The current server backend can:

- authenticate local username/password accounts;
- manage opaque server-side sessions and optional browser cookie sessions;
- require account second-factor setup with email challenge, TOTP, or configured WebAuthn/FIDO2 security keys;
- require active second-factor verification before private admin operator access;
- expose authenticated main `/v1` routes;
- expose private admin-only web and JSON surfaces under the private admin listener;
- expose token-gated, read-only incident viewer routes;
- receive already-encrypted chunks;
- verify complete encrypted chunk uploads with SHA-256;
- store metadata in SQLite by default, with optional PostgreSQL when configured;
- store encrypted blobs on local disk by default, with optional S3-compatible object storage when configured;
- use optional Valkey/Redis-compatible coordination for selected coordination and rate-limit paths;
- create encrypted ZIP evidence bundles with JSON manifests;
- track account/device keys, trusted-contact metadata, sharing grants, and wrapped-key metadata for future authorised review flows;
- support private deletion/retention workflows and safe operator maintenance tooling;
- support a regional stream-ingress relay for temporary ciphertext staging, hash validation, core forwarding, and optimistic encrypted fanout while keeping the core API authoritative.

The current web client can:

- render an experimental React account portal prototype;
- provide login/logout, registration, and email-verification UI flows;
- keep browser session handling conservative and explicit;
- run in mock mode without a live backend;
- call live backend routes where the API contract is confirmed;
- display account, incident, stream, chunk, contact public-key, sharing-grant, and wrapped-key metadata;
- provide visible prototype and emergency-reliance warnings;
- run frontend validation with typecheck, lint, tests, build, and browser smoke checks.

## What does not exist yet

Proofline does not currently provide:

- production mobile recording clients;
- production public hosted accounts;
- production payment or billing flows;
- production account recovery;
- push, SMS, Messenger, or trusted-contact notification delivery;
- emergency-services integration;
- guaranteed real-time trusted-contact review;
- backend decryption;
- browser decryption;
- trusted-contact decryption;
- raw server-held media keys;
- key escrow;
- break-glass key access;
- playable media export;
- production deployment hardening.

## Community services

Proofline may also operate or promote separate privacy-respecting community services. These services are separate from Proofline's safety and evidence-capture system.

Community services do not store Proofline evidence, encrypted chunks, incident records, wrapped keys, account data, or safety-context records. They should not be treated as emergency infrastructure, service-level commitments, or support channels for urgent safety needs.

## Maintainer and funding reality

Proofline is currently a maintainer-led open-source project. There is no company, large team, support department, charity, nonprofit status, or emergency response centre behind it.

A future official hosted Proofline service may require paid subscriptions for cost recovery. That would be intended to help cover hosting, database, object storage, email delivery, monitoring, backup, maintenance, abuse-control, and release costs. It is not intended as profit-maximising SaaS branding.

Self-hosting remains part of the open-source direction. Donations or future subscriptions must not be treated as emergency assistance, account recovery, support priority, tax-deductible charity support, or proof that Proofline is production-ready.

## Security

Do not report security vulnerabilities through public GitHub issues.

For the current server implementation, follow the security policy in:

[`open-proofline/server/SECURITY.md`](https://github.com/open-proofline/server/blob/develop/SECURITY.md)

For the current web-client prototype, follow the security policy in:

[`open-proofline/web-client/SECURITY.md`](https://github.com/open-proofline/web-client/blob/develop/SECURITY.md)

Do not publish raw incident tokens, session tokens, secrets, uploaded bytes, request bodies, Authorization headers, private deployment details, plaintext, raw keys, raw media keys, contact private keys, wrapped-key ciphertext, exploit details, object-store credentials, stored paths, object keys, or user safety data.

## License

The current server implementation is licensed under the GNU Affero General Public License v3.0 only (`AGPL-3.0-only`).

The current web-client prototype is also intended to use the project license declared in its repository. Tailwind Catalyst/Tailwind Plus-derived component source files, if present, remain governed by the Tailwind Plus license and are used as part of the web-client application only. They must not be redistributed as a standalone UI kit, template, starter, package, or design asset set.

The public website is licensed under the GNU Affero General Public License v3.0 only (`AGPL-3.0-only`).

Future repositories should declare their own licence explicitly.
