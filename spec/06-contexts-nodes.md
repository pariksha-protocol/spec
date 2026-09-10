# 6. Contexts and Nodes

## 6.1 The context

A context is a bounded interaction locale with its own participant set and event stream — in the Core Profile, one examination centre for one exam instance. Contexts do not contend: no event in one centre's stream conflicts with another's, so no global consensus is required during conduct. Consensus is needed only where contexts touch — at federation checkpoints.

## 6.2 The context node (centre validator)

Each centre runs a validator: a Device Credential holder (class validator) granted, per exam instance, the scoped authority validator:centre:exam:window. The validator verifies presentations locally (signature verification requires no network), anchors the centre's hash chain, arbitrates device sessions over LAN, and witnesses all centre events in real time. Validator authority is just-in-time and expiring like all authority in the Protocol: the physical machine MAY differ every day; the role is granted fresh through the standard ceremony. Any number of validators MAY serve one context for redundancy; they share one chain.

## 6.3 Federation

On connectivity, each context checkpoints: its chain head, countersigned by the centre quorum, merges into the national ledger as a subtree. The national chain is a Merkle forest of context subtrees under one root; the root, co-signed, is the Integrity Certificate (#12). Tampering within any context breaks that context's subtree visibly and is contained to it — blast radius one centre, at the infrastructure layer.
