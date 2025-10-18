# **Appendices**

---

## **A. Record Schema for `selfid` and `attest` Types**

This appendix provides canonical schema definitions for two core record types in the SelfID system: `selfid` and `attest`. These schemas are expressed in structured JSON form, but actual transport uses CBOR for compactness.

### **A.1 `selfid:create` Record**

```json
{
  "protocol": "rhex/1",
  "scope": "<identity.scope>",
  "record_type": "selfid:create",
  "data": {
    "display_name": "<string>",
    "traits": {
      "dob": "<optional ISO8601>",
      "role": ["developer", "artist"],
      "public_keys": ["ed25519:<base58>"]
    }
  },
  "fingerprint": "<ed25519 public key>",
  "at": "GT[xxx.xx.xx@xxx]",
  "signature": "<ed25519 signature>"
}
```

* **scope** defines the globally unique name.
* **data.traits** holds initial identity traits (optional, minimal by design).
* **fingerprint** is the signing key for this record.
* **at** anchors the record in Genesis Time.

### **A.2 `attest` Record**

```json
{
  "protocol": "rhex/1",
  "scope": "attest.<signer-scope>",
  "record_type": "attest",
  "data": {
    "subject": "<selfid-scope>",
    "claim": {
      "type": "skill",
      "name": "Rust Programming",
      "level": "advanced"
    },
    "expiry": "GT[optional]"
  },
  "fingerprint": "<signer public key>",
  "at": "GT[xxx.xx.xx@xxx]",
  "signature": "<ed25519 signature>"
}
```

* **subject** is the SelfID being attested to.
* **claim** is the structured or textual assertion.
* **expiry** (optional) sets temporal validity.

Revocations reference the hash of the original record using a `attest:revoke` record.

---

## **B. Trait Naming Conventions and Policies**

Traits describe attributes of identities. Consistent naming ensures interoperability and clarity across ecosystems.

### **B.1 Naming Conventions**

* Use **lowercase kebab-case** for trait names: `date-of-birth`, `university-degree`, `rust-skill-level`.
* Avoid ambiguous names. Be explicit: `phd-computer-science` rather than `phd`.
* Group related traits under common prefixes when possible: `contact:email`, `contact:phone`.
* Use short but descriptive names—traits should be human-readable without external documentation.

### **B.2 Trait Policies**

* **Minimalism:** Only include traits necessary for identity function or proof contexts.
* **Verifiability:** Traits should be attestable by external signers where relevant.
* **Privacy First:** Sensitive traits (e.g., DOB, legal names) should use selective disclosure or encryption by default.
* **Expiry:** Where appropriate, traits should have clear validity periods (e.g., licenses, memberships).
* **Versioning:** Trait definitions can include version fields to support schema evolution.

---

## **C. Example Attestation Chains**

Attestation chains demonstrate how claims build on each other to form provenance.

### **C.1 Academic → Employment → Research**

1. **University → Alice**

```json
{
  "subject": "alice.id",
  "claim": {
    "type": "degree",
    "field": "Computer Science",
    "institution": "Example University"
  }
}
```

2. **Company → Alice**

```json
{
  "subject": "alice.id",
  "claim": {
    "type": "employment",
    "role": "Software Engineer",
    "period": "2022-2025"
  }
}
```

3. **Research Lab → Alice**

```json
{
  "subject": "alice.id",
  "claim": {
    "type": "publication",
    "doi": "10.1234/example.paper"
  }
}
```

Chaining these:

* Employer verifies degree.
* Research lab verifies employment.
* Collaborators verify publication.

Anyone can follow the chain to confirm Alice’s credentials **without contacting intermediaries**.

### **C.2 Peer Skill Web**

A distributed group of developers sign skill attestations for each other’s work in an open-source project. Over time, this forms a **dense skill web** that can be visualized and analyzed to identify expertise clusters and bridges.

---

## **D. Rust/JS Implementation Notes**

### **D.1 Rust**

The Rust core uses the `hl_core` crate family:

* `hl_proto` for record schemas and serialization (CBOR + canonical JSON).
* `hl_crypto` for Ed25519 signing and verification.
* `hl_io` for local caching and ledger sync.

Key concepts:

* Use canonical serialization before signing.
* Maintain local SQLite caches for key and scope lookups.
* Handle time using Genesis Time (sidereal days), not UNIX timestamps.

```rust
use hl_proto::record::RhexRecord;
use hl_crypto::sign;

let record = RhexRecord::new_selfid("alice.id", &display_name);
let signature = sign(&record, &private_key);
```

### **D.2 JavaScript / TypeScript**

JS integrations use `@trustarchi/ledger` for signing and transport. Common patterns:

* Use `TextEncoder`/`TextDecoder` for canonical encoding.
* Generate keys using WebCrypto or libsodium wrappers.
* Store keys in browser secure storage or mobile keychains.

```ts
import { createSelfIDRecord, signRecord } from "@trustarchi/ledger";

const record = createSelfIDRecord({ scope: "alice.id", displayName: "Alice" });
const signature = await signRecord(record, privateKey);
```

---

## **E. Integration Recipes for Web & Native Apps**

### **E.1 Web Login Without Passwords**

1. User signs a challenge from the server with their SelfID key.
2. Server verifies signature against the ledger.
3. User is authenticated without centralized credential storage.

### **E.2 Selective Trait Disclosure**

1. User holds an attestation of DOB.
2. Generates zero-knowledge proof of age >18.
3. Shares proof with relying party; underlying DOB remains private.

### **E.3 Mobile Sub-ID for Temporary Apps**

1. Generate ephemeral sub-ID on device.
2. Link it to primary SelfID with a revocable delegation.
3. Use sub-ID for temporary authentication or event participation.

### **E.4 Organizational Delegation**

1. Root org key delegates signing to departmental keys.
2. Departmental keys sign daily records.
3. Revocation and rotation handled through quorum signatures.

### **E.5 Cross-Platform Identity Portability**

* Sync keys and records between devices using recovery protocols.
* Authenticate seamlessly across browsers, mobile, and native apps.

---

## **F. Glossary of Terms**

**Attestation** — A signed claim about a SelfID by another identity, forming the fabric of trust.

**Delegated Key** — A subordinate key authorized to act on behalf of a primary identity.

**Ephemeral Sub-ID** — A temporary identity derived from a primary SelfID for privacy or contextual use.

**Genesis Time** — The sidereal-based temporal framework anchoring all ledger events.

**Quorum Signature** — A threshold-based multi-signature verifying collective approval.

**Scope** — The globally unique namespace identifier for a SelfID.

**Selective Disclosure** — Proving specific facts without revealing underlying data.

**SelfID** — A sovereign, scope-based, cryptographically anchored identity.

**VeroScore** — A transparent, explainable trust score derived from attestations.

**Zero-Knowledge Proof** — A cryptographic proof allowing someone to prove possession of a fact without revealing the fact itself.

---

This completes the **Appendices**. Together, these references provide developers, stewards, and researchers with the concrete schemas, conventions, examples, and implementation details necessary to build and integrate SelfID systems into real-world applications.
