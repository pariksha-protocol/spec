# 8. Witnessing and the Event

Every event is an instance of one schema (below). Normative rules: E1 — participant is mandatory; there are no system events without a credential. E2 — events hash-chain per context (prev) and anchor to the ledger. E3 — denials are events, not log lines; a refused presentation carries the refusing rule and the presenting credential. E4 — policy changes, registrations, and revocations are events. E5 — the ledger is permissioned with encrypted participant fields in v1; it MUST NOT function as a public directory of officials. presentation_proof is null in v1 and carries the zero-knowledge proof from v1.1.

```jsonc
{
  "event_id": "evt_01J9...",
  "type": "key.released",            // or: papervc.issued, custody.transfer,
                                     //     papervc.verified, artifact.decrypted,
                                     //     session.bound, response.recorded,
                                     //     session.completed, denial.*, ...
  "exam_id": "BOARD-2026-P1",
  "context": "centre:C012",
  "artifact": { "credential_id": "PKG-C012", "sha256": "9f3a..." },
  "participant": { "credential": "vc:example:off:8842",
                   "role": "centre.super" },   // role names are profile-defined
  "grant": { "grant_id": "grt_7be1", "scope": "decrypt:PKG-C012",
             "quorum": "2-of-3", "window": { "start": "...", "end": "..." } },
  "witness": { "ledger_anchor": "ledger:tx:4c19...", "ts": "..." },
  "presentation_proof": null,
  "prev": "sha256:1d0c..."
}
```
