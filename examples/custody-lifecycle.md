# The custody lifecycle, end to end

One examination, one centre, walked through the three verbs. Each stage names the events it MUST emit. This is illustrative; the normative requirements are in spec §7–§10 and the event schema in `schemas/event.schema.json`.

| # | Stage | Verb | What happens | Events |
|---|---|---|---|---|
| 1 | Define | — | The examination body registers the exam instance: centres, schedule, quorum policy, unlock window. Any per-centre variance from baseline references a justification. | `exam.defined`, `policy.set`, `policy.variance` |
| 2 | Register | — | Every participant that will act — officials, devices, couriers, candidates — is registered and issued a credential at the proof tier its role requires. | `participant.registered` |
| 3 | Issue | ISSUE | The assembler finalises content, embeds a per-centre watermark, encrypts one payload per receiving context, threshold-splits each content key to that context's quorum, wraps the result as an Exam Paper Credential, signs, and destroys plaintext. Destruction is attested by the sealing witness. | `papervc.issued` (per context), `key.split`, `plaintext.destroyed` |
| 4 | Distribute | CUSTODY | Sealed credentials move to their destination context, hop by hop, each hop naming both parties' credentials. Pre-staging days early is RECOMMENDED: custody of ciphertext carries no access risk. | `custody.transfer`, `custody.received` |
| 5 | Sync | — | During the last connected window the context node receives its sealed papers, its roster of Candidate/Admit credentials with sealed biometric templates, and Capability Tokens pre-authorising the window's grants (spec §9). | `context.checkpoint` |
| 6 | Arm | — | At the policy time the window opens. Nothing is decryptable before this moment; a request before it is a witnessed denial, not a log line. | `window.armed`, `denial.*` |
| 7 | Verify + Unlock | PRESENT | Verify first: issuer signature, centre binding, window, revocations, presenters' social proof at tier. Only on success: quorum members' shares unwrap, the content key reconstructs inside the presenting device's secure enclave, payload decrypts, key zeroises, grant expires on use. | `papervc.verified`, `key.requested`, `grant.issued`, `key.released`, `artifact.decrypted`, `key.expired` |
| 8 | Bridge (paper delivery only) | — | Render on a certified device directly to output; record page and copy counts; bracket the plaintext interval with observer-attested seal and distribution events; reconcile collection against witnessed counts (spec §10). | `room.sealed`, `render.completed`, `distribution.completed`, `collection.reconciled` |
| 9 | Conduct (device delivery) | PRESENT | Session binds Admit Credential + live biometric match, locally. Each response signs into the context chain. Completion issues the Response Credential with the candidate's receipt code. | `session.bound`, `response.recorded`, `session.completed` |
| 10 | Watch | — | Out-of-window, out-of-role, or same-root quorum attempts are denied automatically and surfaced to the duty role. | `denial.*`, `alert.raised`, `alert.acknowledged` |
| 11 | Federate | — | On connectivity the context's chain head, countersigned by the centre quorum, checkpoints into the national ledger as a subtree (spec §6.3). | `context.checkpoint` |
| 12 | Certify | ISSUE | The controller signs the marks list; the ledger anchors it; Result Credentials issue to candidates. The co-signed Merkle root over all context subtrees is the Integrity Certificate. | `results.anchored`, `vc.issued`, `integrity.certified` |
| 13 | Verify outcome | PRESENT | Any party, anywhere, without registration, verifies a Result Credential against signature, ledger anchor and revocation registry (spec §3.4). | `vc.verified` |

## Event vocabulary

Namespaces: `exam.*`, `policy.*`, `participant.*`, `papervc.*`, `key.*`, `custody.*`, `window.*`, `grant.*`, `artifact.*`, `room.*`, `render.*`, `distribution.*`, `collection.*`, `session.*`, `response.*`, `alert.*`, `context.*`, `results.*`, `vc.*`, `integrity.*`, and `denial.*`.

`denial.<type>` mirrors the event that was refused: a refused `key.requested` is `denial.key.requested`, carrying the refusing rule (`window.closed`, `proof.tier.insufficient`, `quorum.same-root`, `context.mismatch`, `credential.revoked`, `custody.gap`, `session.duplicate`).

Implementations MAY add types under `x-<vendor>.*`. They MUST NOT redefine the meaning of the types above.

## Two rules worth restating

- The chain authorises and witnesses; the enclave decrypts. No key or share ever touches the ledger.
- A refused attempt is an event with the same evidentiary weight as a grant. If your ledger has a "log level," you have not implemented the protocol.
