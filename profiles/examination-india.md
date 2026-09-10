# Profile: Examinations — India

Profile identifier: `pariksha:profile:exam-in:draft-01`

This profile is normative. It fills the blanks the core leaves open — identity substrate, candidate identifier, role taxonomy, tier assignment, quorum composition — for public examinations in India. An Implementation claiming this profile MUST meet everything below in addition to the core conformance checklist.

## Identity floor

Human participants: Aadhaar-verified via DigiLocker (including UIDAI offline artifacts), captured at credential issuance and sealed into `identity_binding`. Exam-day verification is local against the sealed template; no network call to UIDAI at presentation.
Devices: hardware attestation (attested boot, certified capability set).
Candidate identifier: APAAR.
Wallet and verification endpoint for outcome credentials: DigiLocker.
Signatures on authoring, review and custody events: eSign where a legally recognised signature is required.
Consent for sharing outcome data beyond admission: DEPA-pattern consent artefact, expressed as claims.

## Actor taxonomy

| Domain | Roles |
|---|---|
| Authority | examination body (root); `board.controller`; policy administrator |
| Artifact | paper setter; paper assembler; sealing witness; translator/moderator |
| Custody | `custody.courier`; strongroom custodian |
| Centre | `centre.super`, `centre.observer`, `centre.boardrep` (quorum); invigilator; centre validator device; render/terminal devices |
| Candidate | candidate; nominee/scribe (witnessed delegation) |
| Machine | assembly, custody and integrity agents (later rungs); platform services under service credentials |
| Oversight | `board.duty` (console, read + acknowledge); auditor (post-hoc, scoped read) |

## Proof tiers (assignment of roles to the core's four tiers)

| Tier | Proof | Roles |
|---|---|---|
| 1 | Aadhaar identity | candidate |
| 2 | Tier 1 + institutional attestation per instance | invigilator, courier, custodian, duty officer |
| 3 | Tier 2 + cross-authority endorsement (attester outside the board's root) | quorum roles; sealing officer |
| 4 | Tier 3 + multi-party issuance ceremony; fresh quorum co-signature at time of act | setter, assembler, controller, policy administrator; the root itself |

## Separation of masters

Registry rule R4 applies: a centre quorum MUST include at least one credential chaining to a root other than the conducting body's — in practice the independent observer. A quorum whose proofs all chain to one root fails verification (S3). The quorum policy for this profile is 2-of-3 by default, 3-of-3 by policy.

## Physical bridge parameters

Unlock window is per-context metadata sized to rendering logistics: duplicator-class printing for short papers; wider windows or district render hubs for booklet-scale exams. The protocol does not change; only the claims do.

## Other domains

The kernel is domain-free. Land records, procurement, evidence custody and inter-agent handoffs are profiles over the same nouns and verbs (see the companion paper, *On the Truth of Custody*, §8). Proposals for further profiles go in this directory.
