# 5. The Credential Taxonomy

Twelve types, four families, one shape: issuer → subject, claims, optional payload, proof. Cross-cutting requirements: every Credential MUST carry scope (context-bound, never global), issuing_authority, revocation_registry_uri, and presentation_proof_type (plain in v1; zk from v1.1). Policy variance from a baseline MUST be drawn from an enumerated set and MUST reference a witnessed justification event (bounded degrees of freedom: window width, quorum size, observer count).

## Family 1 — Identity and role

| **#** | **Credential** | **Issuer → Subject** | **Key metadata claims** |
| --- | --- | --- | --- |
| 1 | Authority | root ceremony → examination body | jurisdiction; exam_types; validity; revocation_registry_uri |
| 2 | Role | authority/registrar → official | role; scope (exam-instance + context); identity_binding (sealed); issuing_authority; required_proof_level; validity_window |
| 3 | Device | certification → device | device_class (validator │ terminal │ render │ quorum-app); attestation; certified_capabilities; context_binding (per instance); validity (per exam-day) |
| 4 | Candidate | authority → candidate | candidate_id (profile-defined; APAAR in India); identity_binding (face template, sealed to centre); registered_exam; assigned_context (one hall); accommodations (incl. nominee ref) |

## Family 2 — Artifact

| **#** | **Credential** | **Issuer → Subject** | **Key metadata claims** |
| --- | --- | --- | --- |
| 5 | Exam Paper | setter/assembly authority → receiving context (centre; candidate at later rungs) | exam_id; centre_binding; unlock_window; quorum_policy; payload_sha256; watermark_commitment; language; form_id; policy_variance_ref; payload = P2P-encrypted paper; keyShares[] per quorum member |
| 6 | Response | bound session (device + candidate) → evaluation authority | session_ref; candidate_ref; exam_id; chain_head; response_count; timestamps; receipt_code; payload = responses sealed to collection key |
| 7 | Marks-List | controller → exam instance | exam_id; evaluation_method; result_set_hash; normalization_ref (published equating parameters); ledger_anchor; signed_ts |

## Family 3 — Authority in motion

| **#** | **Credential** | **Issuer → Subject** | **Key metadata claims** |
| --- | --- | --- | --- |
| 8 | Grant | grant engine → requesting participant(s) | scope (e.g. decrypt:PKG-C012); quorum_satisfied (co-signing credentials); window; expires_on_use = true; context |
| 9 | Capability Token | grant engine at last sync → centre context | as Grant, plus offline_valid = true; sync_deadline; local_chain_required = true |

## Family 4 — Outcome

| **#** | **Credential** | **Issuer → Subject** | **Key metadata claims** |
| --- | --- | --- | --- |
| 10 | Result | authority (via marks-list chain) → candidate / candidate_id | exam_id; score; percentile; rank; marks_list_ref; ledger_anchor; revocation_status_uri; issued_ts — verifiable by anyone, no registration |
| 11 | Admit | authority → candidate | exam_id; centre; seat; report_time; identity_binding_ref (into #4); single_use_binding = true (consumed at session bind) |
| 12 | Integrity Certificate | authority + independent observer authority, co-signed → exam instance | exam_id; centres_reporting; chain_root (Merkle root over centre subtrees); anomalies {raised, resolved}; unbroken |

Structural symmetries an Implementation SHOULD preserve: type 6 is type 5 in reverse (paper in, responses out, same custody discipline); types 8 and 9 differ by one boolean; type 11 consumes itself into a session binding; type 12 is the federation checkpoint (§6.3) wearing a signature.
