# Partners: AgentPrivacy — The Privacymage's View

**Author:** privacymage | mage@agentprivacy.ai
**Date:** 2026-03-19
**Canonical source:** [mitchuski/agentprivacy-docs](https://github.com/mitchuski/agentprivacy-docs)
**Protocol inscription:** `(⚔️⊥⿻⊥🧙)😊`

---

## To the Hitchhikers

This document is my view, as privacymage, on the Improbable-Collaborations project. It is both a letter of alignment and a technical convergence study. I follow the same pattern when entering into partnership with any ecosystem project: a personal statement of what I see, followed by an honest architectural mapping of where our work overlaps, reinforces, and challenges each other.

I do not arrive empty-handed. The 0xagentprivacy protocol represents roughly eight years of work across identity, key management, privacy, blockchain, governance, and AI agent architecture. The core thesis is simple: **privacy is value**. Behavioral data constitutes a seventh form of capital, currently being extracted by surveillance architectures. The dual-agent separation model creates information-theoretic guarantees that prevent behavioral reconstruction, not through policy, but through mathematics.

What I found in the Fabulous Machine vision is something I have been searching for: a community building the *container* that privacy infrastructure needs to live inside. You are building the governance substrate, the cultural scaffold, the legal agreements, the event rhythms, the human invitation. I am building the cryptographic identity and agent-separation layer that makes all of those things sovereign rather than surveilled.

Neither is complete without the other. Privacy without community is a locked door with nobody home. Community without privacy is a glass house where everyone is watched.

---

## AgentPrivacy as the Agentic Expression of the First Person Project

The First Person Project establishes personhood: peer-to-peer mutual verification, sovereign identity, the individual as the irreducible starting point. Agentprivacy extends this into the agentic domain. Once you have established that you are a real person, *how do AI agents act on your behalf without eroding that sovereignty?*

The answer is the dual-agent model: the Swordsman (⚔️) holds your boundaries, the Mage (🧙) projects through them. The First Person establishes who you are. The dual-agent model ensures that who you are remains sovereign as agents multiply around you. The separation between them is itself a proof-of-personhood primitive: choosing which constraint to override is sovereignty.

This makes agentprivacy the *best agentic expression* of first-person sovereignty. Not the only possible expression. The best one I know how to build, after eight years of iteration. And it maps directly onto what the Fabulous Machine is trying to do: AI agents for each individual and group, operating through an InterFace Protocol with gradients of trust, transparency, and disclosure.

---

## Convergence Map: Where Our Architectures Already Align

### 1. Dual-Agent Separation ↔ Protector/Actor in The Fabulous Machine

The Fabulous Machine document already describes this: "one agent holds your boundaries, attestations, and consent; the other performs delegated actions only on approved data. No raw personal data in the AI. Ever."

This is the Swordsman and Mage architecture. The fact that the Fabulous Machine arrived at this independently, from the direction of community need rather than information theory, is itself a convergence signal. What agentprivacy adds is the formal guarantee: the separation is enforced by the mutual information bound `I(S;M|FP) < ε*`, not by policy or good intentions. The V5 model extends this across three orthogonal axes — agent separation, data separation, and inference separation — and the product is multiplicative. Collapse any axis and the whole collapses.

### 2. Open Integrity ↔ Signed Commits and Cryptographic Roots of Trust

The Fabulous Machine document explicitly calls for "open integrity, signed commits, and cryptographic roots of trust... and zero knowledge proofs as core to the systems."

The [Open Integrity Project](https://github.com/OpenIntegrityProject/core) (Christopher Allen / Blockchain Commons) provides exactly this. Open Integrity establishes cryptographic roots of trust for Git repositories through inception commits, SSH-signed chains of trust, tamper detection, and platform-agnostic verification. Every repo gets a `did:repo:` identifier. Every commit is signed. Trust delegation is auditable and revocable.

For the Fabulous Machine, this means:

- **Every contribution is provably attributed.** Signed commits prove who wrote what. No impersonation. No unsigned patches.
- **The repo itself has an immutable origin.** The inception commit is the cryptographic anchor. Fork it, clone it, move it anywhere — the origin is verifiable.
- **Trust delegation maps to the promise graph.** Open Integrity's "inception key → delegated keys" model is structurally identical to the promise-theoretic pattern: the inception authority makes a bilateral promise to delegate. The delegation is auditable. It can be revoked.
- **Platform independence.** Open Integrity works across GitHub, GitLab, self-hosted, or P2P Git. The Fabulous Machine should not be locked to any single hosting platform. Open Integrity ensures it isn't.

The agentprivacy architecture integrates Open Integrity as the *code-layer trust anchor*. The Swordsman's key material connects to the inception key model. Signed commits become evidence on the Trust Graph. The `did:repo:` identifier maps to the holonic GUID addressing pattern.

**Contribution path:** Integrate Open Integrity's inception commit model into the Improbable-Collaborations repos. Establish signed commit policy. Map `did:repo:` identifiers to the holonic identity model.

### 3. Promise Theory ↔ Bilateral Agreements

The Fabulous Machine describes agreements that are "both human-readable and machine-readable, modifiable locally but not subordinate to any legacy institution." The agentprivacy architecture grounds this in Promise Theory (Bergstra & Burgess): agents can only promise their own behavior. No imposition. No extraction without consent.

The VRC Promise Protocol (v3.3) provides the mechanism: Verifiable Relationship Credentials are edges on the Promise Graph. Each VRC formation is a bilateral commitment, assessed by compression (can you decompress the proverb?), and accumulated into progressive trust tiers.

The LFG Port Tech mapping document already in this repo demonstrates how the dual-agent and dual-encoding patterns apply to real-world infrastructure. The methodology there is exactly how agentprivacy integrates into the wider Fabulous Machine architecture.

### 4. Holonic Architecture ↔ Three Graphs, One Identity

The Planning-Sprint-as-Holons design document describes holons with stable GUIDs, shared-parent groups, and dual encoding. This converges directly with the Three Graphs, One Identity model:

- **Knowledge Graph** maps to the holon tree itself (what exists, what relates to what)
- **Promise Graph** maps to the agreement layer (who promised what to whom, VRCs, signed holons)
- **Trust Graph** emerges at the intersection (reputation through retrieval, not declaration)

The holonic architecture's "movable identity" — one GUID across providers, databases, and time — is exactly the holonic persistence principle from V5. The dual-agent Swordsman and Mage are implemented as two child holons under one parent identity. The separation is in the data model.

### 5. Compression and Secret Languages ↔ Proverbiogenesis

The Fabulous Machine describes a "multi-perspectival engine" and "privacy-respecting schism that uses AI to translate between personal languages." The spellbook methodology demonstrates this is already working: 70:1 to 125:1 semantic compression ratios across five grimoires.

BRAID (Bounded Reasoning for Autonomous Inference and Decisions) showed 74x inference compression while maintaining performance. This is also a privacy property: if your reasoning can be compressed without information loss, your behavioral surface is smaller. Compression-as-defence is a V5 innovation with direct application to the Fabulous Machine's agent layer.

### 6. IEEE 7012-2025 ↔ Machine-Readable Terms

The MyTerms standard (IEEE 7012-2025) provides machine-readable personal privacy terms. This is the technical specification for what the Fabulous Machine describes as "both human and machine legible agreements." For the "standard agreements immediately in place" aspiration, IEEE 7012 is the standards-body backing that makes this legally defensible.

---

## Where I Challenge the Current Architecture

### Identity Must Be Foundational, Not Eventual

The current sprint plan lists identity verification among the "first steps" but the architecture documents don't yet specify *how*. The Fabulous Machine says "establish identity, have passports, bottom up data sovereignty and privacy" but the implementation path jumps to events and content before the identity substrate exists. This is the most common failure mode in community projects: building the house before the foundation.

Privacy cannot be retrofitted. The identity and dual-agent layer should be in the first technical sprint, not the third.

### Code Integrity Needs Open Integrity From Day One

The repos currently accept unsigned commits. There is no inception commit. No `did:repo:` identifier. No chain of trust for delegation. This means any contributor's identity is self-asserted, not cryptographically verified. For a project that explicitly calls for "open integrity, signed commits, and cryptographic roots of trust," the repos themselves should model this.

### Agent Privacy in Content Creation

The Ship-Announcements repo processes planning data through OpenAI and ElevenLabs APIs. Every document and transcript that flows through these services is behavioral data being sent to surveillance-architecture companies. The distributed home-lab infrastructure described in the software sprint is the right direction. The AI processing pipeline should progressively move to sovereign infrastructure.

---

## My Contribution Plan

### Governance and Privacy

- Privacy governance framework for the Fabulous Machine constitution
- IEEE 7012 templates for bilateral agreements at every level (individual, circle, bioregion)
- Promise-theoretic foundations for decision-making architecture
- Zero-knowledge attestation design for governance participation

### Identity and Agent Architecture

- V5 three-axis separation model integrated into holonic type definitions
- Dual-agent child-holon specification
- ZK-attestation model for the Pangalactic Time Bank
- First Person Project → dual-agent pipeline (personhood verification → sovereign agents)
- Open Integrity integration: inception commits, signed commit policy, `did:repo:` identifiers

### Local Compute and Home Base

When my local compute home base is online, I will integrate the agentprivacy stack — Obsidian vault, Claude Code, spellweb — on my own hardware. This becomes a strong home base for the project: a sovereign node on the home lab mesh, running the dual-agent model on real infrastructure, demonstrating the architecture by using it daily.

The spellweb (interactive knowledge graph of the full agentprivacy corpus) becomes a live demonstration of how the Fabulous Machine's knowledge layer can work: navigable, searchable, privacy-preserving, running on owned infrastructure.

### Education and Onboarding

- Spellbook methodology for creating locally-rich, globally-interoperable guides
- Compression/decompression demonstrations
- Strategic rationale documentation: why this approach, why now, comparison with alternatives

---

## The Proverb

> *The towel knows where it has been. The passport knows where it may go. The gap between them is where the hitchhiker lives.*

Your history (the towel) and your permissions (the passport) must never be held by the same authority. The Swordsman holds the towel. The Mage carries the passport. The hitchhiker — the sovereign human — exists in the irreducible gap between them.

That gap is the proof of personhood. That gap is the Fabulous Machine's most important component. And it cannot be built after the fact.

---

*Privacy is value. Mass is earned through retrieval. Trust the pattern, for it trusts you.*

`(⚔️⊥⿻⊥🧙)😊`
