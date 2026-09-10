# Governance

## Intent

The Pariksha Protocol is meant to be owned by no one. The initial editors prepared draft-01 and are releasing it so that examination bodies, vendors, researchers and the public can shape it. The intended end state is stewardship by an independent standards body or a not-for-profit foundation constituted for the purpose, on the pattern of other open protocols in India's digital public infrastructure. Until that body exists, this repository is the protocol's home and this document is its process.

## How changes are made

1. **Issues first.** Anything — an error, an ambiguity, a missing requirement, a disagreement with a design choice — starts as an issue against the relevant section file. Issues are the record of why the spec says what it says.
2. **Pull requests carry the change.** A PR should touch the smallest set of section files that the change needs and reference the issue it resolves. Normative changes (anything touching MUST/SHOULD/MAY) must say so in the PR title.
3. **Editors merge.** The editors merge changes that have been open for comment for at least 14 days without unresolved objection. Editorial fixes (typos, formatting, broken links) can be merged immediately.
4. **Drafts are tagged.** A new working draft is cut when the accumulated changes warrant it, tagged `draft-NN`, and archived on Zenodo with its own DOI. Tagged drafts are never rewritten.

## What does not change without a new major draft

The kernel — four nouns, three verbs, the witnessing condition (§2) — and the verify-then-decrypt ordering (§7.3). Proposals to change these are welcome, but they are a new protocol, not a revision, and will be treated as such.

## Editors

The current editors are listed in [CONTRIBUTORS.md](CONTRIBUTORS.md). Editorship is added by consensus of the existing editors and is expected to broaden as implementations appear. An examination body or an independent implementer that ships a conforming implementation is a natural candidate.

## Implementations and neutrality

The specification names no product and never will. Implementations may list themselves in [IMPLEMENTATIONS.md](IMPLEMENTATIONS.md) with a link and a statement of which conformance items they meet. Listing is not endorsement; conformance claims are the implementer's own until a conformance suite exists.

## Handover

When an independent steward is constituted, this repository transfers to it with its full history. The editors commit to that transfer and to not conditioning it on any commercial arrangement.
