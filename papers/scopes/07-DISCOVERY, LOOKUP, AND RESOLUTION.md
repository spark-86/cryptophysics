# **Chapter 7 — Discovery, Lookup, and Resolution**

Finding a scope is like locating a star in a night sky—**stable**, **predictable**, but requiring the right instruments. Once created, a scope is permanently anchored in the lattice. The challenge is not whether it exists, but **how to find it**. Discovery and resolution transform human-readable names into verifiable records without relying on centralized registries.

Ledger scopes use the **`root.branch.leaf`** naming scheme, with the **root scope represented by the empty string (`""`)**. Names are resolved deterministically by walking from the root toward the leaf, verifying parent–child relationships through recorded evidence. Resolution is enhanced by **`rhex://scope/discovery` aliases**, globally available discovery tables that allow any participant to find scopes regardless of what key they use.

This chapter explores how discovery tables work, how scopes opt into being discoverable, how clients bootstrap resolution, and how the network handles unknown or offline scopes without centralized control.

---

## **7.1 From Names to Records**

Resolution is the process of transforming a name like:

```
org.example.project
```

into the set of verifiable records that define its existence and state. This involves:

1. Starting at the **root** (`""`).
2. Finding the `scope:create` record for `org` in the root’s chain.
3. Finding the `scope:create` record for `example` in `org`.
4. Finding the `scope:create` record for `project` in `org.example`.
5. Verifying `project`’s `scope:genesis` and current policy state.

This process is **deterministic** and requires no registries or naming servers. All required data is either cached locally or fetched through **discovery mechanisms**.

---

## **7.2 rhex://scope/discovery Aliases**

To make resolution efficient and universal, each scope publishes a **discovery table** accessible at a canonical alias:

```
rhex://scope/discovery
```

This alias is **globally available and key-agnostic**—any participant can fetch it without needing special authorization. Discovery tables contain metadata and references for subscopes, enabling clients to rapidly resolve and verify children.

A discovery table may include:

* List of **child scopes** marked as discoverable.
* Hash references to their `scope:create` records.
* Optional metadata for indexing or UI.
* Timestamps and versioning.

Because the discovery table is served at a stable alias, clients don’t need to know which keys or endpoints to query; they simply follow the name path and fetch discovery data as they descend the hierarchy.

---

## **7.3 Discoverable vs. Private Scopes**

When a scope is created, its `scope:request` and `scope:create` records include a **`discoverable` flag**. If set to `true`, the new scope is automatically added to its parent’s discovery table. If set to `false`, it still exists and can be resolved if you know its name, but it won’t appear in generic discovery queries.

This allows scopes to choose between **public discoverability** and **private obscurity**, without affecting their underlying validity.

Examples:

* `org.example.public` sets `discoverable = true`. It appears in `org.example`’s discovery table, and anyone can find it by browsing.
* `org.example.internal` sets `discoverable = false`. It exists and can be resolved by name, but doesn’t appear in listings.

This mirrors the difference between **indexed web pages** and **unlisted but accessible URLs**—except discovery here is cryptographically enforced.

---

## **7.4 Bootstrap Strategies**

Every resolution process begins with a **bootstrap**. Clients need to know where to find the root scope (`""`) and its initial discovery table. This is analogous to having the root DNS zone file or trusted root certificates—but simpler and more transparent.

Bootstrap strategies include:

* **Bundled Root**: Clients ship with a hardcoded copy of the root scope and discovery table.
* **Pinned Hash**: Clients pin the hash of the root discovery table and fetch the latest version from multiple mirrors.
* **Quorum Fetch**: Clients fetch the root table from multiple peers and verify consistency through signatures and hashes.

Once the root is known, all other scopes can be resolved deterministically.

---

## **7.5 Caching and Trust-on-First-Use (TOFU)**

Resolution efficiency depends on **caching**. Once a client resolves `org.example`, it can cache the discovery table and relevant records locally, reducing future lookups. Cached data includes:

* Parent discovery tables.
* `scope:create` and `scope:genesis` records.
* Policy snapshots.

Caching is paired with **trust-on-first-use (TOFU)**: the first time a scope is resolved, the client records the hash of the relevant records. Subsequent updates are checked against this pinned state. If the hash changes unexpectedly without valid lineage updates, the client can flag or reject the resolution.

This creates a balance between **speed** and **security**, without requiring live consensus or trusted intermediaries.

---

## **7.6 Resolution Flow in Practice**

Let’s walk through resolving `org.example.project` step by step:

1. **Start at Root**: Client loads the root discovery table from `rhex:///discovery`.
2. **Find org**: Client checks the root discovery table for `org`. If present, it fetches the `scope:create` record and verifies it.
3. **Load org’s Discovery Table**: Client fetches `rhex://org/discovery` within `org`.
4. **Find example**: Same process, descending to `example`.
5. **Find project**: Finally, the client resolves `project` within `org.example`.
6. **Verify**: Client fetches and verifies the `scope:genesis` and any relevant policy records in `org.example.project`.

This flow is **stateless** and **peer-independent**. Any client can do this without asking permission from a centralized registry.

---

## **7.7 Offline and Unknown Scopes**

Sometimes a scope might not be discoverable because:

* It is marked `discoverable = false`.
* Its discovery table is offline or unreachable.
* The client is attempting resolution without prior cache.

In such cases, resolution falls back to **direct name walking**: the client attempts to locate parent records via peer-to-peer fetches, archives, or known mirrors. If all else fails, the client can record the failed resolution attempt, which can later be retried or audited.

Importantly, the **existence of a scope is not dependent on availability**. Even if a discovery table is offline, the scope’s creation records remain valid and can be fetched from other peers or archives.

---

## **7.8 Discovery Tables as Living Indexes**

Discovery tables are **not registries**; they are **indexes generated by scopes themselves**. Because they are signed and anchored in the parent scope’s chain, they are tamper-evident. Over time, scopes can update their discovery tables to add or remove child entries, change metadata, or rotate hashes.

This creates a **living, distributed index** that scales with the namespace, avoiding the bottlenecks of centralized registrars.

---

## **7.9 Federation and Cross-Scope Discovery**

Federated scopes can cross-reference each other’s discovery tables. For example, `org.example` and `guild.example` may cross-sign each other’s discovery tables, allowing clients to resolve shared subscopes more efficiently.

Discovery tables can include **cross-scope aliases**, enabling clients to traverse federations without hardcoding relationships. This supports **emergent trust networks** built on evidence rather than static configuration.

> [EDIT] This section needs more work. Cross-signing is still not a thing.

---

## **7.10 Resilience Through Redundancy**

Because discovery tables are globally accessible and cached widely, the discovery system is **highly resilient**. Even if a particular host or organization disappears, cached discovery tables and record archives allow resolution to continue. This is analogous to how DNS continues to function through distributed caching—but without trusted resolvers.

---

## **7.11 A Telescope, Not a Gatekeeper**

The discovery system is not a gatekeeper. It doesn’t grant names or authorize scopes. It simply provides **instruments for finding what already exists**. Discovery tables act like telescopes pointed at a shared sky; the stars are the scopes, fixed in the lattice.

By separating **existence** (determined by records) from **visibility** (determined by discovery tables), the ledger avoids the pitfalls of centralized registries while maintaining usability and global coherence.

---

*In the next chapter, we will explore how economic and social systems build on this discovery infrastructure—how proofs replace payments, and how transparent flows reshape trust at scale.*
