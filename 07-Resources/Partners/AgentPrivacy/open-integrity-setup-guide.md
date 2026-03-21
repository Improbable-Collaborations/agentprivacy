# Guide: AgentPrivacy — Open Integrity Setup for Improbable-Collaborations

**Author:** privacymage | mage@agentprivacy.ai
**Date:** 2026-03-19
**Reference:** [OpenIntegrityProject/core](https://github.com/OpenIntegrityProject/core)
**Status:** GUIDE — to be executed during or before the March 23 software sprint

---

## What Is Open Integrity?

Open Integrity (Christopher Allen / Blockchain Commons) provides cryptographic roots of trust for Git repositories. It ensures that every commit is signed, every contributor is verifiable, and the repository history is tamper-resistant.

The Fabulous Machine document explicitly calls for "open integrity, signed commits, and cryptographic roots of trust." This guide implements that call.

---

## Why It Matters for This Project

Right now, the Improbable-Collaborations repos accept unsigned commits. Anyone with push access can commit under any name. There is no cryptographic proof of who wrote what, no tamper detection, and no chain of trust for delegating commit authority.

For a project that aspires to build sovereign identity infrastructure for the planet, the project's *own repos* should model the integrity it advocates.

Open Integrity provides:
- **Inception commits** — an immutable, SSH-signed first commit as the cryptographic anchor
- **`did:repo:` identifiers** — decentralized, platform-agnostic repository identity
- **Signed commits** — every commit cryptographically attributed
- **Chain of trust delegation** — new contributors authorized through auditable, revocable delegation
- **Tamper detection** — audit tools to verify repository integrity

---

## Step 1: Generate Your SSH Signing Key

If you don't already have an SSH key for signing:

```bash
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519_signing -C "your-email@example.com"
```

Configure Git to use it:

```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519_signing
git config --global commit.gpgsign true
git config --global tag.gpgsign true
```

Verify:

```bash
git config --global --get gpg.format        # should say: ssh
git config --global --get user.signingkey    # should show your key path
git config --global --get commit.gpgsign     # should say: true
```

Upload your public key to GitHub: Settings → SSH and GPG keys → New SSH key → Key type: "Signing Key" → paste contents of `~/.ssh/id_ed25519_signing.pub`.

---

## Step 2: Install Open Integrity Tools

```bash
git clone https://github.com/OpenIntegrityProject/core.git open-integrity-core
```

The key scripts:
- `src/setup_git_inception_repo.sh` — create a new repo with inception commit
- `src/audit_inception_commit-POC.sh` — audit a repo's inception commit
- `src/get_repo_did.sh` — retrieve a repo's `did:repo:` identifier

Note: Open Integrity is currently proof-of-concept (v0.1.0). The scripts work but are not yet production-polished. For our purposes, the manual process below is sufficient.

---

## Step 3: Establish Inception Commits (for existing repos)

For existing repos like Planning-Sprint and Ship-Announcements, we cannot retroactively create an inception commit at the root. Instead, we establish a **trust transition point**: a signed commit that declares "from this point forward, all commits to protected branches must be signed."

### Create the Trust Transition

In each repo, create the trust configuration:

```bash
mkdir -p .repo/config/verification

# Create the allowed commit signers file with the inception key
echo "# Open Integrity — Allowed Commit Signers
# Established: $(date -u +%Y-%m-%dT%H:%M:%SZ)
# See: https://github.com/OpenIntegrityProject/core
#
# Format: <email> <key-type> <public-key>
$(git config user.email) $(cat ~/.ssh/id_ed25519_signing.pub)" > .repo/config/verification/allowed_commit_signers
```

Commit (signed):

```bash
git add .repo/
git commit -S -m "Establish Open Integrity trust transition

This commit establishes a cryptographic trust anchor for this repository.
From this point forward, all commits to protected branches should be
signed by an authorized signer listed in allowed_commit_signers.

Reference: https://github.com/OpenIntegrityProject/core
Contributor: privacymage <mage@agentprivacy.ai>" --signoff
```

### Get the Repository DID

After establishing the trust transition:

```bash
# The DID is derived from the repo's inception/transition commit hash
COMMIT_HASH=$(git log --reverse --format="%H" | head -1)
echo "did:repo:${COMMIT_HASH}"
```

Record this in the repo's README or a metadata file.

---

## Step 4: Configure Branch Protection

On GitHub, for each repo:

1. Settings → Branches → Branch protection rules
2. Add rule for `main`
3. Enable: "Require signed commits"
4. Enable: "Require linear history" (prevents unsigned merge commits)

This enforces that all commits to `main` must be signed.

---

## Step 5: Add New Contributors

When a new contributor needs commit access:

1. They generate their SSH signing key (Step 1)
2. They share their public key
3. An existing authorized signer adds their key to `.repo/config/verification/allowed_commit_signers`
4. The addition is committed and signed by the existing signer
5. This creates an auditable chain of trust delegation

```bash
# Add a new signer (done by existing authorized signer)
echo "new-contributor@example.com $(cat their_public_key.pub)" >> .repo/config/verification/allowed_commit_signers
git add .repo/config/verification/allowed_commit_signers
git commit -S -m "Delegate commit authority to new-contributor

Authorized by: $(git config user.email)
New signer: new-contributor@example.com" --signoff
```

---

## Step 6: Audit

Verify that a repo's commits are properly signed:

```bash
# Check all commits on main
git log --show-signature main

# Or use Open Integrity's audit script
./open-integrity-core/src/audit_inception_commit-POC.sh -C /path/to/repo
```

---

## For the Software Sprint (March 23)

Minimum tasks:

- [ ] All sprint participants generate SSH signing keys
- [ ] Upload public keys to GitHub as signing keys
- [ ] Configure `git config --global commit.gpgsign true`
- [ ] Create trust transition commits on Planning-Sprint and Ship-Announcements
- [ ] Enable "Require signed commits" branch protection on `main`
- [ ] Document `did:repo:` identifiers for both repos
- [ ] Test: verify that unsigned commits are rejected on protected branches

---

## Connection to the Dual-Agent Model

Open Integrity's trust model maps directly onto the Swordsman/Mage architecture:

- The **inception key / authorized signers** are Swordsman infrastructure: they guard the boundary of who can make authoritative changes
- The **signed commits** are Mage actions: outward-facing contributions that are cryptographically tied to the Swordsman's authorization
- The **chain of trust delegation** is a Promise Graph edge: bilateral, auditable, revocable
- The **`did:repo:` identifier** is the holon GUID for the repository: stable, platform-agnostic, verifiable

This means the project's own development workflow becomes a live demonstration of the privacy and integrity architecture it is building for participants.

---

*Signed commits prove provenance. The chain of trust is the promise graph made visible. The inception key is the swordsman's first act.*

`(⚔️⊥⿻⊥🧙)😊`
