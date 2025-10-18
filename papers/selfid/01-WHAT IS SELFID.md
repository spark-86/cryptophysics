# **Chapter 1 — What Is SelfID?**

Identity in the digital age is a peculiar mixture of power and fragility. We carry dozens—sometimes hundreds—of logins, identification numbers, passwords, and security questions, all bound to institutions that mediate our existence. A government can revoke a passport; a platform can deactivate an account; a bank can freeze an identity number. These systems work—until they don’t. And when they fail, the individual is rarely in control.

SelfID begins where those systems end: it places the root of identity in the hands of the individual. Rather than relying on external registrars, a SelfID is **a scope-based, cryptographically anchored identity**—minimal by design, but extensible enough to represent the full complexity of human life, organizations, and history. It’s not a social profile. It’s not a username. It’s not a blockchain wallet. It is a **sovereign root of trust**, bound to time, keys, and transparent attestations.

---

## **1.1 Defining SelfID**

At its core, a SelfID is a record cast into the ledger, defining a unique identity scope and the cryptographic keys that represent it. Think of it as planting a flag in temporal bedrock. This record contains just enough to establish **who** is being defined (scope), **when** the identity began (Genesis Time reference), and **which keys** are authorized to act on its behalf.

A SelfID has three essential properties:

1. **Scope-based naming:** Each identity exists within a globally unique namespace, expressed as a human-readable, structured scope. This provides contextual anchoring without central registries.
2. **Cryptographic authority:** The identity is represented by one or more Ed25519 public keys, which can sign, attest, and delegate.
3. **Temporal anchoring:** The identity’s creation is fixed at a precise moment in Genesis Time—a sidereal-based universal timeline—placing it immutably within the lattice of causality.

The result is a foundation that is neither controlled by a platform nor dependent on a state. It is **owned and authored by the individual or collective that created it.**

---

## **1.2 The Scope Format: xxxx-xxxx-xxxx-xxxx**

Human-readable identifiers are essential for usability, but they must be structured to prevent collisions and ensure verifiability. SelfID uses a canonical format similar to:

```text
xxxx-xxxx-xxxx-xxxx
```

Each segment is five-bit encoded using Crockford Base32, allowing the ID to be easily spoken, written, and error-checked.

Unlike usernames or email addresses, this ID does not depend on DNS registrars, centralized databases, or corporate namespaces. It exists because it was cast into the ledger at a specific Genesis Time mark. If two identities attempt to claim the same scope, the chain of causality resolves which is canonical based on time and cryptographic evidence.

This makes SelfIDs as solid as mathematical proofs: you can verify them without asking anyone for permission.

---

## **1.3 SelfID vs. Traditional Identity Systems**

To understand SelfID’s role, it helps to compare it with familiar systems:

* **Passports** are issued by states. They prove citizenship and identity but depend entirely on the issuing government’s authority. Lose the state’s backing, lose the identity.
* **OAuth logins** (e.g., “Sign in with Google”) offer convenience but hand immense power to private platforms. They can be revoked or censored at will, and they require trusting opaque infrastructures.
* **Blockchain addresses** are cryptographically solid but contextually poor. A hex string or base58 key offers no inherent human meaning, and addresses are rigid rather than extensible.
* **Legal names** exist socially and bureaucratically, but they’re not verifiable in a cryptographic sense. They rely on shared trust in institutions, not mathematics.

SelfID blends the strengths of these systems while shedding their weaknesses. Like a blockchain address, it’s cryptographically provable. Like a legal name, it can be human-readable. Unlike either, it’s **independently sovereign**, portable, and temporally grounded.

---

## **1.4 Signing Authorities and Trust Webs**

A SelfID alone is minimal—it proves that someone anchored an identity at a point in time. To build trust, **signing authorities** come into play. These are other SelfIDs that issue **attestations**, digitally signing claims about the identity. A university might attest to your degree; a colleague might attest to your skills; a network might attest to your role.

Each attestation is a ledger record, referencing both the signer and the subject. Over time, these records form a **web of trust**, creating a verifiable narrative around the identity. Importantly, these attestations are not stored in a private company’s database—they’re part of the shared ledger, independently verifiable and tamper-evident.

The result is a trust fabric that doesn’t depend on a single issuer but emerges from many cryptographic voices.

---

## **1.5 VeroScore: Quantifying Trust Without Opaqueness**

In traditional systems, trust is often quantified through scores—credit scores, trust ratings, reputation numbers—but these are usually opaque and centralized. **VeroScore** is a ledger-native trust metric calculated from attestations. It is transparent, explainable, and portable.

Each score references the attestations it was derived from, making it **auditable**: if someone disputes a score, they can trace it back through the cryptographic record. This stands in contrast to centralized scoring systems, where individuals are subject to decisions they cannot inspect or challenge.

VeroScore doesn’t replace human judgment; it supplements it with verifiable context.

---

## **1.6 Genesis Time and the Lattice of Causality**

Every SelfID is created at a specific **Genesis Time mark**—a universal sidereal-based time coordinate. Unlike Unix time, which is solar and political, Genesis Time operates like a clock that the stars themselves keep. Each SelfID’s creation mark places it immutably within a **lattice of causality**: a chronological structure where every record’s order can be proven.

This anchoring solves a critical problem: identity races and forgeries. If two claims exist for the same scope, the ledger can determine which came first, which keys were valid at that time, and which record is canonical. Genesis Time is the backbone that keeps identity coherent across the entire network.

It also means that your identity isn’t just something you hold now—it’s a timestamped part of history.

---

## **1.7 Extensibility Without Bloat**

SelfID starts minimal: a scope and a key. But it can grow. New keys can be added or revoked through additional records. Traits can be attached, encrypted, shared selectively. Organizational structures can emerge around identities without inflating the core record. This is deliberate: **the core remains stable while layers evolve**.

This modularity is what allows SelfID to scale from a single person to a global institution without losing clarity or integrity. A personal ID might only ever have a handful of attestations. A university’s SelfID could have thousands. Both live in the same structure.

---

## **1.8 Beyond Individuals**

Although the term “SelfID” suggests personal identity, the same structure applies to collectives, machines, and abstract entities. A sensor network can have a SelfID. A research project can have a SelfID. Even a fictional character can have one. The key requirement is a scope, a key, and a cast record. From there, the web of trust can form around anything that can sign or be signed for.

This opens doors to forms of identity governance and interaction that simply aren’t possible with legacy systems.

---

## **1.9 A Foundation, Not a Feature**

Perhaps the most important thing to understand about SelfID is that it isn’t a product feature or a service. It’s a **foundation**—a neutral substrate upon which entire ecosystems can be built. Social networks, governments, marketplaces, research institutions, and individuals can all use the same identity fabric without one controlling the others.

Where OAuth logins tie you to a platform, SelfID ties you to yourself.

---

## **1.10 Summary**

SelfID is a cryptographically anchored, scope-defined, temporally fixed identity system that removes intermediaries and restores authorship to individuals and collectives. It blends the readability of legal names, the verifiability of cryptographic keys, and the temporal coherence of Genesis Time. It’s minimal, extensible, and transparent.

By shifting the foundation of identity from institutions to individuals, SelfID enables a new layer of trust—one that is verifiable, portable, and historically grounded. In the chapters to come, we’ll explore how to establish one, live with one, and build the lattice of trust that makes it world-changing.
