# 3. Participants and the Registry

## 3.1 Registry rules

R1. Every Participant MUST be registered before acting; registration and revocation are themselves witnessed events. The registry has no silent edits. R2. Roles bind to individuals per proceeding instance and context (“quorum member for instance X at context C”), never globally; scope lives in the Credential. R3. Machines that act — servers, terminals, unlock devices, agents — are Participants with Device Credentials; there are no anonymous system events. R4. Quorum roles MUST span at least two issuing authorities (separation of masters): a body cannot form a quorum entirely from Credentials chaining to its own root.

## 3.2 Actor taxonomy (profile-defined)

The core does not name roles. A conforming profile MUST define a role taxonomy covering at least: an Authority domain (the root and its policy administrators), an Artifact domain (those who create and seal content), a Custody domain, a Context domain (the roles that form quorums at the place of conduct, plus the validator and terminal devices), a Subject domain (the participants whose sessions are bound), a Machine domain (agents and platform services acting under service credentials), and an Oversight domain (live monitoring and post-hoc audit). Every quorum role MUST be a role the profile names, and the profile MUST state which roles satisfy R4. The role taxonomy for Indian public examinations is in the [Examination Profile — India](../profiles/examination-india.md).

## 3.3 Contextual locality

A human Participant occupies exactly one physical context at a time. The Protocol treats this as load-bearing: a Candidate Credential MUST bind to at most one active session in one context; a second concurrent binding attempt is semantically invalid and MUST be rejected and witnessed as a denial. Impersonation-by-parallel-presence is thereby unexpressible rather than merely detectable.

## 3.4 The one unregistered role

Verification of outcome Credentials (§5, type 10) MUST be possible by any party, anywhere, with no registration, account, or permission. The registry's boundary is meaningful precisely because outcome trust is consumed permissionlessly while all authority is exercised accountably.
