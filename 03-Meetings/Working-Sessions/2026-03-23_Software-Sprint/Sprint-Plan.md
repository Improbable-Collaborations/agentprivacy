# Software Sprint — Week of 2026-03-23

**Theme:** Agentic-First Community-Driven Development
**Duration:** Monday 23 – Friday 27 March 2026
**Proposed by:** David Bovill

---

## Goals

1. Connect 3–4 home labs into a working peer-to-peer network
2. Build the voice/media processing pipeline as the first distributed workflow
3. Establish a shared development environment and workflow coding approach
4. Port existing software to the Spectra development workflow
5. Establish privacy and integrity foundations for the distributed infrastructure

## Daily Structure

### Monday — Setup and Kickoff
- Confirm participants and home lab availability
- Inventory: what each person is running (hardware, OS, connectivity)
- Agree on shared tooling (git workflow, communication channel, deployment approach)
- David presents the Spectra / agentic workflow methodology
- Set up SSH signing keys for Open Integrity (all participants)

### Tuesday — HomeLab Networking
- Establish connectivity between home labs (VPN, P2P, or overlay network)
- Set up shared storage (NextCloud sync, IPFS, or similar)
- Test: can each lab see and process files placed by another?
- Document the data flow: which data touches which node, which exits the mesh

### Wednesday — Pipeline Building
- Build the voice transcript pipeline as the first distributed workflow:
  - Audio in → Whisper transcription (local) → LLM summarisation → Git commit (signed)
- Assign pipeline stages to different home labs
- Test end-to-end with real voice messages
- Identify which pipeline stages should run behind the Swordsman (local) vs through the Mage (external)

### Thursday — Media Processing and Expansion
- Extend to video: Fathom recordings, presentation editing
- Agentic coding of transformations (FFmpeg, audio/visual processing)
- Visual interface / documentation of workflows
- Establish API gateway pattern for external API calls (logging, future redaction)

### Friday — Integration and Retrospective
- End-to-end demo of the full pipeline
- Document what works, what doesn't
- Privacy review: what data left the mesh? Was it necessary?
- Retrospective: what to continue, what to change
- Plan for ongoing operation beyond the sprint

## Participants

| Name | Role / Focus | Home Lab? |
|------|-------------|-----------|
| David Bovill | Sprint lead, Spectra workflow, software-defined networks | Yes |
| | | |
| | | |
| | | |

**Invited / to confirm:**
- Nameless One — agentic text workflows
- OASIS team — software collaboration
- Pete Kaminsky — HomeLab infrastructure
- Mitch (privacymage) — privacy architecture, TailScale alignment, Open Integrity, dual-agent model (remote, TBC)

## Prerequisites

- [ ] Each participant has a working home lab or VPS
- [ ] Git access to the Planning-Sprint repo
- [ ] NextCloud or shared folder access
- [ ] Whisper (local install or API access)
- [ ] SSH signing key generated (for Open Integrity signed commits)

## Success Criteria

- [ ] At least 3 home labs connected and passing files between them
- [ ] Voice transcript pipeline running end-to-end across labs (not dependent on one machine)
- [ ] Documented workflow that others can replicate
- [ ] Clear next steps for scaling to more groups
- [ ] All sprint commits signed via Open Integrity
- [ ] Data flow documented: what data stays local, what exits the mesh

## Privacy and Identity Track

*Contributed by privacymage. See [TailScale alignment assessment](../../07-Resources/Partners/AgentPrivacy/tailscale-alignment-assessment.md) for detailed analysis.*

### Sprint Tasks

- [ ] TailScale setup on participating home labs — verify P2P encrypted connectivity
- [ ] Deploy Whisper locally on at least one lab — remove first external API dependency
- [ ] Establish API gateway pattern — route external API calls through TailScale-mediated gateway with logging
- [ ] Document data flow for each pipeline stage — map which data touches which node, which exits the mesh
- [ ] Evaluate Headscale (self-hosted coordination) on one lab if capacity allows
- [ ] Open Integrity: generate SSH signing keys on each lab, establish inception commits, require signed commits

### Privacy Principles for the Sprint

1. **Whisper local by default.** Transcription on the home lab, not via external API.
2. **Log before you send.** Every API call to an external service should be logged locally before sending, enabling future audit and redaction.
3. **Sign everything.** All commits signed. Open Integrity chain of trust from day one.
4. **Document the data flow.** For each pipeline stage: what data, which node, does it leave the mesh?
5. **Progressive, not absolute.** External APIs are acceptable for now. The goal is to *know* what's leaving and *plan* the migration to local, not to block all external calls immediately.

## Outputs

All sprint outputs should be committed to:
- `06-Resources/Projects/` — for any new project documentation
- `scripts/` — for pipeline and automation scripts
- `03-Meetings/Working-Sessions/2026-03-23_Software-Sprint/` — session notes and retrospective
- `07-Resources/Partners/AgentPrivacy/` — for privacy architecture documentation
