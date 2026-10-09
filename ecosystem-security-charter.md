# Ecosystem Security Team Charter

> Draft for Council review, accompanying the [t-security proposal](https://rust-lang.zulipchat.com/#narrow/channel/613087-security-chat/topic/Should.20we.20make.20t-security.3F). `ecosystem-security` is a proposed new subgroup of `security` (initially under `launching-pad`).
>
> As a new group, this charter is somewhat aspirational; initial team members can tweak the scope based on early discussions. Moving RustSec/advisory-db inside rust-lang and under this group is a separate proposal, though it seems like a good idea in the future.

## Mission

Improve the security posture of the wider Rust ecosystem, including crates published on crates.io, and other non-Rust Project software.

This spans proactive work (tooling, detection, information feeds, community guidance) and response work (advisories, author outreach, coordinating action on malicious or vulnerable crates).

## How does this further the Rust Project goals?

Rust's value depends heavily on a trustworthy crate ecosystem, but, at the time of writing, ecosystem security is fragmented: RustSec/advisory-db lives under wg-secure-code, malicious-crate response falls implicitly on the crates.io oncall and Foundation security engineers, and proactive tooling is scattered. Consolidating this into one group gives the ecosystem a coherent home, a sustainable path for response, and an accessible entry point for the growing set of contributors interested in this space.

## Responsibilities & Commitments

### Decision Maker

The team is the decision maker on:

- The design and roadmap of ecosystem-security tooling and information feeds it owns or maintains (e.g. scanning pipelines, detection heuristics, CI tooling).
- Its own internal division of labor between "response" (advisories, takedown coordination, author outreach) and "proactive" (scanning, tooling, feeds).
- The content and publication of security advisories for ecosystem crates (RustSec / advisory-db), once RustSec lives here (contingent on a separate proposal)

The team is **not** the decision maker on crates.io or cargo behavior. Actions taken on crates.io (e.g. removing a malicious crate, acting on ownership) are done only under explicit delegation from the crates.io team, with access granted and revocable by them.

### Accountable for results

The team is accountable for:

- Ecosystem-security tooling and feeds it commits to remaining maintained and useful to consumers.
- Malicious/vulnerable-crate situations having an owner for the parts within this group's remit: reaching out to affected/unreachable authors and publishing advisories. Actioning crates on crates.io (yank/quarantine/delete) stays with crates.io (see "Responsible for work" for more on delegation).
    - The group will set standards for which cases the group will take action on. The group does not assume responsibility for resolving all cases.
- Ecosystem vulnerability reports and advisories being triaged and published in a timely way (RustSec operations). `[Once RustSec is placed here via separate proposal.]`

### Responsible for work

The team members do the work of:

- Authoring and maintaining the ecosystem component of the Project threat model (crates ecosystem / supply-chain threats), contributed to the parent `security` group to include in the broader Project threat model.
- Building and running detection/scanning (e.g. typosquatting checks, dependency-graph analysis, publish-time checks that route suspicious uploads to a manual review queue, continuous scanning of published crates to enrich feeds).
- Author outreach for vulnerable crates. **Coordinating** with the crates.io team on clearly-malicious crates, providing evidence and recommendations. 
    - The group starts with no delegated authority on crates.io. Down the road, the crates.io team may choose to delegate some operational authority to this group. If they do, it happens only under an explicit, revocable program that spells out audit logging, review for destructive actions (deletion), and who is accountable.
    - Setting that up is crates.io's call and is out of scope for the initial chartering request.
- Producing consumer-facing security tooling/guidance (e.g. nicer GitHub Actions around cargo audit/deny/vet-style checks)
    - Note that formal Project adoption of external tools is a separate proposal.
- (If the team chooses to establish it) staffing an opt-in, trained ecosystem-security oncall operating under crates.io-delegated access. This needs more design and is explicitly *not* part of the initial chartering request.
- RustSec / advisory-db maintenance and advisory authoring. `[Once RustSec is placed here via separate proposal.]`

### Consulted for input

The team should be consulted on:

- crates.io / cargo designs with ecosystem-security implications (e.g. trusted publishing, yanking/quarantine semantics, publish-time policy).
- Project decisions about adopting or first-partying ecosystem security tooling.

### Informed for awareness

The team should be informed of:

- Project-internal incidents from security-response that have ecosystem spillover.
- Relevant Foundation security-engineering work, to align and avoid duplication.

## How does this group make decisions?

By team consensus, with a clear internal understanding of who leads response vs. proactive work. Advisory publication follows RustSec/advisory-db's existing process; broader Project decisions use the standard [RFC/FCP process](../../common/rfc_fcp.md). `[TODO: confirm with initial members and with RustSec maintainers.]`

## What work is not specifically part of this group's remit?

- Project-internal hardening (Project repos/CI/publishing): belongs to project-security.
- Reactive response to vulnerabilities in Project-owned code: belongs to security-response.
- Deciding crates.io / cargo policy or operating their systems outside delegated actions: — stays with those teams.
- Formal Project adoption of external tooling (cargo audit/vet/deny, etc.) as governed by Rustlang
    - Individual contribution is fine.
    - This group may raise proposals for adoption of tools to the broader Project.
    - The RustSec/advisory-db placement is an example of tooling that will require a process beyond this group's initial charter.

# Team Processes

## Contact Point

`@jlizen` can be point of contact until group discusses further leadership processes. General discussion happens in the `#security-chat` Zulip channel.

## Team Membership

Proposed initial members (all pending confirmation): @jlizen, @djc, @LawnGnome, @walterhpearce, @amousset, @alex, @tarcieri, @teor2345, @Eh2406

Members are expected to:

- Contribute recurring work to advisory operations, tooling/detection, or ecosystem response.
- When acting on crates.io, operate strictly within crates.io-delegated authority and access.
- Follow the [common member requirements](../../common/member_requirements.md).

## How is team membership managed?

`[TODO: to be defined by the initial members, in coordination with RustSec maintainers]`

## Relationship to the `security` umbrella, RustSec, and wg-secure-code

- security: ecosystem-security is a subgroup of `security` (initially under `launching-pad`), expected to send at least one delegate to the top-level coordination group.
- RustSec: should ultimately be housed in this group, but this will be discussed in a separate proposal which @djc intends to drive
- wg-secure-code: almost certainly belongs here, but we want to have further discussions before moving forward.

## Where does this group work?

`[TODO: decide on a repository/tracker.]` 

Primarily async, on Zulip. We can use the `#security-chat` Zulip channel until the throughput of the channel becomes overwhelming, at which point we can split.

We expect to spin up recurring meetings but need to discuss further first.

RustSec work would continue in the advisory-db / rustsec repositories.
