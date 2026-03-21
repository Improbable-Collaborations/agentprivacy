# Privacymage Sync Brief — March 22

## State of Play

30+ new commits since March 19. Zero conflicts with our files. The team is expecting your commits — Max's summary doc says "Mitchell is making commits to the Improbable repo this week." BRAID doc for Tim references them.

New in repo since we prepared: Mitch-Max transcript, BRAID identity layer doc for Tim, 10 protocol templates (MOU, Onboarding, Time-Banking etc.), new contributors (Magpie, Ahmed/Jade), .claude directory, Website, Facilitation folder.

## Package Contents

**For the repo commit** (paths match repo root):
```
07-Resources/Partners/AgentPrivacy/AgentPrivacy.md              ← partner index
07-Resources/Partners/AgentPrivacy/privacymage-convergence-letter.md  ← your public statement
07-Resources/Partners/AgentPrivacy/identity-architecture-spec.md      ← foundational spec
07-Resources/Partners/AgentPrivacy/getting-started-for-hitchhikers.md ← team guide
07-Resources/Partners/AgentPrivacy/strategic-rationale.md             ← why/why now/comparison
07-Resources/Partners/AgentPrivacy/tailscale-alignment-assessment.md  ← sprint input
07-Resources/Partners/AgentPrivacy/open-integrity-setup-guide.md      ← Open Integrity setup
README.md                                                        ← AgentPrivacy in Partners
04-Artifacts/Goals-and-Objectives/Goals.md                       ← identity goals populated
04-Artifacts/Roadmap/Roadmap.md                                  ← four phases populated
04-Artifacts/Risk-Register/Risks.md                              ← seven risks
04-Artifacts/Decision-Log/Decisions.md                           ← three decisions
04-Artifacts/Working-Documents/Documentation-Sprint-Areas.md     ← name fix
03-Meetings/.../Sprint-Plan.md                                   ← privacy track added
PUSH_INSTRUCTIONS.md                                             ← git commands
```

**Your working docs** (not for the repo):
```
_privacymage-working/agentprivacy-strategic-review-improbable.md  ← personal review + priorities
_privacymage-working/team-note-19-march.md                        ← note to share with team
_privacymage-working/PUSH_INSTRUCTIONS.md                         ← duplicate for easy access
_privacymage-working/SYNC_BRIEF.md                                ← this file
```

## Coding Agent Prompts

### Prompt 1: Partner folder
```
Create the directory 07-Resources/Partners/AgentPrivacy/ and add these 7 markdown files from the package I've provided. Then stage and commit:

git add 07-Resources/Partners/AgentPrivacy/
git commit -m "Add AgentPrivacy partner folder — privacy-first identity architecture

Establishes 0xagentprivacy as the identity and privacy layer for the
Fabulous Machine, and the agentic expression of the First Person Project.

Ref: https://github.com/mitchuski/agentprivacy-docs
Ref: https://github.com/OpenIntegrityProject/core

Signed-off-by: privacymage <mage@agentprivacy.ai>"
```

### Prompt 2: README
```
In README.md, add this line after the Constitutional-Drafting entry in the Partners section:

- [[AgentPrivacy]] — 0xagentprivacy — privacy-first AI agent architecture, identity layer, Open Integrity

git add README.md
git commit -m "Add AgentPrivacy to partners list in README

Signed-off-by: privacymage <mage@agentprivacy.ai>"
```

### Prompt 3: Artifacts
```
Replace these four files with the versions from the package:
- 04-Artifacts/Goals-and-Objectives/Goals.md
- 04-Artifacts/Roadmap/Roadmap.md
- 04-Artifacts/Risk-Register/Risks.md
- 04-Artifacts/Decision-Log/Decisions.md

git add 04-Artifacts/Goals-and-Objectives/Goals.md 04-Artifacts/Roadmap/Roadmap.md 04-Artifacts/Risk-Register/Risks.md 04-Artifacts/Decision-Log/Decisions.md
git commit -m "Populate identity and privacy goals, roadmap, risks, and decisions

Signed-off-by: privacymage <mage@agentprivacy.ai>"
```

### Prompt 4: Sprint plan
```
Replace 03-Meetings/Working-Sessions/2026-03-23_Software-Sprint/Sprint-Plan.md with the version from the package.

git add 03-Meetings/Working-Sessions/2026-03-23_Software-Sprint/Sprint-Plan.md
git commit -m "Add privacy and identity track to March 23 software sprint

Signed-off-by: privacymage <mage@agentprivacy.ai>"
```

### Prompt 5: Name fix
```
In 04-Artifacts/Working-Documents/Documentation-Sprint-Areas.md, replace "Mitchell Travers (privacy)" with "privacymage (privacy/identity)" on line 20.

git add 04-Artifacts/Working-Documents/Documentation-Sprint-Areas.md
git commit -m "Update contributor name to pseudonym in documentation sprint areas

Signed-off-by: privacymage <mage@agentprivacy.ai>"
```

### Prompt 6: Push
```
git push origin main
```

## After Push

1. Share team-note-19-march.md in the group chat
2. Open Integrity inception commit (follow open-integrity-setup-guide.md)
3. Review new Protocols folder for IEEE 7012 integration points
4. Check Pan-Galactic Monitor on Telegram (Max asked for trust graph thoughts)
5. March 26: compression/decompression demo
