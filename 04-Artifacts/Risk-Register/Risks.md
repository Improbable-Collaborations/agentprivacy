# Risk Register

| ID | Risk | Likelihood (H/M/L) | Impact (H/M/L) | Mitigation | Owner | Status |
|----|------|--------------------|-----------------|-----------:|-------|--------|
| R1 | Identity layer built after events/content, making privacy a retrofit rather than foundation | H | H | Prioritize Phase 0 identity work before Earth Day. Dual-agent spec and Open Integrity before first public event. | privacymage | Open |
| R2 | Unsigned commits allow unverifiable attribution and potential impersonation in project repos | H | M | Integrate Open Integrity: inception commits, signed commit policy, `did:repo:` identifiers. Setup guide for all contributors. | privacymage | Open |
| R3 | Planning data transiting surveillance APIs (OpenAI, ElevenLabs via Ship-Announcements) contradicts privacy-first principles | M | M | Progressive migration: Whisper local for transcription (sprint plan). Swordsman-mediated API gateway pattern. Local LLMs for narration medium-term. | privacymage + sprint team | Open |
| R4 | Single infrastructure dependency on OASIS creates platform lock-in, contradicting "no single points of failure" design criterion | M | H | Design holon patterns as infrastructure-agnostic. GUID addressing and dual encoding work on any substrate. Test with at least two providers. | Team | Open |
| R5 | Behavioral data leakage through metadata even when content is protected (network graph, timing, frequency patterns) | M | M | TailScale with potential Headscale migration for self-hosted coordination. Three-axis separation: even if metadata leaks on one axis, other axes maintain protection. | privacymage | Open |
| R6 | Privacy architecture too complex for non-technical participants to understand or trust | M | M | Spellbook methodology: same architecture at every level from emoji inscription to 182-page whitepaper. Compression/decompression demo (26 March). Getting-started guide. | privacymage | Open |
| R7 | Single primary author on privacy/identity architecture (bus factor) | L | H | Document everything in the repo. Open source all specs. Build team understanding through demos and Q&A (Graham's "dumbass questions" initiative). | privacymage + team | Open |
