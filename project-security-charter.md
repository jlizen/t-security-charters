# Project Security Team Charter

> Draft for Council review, accompanying the [t-security proposal](https://rust-lang.zulipchat.com/#narrow/channel/613087-security-chat/topic/Should.20we.20make.20t-security.3F). `project-security` is a proposed new subgroup of `security` (initially under `launching-pad`).
>
> As a new group, this charter is somewhat aspirational.

## Mission

Proactively protect Project-owned repositories and infrastructure and improve the forward security posture of Rust Project contributors. Success for this group means that fewer incidents ever reach `security-response`.

The team produces guidance, tooling, training, and threat-model input that Project teams and contributors are encouraged to adopt, and works alongside t-infra to harden the Project's own resources.

This is the complement to `security-response`: response is reactive, project-security is preventive. Both concern the Project's own systems (as opposed to `ecosystem-security`, which focuses primarily on the wider crates.io ecosystem).

## How does this further the Rust Project goals?

The recent rise in targeted attacks and supply-chain incidents shows that the Project's own repos, CI, and publishing flows are high-value targets. Today, proactive hardening happens ad hoc (some under t-infra, some via the Foundation).

A dedicated group that develops shared best-practice guidance, training, and enforcement tooling raises the baseline security of Project resources while respecting each owning team's autonomy.

## Responsibilities & Commitments

### Decision Maker

The team is the decision maker on:

- The content of its recommendations, guidance, and training (e.g. safe GitHub Actions usage policy, crates.io publishing hygiene, CI hardening advice, "you are a high-value target" anti-spearphishing training).
- The design of any tooling it builds to help teams audit or enforce those recommendations.
- The Project-infrastructure-and-contributors component of the threat model
     - project-security is responsible for authoring and maintaining it
     - Covers both Project-owned infrastructure (repos, CI, publishing) and the forward security posture of Project contributors themselves (contributors as high-value targets, account/credential and device hygiene, spearphishing).
     - The overall threat model is owned by the parent `security` group, but project-security decides the content of its portion.

The team *does not decide* whether other teams adopt its recommendations, and does not hold decision authority over infrastructure, crates.io, or cargo. Adoption is at each owning team's discretion. These are recommendations with supporting tooling, not requirements (per @Mark-Simulacrum's feedback). This mirrors how t-infra already operates with the teams whose systems it touches.

### Accountable for results

The team is accountable for:

- The existence and upkeep of a set of proactive-security recommendations for Project properties.
- Proposing concrete mitigations to reduce the blast radius of likely failure modes (e.g. credential compromise of an individual Project member) and sharing them with owning teams (primarily t-infra).
- Delivering a security-awareness training program
- Growing a cross-team network of security-oriented Rust Project members, who can guide their peers.

### Responsible for work

The team members do the work of:

- Writing and maintaining Rust Project guidance/policies for GitHub Actions usage, CI, and publishing hygiene, and building audit/enforcement tooling for them.
- Developing and delivering trainings (anti-spearphishing, high-value-target awareness) and recruiting/mentoring per-team security points of contact.
    - The Rust Foundation will offer funding and logistics support for this work.
- Authoring and maintaining the Project-infrastructure-and-contributors component of the threat model
- Collaborating with t-infra on proactive hardening initiatives (e.g. work in the spirit of crabwatch)

### Consulted for input

The team should be consulted on:

- Changes to Project CI, repository settings, or publishing flows where a security perspective is valuable.
- Designs of security-relevant Project-infrastructure features by owning teams (t-infra, crates.io, cargo).
- Decisions about moving critical tooling with security implications into rust-lang (e.g. widely-used GitHub Actions)

### Informed for awareness

The team should be informed of:

- Incidents handled by security-response, so its preventive guidance can learn from real failures.
- Infrastructure changes across the Project with security relevance.

## How does this group make decisions?

By team consensus; where a public Project decision or a broadly-scoped recommendation is involved, via the standard RFC/FCP process. `[TODO: confirm with initial members.]`

## What work is not specifically part of this group's remit?

- Reactive incident response: belongs to security-response.
- Ecosystem-facing security (crates.io-wide scanning, RustSec, malicious-crate response): belongs to ecosystem-security.
- Owning or operating other teams' infrastructure: project-security only advises and offers tooling.
    - Any hands-on operation of Project repos/CI/publishing happens only under explicit, revocable delegation from the team that owns that surface (primarily **t-infra**, and the relevant repo/org owners for a given repository), with access scope defined and granted by them.
- Building missing security *features* (e.g. trusted-publishing lockdown, build-script sandboxing) — those are for the owning teams (crates.io, cargo)
    - Project-security may help surface the need via Project Goals and other collaboration venues.

# Team Processes

## Contact Point

`[TODO: figure out a lead / point person.]` General discussion happens in the `#security-chat` Zulip channel.

## Team Membership

Proposed initial members (all pending confirmation): @Mark-Simulacrum, @LawnGnome, @m-ou-se, and @teor2345

Members are expected to:

- Contribute to guidance, tooling, training, or threat-model work on a recurring basis.
- Engage with owning teams (especially t-infra) collaboratively, respecting their authority.

## How is team membership managed?

`[TODO: to be defined by the initial members.]`

## Relationship to the `security` umbrella

A subgroup of `security` (initially under `launching-pad`). Expected to send at least one delegate to the top-level coordination group.

## Where does this group work?

`[TODO: decide on a repository/tracker.]` Discussion in the `#security-chat` Zulip channel.
