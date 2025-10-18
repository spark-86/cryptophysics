# **Chapter 7 — Collective Identities and Organizations**

Identity is not limited to individuals. Human history is filled with collectives—guilds, companies, religious orders, governments, co-ops, research labs, and spontaneous movements. These entities shape culture, build infrastructure, govern nations, and create knowledge. Yet their identities have always been **mediated through legal and bureaucratic frameworks**. A state issues a charter. A platform grants an organizational account. A notary seals the incorporation documents.

SelfID offers a new path: **collective identities** that exist natively on the ledger, cryptographically anchored and transparently governed. Groups, DAOs, corporations, labs, unions, co-ops, and informal collectives can establish organizational SelfIDs, wield delegated keys, use quorum signatures, and evolve membership over time—all without waiting for state approval or platform permission.

This chapter explores how collective SelfIDs work, how they differ from traditional incorporation, and how they enable new forms of coordination and trust.

---

## **7.1 Why Collective Identity Matters**

Collectives are fundamental actors in society. They build cathedrals, run businesses, govern cities, and publish scientific knowledge. But their identity systems are archaic:

* **State incorporation:** A legal document defines existence. Trust flows from the state.
* **Platform accounts:** A company or group depends on a platform’s continued existence and policies.
* **Informal collectives:** Movements operate through shared hashtags or group chats, but have no verifiable identity.

These systems either depend on external grant of authority (state, platform) or remain ephemeral and unverifiable. They lack **cryptographic authorship** and **transparent governance structures**.

Ledger-based collective SelfIDs invert this relationship. The collective authors its identity, proves control through keys and quorum signatures, and builds reputation through attestations and action—not bureaucratic endorsement.

---

## **7.2 Establishing a Collective SelfID**

Creating a collective SelfID mirrors the individual process, with some additional layers:

1. **Scope Selection:** Choose a globally unique scope, e.g. `research.collective.tempe`.
2. **Key Generation:** Generate one or more Ed25519 keypairs for the organization.
3. **Casting the Record:** Issue a `selfid:create` record under the chosen scope.
4. **Delegation:** Assign roles and permissions to different keys.
5. **Attestation and Trust:** Begin receiving and issuing attestations as an entity.

The result is a **cryptographically anchored collective** that can sign, speak, and act on the ledger just like an individual SelfID.

---

## **7.3 Delegated Keys and Role Separation**

Organizations rarely operate with a single key. They require **delegated keys** for different functions:

* **Root key:** Stored securely, used for foundational decisions (e.g., revoking other keys).
* **Operational keys:** Used for daily actions, signing communications, or publishing records.
* **Departmental keys:** Assigned to subgroups (e.g., a lab’s physics division vs. its admin office).

Delegation allows large collectives to function securely. Compromising a single operational key doesn’t jeopardize the entire organization. Key delegation can be explicitly recorded on the ledger through `key:grant` and `key:revoke` records, providing **transparent key hierarchies**.

---

## **7.4 Quorum Signatures and Collective Decisions**

Many collective actions require agreement among multiple members. SelfID supports **quorum signatures**, where a threshold number of signatures must be collected before a record is valid.

For example, a DAO might require 5 of 9 board members to sign off on a funding proposal. A university department might require a quorum of faculty to publish official statements. A co-op might use majority signatures for financial decisions.

Quorum signatures are:

* **Transparent:** The required threshold and signers are known.
* **Verifiable:** Each signature is individually checkable against the ledger.
* **Immutable:** Once collected and cast, the record is fixed in the temporal lattice.

This eliminates the need for centralized secret ballots or opaque voting software. Governance becomes **cryptographically verifiable**, without sacrificing flexibility.

---

## **7.5 Evolving Membership**

Organizations change. People join, leave, and shift roles. Traditional systems require bureaucratic paperwork to reflect this. SelfID makes membership evolution a **living process**:

* New members receive delegated keys or trait attestations.
* Departing members have keys revoked and attestations updated.
* Role changes are reflected in updated delegation records.

Because all these changes are recorded on the ledger, the organization’s **membership state is auditable** at any point in time. You can see who held what role, when, and under whose authority.

---

## **7.6 Trust Without State Incorporation**

Traditional legal incorporation works by having a **state vouch** for the existence and governance of an organization. A company charter says, “This group exists, and here are its rules.”

In a ledger-native system, **trust is earned, not granted**:

* The organization proves continuity through cryptographic keys.
* It demonstrates governance through quorum signatures and delegation structures.
* It builds reputation through attestations from peers, collaborators, and institutions.

There’s no need to file paperwork to “exist.” Existence is proven by records in the temporal lattice. Trust emerges from action and verification, not from state-backed declarations.

This doesn’t necessarily replace legal incorporation—in many contexts, legal status remains useful—but it **liberates collective identity from dependence on it**.

---

## **7.7 Transparency vs. Bureaucracy**

Traditional organizational identity is **opaque**: bylaws stored in filing cabinets, board decisions recorded in minutes that may or may not be public, ownership structures buried in legal documents.

Ledger-based collective identities are **transparent by default**:

* Key delegations are on-chain.
* Quorum signatures are visible and verifiable.
* Membership changes are timestamped and permanent.
* Attestations are public or selectively disclosed.

Transparency replaces bureaucratic opacity with verifiable cryptographic evidence. This is especially powerful for public-interest organizations, DAOs, and research groups that need to maintain trust without relying on opaque intermediaries.

---

## **7.8 Organizational Reputation Through Attestations**

Organizations, like individuals, build reputation through **attestations**:

* Partners attest to collaborations.
* Customers attest to services.
* Members attest to their roles and experiences.
* Other organizations attest to affiliations.

These attestations form **institutional trust webs**. A lab with dozens of peer institutions attesting to its contributions develops global credibility. A DAO with transparent quorum decisions and member attestations builds legitimacy in the absence of legal charters.

VeroScores can be computed for organizations just as they can for individuals, providing **explainable, portable trust metrics**.

---

## **7.9 Collective Sub-Identities**

Large organizations can issue **sub-identities** for teams, departments, or projects. For example:

* A university issues sub-IDs for each department.
* A company issues sub-IDs for different product teams.
* A DAO issues sub-IDs for task forces.

These sub-identities inherit trust from the parent while maintaining **operational independence**. Each sub-ID can have its own keys, attestations, and governance rules, all traceable through the ledger.

This allows complex organizations to structure themselves **cryptographically**, rather than through ad hoc platform permissions or informal hierarchies.

---

## **7.10 DAOs and Ledger-Native Governance**

Decentralized Autonomous Organizations (DAOs) have struggled with governance, often relying on smart contracts or platform-based voting systems. By anchoring governance in **SelfID structures**:

* Membership is defined through trait attestations.
* Proposals are signed records.
* Votes are quorum signatures.
* Decisions are timestamped and auditable.

This approach removes reliance on brittle platform infrastructure and brings DAO governance **into the same temporal lattice** as identity and trust. It bridges social and technical legitimacy.

---

## **7.11 Informal Collectives and Movements**

Not every group wants to incorporate or formalize. Movements, artistic collectives, or ad hoc coalitions can still benefit from collective SelfIDs:

* A movement can anchor its manifesto and timeline.
* Collaborators can use quorum signatures to issue joint statements.
* Anonymous contributors can attest to participation through ephemeral sub-IDs.

These groups can exist **cryptographically**, without needing to file any paperwork or trust a platform’s longevity.

---

## **7.12 Hybrid Models: Legal and Ledger**

Many organizations will operate in **hybrid modes**, combining legal incorporation with ledger-based identity. For example:

* A nonprofit remains legally incorporated for tax and regulatory reasons but conducts governance through quorum-signed ledger records.
* A company uses legal incorporation for liability but uses ledger-based identity for transparent supply chain management.
* A university maintains legal charters but issues cryptographically verifiable departmental identities and credentials.

This hybrid approach leverages the strengths of both worlds: legal recognition where required, and **cryptographic sovereignty** everywhere else.

---

## **7.13 Summary**

Collective identities extend SelfID beyond individuals into the realm of organizations, DAOs, labs, co-ops, and movements. Through delegated keys, quorum signatures, evolving membership, and transparent attestations, collectives can establish **ledger-native existence** without waiting for state approval or platform permission.

Unlike traditional incorporation, which depends on bureaucratic grant of authority, ledger-based collective identity **earns trust through action, transparency, and verifiable governance**. It creates new possibilities for how groups organize, collaborate, and persist across time and space.
