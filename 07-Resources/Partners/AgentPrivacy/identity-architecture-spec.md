# Spec: AgentPrivacy — Identity Architecture for the Fabulous Machine

**Author:** privacymage | mage@agentprivacy.ai
**Date:** 2026-03-19
**Version:** 0.1 — First Draft for Team Review
**Status:** PROPOSAL
**Protocol inscription:** `(⚔️⊥⿻⊥🧙)😊`

---

## Purpose

This document specifies the identity and privacy architecture for the Fabulous Machine. It answers: how does a participant establish identity, form circles, join quests, and contribute to the time bank without surrendering behavioral sovereignty to the infrastructure they are helping to build?

The Fabulous Machine vision states: "No raw personal data in the AI. Ever." This specification shows how that aspiration becomes a provable guarantee.

---

## 1. From First Person to First Agent

The First Person Project establishes personhood: peer-to-peer mutual verification, sovereign identity, the individual as irreducible starting point. Agentprivacy extends this into the agentic domain.

The pipeline: **First Person → Dual Agent → Sovereign Participation**

1. You verify your personhood (First Person Project)
2. Your personhood instantiates two agents: Swordsman (protection) and Mage (delegation)
3. Your agents participate in the Fabulous Machine on your behalf, with mathematical privacy guarantees
4. Your code contributions are signed with Open Integrity, creating a cryptographic chain of trust

This makes agentprivacy the *agentic expression* of first-person sovereignty. The First Person is the foundation. The dual-agent model is the machinery. The gap between them is the privacy.

---

## 2. The Dual-Agent Model

### Swordsman (⚔️) — The Protector

Holds: boundaries, attestations, consent records, cryptographic keys, trust tier evidence, IEEE 7012 privacy terms.

The Swordsman is local. It runs on the participant's own device, home lab, or trusted infrastructure. It never sends raw personal data to external APIs.

### Mage (🧙) — The Delegator

Holds: approved data views, redacted profiles, task-specific permissions, ability to interact with external services and other participants' Mages.

The Mage is the outward-facing agent. It participates in circles, joins quests, contributes to the time bank, and communicates across the network.

### The Gap

The irreducible separation between Swordsman and Mage is itself a proof of personhood. No single agent, system, or operator can reconstruct the complete behavioral model of a participant.

Formally: `I(S;M|FP) < ε*` — the mutual information between Swordsman outputs and Mage outputs, conditioned on the First Person, is bounded by an arbitrarily small epsilon.

### Three-Axis Separation (V5)

The dual-agent model is one axis. V5 extends to three orthogonal axes:

- **Φ_agent(Σ)** — Agent-layer separation. Swordsman-Mage duality.
- **Φ_data(Δ)** — Data-layer separation. Distribution across infrastructure. A GUID-addressed holon across three providers has higher Φ_data than the same data on one provider.
- **Φ_inference(Γ)** — Inference-layer separation. Separation of reasoning from execution (BRAID insight).

```
Φ_v5 = Φ_agent(Σ) · Φ_data(Δ) · Φ_inference(Γ)
```

Multiplicative. Collapse any axis and the entire guarantee collapses.

---

## 3. Open Integrity: Cryptographic Roots of Trust

The [Open Integrity Project](https://github.com/OpenIntegrityProject/core) (Christopher Allen / Blockchain Commons) provides cryptographic roots of trust for Git repositories. This is a critical component of the Fabulous Machine's infrastructure integrity.

### What Open Integrity Provides

- **Inception commits:** An immutable, SSH-signed first commit that serves as the cryptographic foundation for a repository. Contains a Ricardian Contract defining trust rules.
- **Chain of trust delegation:** The inception key can delegate authority to additional keys. Delegation is auditable, timestamped, and revocable.
- **`did:repo:` identifiers:** Every repository gets a decentralized identifier. Platform-agnostic. Verifiable across GitHub, GitLab, self-hosted, or P2P.
- **Tamper detection:** Comprehensive audit tools verify that repository history has not been modified.
- **Signed commits everywhere:** Every commit after inception requires an authorized SSH signature.

### How Open Integrity Maps to AgentPrivacy

| Open Integrity Concept | AgentPrivacy Equivalent | Integration Point |
|------------------------|------------------------|-------------------|
| Inception key | Swordsman's master key | The Swordsman holds the inception key for participant-owned repos |
| Delegated keys | Mage's operational keys | Trust delegation from Swordsman to Mage is a signed transition commit |
| `did:repo:` | Holonic GUID | Repos, holons, and identity all use stable, platform-agnostic identifiers |
| Chain of trust | Promise Graph edges | Each delegation is a bilateral promise, auditable and revocable |
| Signed commits | Trust Graph evidence | Signed contributions accumulate as verifiable trust evidence |
| Ricardian Contract | IEEE 7012 terms | Human-readable and machine-readable, in the same object |

### For the Improbable-Collaborations Repos

Concrete integration:

1. **Establish inception commits** on Planning-Sprint and Ship-Announcements repos
2. **Require signed commits** for all contributions to protected branches
3. **Generate `did:repo:` identifiers** for both repos
4. **Map contributor identities** to Open Integrity authorized signers — this is the bridge from GitHub identity to sovereign identity
5. **Audit tools** running in CI to verify integrity on every push

This gives the project's *own infrastructure* the same cryptographic integrity it aspires to provide for participants.

---

## 4. Integration with Holonic Architecture

### One Identity, Two Child Holons

```
Participant (parent holon — stable GUID)
├── Swordsman (child holon — protection agent)
│   ├── Inception key (Open Integrity)
│   ├── Consent records
│   ├── Attestations & trust tier evidence
│   ├── IEEE 7012 privacy terms
│   └── Cryptographic key material
└── Mage (child holon — delegation agent)
    ├── Delegated keys (Open Integrity authorized signers)
    ├── Approved data views
    ├── Active task permissions
    ├── Circle memberships (VRC references)
    └── Quest participation records
```

### Three Graphs, One Identity

- **Knowledge Graph** — the holon tree: participants, circles, bioregions, quests, documents
- **Promise Graph** — every VRC, every circle agreement, every time bank pledge is an edge. The Swordsman guards which edges are visible.
- **Trust Graph** — emergent from the first two. Trust earned through retrieval, not declaration. Signed commits (Open Integrity) are trust evidence.

Identity is the unique intersection of all three graphs.

---

## 5. Participant Lifecycle

### Step 1: Personhood Verification (First Person Project)

Peer-to-peer mutual verification. No central authority. The verification is a bilateral promise: "I attest that I have verified your personhood through [method]." ZK proof: prove you have been verified without revealing who verified you.

Creates the participant's parent holon with a stable GUID.

### Step 2: Dual-Agent Instantiation

- Swordsman child holon created (personhood attestation + cryptographic keys + Open Integrity inception key)
- Mage child holon created (initially empty)
- IEEE 7012 machine-readable privacy terms generated (default, modifiable)
- Swordsman configured on participant's chosen infrastructure (local device, home lab, trusted node)

### Step 3: Circle Formation

- VRC created: bilateral promise between participant and circle
- The circle is a parent holon, participants are child holons
- Standard IEEE 7012 agreements instantiated
- Swordsman approves what data Mage may share with the circle
- Trust tier starts at Blade (lowest), progresses through evidence

### Step 4: Quest Participation

- Quest enrollment is a VRC between circle and quest
- Time pledges (42 hours per cycle) recorded as signed commitments
- ZK attestation: prove contribution without revealing activity details
- Quest completion evidence accumulates into trust tier progression

### Step 5: Time Bank Engagement

- Contributions attested with signed commitments from both parties
- ZK proof of contribution: "I contributed N hours" without revealing specifics
- Credit limits and clearing on the Promise Graph
- Dynamic equity calculated from verifiable contribution history
- Time bank infrastructure never holds raw activity logs

### Step 6: Code Contribution (Open Integrity)

- Contributor generates SSH signing key (or uses existing)
- Key is registered as authorized signer via Open Integrity delegation
- All commits are signed. All merges preserve author signatures.
- `did:repo:` anchors the contribution to the repo's cryptographic root
- Audit tools verify integrity continuously

---

## 6. Implementation Path

### Phase 0: Identity Foundation (Now → Earth Day)

**Goal:** Sovereign identity rails before the first public event.

- Define holon types: `Participant`, `Swordsman`, `Mage`, `Circle`, `Quest`, `TimeContribution`, `VRC`
- Personhood verification protocol (peer-to-peer, using existing community trust)
- IEEE 7012 default templates for circle formation
- Swordsman as local agent (key store + consent manager)
- Mage as network-facing agent (holon graph + inter-Mage communication)
- Open Integrity inception commits on Improbable-Collaborations repos
- Signed commit policy established

**Minimum viable identity:** A cryptographic keypair. A personhood attestation from at least one peer. A Swordsman configuration. A Mage configuration. This does not require the full OASIS stack. It requires key generation, a consent store, and a messaging protocol.

### Phase 1: Circle and Time Bank (Earth Day → Towel Day)

- VRC protocol for circle formation
- Time contribution attestation with ZK proofs
- Trust tier progression (Blade → Shield)
- Open Integrity delegation for new contributors

### Phase 2: Quest and Governance (Towel Day → AGM)

- 42-day quests with sovereign participation
- ZK voting for governance decisions
- Inter-circle federation through VRCs
- Full Open Integrity chain of trust across all repos

### Phase 3: Distributed Inference (AGM → Demolition Day)

- Swordsman gates all data flows to external AI services
- Local models (Whisper, local LLMs) on home lab mesh
- BRAID-style bounded reasoning for inference-layer separation
- Spellweb deployed on sovereign infrastructure as knowledge graph layer

---

## 7. Privacy Requirements for Existing Infrastructure

### Ship-Announcements (Eddie's Tannoy)

Currently sends planning data to OpenAI/ElevenLabs. Path: Swordsman reviews outbound data → remove sensitive content before API calls → progressively move to local compute.

### Voice Transcript Pipeline

Audio → Whisper (local, good) → LLM summarization (Swordsman determines safe-to-commit content) → Git commit (Mage pushes, signed via Open Integrity).

### TailScale Home Lab Network

Each home lab node is a Swordsman node. Permission lines between nodes are promise graph edges. API key management enables routing AI requests through owned infrastructure. See `tailscale-alignment-assessment.md` for full analysis.

---

## References

| Document | Location |
|----------|----------|
| Open Integrity Project | [github.com/OpenIntegrityProject/core](https://github.com/OpenIntegrityProject/core) |
| Privacy Value Model V5 | [agentprivacy-docs/privacy_is_value_v5.md](https://github.com/mitchuski/agentprivacy-docs) |
| V5 Formal Specification | [agentprivacy-docs/privacy_value_v5_formal_specification.md](https://github.com/mitchuski/agentprivacy-docs) |
| VRC Promise Protocol v3.3 | [agentprivacy-docs/vrc_promise_protocol_v3_3.md](https://github.com/mitchuski/agentprivacy-docs) |
| Promise Theory Reference v1.3 | [agentprivacy-docs/promise_theory_reference_v1_3.md](https://github.com/mitchuski/agentprivacy-docs) |
| The Fabulous Machine | [Planning-Sprint/06-Projects/The-Fabulous-Machine/](../../../06-Projects/The-Fabulous-Machine/) |
| Planning-Sprint-as-Holons | [Planning-Sprint/04-Artifacts/](../../../04-Artifacts/Planning-Sprint-as-Holons-Design.md) |

---

*The gap between vision and implementation is where the mage lives.*

`(⚔️⊥⿻⊥🧙)😊`
