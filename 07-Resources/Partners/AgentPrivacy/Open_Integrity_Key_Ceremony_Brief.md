# Open Integrity Key Ceremony Brief

> **Author:** privacymage  
> **Date:** 2025-03-22  
> **Context:** Improbable-Collaborations / agentprivacy  
> **Framework:** [OpenIntegrityProject/core](https://github.com/OpenIntegrityProject/core) (Blockchain Commons)  
> **Status:** Pre-ceremony planning

---

## Purpose

This brief outlines the process for conducting a key ceremony following the Open Integrity framework to establish a cryptographic root of trust for the `agentprivacy` repository. Open Integrity, an initiative of Blockchain Commons (led by Christopher Allen), integrates cryptographic trust mechanisms into Git repositories using SSH-based signing. No modifications to Git are required.

The ceremony produces an **Inception Commit**: a signed, empty commit that serves as the immutable cryptographic anchor for all future commits, trust delegation, and key governance in the repository.

## Why This Matters

Git's default configuration has no cryptographic enforcement of commit authenticity, history integrity, or repository provenance. Anyone can commit under a false identity, unsigned commits can be merged into signed repositories, and commit history can be rewritten without detection. For a project concerned with privacy-first AI agent architecture, this is an unacceptable foundation. The key ceremony fixes this at the root.

## Pre-Ceremony Requirements

**Environment:**
- Git 2.34+ (SSH signing support)
- ZSH or Bash shell
- `ssh-keygen` (standard OpenSSH)

**Git Global Config (verify before ceremony):**
```bash
git config --global gpg.format ssh
git config --global user.signingkey /path/to/your/ed25519_key
git config --global commit.gpgsign true
git config --global user.name "your-name"
git config --global user.email "your-email@domain"
```

**Key Generation (if needed):**
```bash
ssh-keygen -t ed25519 -C "your-email@domain" -f ~/.ssh/agentprivacy_inception_key
```

Use Ed25519. This provides approximately 128-bit security. The inception key should be purpose-specific, not reused from everyday SSH authentication.

## Ceremony Steps

### Step 1: Generate the Inception Key

Create a dedicated Ed25519 SSH keypair for this repository. This key is the root of all trust that follows. Store it securely. Consider hardware-backed storage (YubiKey/FIDO) or an air-gapped machine for high-assurance contexts.

```bash
ssh-keygen -t ed25519 -C "mage@agentprivacy.ai" -f ~/.ssh/agentprivacy_inception
```

Record the public key fingerprint:
```bash
ssh-keygen -E sha256 -lf ~/.ssh/agentprivacy_inception.pub
```

### Step 2: Create the Inception Commit

The inception commit is an empty commit, signed with the inception key, containing a Ricardian Contract in the commit message. The empty commit is deliberate: it reduces the SHA-1 collision attack surface while the SSH signature provides 128-bit cryptographic security on top.

Using the Open Integrity script:
```bash
./src/create_inception_commit.sh -r agentprivacy
```

Or manually (ZSH):
```zsh
# Initialize the repo
mkdir agentprivacy && cd agentprivacy && git init

# Set variables
SIGNING_KEY="$HOME/.ssh/agentprivacy_inception"
AUTHOR_NAME="privacymage"
AUTHOR_EMAIL="mage@agentprivacy.ai"
TIMESTAMP="$(date -u +"%Y-%m-%dT%H:%M:%SZ")"
FINGERPRINT="$(ssh-keygen -E sha256 -lf "$SIGNING_KEY" | awk '{print $2}')"

# Create the signed inception commit
GIT_AUTHOR_NAME="$AUTHOR_NAME" \
GIT_AUTHOR_EMAIL="$AUTHOR_EMAIL" \
GIT_COMMITTER_NAME="$FINGERPRINT" \
GIT_COMMITTER_EMAIL="$AUTHOR_EMAIL" \
GIT_AUTHOR_DATE="$TIMESTAMP" \
GIT_COMMITTER_DATE="$TIMESTAMP" \
git -c gpg.format=ssh -c user.signingkey="$SIGNING_KEY" \
  commit --allow-empty --no-edit --gpg-sign \
  -m "Initialize repository and establish a SHA-1 root of trust" \
  -m "This key certifies future commits' integrity and origin. Other keys can be authorized via .repo/config/verification/allowed_commit_signers. This file must initially be signed by this inception key." \
  --signoff
```

**Key design choices:**
- The committer name is set to the SSH key fingerprint, cryptographically binding identity to the key itself.
- Author and committer dates are synchronized to a deterministic UTC timestamp.
- The commit message body is a Ricardian Contract defining the trust rules for the repository.

### Step 3: Verify the Inception Commit

Run the Open Integrity audit script to confirm the commit meets specification:

```bash
./src/audit_inception_commit-POC.sh -C /path/to/agentprivacy
```

Check manually:
```bash
git log --show-signature
git verify-commit HEAD
```

Expected: the commit is empty, signed, signature is valid against the inception key, and the Ricardian Contract is present in the message body.

Retrieve the repository DID:
```bash
./src/get_repo_did.sh -C /path/to/agentprivacy
```

### Step 4: Trust Transition (Delegate Authority)

Once the inception commit is locked, create a trust transition commit to delegate authority from the inception key to operational signing keys. This is another signed, empty commit.

```bash
# Point the repo to an allowed signers file
git config --local gpg.ssh.allowedSignersFile .repo/config/verification/allowed_commit_signers

# Create the allowed signers file
mkdir -p .repo/config/verification
cat > .repo/config/verification/allowed_commit_signers << EOF
# Authorized commit signers for agentprivacy
# Inception key is NOT included (retired after this transition)
mage@agentprivacy.ai ssh-ed25519 AAAA... (Device 1 - primary)
collaborator@example.com ssh-ed25519 AAAA... (Collaborator Device)
EOF

# Commit the transition, signed by the inception key
git add .repo/
git commit -S -m "Trust transition: establish allowed commit signers" \
  -m "Inception key retired from future signing authority. Delegated keys now govern this repository."
```

After this commit, the inception key is explicitly retired from ongoing signing. Only keys listed in `allowed_commit_signers` can authorize future commits.

### Step 5: Install Verification Hooks

Set up a pre-receive hook to enforce authorized signers on all incoming commits:

```bash
cat > .git/hooks/pre-receive << 'EOF'
#!/bin/sh
while read oldrev newrev refname; do
  verify_authorized_signer $newrev
done
EOF
chmod +x .git/hooks/pre-receive
```

### Step 6: Key Lifecycle Management

As the repository evolves, manage key rotation and revocation through signed commits that modify the `allowed_commit_signers` file. Each modification must be signed by a currently authorized key.

**Revocation** is timestamped using Git notes:
```bash
git notes --ref=key-history add -m "Revoked: $(date -u +"%Y-%m-%dT%H:%M:%SZ") KEY_FINGERPRINT"
```

Attempts to use a revoked key will be reported and blocked from merging into protected branches.

### Step 7: Push to Remote and Audit

```bash
git remote add origin git@github.com:Improbable-Collaborations/agentprivacy.git
git push -u origin main
```

Upload the signing public key to GitHub as a **signing key** (not just authentication). Periodically run audits to verify the full trust chain from inception to HEAD.

## Trust Model Summary

```
Inception Commit (root of trust)
  │
  ├── Signed empty commit with Ricardian Contract
  ├── Committer = SSH key fingerprint
  └── SSH signature (~128-bit security)
        │
        ▼
Trust Transition Commit
  │
  ├── allowed_commit_signers file created
  ├── Inception key retired
  └── Delegated keys take authority
        │
        ▼
Ongoing Governance
  │
  ├── All commits to protected branches require authorized signatures
  ├── Key rotation via signed commits modifying allowed_commit_signers
  ├── Revocation timestamped via git notes
  └── Unauthorized signatures blocked and reported
```

## Convergence Notes

The Open Integrity framework maps naturally onto the 0xagentprivacy dual-agent separation model:

- The **inception key** functions as the Swordsman's root: a sovereignty anchor that establishes the boundary.
- The **trust delegation** mechanism is the Mage's projection: controlled extension of authority through the `allowed_commit_signers` chain.
- The **gap** between inception key retirement and delegated key authority is itself a trust boundary. The inception key chose its own obsolescence. That choice is sovereignty.
- The `did:repo` identifier aligns with the Three Graphs model, particularly the Trust Graph layer, where repository identity persists independently of hosting platform.

The Ricardian Contract in the inception commit is a promise in the Promise Theory sense: a bilateral declaration of the repository's trust rules, made by the key to the network. Agents can only promise their own behavior.

## References

- [OpenIntegrityProject/core](https://github.com/OpenIntegrityProject/core)
- [Open Integrity Problem Statement](https://hackmd.io/@bc-bizdev/r1BGEnqFkx)
- [Musings of a Trust Architect (Christopher Allen)](https://www.lifewithalacrity.com/article/open-integrity/)
- [Blockchain Commons Gordian Principles](https://developer.blockchaincommons.com/principles/)

---

*The fragment holds the whole. By choosing to be bounded, we become immeasurable.*
