# Security Team Charter

> Draft for Council review, accompanying the [t-security proposal](https://rust-lang.zulipchat.com/#narrow/channel/613087-security-chat/topic/Should.20we.20make.20t-security.3F). This charters the top-level `security` group; its subgroups (`security-response`, `project-security`, `ecosystem-security`) each have their own charter.
>
> `security` is proposed to live under `launching-pad` initially, revisiting top-level status after ~6 months.

## Mission

Coordinate the Rust Project's security work across its subgroups, act as an entry point for people who want to get involved in security, and keep track the big picture of the Project's overall security posture (reactive, proactive, and ecosystem-facing).

The top-level group is intentionally thin. Beyond owning and integrating the Project threat model, it does not do the hands-on security work itself; that happens in the subgroups. Its job is coordination, routing, and representation.

## How does this further the Rust Project goals?

Security work in the Project is currently spread across security-response, Rust Foundation security engineers, RustSec maintainers, and t-infra, with no single place that connects them or that a newcomer can approach. As the number and severity of supply-chain incidents grows (e.g. [arrayref](https://blog.rust-lang.org/2026/08/20/supply-chain-attack-on-arrayref/), [spearphishing attacks on Project members](https://blog.rust-lang.org/2026/09/17/targeted-attacks/)), the Project benefits from a group that can coordinate these efforts and surface issues and needs to the relevant teams. It also offers an on-ramp for new contributors.

## Responsibilities & Commitments

### Decision Maker

The top-level group is the decision maker on:

- Its own internal coordination: meeting cadence, how subgroups keep each other informed, and how cross-subgroup questions are routed.
- Proposing the creation, naming, and scope boundaries of subgroups within `security`.
    - As a group under `launching-pad`, creating or re-scoping subgroups is proposed to the Council/parent team for approval; the group does not have authority to create teams on its own.
- Which cross-cutting security needs to surface (e.g. to the Council, to the Foundation for funding, or to owning teams via the Project Goals process) and how to represent them.
- The Project threat model: the top-level group is its single owner. It decides the model's overall structure and integrates the components maintained by each subteam.

It is explicitly not the decision maker on any other team's purview: infrastructure, crates.io, and cargo decisions remain with those teams (see Authority in the proposal).

### Accountable for results

The group is primarily responsible for coordination:

- Running the coordination touchpoints between subgroups.
- Maintaining the group's public-facing "how do I get involved in Rust security?" entry point.
- Keeping the integrated Project threat model current: collecting each subteam's component and connecting them into one up-to-date model.
- Surfacing and escalating gaps, i.e. noticing when the subgroups collectively leave part of the intended security scope unowned, and raising it to the Council/parent team.

It is explicitly not accountable for the subgroups' actual outcomes (incident response times, ecosystem coverage, hardening adoption).

### Responsible for work

Hands-on work is done by the subgroups, not here. The top-level group's own "work" is limited to:

- Running coordination touchpoints between subgroups.
- Highlighting cross-cutting security needs and, where the group chooses, helping the Foundation and funding team seek funding for security work (including work that mostly happens in other teams, e.g. build-script sandboxing). 
- Maintaining the group's public-facing "how do I get involved in Rust security?" entry point.
- Integrating the subteams' threat-model components into the single Project threat model

### Consulted for input

The group should be consulted on:

- Cross-team decisions with broad security implications where no single subgroup is the obvious owner.
- Proposals to fund, staff (e.g. Maintainers in Residence), or restructure security work in the Project.

### Informed for awareness

The group should be informed of significant security-relevant activity in any subgroup or adjacent team (major hardening initiatives, ecosystem takedowns, incidents) so it can keep the overall picture current and keep subgroups in sync **but only at a post-disclosure / non-embargoed level of detail.** 

Because the top-level group has open membership, embargoed incident details, in-progress advisories, and any secrets remain confined to the relevant subgroup's access-controlled channels and are never shared into the coordination group or `#security-chat`.

## Subgroups

`security` starts with three working subteams. See each subteam's charter for more information.
- security-response - reactive - [charter](security-response-charter.md)
- project-security - proactive, Project-internal - [charter](project-security-charter.md)
- ecosystem-security - crates.io crates and ecosystem - [charter](ecosystem-security-charter.md)

## security-advisors

The group also includes an advisory pool of trusted people in a private Zulip channel, `security-advisors`. This channel acts as a rendezvous point for security operators to reach contributors
from across Rust Project teams — t-compiler, t-infra, crates.io, cargo, libs, lang, the Foundation, etc. — and individuals with relevant expertise. This allows operators to pull people into private
response threads quickly, without widening an embargo to a whole team.

The channel also offers an opportunity to privately seek feedback and a thumbs up on whether security measures meet Project norms and published policies. This is necessary because security efforts involve
some amount of cat-and-mouse tactics where public discussion of methods undermines efficacy.

The group is modeled on [`funding-advisors`](https://github.com/rust-lang/team/blob/master/teams/funding-advisors.toml). [Proposed initial members](security-advisors.toml)


## How does this group make decisions?

By consensus among its members, who include the group's lead(s), once determined, plus at least one delegate from each subgroup.

Most substantive decisions belong to a subgroup or another team; where a public Project decision is needed the group uses the standard RFC / FCP process.

New members of `security-advisors` are nominated by members of this group or its subteams, then approved by this group's lead(s).

## What work is not specifically part of this group's remit?

- Doing incident response, proactive Project hardening, or ecosystem tooling itself. Those belong to subgroups.
- Making decisions inside crates.io / cargo / infra purviews. The group can surface needs and offer help, but does not decide for those teams.

# Team Processes

## Contact Point

`@jlizen` can be point of contact until group discusses further leadership processes. General discussion happens in the `#security-chat` Zulip channel.

## Team Membership

Members: the lead(s) once determined, at least one delegate from each subgroup (so that each subgroup stays looped in), and anyone else who wants to help coordinate. Membership is intended to stay small.

Proposed initial members, along with subteam nominees: @jlizen, @Manishearth, @djc, @LawnGnome, @m-ou-se, @Eh2406

Members are expected to:

- Represent their subgroup's status and needs in coordination, and carry information back.
- Help route interested contributors and surface cross-cutting needs.

## How is team membership managed?

Each subgroup nominates its delegate(s). Additional coordinating members join by consensus of the group. `[TODO: confirm with initial members.]`

## Where does this group work?

Coordination happens in the `#security-chat` Zulip channel and, as needed, in the security group's repository/tracker. `[TODO: decide where the group tracks its coordination work.]`
