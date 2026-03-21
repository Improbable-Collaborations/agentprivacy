# Brief: AgentPrivacy — TailScale Alignment Assessment

**Author:** privacymage | mage@agentprivacy.ai
**Date:** 2026-03-19
**Context:** Evaluate TailScale for alignment with swordsman technology. Input for the software sprint.

---

## Summary

TailScale is strongly aligned with the Swordsman layer of the dual-agent architecture. It provides encrypted overlay networking with per-device cryptographic identity, which maps directly to the "guarded key node" concept. The alignment is natural. TailScale solves the network-layer problem that the Swordsman needs solved.

Where TailScale falls short is at the agent and inference layers. It provides the plumbing, not the privacy logic. The Swordsman needs to be built *on top* of TailScale, not replaced by it.

---

## Where TailScale Aligns

### Cryptographic Identity per Node

Every device in a TailScale network has a cryptographic identity derived from its key material. Functionally equivalent to the Swordsman's key-holding role: the node *is* its keys. This also connects to Open Integrity: the same SSH key material used for TailScale identity can anchor signed commits, creating a unified cryptographic identity across network access and code contribution.

### Permission Lines = Promise Graph Edges

TailScale ACLs define which nodes talk to which, on which ports, for which services. These are bilateral permission declarations. This is a promise graph: each ACL rule is an edge. Explicit, auditable, revocable.

### Encrypted by Default

All traffic is WireGuard-encrypted. No cleartext. Not optional. Baseline Φ_data for all data flowing between home labs.

### No Central Data Path

Actual data traffic flows directly between nodes (peer-to-peer). The coordination server handles key exchange and NAT traversal but never sees content. The data path respects Φ_data.

### API Key Management (Alpha)

Pooling AI token budgets, routing AI API requests through owned infrastructure, full logging of what was sent and received. This is Swordsman technology for the inference layer: the home lab mesh routes requests through a TailScale-mediated gateway that logs, redacts, and controls.

---

## Where TailScale Falls Short

### No Agent-Layer Separation

TailScale provides network security, not application-layer separation. A single app on a TailScale node can still be both protector and delegator.

**Bridge:** Build dual-agent logic as application-layer services running *on* TailScale nodes. Swordsman service manages keys and consent. Mage service handles outward interaction. TailScale provides the encrypted transport.

### No Consent Management

ACLs control *network* access, not *data* access. Network permission doesn't equal data consent.

**Bridge:** IEEE 7012 consent management layered above TailScale ACLs. Network access is necessary but not sufficient.

### No ZK Proof Infrastructure

TailScale verifies identity through keys. It cannot generate zero-knowledge proofs.

**Bridge:** ZK proof generation as a service on the home lab mesh. TailScale transports. The ZK service proves.

### No Trust Tier Progression

Nodes are in the tailnet or not. No progressive trust model.

**Bridge:** Trust tier model (Blade → Dragon) as application-layer service adjusting ACL rules and data access based on accumulated evidence.

### Coordination Server Metadata

The TailScale control plane sees the network graph: which nodes exist, which talk to which, when. This metadata is behavioral data. Headscale (open source, self-hosted) is the alternative.

**Recommendation:** Start with TailScale (free, fast). Evaluate Headscale for medium-term migration. TailScale metadata is manageable risk for early development. For production, self-hosted coordination is preferable.

---

## Recommended Architecture

```
┌──────────────────────────────────────────────────┐
│              Home Lab Node                         │
│                                                    │
│  ┌─────────────┐        ┌─────────────┐          │
│  │  Swordsman   │◄──────►│    Mage     │          │
│  │  Service     │ consent │  Service    │          │
│  │              │ checks  │             │          │
│  │ • Key store  │        │ • Circle    │          │
│  │ • Consent    │        │   tasks     │          │
│  │ • IEEE 7012  │        │ • Time bank │          │
│  │ • ZK proofs  │        │ • Quest     │          │
│  │ • Audit log  │        │   work      │          │
│  │ • Open       │        │ • Signed    │          │
│  │   Integrity  │        │   commits   │          │
│  │   keys       │        │   (via Mage)│          │
│  └──────┬───────┘        └──────┬──────┘          │
│         └────────┬───────────────┘                 │
│         ┌────────▼────────┐                        │
│         │   TailScale      │                        │
│         │   (WireGuard)    │                        │
│         └────────┬─────────┘                        │
└──────────────────┼──────────────────────────────────┘
                   │
        ┌──────────▼──────────┐
        │  Encrypted P2P Mesh  │
        │  (home lab ↔ home lab)│
        └──────────┬──────────┘
                   │
        ┌──────────▼──────────┐
        │  API Gateway         │
        │  • Redaction          │
        │  • Logging            │
        │  • Budget mgmt        │
        └──────────┬──────────┘
                   │ (approved data only)
        ┌──────────▼──────────┐
        │  External APIs       │
        │  (progressively       │
        │   replaced by local)  │
        └─────────────────────┘
```

---

## For the Software Sprint

1. **Set up TailScale on participating home labs.** Free tier. Verify P2P connectivity.
2. **Deploy Whisper locally.** Remove first external API dependency for the voice pipeline.
3. **Establish the API gateway pattern.** Route external API calls through TailScale-mediated gateway. Log everything. Enable future redaction.
4. **Document the data flow.** For each pipeline stage, map which data touches which node and which data exits the mesh.
5. **Evaluate Headscale.** Test self-hosted coordination server on one lab.
6. **Set up Open Integrity.** Generate SSH signing keys on each lab. Establish inception commits. Require signed commits.

---

*Each home lab is a swordsman. The mesh is the promise graph made physical. The gap between labs is where privacy lives.*

`(⚔️⊥⿻⊥🧙)😊`
