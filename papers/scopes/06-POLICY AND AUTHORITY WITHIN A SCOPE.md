# **Chapter 6 — Policy and Authority Within a Scope**

Each scope is more than a name and a chain of records—it is a **governance domain**. Policies define who can act, how actions are validated, what records are allowed, and how authority evolves over time. This is the **constitution layer** of the namespace. Crucially, these rules are defined and enforced **within the scope itself**, not by any external registry or centralized intermediary.

The root scope (`""`, the empty string) provides the bootstrap trust anchor, but every other scope sets its own internal constitution through **policy records** and **authority structures**. This chapter explores how policies are encoded, how keys and quorum are managed, and how these rules shape the behavior of every scope in the lattice.

---

## **6.1 Policy as the Constitution Layer**

A scope’s policies function like a constitution: they define **who may act**, **what actions require approval**, and **how authority can be transferred or revoked**. Policies are:

* **On-ledger** — recorded as `policy:set` records within the scope’s own chain.
* **Immutable in history** — previous policies remain visible even when superseded.
* **Deterministically enforced** — no external arbitrators are needed.

Policies govern:

* Key grants and revocations.
* Quorum rules for record validation.
* Permitted record types.
* Delegation of authority.
* Attestation requirements.

This transforms each scope into a **self-governing enclave**, able to operate independently while maintaining global interoperability.

---

## **6.2 The Root Scope as Bootstrap Trust Anchor**

The root scope, represented by the **empty string (`""`)**, anchors the entire lattice. It doesn’t govern other scopes directly; instead, it defines the **initial authorities and temporal epoch** that all other scopes reference.

When resolving a name like:

```
org.example.project
```

you begin at `""` (the root), look up the `scope:create` for `org`, then for `example` under `org`, then for `project` under `org.example`, and finally read the policy records in `org.example.project`. Each scope governs itself; the root merely provides the **fixed reference point** for global resolution.

---

## **6.3 Policy Records: `policy:set` and Friends**

Policy changes are expressed through **ledger records**. The primary record type is `policy:set`. It includes:

* `scope`: the scope where the policy applies.
* `at`: Genesis Time timestamp.
* `current_hash`: a deterministic hash.
* `rules`: structured data describing the policy.
* `author_pk`: key of the signer.
* `signature`: cryptographic proof of authorization.

Policies may cover different aspects of governance, such as key roles, quorum rules, and permitted record types.

### **6.3.1 Policy Evolution**

Policies can evolve over time. A new `policy:set` does not erase the old one—it simply **supersedes** it going forward. This allows for historical audits and governance transparency. Anyone can reconstruct the policy state at any point in time by replaying the chain.

> [EDIT] But they do. A new `policy:set` redoes whatever previous `policy:set` has done so we don't have a mixed state
---

## **6.4 Key Management: Granting and Revoking Authority**

At the heart of policy is **authority**, and authority is expressed through **keys**. Scopes manage keys through `key:grant` and `key:revoke` records.

### **6.4.1 `key:grant`**

A `key:grant` record assigns a role to a public key within the scope. It includes:

* The public identifier of the key, `public_key`. 
* The role being granted (e.g., `admin`, `signer`, `quorum-member`).
* Optional expiration times.
* Policy references indicating why the grant is valid.

### **6.4.2 `key:revoke`**

A `key:revoke` record removes or suspends authority from a previously granted key. Revocations are immediate and irrevocable in history: the chain always shows **who was revoked, when, and why**.

### **6.4.3 Hierarchical Key Structures**

Scopes often organize keys hierarchically:

* **Root keys**: define initial governance.
* **Administrative keys**: manage policy updates and delegation.
* **Operational keys**: sign day-to-day records.

Policies specify which roles are required to perform which actions, and what quorum is needed.

---

## **6.5 Quorum Rules**

Not all actions require the same level of authority. Scopes define **quorum rules** to determine how many keys (and which roles) must approve a record before it is valid.

Examples:

* A simple scope might require **1-of-1** for all actions.
* A research institution might require **3-of-5** trusted signers to approve new subscopes.
* A multinational federation might use **tiered quorum**, requiring multiple signatures from different geographic or organizational groups.

These quorum rules are expressed in the `policy:set` data and enforced deterministically by ledger clients.

---

## **6.6 Permitted Record Types**

Policies can constrain **what types of records** may be appended within a scope. For example:

* `org.example` might only allow `scope:request`, `scope:create`, `scope:genesis`, and `policy:set` records.
* `org.example.project` might allow additional `attest` or `data:publish` records.

This prevents unauthorized use of a namespace and keeps the scope’s chain **predictable and auditable**.

---

## **6.7 Delegation and Subscope Governance**

Policies allow scopes to **delegate authority downward**. For example, `org.example` might delegate authority to `org.example.research` to create its own subscopes. This is encoded through a combination of `policy:set` and `key:grant` records, making delegation **transparent and verifiable**.

Delegation doesn’t remove authority from the parent; it **shares it**. Parents can still override or set global constraints if desired, but the child governs its internal policies independently after genesis.

---

## **6.8 Enforcement Without Intermediaries**

One of the most powerful aspects of this policy system is that **no external intermediaries are required**. Enforcement happens through deterministic verification:

* Clients validate signatures and quorums.
* Invalid records are simply ignored.
* Policy state is reconstructed by replaying the chain.

No courts, registrars, or administrators are required to adjudicate validity. **Evidence is the final arbiter**.

---

## **6.9 Policy Transparency and Auditing**

Because all policy records live in the ledger, they form a **transparent historical trail**. Auditors, researchers, or other scopes can:

* Inspect past and current policies.
* Verify who changed what and when.
* Reconstruct decision-making contexts.

This transparency builds trust and prevents silent power shifts.

---

## **6.10 Case Studies**

### **6.10.1 Academic Consortium**

An academic consortium under `edu.research` uses a **3-of-5 quorum** of institutional keys for major policy changes. Each university holds one key. Policies define which actions require consensus and which can be delegated to working groups.

### **6.10.2 Corporate Department**

A corporate scope under `org.example` delegates sub-policy control to departments. `org.example.eng` uses a single administrative key for daily operations but requires approval from corporate leadership for major changes.

### **6.10.3 Open Commons**

A commons scope under `commons` allows anyone to append `attest` records but restricts `policy:set` and `key:grant` to a quorum of maintainers. Policies are simple and transparent, encouraging broad participation without chaos.

---

## **6.11 Policy as Living Law**

Policies are not static documents; they are **living law**, evolving as scopes grow and change. Because they are recorded on-ledger, every change is permanent and auditable. This allows governance to **adapt without losing legitimacy**.

---

## **6.12 Toward Self-Governing Federations**

When multiple scopes federate, their policies interact. Federation agreements are implemented through **attestations and cross-signatures**, not treaties. Each scope retains its own constitution while participating in larger governance structures. This creates a fabric of **self-governing enclaves**, each defined by its policies, connected through evidence rather than centralized law.

---

*In the next chapter, we will explore how economics emerges from this landscape—how proofs replace payments, how transparent flows reshape capital, and how trust itself becomes a currency.*
