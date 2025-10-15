# 🕰 **Cryptophysics: A Practical Guide**

> *Temporal substrates. Deterministic trust. A lattice that outlives us.*

---

## 📖 Overview

**Cryptophysics** is a new scientific discipline centered on the deterministic intersection of **time**, **cryptography**, and **information flow**. This repository accompanies the book *Cryptophysics: A Practical Guide* — a field manual for building civilization-scale systems on a substrate of immutable temporal records.

At its core lies the **HodeauxLedger**, a sidereal-time anchored, cryptographically signed, append-only data lattice. Unlike blockchains, which rely on chain height and probabilistic consensus, the lattice derives order directly from **Genesis Time**. Every record is a point in temporal-spatial coordinates:

```
Turn.Mark.Submark.Micromark (t, x, y, z)
```

Temporal placement is deterministic. Spatial coordinates (x, y, z) are optional, but when present, they bind records to physical or conceptual space with the same precision as time.

This README gives you the conceptual lay of the land. The book and accompanying papers dive deep into:

* Temporal anchoring and the Genesis Lineage
* Record casting, ushering, and deterministic placement
* Scopes and namespace hierarchy
* SelfID and sovereign identity
* VeroCoin and lattice-native economics
* Governance through math and trust, not committees

---

## 🌍 What Is Cryptophysics?

Cryptophysics treats **information as a physical phenomenon**. Instead of mutable ledgers and probabilistic clocks, it relies on:

* **Sidereal Time** — a fixed temporal substrate based on Earth’s rotation relative to distant stars.
* **Deterministic Hashing** — Ed25519 cryptography ensures every record’s identity is immutable and verifiable.
* **Temporal Lattice Structure** — Each record is anchored in time and space, forming a crystal-like informational structure.

It’s not a blockchain. It’s not a database. It’s a **time crystal for information** — where each cast record becomes an immutable facet of civilization’s shared memory.

---

## 🪄 Key Concepts

### 🪐 **Genesis Time**

Genesis Time (GT[0]) is the fixed epoch:

> **Saturday, July 19, 2025 09:13:07 MST (UTC−7)**

All temporal calculations are measured in sidereal milliseconds since this moment.

### 🧱 **Records (R⬢)**

Each record is cast with cryptographic signatures and deterministic coordinates. Fields include `previous_hash`, `scope`, `nonce`, `author_pk`, `usher_pk`, `record_type`, `data`, and `context` (temporal + spatial coordinates).

### 🚪 **Ushers**

Ushers are deterministic insertion authorities. They don’t compete like miners; they **anchor** intents into the lattice, ensuring proper ordering and routing by scope.

### 🧭 **Scopes**

Scopes are cryptographic namespaces. They organize identity, governance, and data flows. Scopes create a **hierarchical lattice** — similar to DNS, but cryptographically enforced and temporally anchored.

### 🪪 **SelfID**

SelfID provides sovereign identity: minimal, cryptographically verifiable, scope-relative identities that can collect attestations to build decentralized trust graphs.

### 💰 **VeroCoin**

VeroCoin is the lattice-native economic unit. Fixed supply, micro-denominated (Vera, Vint), and tied directly to eMotor.ID’s industrial backbone. It enables **transparent, deterministic economics** without central issuers.

---

## 🧭 Directory Structure

```
/
├── 📚 book/                 # Full manuscript (Markdown)
├── 📜 papers/               # Supplemental academic papers
├── 🧠 examples/             # Reference implementations & schemas
├── 🧰 tools/                # Command-line & SDK tools
├── 🧪 specs/                # Temporal math, R⬢ schema, protocol definitions
└── README.md               # You are here
```

---

## 🧪 Quickstart

1. **Install usher node** (Rust / Node)
2. **Load bootstrap.json** with root scope keys
3. **Cast a record** under `test.scope`
4. **Read it back** using deterministic Turn.Mark.Submark

```bash
usher init --bootstrap ./bootstrap.json
usher cast --scope test.example --type message --data '{"hello": "world"}'
usher read --scope test.example --turn 15 --mark 400
```

---

## 📝 Citation

If referencing this work in academic or technical contexts:

```
Hodo, Veronica. *Cryptophysics: A Practical Guide*. Verozaa Press, 2025.
```

---

## ⚖️ License

Licensed under Creative Commons Attribution-ShareAlike (CC BY-SA). Knowledge should flow, fork, and grow.

---

## 🌟 Acknowledgements

This work stands on the shoulders of:

* Sidereal timekeepers
* Cryptographers
* Hackers who never asked for permission
* Friends who believed before anyone else could see it

---

> “Time is no longer an external clock. It is the medium itself.”
