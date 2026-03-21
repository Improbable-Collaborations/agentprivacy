# PUSH INSTRUCTIONS

Drop the contents of this package into your local Planning-Sprint repo clone. The file paths match the repo structure exactly.

## Files in this package

**New files (add):**
```
07-Resources/Partners/AgentPrivacy/AgentPrivacy.md
07-Resources/Partners/AgentPrivacy/privacymage-convergence-letter.md
07-Resources/Partners/AgentPrivacy/identity-architecture-spec.md
07-Resources/Partners/AgentPrivacy/getting-started-for-hitchhikers.md
07-Resources/Partners/AgentPrivacy/strategic-rationale.md
07-Resources/Partners/AgentPrivacy/tailscale-alignment-assessment.md
07-Resources/Partners/AgentPrivacy/open-integrity-setup-guide.md
```

**Modified files (overwrite):**
```
README.md                                                    ← AgentPrivacy added to Partners list
04-Artifacts/Goals-and-Objectives/Goals.md                   ← Sovereign Identity Foundation goal
04-Artifacts/Roadmap/Roadmap.md                              ← Four phases populated
04-Artifacts/Risk-Register/Risks.md                          ← Seven risks with mitigations
04-Artifacts/Decision-Log/Decisions.md                       ← Three decisions logged (refs Mitch-Max call + BRAID doc)
04-Artifacts/Working-Documents/Documentation-Sprint-Areas.md ← Name updated to privacymage
03-Meetings/Working-Sessions/.../Sprint-Plan.md              ← Privacy track + Open Integrity tasks
```

## Git commands

```bash
cd /path/to/Planning-Sprint
git pull origin main

# Copy package contents over repo (overwriting modified files)
cp -r /path/to/this-package/* .

# Stage and commit
git add 07-Resources/Partners/AgentPrivacy/
git commit -m "Add AgentPrivacy partner folder — privacy-first identity architecture

Establishes 0xagentprivacy as the identity and privacy layer for the
Fabulous Machine, and the agentic expression of the First Person Project.

Ref: https://github.com/mitchuski/agentprivacy-docs
Ref: https://github.com/OpenIntegrityProject/core

Signed-off-by: privacymage <mage@agentprivacy.ai>"

git add README.md
git commit -m "Add AgentPrivacy to partners list in README

Signed-off-by: privacymage <mage@agentprivacy.ai>"

git add 04-Artifacts/Goals-and-Objectives/Goals.md \
       04-Artifacts/Roadmap/Roadmap.md \
       04-Artifacts/Risk-Register/Risks.md \
       04-Artifacts/Decision-Log/Decisions.md
git commit -m "Populate identity and privacy goals, roadmap, risks, and decisions

Signed-off-by: privacymage <mage@agentprivacy.ai>"

git add 03-Meetings/Working-Sessions/2026-03-23_Software-Sprint/Sprint-Plan.md
git commit -m "Add privacy and identity track to March 23 software sprint

Signed-off-by: privacymage <mage@agentprivacy.ai>"

git add 04-Artifacts/Working-Documents/Documentation-Sprint-Areas.md
git commit -m "Update contributor name to pseudonym in documentation sprint areas

Signed-off-by: privacymage <mage@agentprivacy.ai>"

git push origin main
```

## Verified

- Zero conflicts with commits through 78a4b01 (March 20)
- All relative links resolve against current repo structure
- No full name in any file (grep -r "Mitchell Travers" returns nothing)
- Decisions.md references both the March 17 and March 19 transcripts already in repo
- New Protocols folder, BRAID doc for Tim, and .claude directory are untouched
