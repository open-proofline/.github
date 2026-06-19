# Proofline

<h2 align="center">Record the truth. Keep the keys.</h2>

<p align="center">
  <a href="https://proofline.live/"><img alt="Website: proofline.live" src="https://img.shields.io/badge/website-proofline.live-0891b2.svg" /></a>
  <a href="https://github.com/open-proofline/website/blob/main/LICENSE"><img alt="License: AGPL-3.0-only" src="https://img.shields.io/badge/license-AGPL--3.0--only-blue.svg" /></a>
  <a href="#current-status"><img alt="Status: Experimental" src="https://img.shields.io/badge/status-experimental-orange.svg" /></a>
  <a href="https://github.com/open-proofline/website/blob/main/docs/governance-and-political-alignment.md"><img alt="Governance: public-good" src="https://img.shields.io/badge/governance-public--good-22c55e.svg" /></a>
  <a href="https://github.com/open-proofline/server/blob/develop/SECURITY.md"><img alt="Security policy" src="https://img.shields.io/badge/security-policy-blue.svg" /></a>
  <a href="https://proofline.live/support/"><img alt="Support Proofline" src="https://img.shields.io/badge/support-%E2%99%A5%20Proofline-d946ef.svg" /></a>
</p>

<p align="center">
  Experimental public-interest open-source privacy and evidence infrastructure,
  built to stay in public hands.
</p>

Proofline is being built for records that should not disappear just because a
phone does. The project aims to preserve encrypted evidence as events unfold,
while keeping access explicit, bounded, and user-controlled.

Proofline is experimental. It is not an emergency service, emergency dispatch
system, emergency-services integration, staffed response center, or guaranteed
real-time response workflow.

## What This Organization Is

`open-proofline` is the GitHub organization for Proofline's public source code,
project documentation, and community-service repositories.

The organization currently includes:

- the public website and project framing surface
- the experimental Go server backend
- the experimental React web-client prototype
- best-effort community-service work kept separate from Proofline's safety and
  evidence system
- source-of-truth documentation for governance, security boundaries, and current
  implementation status

Proofline should read like public-interest infrastructure with a spine, not a
startup pitch deck that discovered the word "community" under a desk.

## What This Organization Is Not

This organization is not:

- an emergency service
- an emergency dispatch system
- emergency-services integration
- a staffed response center
- a production safety workflow
- a mobile recording app today
- a guarantee that any public deployment is production-ready
- a place to publish secrets, private deployment details, exploit payloads,
  incident data, request bodies, uploaded bytes, plaintext, raw keys,
  wrapped-key ciphertext, object-store details, or user safety data

Users and trusted contacts remain responsible for contacting emergency services.
Proofline must not be treated as a guaranteed real-time safety system.

## What Proofline Is Trying To Support

The long-term project direction is to support:

- encrypted incident capture
- timed safety checks
- non-emergency interaction records
- evidence notes
- near-live encrypted upload of short audio, video, location, timestamp, and
  context chunks where clients support it
- evidence preservation if a device is lost, damaged, powered off, destroyed, or
  taken
- controlled trusted-contact access for authorized review
- end-to-end encryption so Proofline itself is not meant to read sensitive
  material
- clear separation between capture, escalation, sharing, retention, and export

The goal is not to pretend software can replace emergency services, legal
advice, a support network, or human judgment. It cannot.

## Current Status

Proofline is experimental, maintainer-led, and not production-ready emergency
infrastructure.

Current core repositories:

| Repository                                                                  | Status                | Role                                                                                                                                                                                                                                                                                                                                                                     |
| --------------------------------------------------------------------------- | --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [`open-proofline/website`](https://github.com/open-proofline/website)       | Current, experimental | Static public website for user-facing project framing, current status, community services, support links, repository links, governance posture, README baseline, and safety boundaries. It is not a backend, client app, admin tool, or emergency system.                                                                                                                |
| [`open-proofline/server`](https://github.com/open-proofline/server)         | Current, experimental | Go backend for authenticated `/v1` routes, private admin web/operator surfaces, read-only incident viewer routes, local account/session auth, email/TOTP/WebAuthn second-factor flows, encrypted chunk ingest, metadata, storage, sharing/wrapped-key metadata, deletion/retention workflows, optional PostgreSQL/S3-compatible/Valkey backends, relay support, and docs. |
| [`open-proofline/web-client`](https://github.com/open-proofline/web-client) | Current, experimental | React account portal and incident-review prototype. Current scope includes login/logout, registration and email-verification flows, conservative browser session handling, mock/live API modes, account and incident metadata views, contact/sharing/wrapped-key metadata views, Tailwind/Catalyst UI components, and frontend validation workflows.                     |

Planned future repositories:

| Repository                      | Status  | Intended Role                                                                                                             |
| ------------------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------- |
| `open-proofline/ios-client`     | Planned | Future native iOS capture, encrypted local staging, upload, account flows, and platform-specific recording behavior       |
| `open-proofline/android-client` | Planned | Future native Android capture, encrypted local staging, upload, account flows, and platform-specific recording behavior   |
| `open-proofline/protocol`       | Planned | Future shared API specs, encryption envelope specs, bundle manifests, compatibility matrix, and conformance tests         |

Planned repositories should not be described as implemented until they exist and
their scope is documented. Prototype optimism is not a safety feature.

## Source-Of-Truth Map

Use the right source for the claim:

| Topic                                                 | Read                                                                                                                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Public website, project framing, and source links     | [`open-proofline/website`](https://github.com/open-proofline/website)                                                                                   |
| Governance and political posture                      | [`website/docs/governance-and-political-alignment.md`](https://github.com/open-proofline/website/blob/main/docs/governance-and-political-alignment.md)  |
| Reusable README structure and public voice            | [`website/docs/repository-readme-baseline.md`](https://github.com/open-proofline/website/blob/main/docs/repository-readme-baseline.md)                  |
| Current public-facing project status                  | [`proofline.live/status/`](https://proofline.live/status/)                                                                                              |
| Backend behavior, deployment, API, and security facts | [`open-proofline/server`](https://github.com/open-proofline/server)                                                                                     |
| Web-client behavior and prototype limits              | [`open-proofline/web-client`](https://github.com/open-proofline/web-client)                                                                             |
| Community services and their boundaries               | [`proofline.live/services/`](https://proofline.live/services/)                                                                                          |
| Support and donation boundaries                       | [`proofline.live/support/`](https://proofline.live/support/)                                                                                            |

Repository-specific facts belong in the repository that owns them. Project-wide
governance posture belongs in the website repository.

## Governance And Public-Good Posture

Proofline is intended to grow as public-good open-source infrastructure. The
planned long-term direction is a non-distributing cooperative or similar
mission-locked public-good structure aligned with cooperative and libertarian
socialist principles.

The core posture:

- public-good infrastructure
- workplace democracy and shared accountability
- transparent worker compensation
- pay for labour, not ownership extraction
- surplus reinvestment into Proofline and aligned public-good work
- self-hosting and open source as anti-capture design constraints
- resistance to vendor lock-in, investor capture, and trust-branded SaaS
  mutation

Proofline does not currently claim to be an incorporated cooperative, registered
charity, registered nonprofit, foundation, company, or staffed governance body.
If the project reaches that stage, governance should make project capture
harder, not merely better branded.

Read the canonical source:
[`website/docs/governance-and-political-alignment.md`](https://github.com/open-proofline/website/blob/main/docs/governance-and-political-alignment.md).

## Maintainer And Funding Reality

Proofline is currently a maintainer-led open-source project. There is no company,
large team, support department, charity, nonprofit status, or emergency response
center behind it.

Donations are optional and help with maintainer time, development,
documentation, testing, security-conscious review, hosting, monitoring, backups,
maintenance, abuse-control, and release work. The boring parts are,
unfortunately, load-bearing.

Donations and contributions do not create accounts, unlock features, provide
support priority, provide emergency assistance, create ownership, produce
investment returns, or imply tax-deductible charity status.

Future official hosted-server cost recovery, subscriptions, or payment-gated
account access, if they exist, should recover hosting and maintenance costs.
They should not turn Proofline into a profit-maximizing SaaS creature wearing a
public-good hat.

Support information lives at
[`proofline.live/support/`](https://proofline.live/support/).

## What Exists Today

At a high level:

- the public website is live at [`proofline.live`](https://proofline.live)
- the server repository contains the experimental Go backend, authenticated
  `/v1` API, private admin surfaces, encrypted chunk ingest, metadata storage,
  token-scoped incident viewer, release workflow, and deployment/security docs
- the web-client repository contains an experimental React account and
  incident-review prototype for authenticated metadata review and future
  user-facing account flows
- community services are operated separately from Proofline's safety, evidence,
  account, and emergency boundaries

The current server backend can authenticate local accounts, manage sessions and
reviewed second-factor flows, expose authenticated main routes and private admin
surfaces, receive already-encrypted chunks, verify uploads, store encrypted
blobs and metadata, create encrypted ZIP evidence bundles, track
trusted-contact and wrapped-key metadata for future authorized review flows, and
support selected relay and operator-maintenance workflows.

The current web client can render an experimental account portal prototype,
provide login/logout, registration, and email-verification flows, run in mock or
reviewed live API modes, display account and incident metadata views, display
contact/sharing/wrapped-key metadata views, show prototype and
emergency-reliance warnings, and run frontend validation.

For implementation details, read the owning repository. Summaries here are not a
substitute for source-of-truth docs.

## What Does Not Exist Yet

Proofline does not currently provide:

- production mobile recording clients
- production public hosted accounts
- production payment or billing flows
- production account recovery
- push, SMS, Messenger, or trusted-contact notification delivery
- emergency-services integration
- guaranteed real-time trusted-contact review
- backend decryption
- browser decryption
- trusted-contact decryption
- raw server-held media keys
- key escrow
- break-glass key access
- playable media export
- public production admin/operator surfaces
- production deployment hardening

Future concepts must stay future-tense unless the source repositories document
them as implemented.

## Community Services

Proofline may operate separate public-interest open-source services, such as the
current best-effort Redlib community service listed on the website.

These services may be useful to the public web, but they are not part of
Proofline's evidence system. They do not store Proofline evidence records,
encrypted chunks, incident records, wrapped keys, account data, or safety-context
data. They should not be treated as emergency infrastructure, service-level
commitments, or support channels for urgent safety needs.

Read the current service boundaries at
[`proofline.live/services/`](https://proofline.live/services/).

## Mobile Client Concepts

Proofline is planned around native iOS and Android clients for private capture,
encrypted staging, upload, safety checks, trusted-contact alerts, and evidence
review.

Early mobile interface concepts exist in Figma. They are design concepts only;
native mobile clients, account/recovery flows, and production recording behavior
are not implemented yet.

- [iOS concepts](https://www.figma.com/design/C7ojEm3GNfZ7zfFP7jPK4z/Proofline-Android---iOS-Concepts?node-id=134-2&t=p79BbGYDVQKcMCCM-1)
- [Android concepts](https://www.figma.com/design/C7ojEm3GNfZ7zfFP7jPK4z/Proofline-Android---iOS-Concepts?node-id=135-2&t=p79BbGYDVQKcMCCM-1)

## Security Reporting

Do not report security vulnerabilities through public GitHub issues.

For the current server implementation, follow:

[`open-proofline/server/SECURITY.md`](https://github.com/open-proofline/server/blob/develop/SECURITY.md)

For the current web-client prototype, follow:

[`open-proofline/web-client/SECURITY.md`](https://github.com/open-proofline/web-client/blob/develop/SECURITY.md)

Do not publish raw incident tokens, session tokens, secrets, uploaded bytes,
request bodies, Authorization headers, private deployment details, plaintext,
raw keys, raw media keys, contact private keys, wrapped-key ciphertext, exploit
details, object-store credentials, stored paths, object keys, or user safety
data.

## Public Voice

Proofline's public voice should be:

- serious about safety, privacy, and public trust
- clear and humane
- principled without becoming foggy
- dryly witty where the humour clarifies values
- openly anti-SaaS and anti-capture when discussing governance, vendors,
  funding, and community services

Keep safety, security, implementation status, metadata, navigation, encryption,
decryption, key-custody, vulnerability-reporting, and cryptocurrency transaction
warnings plain. One sharp line per section is usually enough.

## Working With The Repositories

Each active code repository owns its own local development and validation
commands. Start with the repository README and security policy before changing
behavior or public claims.

Useful entry points:

- [`website/README.md`](https://github.com/open-proofline/website/blob/main/README.md)
- [`server/README.md`](https://github.com/open-proofline/server/blob/develop/README.md)
- [`web-client/README.md`](https://github.com/open-proofline/web-client/blob/develop/README.md)

Current files override stale assumptions. Reusable prompts and summaries help
with review, but they are not audits, certifications, or endorsements.

## License

Active code repositories declare their own licenses. The website and current
server implementation are licensed under the GNU Affero General Public License
v3.0 only (`AGPL-3.0-only`).

The web-client repository also contains its own license and third-party license
notes. Tailwind Catalyst/Tailwind Plus-derived component source files, if
present, remain governed by the Tailwind Plus license and must not be
redistributed as a standalone UI kit, template, starter, package, or design
asset set.

Future repositories should declare their own license explicitly.
