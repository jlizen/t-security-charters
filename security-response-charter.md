# Security Response Team Charter

> Draft for review by the current Security Response team (@Manishearth, @emilyalbini, @cuviper)
>
> This charter documents current practice; it is not intended to expand or change the team's scope.
> 
> The one exception is that this charter moves portions of the Rust Project threat model BESIDES security response, to sibling groups.

## Mission

Triage and respond to incoming vulnerability reports for the Rust Project, coordinate the development and disclosure of fixes, and maintain the Project's ability to respond to security incidents in a timely, confidential, and trustworthy manner.

The team is the reactive arm of the Project's security programs. It handles reports that arrive at `security@rust-lang.org` and drives them to resolution and public disclosure.

The team It is intentionally *not* responsible for proactive security work or for wider ecosystem security beyond narrow situations. Those are the scope of the sibling `project-security` and `ecosystem-security` groups under the `security` umbrella.

## How does this further the Rust Project goals?

Users and downstream distributors need to trust that vulnerabilities in the Rust toolchain and the Project's own repositories are handled responsibly: assessed quickly, fixed privately where appropriate, disclosed responsibly, and communicated clearly.

A dedicated response team ensures there is always a known, staffed path for security reporters to reach the Project. It also allows us to fine tune and document our response processes to best handle new incidents.

## Responsibilities & Commitments

### Decision Maker

The team is the final decision maker on:

- Whether an incoming report constitutes a security vulnerability in scope for the Project, and its severity assessment.
- The handling and disclosure plan for a given report: embargo timelines, the disclosure date, whether a private/pre-notified release is warranted, and coordination with reporters and downstream distributors (e.g. `distros@`, `oss-security@`).
- The content and timing of security advisories and announcements published through Project channels (security mailing list, blog, users.rust-lang.org, GitHub Security Advisories).
- The contents of the incident-response component of the Project threat model.
    - The integrated threat model is owned by the top-level `security` group.
    - security-response is responsible for the response/incident portion and brings it to the top-level group.

Fixes to the underlying vulnerable code are ultimately decided by the team that owns that code (e.g. the compiler, libs, cargo, or crates.io teams). security-response coordinates and is accountable for the response process around them, but does not override those teams' technical decisions.

### Accountable for results

The team is accountable for:

- Every report sent to `security@rust-lang.org` receiving a timely acknowledgement and being driven to a resolution (fix + disclosure, or a documented decision that no action is needed).
- Coordinated disclosure happening on the agreed timeline, including the required upstream notifications for medium-or-higher severity issues.
- The incident-response component of the Project threat model being kept current.
- The security response process itself being documented and functional (see the [wg-security-response repo](https://github.com/rust-lang/wg-security-response)), including custody of the security team's signing key and access to the shared secrets store.

### Responsible for work

The team members do the hands-on work of:

- Monitoring and triaging the `security@rust-lang.org` inbox (including decrypting GPG-encrypted reports).
- Passing `security@rust-lang.org` reports related to ecosystem incidents to `ecosystem-security` processes.
- Setting up per-incident private Zulip streams and running the investigation and response with the reporter.
- Coordinating the fix, arranging point releases/patches, and distributing patch files (signed with the security key).
- Writing and publishing advisories and announcements across the required channels, and sending the pre-disclosure notifications to `distros@lists.openwall.com` / `oss-security@lists.openwall.com`.
- Authoring and maintaining the incident-response component of the Project threat model, and feeding it to the parent group.

### Consulted for input

The team should be consulted on:

- Changes to Project infrastructure, release processes, repository policies, or security scope that would materially affect the Project's ability to respond to or contain a security incident
- Sibling `security` subgroups' proactive work where it intersects with incident handling (e.g. `project-security` guidance on repo hardening, `ecosystem-security` handling of malicious/vulnerable crates that may generate reports into this team's inbox).
- Designs of security-relevant features by owning teams (e.g. crates.io trusted publishing, cargo build-script sandboxing) where the response team's incident experience is relevant.
- `ecosystem-security` handling of security incidents, particular 

### Informed for awareness

The team should be informed of:

- Security-relevant changes shipping in `rust-lang`/`rust-lang-nursery` repositories significant enough to warrant mention in release notes or advisories.
- Ecosystem incidents handled by `ecosystem-security` (e.g. malicious-crate takedowns) so that response and ecosystem work stay coordinated even when the response team is not the one acting.

## How does this group make decisions?

Response decisions are made by team consensus, typically in the private per-incident Zulip stream, given the confidential nature of the work.

## What work is not specifically part of this team's remit?

- Proactive security of Project properties (GitHub Actions usage policy, CI hardening recommendations, publishing hygiene, spearphishing training): this belongs to `project-security`.
- Wider ecosystem security (RustSec/advisory-db operations, scanning and outreach for crates the Project does not itself depend on, malicious-crate response on crates.io):  this belongs to `ecosystem-security`
    - The exception to this is if a report in ecosystem-security scope happens to arrive through the security-response inbox, in which case security-response is responsible for handing the incident off to ecosystem-security but not following it to completion.
- Building security tooling or detection systems: response consumes such tooling but does not own its development.

# Team Processes

## Contact Point

Reports and contact go through security@rust-lang.org per the [Rust security policy](https://www.rust-lang.org/policies/security). Do not open public issues for vulnerabilities.

## Team Membership

Current members: @cuviper, @emilyalbini, @Manishearth. Alumni: alexcrichton, nikomatsakis, steveklabnik.

Team members are expected to:

- Be reachable for incident response and share the load of monitoring/triaging the `security@` inbox.
- Handle reports confidentially and follow the documented process (including key handling and coordinated-disclosure obligations).

## How is team membership managed?

Given the sensitivity of the work (access to embargoed reports, the security signing key, and the shared secrets store), membership changes warrant deliberate onboarding/offboarding, including provisioning and revoking access to those secrets.

These decisions are made via team consensus in private channels.

## Relationship to the `security` umbrella

This team is the existing Security Response working group. Its team entry in [rust-lang/team](https://github.com/rust-lang/team) is named `security-response` (already under `launching-pad`), while its repo and Zulip presence still carry the older `wg-security-response` name.
This charter uses "security-response" for the team and "wg-security-response" only for those existing artifacts. No rename is proposed here unless current team members prefer it.

This team is proposed to sit as a subgroup of the new `security` group (initially under `launching-pad`), alongside `project-security` and `ecosystem-security`.

The team is *invited* to send a delegate to the thin top-level `security` coordination group so that response and proactive work stay in sync. Given the team is small (three members), this is best-effort and optional rather than an obligation.

Any coordination across subgroups happens at a non-embargoed level. The private security-advisors Zulip channels offers a venue for sensitive cross-group communication.

## Where does this team work?

Process documentation lives in [rust-lang/wg-security-response](https://github.com/rust-lang/wg-security-response).

Live incident handling happens in private, per-incident Zulip streams on the [rust-lang Zulip instance](https://rust-lang.zulipchat.com), named `wg-security-response/<incident>`.

General (non-incident) coordination happens in the `#security-chat` Zulip channel and the `WG-security-response` Zulip group.
