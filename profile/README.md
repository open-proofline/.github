# Proofline

**Alert your people. Record the truth.**

Proofline is an open-source safety and evidence-capture project intended to help people notify trusted contacts, share critical context, and preserve a secure record when something goes wrong.

The project is designed around preserving encrypted records of important incidents, including emergencies, safety checks, evidence notes, and non-emergency interactions where a durable private record may matter.

Proofline is experimental and not production-ready public infrastructure.

## Current status

Proofline is currently split across two active repositories:

| Repository                                                   | Status               | Purpose                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------------------------------ | -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`server`](https://github.com/open-proofline/server)         | Active, experimental | Go backend for the main authenticated `/v1` API, private admin dashboard, read-only incident viewer, local account/session authentication, encrypted chunk ingest, incident/stream metadata, contact public-key metadata, sharing grants, wrapped-key metadata, deletion/retention workflows, optional SQLite/PostgreSQL metadata, optional local/S3-compatible encrypted blob storage, optional Valkey/Redis-compatible coordination, Docker/GHCR release workflow, and deployment documentation. |
| [`web-client`](https://github.com/open-proofline/web-client) | Active, experimental | React account portal and incident-review prototype. Current scope includes login/logout prototype flows, conservative browser session handling, mock/live API modes, incident metadata views, contact public-key metadata views, sharing-grant metadata views, wrapped-key metadata views, Tailwind/Catalyst UI components, and frontend validation workflows. Future scope may include paid public account registration and separately scoped browser-based recording prototypes.                 |

Planned future repositories:

| Repository                      | Purpose                                                                                                                    |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `open-proofline/ios-client`     | Native iOS incident capture, encrypted local staging, upload, account flows, and platform-specific recording behavior.     |
| `open-proofline/android-client` | Native Android incident capture, encrypted local staging, upload, account flows, and platform-specific recording behavior. |
| `open-proofline/protocol`       | Shared API specs, encryption envelope specs, bundle manifests, compatibility matrix, and conformance tests.                |

These future repositories will be created when their scope is ready. Until then, planning notes may live in the active repositories.

## Project goals

Proofline aims to support:

* encrypted incident capture
* local-first media encryption before upload
* continuous upload of already-encrypted chunks
* evidence preservation if a device is lost, damaged, powered off, or taken
* trusted-contact and authorised review workflows
* clear separation between capture, escalation, sharing, retention, and export
* clear documentation of security limits, deployment assumptions, and recovery boundaries
* public hosted account access only after payment, abuse-control, deployment, and operational hardening work is ready

## Current server boundaries

The current server backend can:

* authenticate local username/password accounts
* manage opaque server-side sessions
* expose a main authenticated `/v1` API listener
* expose a private `/admin` dashboard listener
* expose a token-gated, read-only incident viewer
* receive already-encrypted chunks
* verify complete encrypted chunk uploads with SHA-256
* provide metadata-backed `Idempotency-Key` support for complete chunk retries
* store metadata in SQLite by default, with optional PostgreSQL when explicitly configured
* store encrypted blobs on local disk by default, with optional S3-compatible object storage when explicitly configured
* use optional Valkey/Redis-compatible coordination for startup checks, route-class counters, and short-lived complete-upload leases
* maintain incident, stream, chunk, check-in, deletion, retention, contact public-key, sharing-grant, and wrapped-key metadata
* provide owner/admin incident authorization
* create encrypted ZIP evidence bundles with JSON manifests
* support private deletion/retention workflows and safe operator maintenance tooling
* publish server releases, binaries, Docker images, and deployment documentation

The server is still experimental. Public deployment still requires deployment-specific TLS, edge filtering, abuse controls, browser credential review, logging review, monitoring, backup/restore drills, incident response planning, external security review, and operational hardening.

Admin/operator surfaces must not be exposed publicly. Existing `/v1/admin/...` JSON routes remain authenticated admin-only routes and must be blocked from public edges. The private `/admin` dashboard listener must remain behind localhost, LAN, WireGuard, a firewall, or a strict reverse proxy.

The server does not currently provide:

* production public account registration
* payment-gated account creation
* production account recovery
* push/SMS/Messenger notification workflows
* emergency-services integration
* backend decryption
* browser decryption
* trusted-contact decryption
* raw server-held media keys
* key escrow
* break-glass key access
* playable media export
* production deployment hardening

## Current web-client boundaries

The current web client can:

* render an experimental React account portal prototype
* provide login/logout prototype flows
* maintain conservative memory-first session state
* optionally use local-storage session persistence for local development only
* run in mock mode without a live backend
* call live backend routes where the API contract is confirmed
* display incident metadata
* display stream and chunk metadata
* display contact public-key metadata
* display sharing-grant metadata
* display wrapped-key metadata
* provide visible prototype and emergency-reliance warnings
* run frontend validation with typecheck, lint, unit tests, build, and Playwright smoke tests

The web client does not currently provide:

* production account registration
* payment or billing flows
* recording or capture behavior
* browser decryption
* trusted-contact decryption
* key unwrapping
* playable media export
* emergency dispatch
* notification delivery
* production safety workflows

Future browser-based recording may be explored as a separately scoped prototype for desktop/browser use cases such as meetings, calls, interaction records, evidence notes, or screen capture. Browser recording must not be presented as a replacement for native iOS or Android recording clients, and must not be described as reliable emergency capture.

## Future hosted service direction

The intended public service model is not invite-only by default.

When the backend and deployment are ready, Proofline may support public paid account creation on a hosted server. Account creation should be payment-gated and backed by reviewed server-side account lifecycle, billing state, abuse controls, and disabled/unpaid account behavior.

Public deployment must come after the required backend, web-client, payment, security, monitoring, and operational work is implemented, reviewed, documented, and tested.

Until then, public account creation remains out of scope.

## Mobile client concepts

Proofline is planned around native iOS and Android clients for private recording, encrypted staging, upload, safety checks, trusted-contact alerts, and evidence review.

The images below are from the Android Material 3 Figma prototypes. They are early interface concepts only. Native mobile clients, account/recovery flows, and production recording behavior are not implemented yet.

![Proofline Android M3 UI concept screens](/assets/android-m3-concept-screens.png)

**View the full mobile concept set on Figma:**

* [iOS 26 Concepts](https://www.figma.com/design/C7ojEm3GNfZ7zfFP7jPK4z/Proofline-Android---iOS-Concepts?node-id=134-2&t=p79BbGYDVQKcMCCM-1)
* [Android M3 Concepts](https://www.figma.com/design/C7ojEm3GNfZ7zfFP7jPK4z/Proofline-Android---iOS-Concepts?node-id=135-2&t=p79BbGYDVQKcMCCM-1)

## Security

Do not report security vulnerabilities through public GitHub issues.

For the current server implementation, follow the security policy in:

[`open-proofline/server/SECURITY.md`](https://github.com/open-proofline/server/blob/main/SECURITY.md)

For the current web-client prototype, follow the security policy in:

[`open-proofline/web-client/SECURITY.md`](https://github.com/open-proofline/web-client/blob/develop/SECURITY.md)

Do not publish raw incident tokens, session tokens, secrets, uploaded bytes, request bodies, Authorization headers, private deployment details, plaintext, raw keys, raw media keys, contact private keys, wrapped-key ciphertext, exploit details, object-store credentials, stored paths, object keys, or user safety data.

## License

The current server implementation is licensed under the GNU Affero General Public License v3.0 only (`AGPL-3.0-only`).

The current web-client prototype is also intended to use the project license declared in its repository. Tailwind Catalyst/Tailwind Plus-derived component source files, if present, remain governed by the Tailwind Plus license and are used as part of the web-client application only. They must not be redistributed as a standalone UI kit, template, starter, package, or design asset set.

Future repositories should declare their own licence explicitly.
