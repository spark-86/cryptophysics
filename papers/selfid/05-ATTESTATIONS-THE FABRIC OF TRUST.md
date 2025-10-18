# **Chapter 5 — Attestations: The Fabric of Trust**

Identity alone doesn’t create trust. A key and a scope prove that you exist and control a cryptographic identity—but they don’t say *why* anyone should trust you. That trust emerges through **attestations**: signed claims made by others about your identity. Attestations form the **fabric of trust**—the living tissue between identities in the lattice.

Attestations are not likes, endorsements, or ephemeral badges. They’re cryptographic testimonies—verifiable statements anchored in time. This chapter explores how attestations work, their structure, how they accumulate into VeroScores, and how they transform reputation from opaque ratings into transparent, auditable trust webs.

---

## **5.1 What Are Attestations?**

An attestation is a signed claim made by one SelfID about another. It can assert a fact, an opinion, or a credential:

* “This person worked at my company from 2022–2025.”
* “This lab verified these experimental results.”
* “This artist is part of our collective.”
* “This key belongs to this device.”

Each attestation is a **ledger record** that:

* References the **subject** (the SelfID being attested to).
* Identifies the **signer** (the SelfID making the claim).
* Contains the **claim** data (structured or unstructured).
* Is **signed** by the signer’s private key.
* Is anchored to a **Genesis Time mark** for temporal ordering.

Unlike centralized endorsements or social media likes, attestations are portable, durable, and verifiable by anyone.

---

## **5.2 Anatomy of an Attestation**

Attestations follow a clear structure, typically represented in R⬢ form:

```json
{
  "scope": "self.8j3p-r9q2-zx1m-7fhd.attestations",
  "record_type": "attest",
  "data": {
    "subject": "alba.neko",
    "claim": {
      "type": "skill",
      "name": "Rust Programming",
      "level": "advanced"
    },
    "expiry": "6000000000"
  },
  "author_pk": "abcd1234...",
  "at": "5122312000",
  "signature": [
    {
      "sig_type": "Author",
      "public_key": "aabbcc...",
      "sig": "ed25519:..."
    },
    {
      "sig_type": "Usher",
      "public_key": "aabbcc...",
      "sig": "ed25519:..."
    }
  ]
}
```

**Key components:**

* **Subject:** The SelfID this attestation is about.
* **Claim:** The actual content being asserted. Can be structured (skills, roles) or textual.
* **Signer:** Implicitly defined by the fingerprint and signature.
* **Timestamp:** When the attestation was cast (Genesis Time mark).
* **Expiry:** Optional. Defines how long the attestation should be considered valid.
* **Signature:** Cryptographic proof that the signer made this claim.

This structure makes attestations easy to verify and audit. Anyone can follow the chain: resolve the signer’s public key, verify the signature, check the timestamp, and decide whether to trust the claim.

---

## **5.3 Types of Attestations**

While attestations are flexible, common patterns emerge:

### **Skill Attestations**

Peers, employers, or communities can attest to skills:

* “Alice is an expert in embedded systems.”
* “Bob contributed significantly to our machine learning stack.”

These accumulate to form a **cryptographically verifiable résumé**, where endorsements are transparent and timestamped.

### **Affiliation Attestations**

Organizations can attest to memberships, roles, or affiliations:

* “Carla is a member of our guild.”
* “Dana served as Treasurer of this collective from 2023–2024.”

Unlike centralized directories, these claims persist beyond the organization’s lifetime.

### **Location and Presence Attestations**

Entities can attest to someone being at a place or event:

* “Eli attended the 2025 Temporal Cryptophysics Summit.”
* “Frank was present at this lab on a given date.”

Useful for credentialing, security, or historical provenance.

### **Achievement Attestations**

Milestones, awards, or accomplishments:

* “Greta completed the ‘Ledger Systems Masterclass.’”
* “Hector’s experiment achieved peer replication.”

---

## **5.4 Accumulation and Webs of Trust**

A single attestation is just a statement. But as attestations **accumulate**, they form a **web of trust** around a SelfID. Over time:

* Multiple peers attest to the same skill → the skill becomes strongly credible.
* Independent organizations attest to an affiliation → the role gains weight.
* A cluster of researchers attest to each other’s work → a scientific trust network emerges.

This accumulation happens organically, without central coordination. Anyone can follow the chain of attestations to understand **who trusts whom and why**.

The ledger provides permanence: attestations aren’t lost when platforms disappear, and they can be cryptographically traced years later.

---

## **5.5 VeroScore: Quantifying Without Opaqueness**

Trust often needs to be summarized—whether for hiring, collaboration, or access control. Traditional systems use opaque scores (credit scores, reputation points) that users cannot inspect or challenge. **VeroScore** changes this.

VeroScore is a transparent, explainable trust metric computed from attestations. Instead of relying on a black box, every component of a VeroScore can be traced to specific R⬢ records.

### **How VeroScore Works**

1. Collect all attestations about a SelfID within a defined scope or domain.
2. Apply weighting functions (e.g., trust of signer, recency, type of attestation).
3. Produce a numeric or categorical score.
4. Publish the calculation **with references to the source attestations**.

Anyone can verify the score by following the cited R⬢ records. If they disagree with the weighting, they can recompute their own.

This **auditable scoring** model replaces opaque authority with transparent computation.

---

## **5.6 Expiry, Revocation, and Trust Dynamics**

Attestations don’t have to last forever. Skills evolve, affiliations change, organizations dissolve. The attestation model includes **expiry** and **revocation** mechanisms:

* **Expiry:** Set a date after which the attestation is no longer considered valid.
* **Revocation:** A signer can issue a `attest:revoke` record, invalidating a previous attestation.

This keeps trust webs accurate over time. It also reflects real human dynamics: trust can fade or be withdrawn, and the ledger records those changes transparently.

---

## **5.7 Social Dynamics of Attestation**

Attestations are not social likes. They are closer to **public testimonies**. When you sign an attestation, you’re staking your reputation. This changes the social dynamics around identity:

* **Attesting carries responsibility.** Reckless attestations damage the signer’s credibility.
* **Endorsements become meaningful.** Instead of button-click popularity, attestations reflect deliberate judgment.
* **Reputation flows both ways.** The subject gains trust, but the signer’s trustworthiness is also on display.

This discourages shallow reputation inflation and encourages thoughtful, contextual attestation.

### Example: A Skill Web

Imagine a global network of open-source contributors. Instead of star counts or follower numbers, contributors sign attestations about each other’s skills and contributions. Over time, clusters form. Some contributors become hubs of expertise. Others form bridges between communities. The web reflects *real collaboration*, not platform-driven metrics.

---

## **5.8 Attestation Chains and Provenance**

Attestations can **reference other attestations**, forming chains that document provenance:

* University attests to degree → Employer attests to hiring based on that degree → Research group attests to published work based on employment.

These chains allow anyone to trace claims back to their roots, checking each signature along the way. This is critical for contexts like science, governance, or finance, where verifying the *lineage* of claims matters as much as the claims themselves.

---

## **5.9 Institutional vs. Peer Attestations**

Both institutions and individuals can issue attestations, but they carry different social weight:

* **Institutional attestations** often serve as strong anchors—e.g., a university’s attestation of a degree.
* **Peer attestations** provide breadth and nuance—e.g., dozens of colleagues vouching for your skills.

The two interact dynamically. A single institutional attestation might seed credibility; peer attestations build texture and resilience around it.

This interplay produces richer trust webs than either centralized credentials or pure peer reputation systems alone.

---

## **5.10 Attestations in Practice**

### **Personal Example: A Researcher**

A researcher builds a SelfID early in their career. Their university issues a degree attestation. Peers attest to their lab work. Collaborators attest to co-authored papers. Over time, their trust web reflects both institutional recognition and peer respect. Their VeroScore for “scientific credibility” is auditable and portable across institutions.

### **Institutional Example: A Collective**

A civic collective issues attestations to its members for roles, contributions, and governance participation. These attestations form the basis for internal decision-making and external recognition. When members leave, their attestations remain in the ledger as historical records.

### **Infrastructure Example: Devices and Sensors**

A network of sensors each has a SelfID. Attestations are used to verify device authenticity, calibration history, and network memberships. Trust flows not from a central hub, but from **chains of attestations** across the network.

---

## **5.11 Reputation Without Gamification**

Modern reputation systems—social media likes, five-star ratings, credit scores—are often gamified or manipulated. They rely on opaque algorithms and centralized platforms. Attestations change the game by making reputation:

* **Explicit:** Each attestation is a deliberate, signed act.
* **Verifiable:** Anyone can audit claims and chains.
* **Contextual:** A skill attestation means something different from a location attestation.
* **Non-transferable:** You can’t buy attestations the way you can buy likes; signers stake their own trust.

This turns reputation into something **earned and traceable**, rather than accumulated through algorithmic popularity contests.

---

## **5.12 Summary**

Attestations transform identity from a static claim into a living, verifiable network of trust. Each attestation is a cryptographic testimony—structured, signed, timestamped, and optionally expiring. As they accumulate, attestations form webs that can be quantified through VeroScores, but always with transparent, auditable lineage.

This fabric of trust replaces opaque rating systems with **open, inspectable provenance**. It shifts reputation from gamified signals to meaningful, verifiable testimony. In a world built on SelfID, attestations are the threads that weave individuals, institutions, and networks into a resilient, honest lattice of trust.
