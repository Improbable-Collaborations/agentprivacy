# Roadmap

## Timeline Overview

| Phase | Timeframe | Key Milestones | Status |
|-------|-----------|----------------|--------|
| Phase 0: Identity Foundation | Now → Earth Day (22 Apr) | Dual-agent spec, Open Integrity inception commits, IEEE 7012 templates | In Progress |
| Phase 1: Circle and Time Bank | Earth Day → Towel Day (25 May) | VRC protocol for circles, ZK attestation for time contributions, trust tiers | Not Started |
| Phase 2: Quest and Governance | Towel Day → AGM (4 Jul) | 42-day quests on sovereign rails, ZK voting, inter-circle federation | Not Started |
| Phase 3: Distributed Inference | AGM → Demolition Day (5 Nov) | Local AI models on home lab mesh, BRAID-style bounded reasoning | Not Started |

## Phase Details

### Phase 0: Identity Foundation (Now → Earth Day)
- **Goal:** Every participant has sovereign identity rails before the first public event
- **Deliverables:**
  - Holon type definitions: `Participant`, `Swordsman`, `Mage`, `Circle`, `Quest`, `TimeContribution`, `VRC`
  - Personhood verification protocol (peer-to-peer, First Person Project)
  - IEEE 7012 default templates for circle formation agreements
  - Open Integrity inception commits on all project repos
  - Signed commit policy and contributor SSH key setup
  - Swordsman as local agent (key store + consent manager)
  - Mage as network-facing agent (holon graph + inter-Mage communication)
  - TailScale alignment assessment for home lab mesh ([done](../../07-Resources/Partners/AgentPrivacy/tailscale-alignment-assessment.md))
- **Dependencies:** GitHub access for privacymage, team review of identity architecture spec, Open Integrity tooling (Blockchain Commons scripts)

### Phase 1: Circle and Time Bank (Earth Day → Towel Day)
- **Goal:** Circles form with bilateral agreements. Time bank records first contributions.
- **Deliverables:**
  - VRC protocol implementation for circle formation
  - Time contribution attestation with ZK proofs
  - Trust tier progression from Blade to Shield
  - Integration with OASIS holon tree (or standalone graph)
  - Open Integrity delegation for new contributors
- **Dependencies:** Phase 0 complete, at least 3 circles formed, time bank ledger design

### Phase 2: Quest and Governance (Towel Day → AGM)
- **Goal:** 42-day quests run with sovereign participation. Governance decisions use privacy-preserving mechanisms.
- **Deliverables:**
  - Quest enrollment VRCs
  - ZK voting for governance decisions
  - Trust tier progression to higher levels
  - Inter-circle federation through VRCs between circle holons
  - Three Graphs mapping for holonic architecture (Knowledge × Promise × Trust)
  - Threat model for the Fabulous Machine
- **Dependencies:** Phase 1 complete, at least one 42-day quest cycle attempted, governance framework drafted

### Phase 3: Distributed Inference (AGM → Demolition Day)
- **Goal:** AI processing moves from centralized APIs to sovereign infrastructure.
- **Deliverables:**
  - Swordsman gates all data flows to external AI services
  - Local models (Whisper, local LLMs) on home lab mesh
  - BRAID-style bounded reasoning for inference-layer separation
  - Spellweb deployed on sovereign infrastructure as knowledge graph layer
  - Soulbae agent deployed for Hitchhiker community
- **Dependencies:** Home lab mesh operational, local model hosting capacity, Phase 2 identity infrastructure stable
