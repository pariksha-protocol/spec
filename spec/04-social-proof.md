# 4. Social Proof

## 4.1 The identity floor

For human Participants, the identity layer MUST anchor to the identity substrate the profile names — a national or institutional identity system capable of unique-person assurance — captured at Credential issuance and sealed into the Credential's identity_binding claim. Presentation consumes this proof locally (live biometric or equivalent against the sealed template) and MUST NOT require network access to the identity substrate at presentation time. For device Participants, the identity layer is hardware attestation (attested boot, certified capability set). A profile MUST state its identity substrate and MUST provide an alternate identity-proof path for legitimate exceptions the substrate does not cover. India's binding (Aadhaar via DigiLocker, APAAR) is in the [Examination Profile — India](../profiles/examination-india.md).

## 4.2 Standing, layered above identity

Standing — current authorisation in a role — chains above identity as separately revocable claims: identity does not revoke, roles do. Both layers ride one Credential and verify in one presentation. In v1 presentations are plain signed disclosures; from v1.1 the presentation_proof field carries a zero-knowledge proof of the conjunction (“identity-verified AND valid standing for this context”) without disclosing identity to the ledger.

## 4.3 Proof tiers

Proof accumulates with authority. The required_proof_level claim in every Role Credential is enforced by the grant engine: presentation below tier is a denial.

| **Tier** | **Proof required** | **Authority carried** |
| --- | --- | --- |
| 1 | Identity floor (§4.1) | power over one's own session only |
| 2 | Tier 1 + institutional attestation, per instance | operational roles: handling, invigilating, monitoring |
| 3 | Tier 2 + cross-authority endorsement (attester outside the operating body's root) | quorum roles; sealing roles |
| 4 | Tier 3 + multi-party issuance ceremony; high-consequence acts require fresh quorum co-signature at time of act | roles that touch content or rules; the Authority root itself |

A profile MUST assign each of its named roles to a tier. The assignment for Indian public examinations is in the Examination Profile — India.
