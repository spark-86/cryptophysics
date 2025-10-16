# 🕰 **Trust Architecture Library Index**

> *Temporal substrates. Deterministic trust. A lattice that outlives us.*

---

## 📚 **Overview**

This repository is the **living library** of **Cryptophysics** — the discipline that unites **time**, **cryptography**, and **information** into a deterministic substrate for civilization.

At the center is the **HodeauxLedger**, a sidereal-time anchored, cryptographically signed, append-only temporal lattice. From this substrate, new sciences and practical systems emerge: identity, governance, economics, namespaces, and post-scarcity infrastructure.

The library is organized into **six core volumes**, each focusing on a pillar of the architecture. Together they form a complete reference set for researchers, builders, and stewards.

---

## 📖 **Core Volumes**

### 1. 🧭 **Cryptophysics: A Practical Guide**

> *The foundation.* Temporal anchoring, lattice construction, and the physics of immutable records.

* Introduces Genesis Time and the sidereal temporal substrate
* Details R⬢ record structure, ushering, and deterministic placement
* Establishes the lattice as a “time crystal for information”
* Practical field manual for implementing the substrate itself

📁 [`papers/cryptophysics/`](./papers/cryptophysics)

---

### 2. 🪪 **SelfID — Sovereign Identity in a Transparent World**

> *Identity without gatekeepers.* Deterministic scope naming, attestations, and trust graphs.

* SelfID derivation from public keys
* Creation rules for SelfID scopes
* Trust accumulation through attestations and VeroScore
* Rotation, revocation, and trait-based identity

📁 [`papers/selfid/`](./papers/selfid)

---

### 3. 💰 **Economy of the Lie**

> *Incentives as physics.* How making lies expensive reshapes civilization.

* Mathematical framing of lie propagation in temporal lattices
* Reward structures for truthful attestation
* Punishment mechanisms for deceit through stake decay and arbitration
* Economic scaffolding for truth-native economies

📁 [`papers/economy/`](./papers/economy)

---

### 4. 🧭 **Scopes — The Namespace of Truth**

> *The organizing principle.* Cryptographic namespaces for identity, governance, and data flows.

* Scope creation, lineage, and hierarchical resolution
* Temporal anchoring of namespaces
* Practical examples: organizational registries, SelfID scopes, service discovery
* Future namespace evolution beyond DNS

📁 [`papers/scopes/`](./papers/scopes)

---

### 5. 🕸 **The Temporal Lattice and You**

> *Living inside the crystal.* How deterministic time reshapes systems, interfaces, and cognition.

* Temporal coordinate system (Turn.Mark.Submark.Micromark)
* Reading, navigating, and projecting within the lattice
* Mapping spatial data onto temporal structure
* Implications for software, governance, and human understanding

📁 [`papers/lattice/`](./papers/lattice)

---

### 6. 🧱 **The Five Pillars of Oppression**

> *Breaking brittle systems.* Energy, food, money, medicine, and war under transparent cryptophysics.

* How each pillar relies on opaque intermediaries
* Strategies for replacement with auditable, cooperative architectures
* Transitional hybrid models and flywheel effects
* Civilization-level implications of trust-native substrates

📁 [`papers/pillars/`](./papers/pillars)

---

## 🗂 **Directory Structure**

```
/
├── 📚 book/                 # Full manuscript (Markdown)
├── 📜 papers/               # Core papers by topic (see index above)
├── 🧠 examples/             # Reference implementations & schemas
├── 🧰 tools/                # Command-line & SDK tools
├── 🧪 specs/                # Temporal math, R⬢ schema, protocol definitions
└── README.md               # You are here
```

---

## 🧪 **Quickstart**

1. **Install usher node** (Rust / Node)
2. **Bootstrap root scope** with provided keys
3. **Cast and read a record** to anchor your first temporal point

```bash
usher init --bootstrap ./bootstrap.json
usher cast --scope test.example --type message --data '{"hello": "world"}'
usher read --scope test.example --turn 15 --mark 400
```

---

## �
