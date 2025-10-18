# **Chapter 2 — Anatomy of a Scope**

A scope is both a **place** in the global namespace and a **sequence** of verifiable records. It has shape. Its **name follows strict grammar**, its **lineage is explicit**, and its **records form a hash-linked chain** anchored in time. Each scope begins life through a signed `scope:request` recorded in its parent, followed by a `scope:create` record that authoritatively declares its birth, and finally a **`scope:genesis` record** that initializes its internal ledger chain. From that moment, the scope becomes a living part of the lattice, simultaneously a **node in a tree** and a **branch in a chain**.

This chapter examines the anatomy of a scope in detail: naming rules, lineage structures, record sequences, and the bootstrap role of the root scope. Understanding these mechanics is essential, because everything else in the ledger builds on these foundations.

---

## **2.1 Naming Grammar: root.branch.leaf**

Scope names follow a deterministic grammar that moves from **general to specific**, left to right:

```
root.example.project
```

This is not reverse DNS. It is **root.branch.leaf**, mirroring how hierarchies are naturally described in human language: world → continent → nation, or root → trunk → branch → leaf. Each segment represents a level of lineage. The **leftmost token** is always the root. Each subsequent segment represents a direct child of the previous segment.

### **2.1.1 Allowed Characters and Canonical Form**

Scope names are composed of lowercase alphanumeric characters and hyphens. They must:

* Begin with a letter.
* Contain only `a–z`, `0–9`, and `-`.
* Be segmented by `.` (periods).
* Not exceed 255 characters per segment or 65535 characters total.
* Be canonicalized to lowercase before hashing or signing.

This strict grammar eliminates ambiguity. It ensures that two entities who independently process the same name arrive at the **same canonical hash**.

---

## **2.2 Lineage: Parent–Child Relationships**

Every scope has a **parent**, except for the root. A scope’s name encodes its lineage: each segment to the right represents a child nested inside the previous segment. The lineage is enforced through **records in the parent’s chain**.

### **2.2.1 `scope:request` → `scope:create` → `scope:genesis`**

The creation of a scope happens in three distinct steps:

1. **`scope:request`** — The would-be creator writes a `scope:request` record into the parent scope’s chain. This record includes:

   * `scope`: the parent scope name.
   * `new_scope`: the proposed child scope name.
   * `public_key`: the public key of the requester.
   * `at`: the Genesis Time timestamp.
   * `signature`: proof of origin.

   This makes the proposal public and auditable.

2. **`scope:create`** — If the parent approves the request according to its policies, it appends a `scope:create` record containing:

   * The **child name**.
   * A reference to the **parent**.
   * The timestamp of approval.
   * The approving authority’s fingerprint and signature.
   * A hash reference to the original request.

   This is the authoritative act by which the parent declares: *“This name exists under me.”*

3. **`scope:genesis`** — Immediately after `scope:create`, the new scope must initialize its own internal chain with a `scope:genesis` record. This record contains:

   * `scope`: the full scope name.
   * `at`: the timestamp of creation.
   * `author_pk`/`public_key`: the key of the scope’s initial steward.
   * Optional policy initialization data.

#### **Editing Note**
>Make this make more sense. Scope genesis is very well documented at this point and therefore a solid example should exist.

   This `scope:genesis` record acts as the **zero block** of the scope’s chain—the anchor from which all subsequent records derive. Without it, the scope does not truly exist as a ledger participant. It is the moment the new namespace gains its own **record space**.

This three-step sequence—**request, create, genesis**—is what transforms a mere naming claim into a **living scope** with lineage and internal state.

### **2.2.2 Unbroken Chains of Ancestry**

Because each child’s creation record lives in its parent, and each scope has a `scope:genesis` in its own chain, you can reconstruct any scope’s lineage by **walking left to right** through its name and checking each parent’s ledger. This produces a **deterministic ancestry chain**, rooted at the global root scope.

---

## **2.3 The Record Chain: Hash-Linked Sequences**

Every scope maintains its own **append-only record chain**, similar to a blockchain but localized to that namespace. Each record contains:

```json
{
	"magic": b'RHEX\x00\x00',
	"intent": {
		"previous_hash": "...",
		"scope": "org.example.building1",
		"nonce": "...",
		"author_pk": "...",
		"usher_pk": "...",
		"record_type": "scope:gensis",
		"data": {
			"scope": "org.example.building1",
			"public_key": "...",
        }
    },
	"context": {
		"at": 12981249744,
		"x": null,
		"y": null,
		"z": null,
		"refer": null
    },
	"signatures": [...],
	"current_hash": "..."
}
```

* `previous_hash`: hash of the prior record.
* `magic`: schema identifier.
* `scope`: the scope name.
* `nonce`: uniqueness salt.
* `at`: Genesis Time timestamp.
* `author_pk`: signer’s key fingerprint.
* `record_type`: e.g., `scope:genesis`, `policy:set`, `attest`, etc.
* `data`: payload.
* `signature`: Ed25519 signature.
* `current_hash`: hash of the entire record.

This structure ensures immutability. Any tampering with prior records breaks the chain.

### **2.3.1 Local Chains, Global Context**

Each scope’s chain is **independent**, but not isolated. Chains interlink through cross-scope references, attestations, and federations. Together, they form the **global lattice**. This design allows for massive horizontal scalability: millions of scopes can operate simultaneously without global consensus overhead.

---

## **2.4 The Root Scope: Bootstrap Anchor**

All lineage ultimately leads back to the **root scope**. It is the **bootstrap trust anchor**. It contains the original creation records, temporal epoch definitions, and initial authority keys. Once a client has the root scope, it can resolve any other scope by **walking the chain of parent records**.

The root scope is not a governing body; it is a **cryptographic anchor**. It provides the minimal shared context required for global interoperability.

### **2.4.1 Immutable Genesis**

The root scope’s records are immutable and widely distributed. This ensures that the **origin story of the namespace** cannot be rewritten. Every other scope ultimately derives its legitimacy through evidence chains leading back to root.

---

## **2.5 Scopes as Nodes and Branches**

A scope is **two things at once**:

1. **A Node in a Tree** — determined by its parent–child relationship.
2. **A Branch in a Chain** — determined by its internal sequence of records.

These two perspectives are complementary. The tree gives you **structural resolution**, while the chain gives you **historical verifiability**. Together, they create a namespace that is both **navigable** and **immutable**.

For example, `root.example.project` sits as a node under `root.example`, which sits under `root`. Its chain begins with `scope:genesis` and contains its own history of policies, attestations, and events. Its **position** in the namespace is determined entirely by its parent’s records.

---

## **2.6 Practical Implications**

Understanding scope anatomy has immediate practical consequences:

* **Resolution**: Deterministic lookup by walking the tree left-to-right.
* **Governance**: Policies apply hierarchically and locally.
* **Security**: Hash-linked records prevent tampering.
* **Interoperability**: Canonical naming and lineage enable independent actors to agree on namespace state.

This design replaces the need for registrars and central DNS resolvers with **purely evidence-based resolution**.

---

## **2.7 Living Structures**

Scopes are not static. Policies evolve. Keys rotate. Subscopes appear and disappear. Records accumulate like growth rings in a tree. The anatomy of a scope provides the **skeletal framework**, but its **record chain is the living tissue**. Together they form evolving, self-governing namespaces that scale organically without losing coherence.

---

*In the next chapter, we will explore naming as cryptographic territory—how deterministic rules and lineage transform names from conventions into evidence-backed real estate.*
