# 7. Processes

## 7.1 ISSUE

Credential issuance MUST be a witnessed ceremony appropriate to the type's proof tier. For the Exam Paper Credential specifically: (a) content is finalised; (b) per-receiver watermark is embedded; (c) payload is encrypted per receiving context; (d) the content key is threshold-split (e.g. Shamir 2-of-3) and shares wrapped to each quorum member's credential key; (e) claims are composed (window, quorum policy, hashes, variance refs); (f) the assembler signs; (g) plaintext is destroyed, and the destruction is attested by the sealing witness as its own event. Steps (a)–(g) each emit witnessed events; papervc.issued and plaintext.destroyed are mandatory.

## 7.2 CUSTODY

Every transfer of a sealed Credential between Participants MUST emit custody.transfer naming both parties' credentials. Pre-staging sealed Credentials at their destination context ahead of time is RECOMMENDED (connectivity resilience): custody of ciphertext carries no access risk by construction. Storage between transfers binds to a custodian credential. There are no anonymous hops: a Credential whose custody chain has a gap MUST fail verification at presentation.

## 7.3 PRESENT

Presentation is one ceremony in two mandatory stages. VERIFY: the presenting context validates the Credential's proof (issuer signature), its claims against the moment (window open, context matches, revocations clear), and the presenting Participants' social proof at the required tier. Any failure is a witnessed denial; the ceremony ends. UNLOCK: only after full verification, quorum members' shares unwrap and the content key reconstructs inside the presenting device's secure enclave; payload decrypts; the key is zeroised and the grant expires on use. For sessions (device delivery): session binding presents the Admit Credential plus live biometric match against the sealed template, locally; the bound session then signs each response into the context chain, and session completion issues the Response Credential with the candidate's receipt_code displayed.
