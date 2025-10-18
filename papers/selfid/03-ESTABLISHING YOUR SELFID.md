# **Chapter 3 — Establishing Your SelfID**

A SelfID is more than a concept—it’s something you can create, anchor, and use. The process isn’t ceremonial; it’s practical and deliberate. It involves generating cryptographic keys, deterministically deriving your scope, casting a `selfid:create` record, and optionally choosing how to present yourself. Think of it as authoring your **root of identity** in a way that’s both minimal and future-proof.

This chapter walks through each step, showing how individuals and collectives can establish their SelfID without needing permission from any platform or state. You’ll learn how to generate keys, derive scopes, craft your first R⬢ record, and begin layering attestations to form a durable web of trust.

---

## **3.1 Identity as Construction, Not Registration**

Traditional identity starts with registration: you fill out a form, hand over documents, and wait for an authority to grant you a credential. Establishing a SelfID reverses this. You don’t register—you **construct**.

Construction happens in three layers:

1. **Cryptographic:** Generate keypairs to represent your authority.
2. **Contextual:** Derive the human-readable xxxx-xxxx-xxxx-xxxx style scope for your identity.
3. **Temporal:** Cast your identity into the ledger with a `selfid:create` record anchored to Genesis Time.

These layers combine to form the base of your SelfID: unique, verifiable, and portable.

---

## **3.2 Generating Keys**

The backbone of SelfID is cryptography. Each identity is represented by one or more **Ed25519 keypairs**—chosen for their speed, security, and compact size. Generating a keypair involves creating a 32-byte private key and a corresponding 32-byte public key.

Unlike passwords or usernames, keys aren’t something you memorize. They’re mathematical entities stored securely on your device or hardware token. Your **public key** will become part of your SelfID record. Your **private key** is your signing authority—guard it carefully.

In practice, you might use a command-line tool, a web interface, or a hardware device to generate the pair. For example:

```bash
selfid keygen --algorithm ed25519
```

This outputs a fingerprint and a public key. The fingerprint is a shortened representation used for quick reference, much like how SSH keys are displayed. It’s what others might see when they inspect your records or verify signatures. It is also what's used to look up a SelfID scope.

### Key Hygiene

* **Never share your private key.** It’s not like a password you can reset.
* **Consider hardware-backed keys** (e.g., YubiKeys) for critical identities.
* **Backup encrypted private keys** securely—if you lose them, you lose your signing authority.
* **Generate subkeys** for different roles (e.g., daily use vs. cold storage) as your identity grows.

---

## **3.3 Deterministic Scopes**

Every SelfID lives inside a **scope**, a globally unique identifier derived deterministically from its public key. Scopes provide context, prevent collisions, and remove the need for human-chosen aliases.

The SelfID is generated as:

```text
group4( crockford32( blake3( public_key )[0..10] ) )
```

This produces a **16-character identifier**, grouped in 4s for readability. For example:

```text
8j3p-r9q2-zx1m-7fhd
```

Scopes are expressed in structured, human-readable form, but the **base of every scope** is always this deterministic SelfID, converted to lowercase automatically. For example:

```text
self.8j3p-r9q2-zx1m-7fhd
```

Organizational or delegated scopes branch from a base SelfID deterministically:

```text
self.8j3p-r9q2-zx1m-7fhd.team.engineering
self.8j3p-r9q2-zx1m-7fhd.devices.2025.batch001
```

The rules are simple but strict:

* Lowercase letters, numbers, hyphens for labels beyond the SelfID.
* Segments separated by periods.
* No leading or trailing hyphens or periods.
* Maximum total length of 65,535 characters (though most are short).

Once a scope is cast, it’s anchored to your key and Genesis Time forever. There’s no naming collision, no namespace squatting, and no registration fees — **your key *is* your namespace**. Choosing the right structure for sub-scopes matters, because while the base ID is permanent, the hierarchy you build on top of it shapes how others will discover and interact with your data.

---

## **3.4 Crafting the `selfid:create` Record**

Once you have keys and a derived scope, it’s time to **cast** your SelfID into the ledger. This happens through a R⬢ record of type `selfid:create`. This record declares:

* The scope name
* Your public key
* Optional display name
* Timestamp (Genesis Time mark)
* Signature (proving you control the key)

An example (simplified):

```json
{
  "scope": "self.8j3p-r9q2-zx1m-7fhd",
  "record_type": "selfid:create",
  "data": {
    "public_key": "aabbcc...",
    "display_name": "Veronica Hodo"
  },
  "at": "1234567000",
  "signature": [
    {
      "sig_type": "Author",
      "public_key": "aabbcc...",
      "sig": "ed25519:..."
    }
  ]
}
```

Casting this record is like planting your flag. Once appended, your identity exists in the ledger’s causal lattice. Others can resolve it, verify your key, and begin interacting with you.

---

## **3.5 Display Names and SelfIDs**

Display names make identities more approachable. You might not remember a 16-character scope or a 44-character base64 public key, but you’ll remember **“Veronica Hodo”** or **“Project Nebula”**. Display names are optional and non-binding—they’re for human readability, not canonical identity.

SelfIDs, on the other hand, are **derived from your public key** and used as shorthand in technical contexts. They’re what developers check when verifying a signature, or what you’d read aloud over a secure channel to confirm identity.

---

## **3.6 Optional Trait Attestations**

Identity doesn’t mean oversharing. Your base SelfID can be barebones: just a scope and a key. Over time, you can **attach optional trait attestations** to enrich your identity:

* **Date of Birth** (attested by a government or trusted organization)
* **Skills** (attested by colleagues, employers, or certification bodies)
* **Roles** (e.g., “Researcher,” “Project Lead,” signed by relevant collectives)
* **Memberships** (e.g., university affiliations, organizational memberships)

Each trait is an attestation record. You can choose to encrypt traits or make them public, depending on context. Traits don’t live *inside* your `selfid:create` record; they’re layered afterward, allowing identities to remain minimal at creation and **grow organically**.

---

## **3.7 Trait Signers and Trust Webs**

A trait attestation gains meaning through its **signer**. Anyone can claim to have a PhD; it matters more if a university SelfID signs that claim. Anyone can declare a skill; it matters if multiple trusted peers attest to it.

Trait signers form **trust webs** around your identity. Over time, these webs act as living resumes, social graphs, and reputation networks—except they’re cryptographically verifiable and decentralized.

Examples:

* A university signs your degree.
* A company signs your employment period.
* A peer signs your open-source contributions.
* A community signs your role in governance.

These attestations can expire, be revoked, or be layered with others, creating a dynamic web that evolves as your life does.

---

## **3.8 Keeping It Minimal**

The temptation is to frontload your SelfID with every detail. Resist it. The strength of SelfID lies in its **minimal core**. A scope, a key, a cast record—that’s enough to start. Traits and attestations can come later, layered modularly.

Why minimal?

* **Privacy:** Less data exposed by default.
* **Portability:** Easier to migrate across systems.
* **Simplicity:** Fewer moving parts at creation means fewer mistakes.
* **Future-proofing:** Traits may change; your core identity shouldn’t.

Think of your SelfID like a seed crystal: small, precise, but capable of growing a vast lattice over time.

---

## **3.9 Example: A Personal SelfID**

Let’s walk through a hypothetical:

1. **Generate keys:** `selfid keygen --algorithm ed25519`
2. **Derive the SelfID** `selfid show`
3. **Craft record:** Use a tool or API to create a `selfid:create` record.
4. **Sign and cast:** Append it to the ledger.
5. **Optional traits:** Later, add attestations for age, skill, or affiliations.

Within seconds, **Alba Neko** now has a persistent, verifiable identity that exists independently of governments or platforms. Anyone can verify its existence, signature, and temporal anchor. Over time, trust webs will grow around it.

---

## **3.10 Organizational Example**

A collective research lab decides to establish a SelfID:

1. Generate a root key and several delegated keys for departments.
2. Derive the organizational SelfID from the root key.
3. Craft and cast a `selfid:create` record.
4. Attest roles for members, assign trait signers for certifications.
5. Use quorum signatures for governance actions.

Now the lab exists as a **cryptographically anchored entity**, capable of signing publications, issuing attestations, and participating in governance as a recognized identity.

---

## **3.11 Summary**

Establishing a SelfID is a deliberate act of authorship. You generate keys, deterministically derive a scope, cast a record, and begin layering trust over time. It’s minimal, permissionless, and extensible. You don’t ask anyone to recognize you; you **anchor yourself** in the lattice of causality and let trust accumulate through verifiable interactions.

Whether you’re an individual staking your claim in digital space or a collective defining its presence, the process is the same: cryptographic roots, temporal anchoring, and narrative authorship.
