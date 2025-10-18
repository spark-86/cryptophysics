# **Chapter 8 — Trust Topologies: Scopes as Graphs**

Scopes are named like trees, but their **trust relationships** form a **graph**. Names provide hierarchical order; trust emerges through **cross-signatures**, **attestations**, and **federated relationships** that link scopes across branches. A single scope can have parent–child lineage like a tree, but simultaneously maintain **peer relationships**, **reciprocal trust links**, and **shared governance structures**. The result is a **graph-shaped reality**: a living trust topology that underpins the ledger.

This chapter explores how these trust graphs are constructed, how inter-scope attestations work, and how resolution and validation operate within this multidimensional network.

---

## **8.1 Trees Give Names, Graphs Give Trust**

The `root.branch.leaf` naming structure provides a **deterministic, hierarchical anchor** for resolution. Each name can be traced back to the root (`""`) through a chain of `scope:create` and `scope:genesis` records. But naming alone does not define **who trusts whom**, or **how authority flows across boundaries**.

Trust relationships emerge when scopes **interact**:

* Authorities in one scope cross-sign another.
* Scopes issue **attestation records** referencing foreign scopes.
* Federations form through shared subscopes or mutual endorsements.

This interaction turns the namespace into a **graph**, where edges represent **cryptographically signed trust relationships**.

---

## **8.2 Trust Graph Fundamentals**

A **trust graph** is composed of:

* **Nodes** — Scopes, identified by their canonical names.
* **Edges** — Trust relationships, created by signed records such as attestations, cross-signatures, or shared governance agreements.
* **Edge Attributes** — Types of trust (e.g., endorsement, delegation, policy alignment), timestamps, and signatures.

Unlike the strict parent–child edges in the naming tree, trust edges can connect **any two nodes**. This allows for **arbitrary topologies**: rings, meshes, stars, or hybrid networks.

For example:

* `org.example` may cross-sign `guild.example`.
* `guild.example` may issue attestations about `org.example.research`.
* A standards body at `std.global` may endorse both.

These edges create **paths of validation** that resolution engines can traverse to verify claims that extend beyond parent–child lineage.

---

## **8.3 Inter-Scope Attestations**

Attestations are the **currency of trust graphs**. A scope can issue a signed `attest` record that references another scope, asserting something about its identity, policies, or behavior. Attestations may include:

* **Existence**: Endorsing that another scope’s creation and policies are valid.
* **Delegation**: Granting limited authority or recognition to another scope.
* **Certification**: Declaring compliance with standards or agreements.

Example:

```
(attest)
  scope: org.example
  target: guild.example
  claim: "Recognized as a peer organization for joint research projects."
  signature: key-org-admin
```

Because attestations are signed and timestamped, they can be **independently verified** and **combined into chains of trust**.

---

## **8.4 Cross-Signing and Reciprocal Trust**

Two scopes can **cross-sign** each other to establish **mutual trust**. This is common for federated organizations, standards bodies, or peer institutions.

For example, `org.example` and `guild.example` may both issue attestations recognizing each other’s legitimacy. This creates a **bidirectional edge** in the trust graph. Downstream clients can use these cross-signatures to verify claims involving either party, even if they belong to different naming trees.

Cross-signing is similar to how certificate authorities can cross-sign intermediate roots, creating alternate chains of validation.

---

## **8.5 Federation as Graph Structure**

Federations naturally produce graph structures. When multiple scopes co-govern a subscope or participate in shared projects, they create **multi-edge relationships** that go beyond simple trees.

Consider a shared research project:

```
org.example.research+guild.example.labx
```

Both `org.example.research` and `guild.example` co-sign the creation and policy of `labx`. This shared governance produces edges from both parents into the shared subscope, forming a **federated triangle** in the trust graph.

Over time, such relationships accumulate into **dense networks** of cross-signatures and attestations. These networks are not ephemeral—they are cryptographically fixed in the ledger, forming the backbone of inter-organizational trust.

---

## **8.6 Discovery in Graph Topologies**

The introduction of **`rhex://scope/discovery`** aliases and `discoverable` flags also plays a critical role in trust graphs. Scopes can publish not only their subscopes, but also **attestations and trust links** in their discovery tables. This allows clients to:

* Fetch both hierarchical and trust edges from a single source.
* Traverse cross-scope relationships during resolution.
* Build local trust graphs incrementally.

A discovery table might list trusted peers or federated scopes, allowing clients to automatically incorporate those edges into their resolution logic.

---

## **8.7 Resolution in a Graph-Shaped Reality**

When resolving names and verifying claims, clients must operate in a **graph context**:

1. **Tree Walk**: Clients follow the `root.branch.leaf` lineage to verify naming and genesis.
2. **Trust Expansion**: Clients fetch attestations and trust edges from discovery tables or cached records.
3. **Graph Traversal**: Clients may traverse multiple edges to find **trust paths** between their local trust anchors and target scopes.

For example, if `org.example` trusts `std.global`, and `std.global` has certified `guild.example`, a client trusting `org.example` can accept `guild.example` via the **org → std.global → guild** path.

This model resembles **web-of-trust** systems, but with deterministic naming and verifiable timestamps anchoring each relationship.

---

## **8.8 Trust Path Evaluation**

Not all trust edges are equal. Policies within each scope can define how trust edges are evaluated:

* **Direct Cross-Signs** may be treated as strong endorsements.
* **Attestations with claims** may be weighted depending on the signer.
* **Indirect Paths** may require minimum hop counts, timestamps within tolerance, or specific types of intermediate signers.

This gives scopes and clients **fine-grained control** over how they interpret the graph, without imposing global rules.

---

## **8.9 Temporal Anchoring of Trust**

Every trust edge—attestation, cross-signature, or shared governance—is **anchored in Genesis Time**. This allows trust graphs to be evaluated **as of any moment in history**. Clients can:

* Reconstruct trust topologies at specific points in time.
* Audit how federations evolved.
* Resolve historical claims with period-correct context.

Temporal anchoring turns trust graphs into **historical records**, not just current snapshots.

---

## **8.10 Graph Resilience and Evolution**

Trust graphs are inherently **redundant**. Multiple attestations and cross-signatures can provide alternate paths, making the system resilient to the compromise or disappearance of single authorities.

Over time, trust graphs evolve:

* New edges are added as organizations federate.
* Old edges expire or are revoked.
* Topologies shift from sparse to dense as the lattice matures.

Because everything is on-ledger, these changes are transparent and analyzable.

---

## **8.11 Trust Graph Applications**

Trust graphs enable powerful applications:

* **Cross-Scope Identity Verification** — Proving that an identity recognized in one scope is valid in another.
* **Standards Enforcement** — Allowing standards bodies to certify compliance through attestations.
* **Supply Chain Audits** — Tracing federated trust links across jurisdictions.
* **Policy Propagation** — Applying trust-based validation rules without central control.

In each case, trust graphs provide the **structural substrate** for interoperability.

---

## **8.12 Toward Emergent Global Trust Networks**

As more scopes issue attestations, cross-sign, and federate, the trust topology will resemble **a planetary-scale graph**: a mesh of organizations, communities, and individuals connected through signed evidence.

This network will not be designed top-down; it will **emerge** from millions of local trust decisions. Clients and systems will traverse this graph using local trust anchors and cryptographic validation, enabling **global interoperability without centralized trust authorities**.

---

*In the next chapter, we will explore how these trust graphs intersect with economics—how proofs replace payments, and how trust relationships form the backbone of transparent, verifiable exchange.*
