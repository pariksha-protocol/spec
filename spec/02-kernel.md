# 2. The Kernel

The Protocol is four nouns, three verbs, and one semantic condition. Everything else in this document is enumeration and constraint.

## 2.1 Nouns

PARTICIPANT — any actor able to take a protocol action: human, organisation, or machine. Every Participant is registered (§3) and holds at least one Credential. There are no unregistered actors on the acting side of the Protocol; the sole unregistered role is the Verifier of outcomes (§3.4).

CREDENTIAL — the only artifact type. Roles, papers, responses, grants, and results are all Credentials: signed objects of the form issuer → subject, with claims, an optional encrypted payload, and a proof. The taxonomy is enumerated in §5.

METADATA — the contextual rules of a relationship, carried inside the Credential's claims: whom it is for, when it may open, under what quorum, with what variances. Policy travels inside the artifact it governs; there is no out-of-band rulebook to consult at verification time.

SOCIAL PROOF — verifiable attestation of identity and standing. Identity answers “is this a real, unique person or device”; standing answers “what is this Participant currently authorised to be.” Proof requirements are tiered by the authority a role carries (§4).

## 2.2 Verbs

ISSUE — the creation ceremony of a Credential: claims composed, payload sealed if present, keys split if quorum-held, proof signed, issuance witnessed.

CUSTODY — the movement and holding of a Credential between issuance and presentation. Custody confers possession, never access: a custodian of a sealed payload holds ciphertext and a witnessed obligation, nothing more.

PRESENT — the consumption ceremony: verification of the Credential and of the presenting Participants' proofs, followed — only on success — by unlock of any sealed payload. Presentation is verify-then-decrypt as a single ceremony; a Credential that fails verification MUST NOT reach decryption.

## 2.3 The semantic condition: witnessing

Witnessing is not a component; it is the condition under which the verbs count as having happened. Every ISSUE, every CUSTODY transfer, and every PRESENT — including every refused attempt — MUST produce a signed event on the ledger (§8). An action without a witnessed event has not occurred, in the Protocol's semantics. Denials are first-class events with the same evidentiary weight as grants.
