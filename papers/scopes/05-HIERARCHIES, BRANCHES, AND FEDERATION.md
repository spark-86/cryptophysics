# **Chapter 5 — Hierarchies, Branches, and Federation**

Scopes form a **tree**, but trees are not isolated—they can **federate**. A company might operate under `org.example`, while a community organizes under `guild.example`. Subscopes inherit trust and policy patterns from their parents, but they can also diverge, creating **overlapping jurisdictions** and **federated governance models**. Unlike DNS, where federation is implicit and often informal, scope hierarchies and federations are **cryptographically enforced**, fully auditable, and structurally deterministic.

This chapter explores how hierarchies emerge from parent–child relationships, how multi-tenant designs and delegated authority function, and how federations allow independent namespaces to interconnect without surrendering autonomy.

---

## **5.1 The Tree: Structural Hierarchies**

The foundational shape of the namespace is a **tree**. Each scope has exactly one parent (except the root), and each child is explicitly created through the three-step ritual: `scope:request`, `scope:create`, and `scope:genesis`. This establishes an **unbroken lineage** from the root to any leaf.

Consider the following hierarchy:

```
org.example
org.example.research
org.example.research.lab42
```

Each segment to the right represents a child scope, created and anchored in the parent. The tree structure is not just conceptual—it is **proven through parent records**, which anyone can verify by walking left to right through the name.

### **5.1.1 Resolution Through Trees**

Resolving `org.example.research.lab42` involves:

1. Starting at ` `.
2. Locating the `scope:create` record for `org` in ` `.
3. Locating the `scope:create` record for `example` in `org`.
4. Locating the `scope:create` record for `research` in `org.example`.
5. Locating the `scope:create` record for `lab42` in `org.example.research`.
6. Verifying the `scope:genesis` record in `org.example.research.lab42`.

Each step is cryptographically signed and timestamped. No central registry or resolver is required—resolution is built into the structure itself.

> [EDIT] Add information about `rhex://scope/discovery`
---

## **5.2 Policy Inheritance and Divergence**

Parent scopes can define policies that apply to their children. These might include:

* Naming conventions for subscopes.
* Requirements for key management.
* Quorum rules for approval.
* Attestation or external verification steps.

These policies are defined in `policy:set` records, which are themselves hash-linked and timestamped. A child scope **inherits** its parent’s context but may **diverge** by setting its own policies after genesis. This allows for hierarchies that are both **coherent** and **flexible**.

For example, `org.example.research` might require 3-of-5 quorum for new subscopes, while `org.example.sales` might allow delegated single-key approval. Both inherit naming structure and temporal anchoring from `org.example`, but they govern themselves differently.

---

## **5.3 Delegated Authority**

Large hierarchies can’t rely on a single authority to create all subscopes. Parents can **delegate authority** to specific keys or groups to manage particular branches. This delegation is recorded in `key:grant` or `policy:set` records.

For example:

* `org.example` grants authority to a key group within the research department.
* That group can approve new subscopes like `org.example.research.lab42` without involving the corporate root.

Delegation enables **scalability**. It mirrors how organizations work in the physical world: a national government delegates to provincial authorities; a corporation delegates to departments. The difference is that delegation here is **transparent and verifiable**, not informal.

---

## **5.4 Multi-Tenant Namespace Designs**

Many modern systems operate under **multi-tenant** models—multiple actors sharing a namespace infrastructure while maintaining autonomy. Scopes natively support this through subscopes and delegation.

Imagine a platform operator under `platform`. Independent developers create subscopes:

```
platform.alice
platform.bob
platform.charlie
```

Each tenant operates independently, but their existence is **anchored in the parent’s chain**, providing a shared structure for resolution and governance. Policies in `platform` can define baseline rules (e.g., naming formats, reserved prefixes), while each tenant defines its own internal policies.

This model mirrors app stores, cloud platforms, or online marketplaces—but **without centralized registrars**.

---

## **5.5 Federation: Beyond the Tree**

Trees provide structure; **federation provides flexibility**. Federation occurs when two or more scopes establish formal relationships through **mutual signatures, attestations, or shared subscopes**.

### **5.5.1 Cross-Signing and Mutual Recognition**

Two scopes can mutually recognize each other by exchanging signed attestation records. For example:

* `org.example` and `guild.example` may cross-sign to establish a partnership.
* These attestations are timestamped and hash-linked, making the relationship public and verifiable.

This allows federated entities to build trust networks **without merging their hierarchies**.

### **5.5.2 Shared Subscopes**

Multiple parents can jointly approve a single child scope. For example, `org.example` and `guild.example` might co-sign the creation of `org-guild.example.projectx`. This child scope exists under **joint governance**, with both parents participating in policy decisions.

This is particularly useful for **joint ventures**, **cross-institutional projects**, or **shared infrastructure**.

> [EDIT] Do we even want this section? We haven't discussed doing this before
---

## **5.6 Federation Patterns**

Several federation patterns emerge in practice:

* **Mutual Recognition** — Scopes attest to each other’s validity.
* **Shared Governance** — Multiple parents co-sign a subscope.
* **Delegated Federation** — One scope grants another the right to create under a shared branch.
* **Attestation Webs** — Scopes issue attestations about each other, forming trust graphs.

These patterns allow **autonomous namespaces** to interoperate without a central coordinator. It’s analogous to how autonomous networks use BGP to form the Internet, but here, federation is **cryptographically explicit**.

---

## **5.7 Overlapping Jurisdictions**

In the physical world, jurisdictions overlap: cities within states, trade federations spanning countries, research collaborations crossing institutions. Scopes reflect this naturally. A university under `edu.example` might federate with a company under `org.example` to form `org-edu.example.labcollab`. Policies from both parents apply to different aspects of governance, and the relationship is **documented, not improvised**.

This transparency makes overlapping jurisdictions predictable and auditable. There is no hidden legal gray zone—just evidence.

---

## **5.8 Conflict and Resolution in Federations**

Conflicts can arise when federated scopes disagree—over governance, policy, or succession. These conflicts are **not hidden**; they are visible through diverging attestation records or incompatible policy sets.

Resolution happens through:

* Temporal ordering of conflicting actions.
* Policy precedence rules defined in the federation agreement.
* Transparent lineage and signatures.

Unlike political federations, which often resolve disputes through opaque negotiations, ledger-based federations produce **deterministic evidence**.

---

## **5.9 Hierarchies Meet Federation**

The real power of this system emerges when **hierarchies and federations intertwine**. Hierarchies provide **structure**; federations provide **bridges**. A corporate tree under `org.example` can federate with a research institution under `edu.example`, a standards body under `std.example`, and a community guild under `guild.example`. Each retains its own governance, but they collaborate through shared subscopes and attestations.

This resembles the Internet’s architecture: DNS provides hierarchical structure, while BGP and PKI enable federated cooperation. Here, both layers are **on-ledger and cryptographically enforced**.

---

## **5.10 Global Federation Patterns**

As the lattice expands, large-scale federations will emerge:

* **Scientific federations** where universities co-sign shared namespaces for open research.
* **Municipal federations** where cities collaborate on infrastructure.
* **Industrial federations** where companies jointly govern supply chain namespaces.

These federations will not be enforced by treaties but by **signed records**, lineage, and time. Trust emerges not from negotiation but from **evidence**.

---

## **5.11 Living Structures**

Hierarchies give the namespace its **bones**. Federation gives it **muscle and connective tissue**. Together, they form **living structures** that can adapt, grow, and evolve without central control. Policies change, subscopes appear and disappear, federations form and dissolve—but the evidence remains.

This is how a self-governing, cryptographically enforced namespace grows to planetary scale: through trees that structure meaning and federations that weave those trees together.

---

*In the next chapter, we will examine how policies and authorities shape governance inside these structures—how rules are encoded, enforced, and evolved through transparent mechanisms rather than institutional fiat.*
