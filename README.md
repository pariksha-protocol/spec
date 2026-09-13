# The Pariksha Protocol

**Verifiable custody and conduct for examinations.**
Working Draft 01 (`draft-pariksha-core-01`) · 29 August 2026

The Pariksha Protocol is an open specification for conducting a public examination such that every artifact is a verifiable credential, every act is bound to an identified participant under explicit, expiring authority, and every event — including every refusal — is witnessed on a tamper-evident ledger.

It is delivery-agnostic (paper or device, online or offline) and implementation-agnostic. Anyone may implement it. The specification names no product.

It is a two-layer standard. The **core** (`spec/`) names no country, identity system or role — it says what must exist. A **profile** (`profiles/`) fills those blanks for one setting. Draft-01 ships with the core and one profile, *Examination Profile — India* (Aadhaar via DigiLocker, APAAR, the roles of an NTA- or state-board examination). Conformance is always "core + a named profile."

The whole protocol is four nouns, three verbs and one condition:

| Nouns | Verbs | Condition |
|---|---|---|
| Participant · Credential · Metadata · Social Proof | Issue · Custody · Present | Witnessing — an unwitnessed act has not happened |

Everything else in the specification is enumeration and constraint over these.

## Reading the specification

The spec is in [`spec/`](spec/), one file per section, in order:

1. [Scope, terminology, conformance language](spec/01-scope.md)
2. [The kernel](spec/02-kernel.md)
3. [Participants and the registry](spec/03-participants-registry.md)
4. [Social proof](spec/04-social-proof.md)
5. [The credential taxonomy](spec/05-credential-taxonomy.md)
6. [Contexts and nodes](spec/06-contexts-nodes.md)
7. [Processes: Issue, Custody, Present](spec/07-processes.md)
8. [Witnessing and the event](spec/08-witnessing-event.md)
9. [Offline operation](spec/09-offline-operation.md)
10. [The physical bridge](spec/10-physical-bridge.md)
11. [Security considerations](spec/11-security-considerations.md)
12. [Conformance checklist](spec/12-conformance.md)

Supporting material:

- [`schemas/`](schemas/) — JSON Schema for the witnessed event and the credential envelope
- [`examples/`](examples/) — worked examples: an exam-paper credential, a witnessed event, and the end-to-end custody lifecycle with its event vocabulary
- [`profiles/`](profiles/) — profiles, which are normative. [`examination-india.md`](profiles/examination-india.md) is the first: identity floor, candidate identifier, role taxonomy, tier assignment.
- [`conformance/`](conformance/) — the conformance checklist as a standalone document
- [`releases/`](releases/) — the frozen, citable draft as published (PDF/DOCX)

## Status

This is a working draft released for public comment. It was submitted to India's High-Powered Task Force on Reforms in Public Examinations (chair: Nandan Nilekani) during its August–September 2026 public consultation.

Nothing here is final. Open an issue against any section. See [GOVERNANCE.md](GOVERNANCE.md) for how changes are made and where the protocol is intended to end up.

## Companion documents

- **Pramāṇa: A National Public Utility for Examination Integrity** — the policy paper that motivates the protocol and proposes the utility, rollout ladder and governance around it. DOI: _(to be added on Zenodo publication)_
- **On the Truth of Custody** (Contextual Compute series, CC7) — the kernel theory: the artifact/action factorisation the protocol rests on. DOI: _(pending)_

## Citing

Until the Zenodo DOI is minted, cite as:

> Pariksha Protocol Editors. *The Pariksha Protocol: Verifiable Custody and Conduct for Examinations*, Working Draft 01 (draft-pariksha-core-01), 29 August 2026. https://github.com/pariksha-protocol/spec

A `CITATION.cff` is provided; GitHub renders a "Cite this repository" button from it.

## Licence

Specification text: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Schemas, examples and any code: [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0).
See [LICENSE.md](LICENSE.md).

## Editors

- **Anantha Krishnan** — architect and initial editor (Sarva Labs Inc.)

Draft-01 was prepared by Sarva Labs Inc. (Princeton, NJ) and Algix
Technologies Pvt. Ltd.  and is released for
independent stewardship. The protocol instantiates participant-centric
computation as developed in the Contextual Compute research programme.
