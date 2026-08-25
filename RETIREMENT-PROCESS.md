# Retirement Process Primitive

Standardized workflow for retiring, archiving, and documenting dead repositories.

## When to Retire

A repo is ready for retirement when:
- **No commits in 2+ months** (except maintenance)
- **Superseded by another repo** (clear successor exists)
- **Test/spike completed** (temporary experiment, learning captured)
- **Research complete** (findings are in docs/infra, not active code)
- **Feature removed from product** (no longer in use)

## Retirement Workflow

### Phase 1: Audit & Verification

```bash
# 1. Verify local repo state
cd ~/repos-greenmark-waste-solutions/REPO
git log -1 --format="%ai %s"  # Last commit
git status --short             # Uncommitted work
git branch -a                  # Branches

# 2. Verify remote state
gh repo view greenmark-waste-solutions/REPO --json isArchived
gh api repos/greenmark-waste-solutions/REPO --jq '.pushed_at'

# 3. Check for dependencies
grep -r "REPO" ~/repos-greenmark/infra --include="*.md" --include="*.toml"
```

### Phase 2: Preservation (Before Deletion)

#### Option A: Already Archived on GitHub
- No action needed (already read-only)
- Document in RETIREMENTS.md

#### Option B: Still Active on GitHub

**If keeping code history:**
```bash
# Create git bundle (for future reference)
git bundle create ~/repos-greenmark-waste-solutions/greenmark-retire/retirement-prims/REPO.bundle --all

# Or: Clone into retirement-prims for offline access
git clone --bare https://github.com/greenmark-waste-solutions/REPO.git \
  retirement-prims/REPO.bundle
```

**Then archive on GitHub:**
```bash
gh repo archive greenmark-waste-solutions/REPO --yes
```

### Phase 3: Documentation

**Update RETIREMENTS.md:**

```markdown
### REPO_NAME
- **Status**: Archived / Deleted
- **Reason**: [Superseded by X] | [Research complete] | [Testing done]
- **Last commit**: YYYY-MM-DD
- **Action**: [Remote archived] | [Local deleted]
- **Recovery**: See retirement-prims/MANIFEST.md
```

**Add to retirement-prims/MANIFEST.md** if archiving on GitHub:

```markdown
| REPO | Date | Reason | Recovery |
|------|------|--------|----------|
| REPO_NAME | YYYY-MM-DD | [reason] | `git clone https://github.com/greenmark-waste-solutions/REPO.git` |
```

### Phase 4: Local Cleanup

```bash
# After archiving on GitHub (or if already archived):
rm -rf ~/repos-greenmark-waste-solutions/REPO
```

### Phase 5: Commit to greenmark-retire

```bash
cd ~/repos-greenmark-waste-solutions/greenmark-retire
git add RETIREMENTS.md retirement-prims/
git commit -m "retire: REPO_NAME — [brief reason]"
git push
```

---

## Batch Retirement Script

For retiring multiple repos at once:

```bash
#!/bin/bash
REPOS=(
  "repo-v2"
  "repo-test"
  "research-xyz"
)

for repo in "${REPOS[@]}"; do
  echo "=== $repo ==="
  
  # Archive on GitHub
  gh repo archive greenmark-waste-solutions/$repo --yes
  
  # Document
  echo "- $repo — archived" >> RETIREMENTS.md
  
  # Delete locally
  rm -rf ~/repos-greenmark-waste-solutions/$repo
  echo "✓ $repo"
done

git add . && git commit -m "retire: batch archive (${#REPOS[@]} repos)" && git push
```

---

## Checklist Template

Use for each retirement:

```
REPO: ___________________
Last commit: ____________
Reason: __________________

[ ] Audit local state
[ ] Audit remote state
[ ] Check for dependencies
[ ] Create bundle (if needed)
[ ] Archive on GitHub
[ ] Update RETIREMENTS.md
[ ] Update retirement-prims/MANIFEST.md
[ ] Delete local clone
[ ] Commit to greenmark-retire
[ ] Verify gone from local
```

---

## Cost Tracking (Post-Retirement)

After retiring a service:
1. Log in greenmark-cost-ledger/RETIREMENTS.md
2. Estimate monthly cost savings
3. Track in cost-ledger ledger

---

## Recovery (If Needed)

**From bundle:**
```bash
git clone --bare retirement-prims/REPO.bundle recovered-REPO
cd recovered-REPO && git log --oneline
```

**From GitHub archive:**
```bash
# Archived repos are still cloneable, just read-only
git clone https://github.com/greenmark-waste-solutions/REPO.git
```

**From disabled-gmw-539:**
Older v2/v3/v4 variants are preserved in the graveyard directory.

---

**Process version**: 1.0  
**Last updated**: 2026-08-25  
**Owner**: Daniel  
**Frequency**: As-needed (monthly review recommended)
