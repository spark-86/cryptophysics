# **Scopes**

*The Namespace of Truth*

---

## **Chapter 1 — The Invention of Scopes**

Every civilization invents ways to name, classify, and delimit. The ledger does this through scopes: bounded namespaces where records accumulate into verifiable chains of truth. Scopes are not mere labels—they are time-anchored jurisdictions of meaning. Like domains on the early internet, scopes enable both local autonomy and global discoverability. This chapter introduces the core idea: a scope is a cryptographic locus, a stable anchor in the lattice of time.

---

## **Chapter 2 — Anatomy of a Scope**

A scope has shape. Its name follows strict grammar; its lineage is explicit; its records form a hash-linked sequence. Each scope begins with a `scope:request` record stored in its parent, ensuring uniqueness and verifiable ancestry. This chapter dissects the schema: naming rules, lineage tracking, parent–child relationships, and the bootstrap role of the root scope. Readers will understand how every scope is simultaneously a node in a tree and a branch in a chain.

---

## **Chapter 3 — Naming as Cryptographic Territory**

Names aren’t just human conventions—they’re cryptographic real estate. A scope name can’t be squatted without evidence, can’t be silently forked, and can’t be forged. Through deterministic naming rules, scopes form a stable addressing system for truth claims. This chapter explores how naming prevents namespace collisions, how lineage handles contested claims, and why canonical naming is the quiet backbone of ledger interoperability.

---

## **Chapter 4 — Creation Rituals: Birth of a Scope**

Creating a scope isn’t a function call—it’s a ritual. A `scope:create` record is signed, timestamped in Genesis Time, and appended to the parent scope. From this moment, the new scope inherits global visibility and participates in the temporal lattice. This chapter walks through the creation process, including key roles, authority structures, quorum requirements, and the social/technical implications of “minting” new namespaces.

---

## **Chapter 5 — Hierarchies, Branches, and Federation**

Scopes form a tree, but trees can federate. A company might own `org.example`, while a community may form `guild.example`. Subscopes inherit trust patterns, but they can also diverge, creating overlapping jurisdictions and federated governance models. This chapter examines scope hierarchies, multi-tenant designs, delegated authority, and patterns for federated structures—mirroring how DNS evolved, but cryptographically enforced.

---

## **Chapter 6 — Policy and Authority Within a Scope**

Each scope can define its own rules of engagement. Policies govern who may append, what quorum looks like, how keys are granted or revoked, and what record types are permitted. This chapter explores how policy records anchor scope behavior, how authorities are structured, and how these rules are enforced without centralized intermediaries. Think of it as the constitution layer for each namespace.

---

## **Chapter 7 — Discovery, Lookup, and Resolution**

Finding a scope is like finding a star in a night sky—stable, predictable, but requiring proper instruments. Resolution transforms human-readable names into verifiable records. Caching strategies, root bootstrap, and trust-on-first-use patterns ensure scopes can be discovered without fragile central registries. This chapter dives into resolution protocols, bootstrap strategies, and handling unknown or offline scopes.

---

## **Chapter 8 — Trust Topologies: Scopes as Graphs**

Scopes may be named like trees, but their trust relationships form a graph. Authorities can cross-sign; records can reference foreign scopes; federations can interlink. This chapter maps the complex web of trust that emerges when scopes interact, introducing trust graphs, inter-scope attestations, and how resolution and validation work in this graph-shaped reality.

---

## **Chapter 9 — Conflict, Forks, and Disputes**

No naming system survives contact with human ambition unscathed. Scopes may collide, authorities may split, forks may emerge. Instead of hiding these conflicts, the ledger records them transparently. This chapter analyzes dispute resolution mechanisms, fork visibility, evidence weighting, and how the network organically favors the branch with stronger, verifiable lineage.

---

## **Chapter 10 — Temporal Anchoring and Genesis Lineage**

Scopes don’t float freely—they’re pinned to Genesis Time. Temporal anchoring gives every scope a precise birth moment and a clear ancestry chain. This chapter explains how temporal ordering prevents replay attacks, supports causal reasoning, and ensures that the structure of scopes mirrors the structure of time itself.

---

## **Chapter 11 — Scopes in Practice**

Theory meets implementation. From organizational registries to personal namespaces, from app domains to federated data spaces, scopes provide the organizing principle for real systems. This chapter shows concrete examples—how scopes power eMotor.ID, SelfID attestations, service registries, and public governance spaces. Schemas meet lived use.

---

## **Chapter 12 — The Future Namespace**

What happens when the world runs on scopes? Global discovery without centralized DNS. Legal jurisdictions mirrored as cryptographic namespaces. Cultural groups preserving their linguistic identity as first-class citizens in the lattice. This chapter speculates on the future of human naming, governance, and identity when scopes become the universal substrate.
