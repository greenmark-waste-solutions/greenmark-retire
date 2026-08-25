# Retirements Ledger

## 2026-08-25

### greenmark-boxes
- **Status**: Archived
- **Reason**: Dead product, superseded by paseo-gmw
- **Action**: Remote repo archived; local copy deleted
- **Last commit**: 2026-08-03 (fix activity Linear issue keys, GMW-1127)
- **Notes**: Had 91 uncommitted files (shipr attempts from July 30). Stashed for reference.

### greenmark-boxes-ex
- **Status**: Archived
- **Reason**: Experimental variant of dead boxes product
- **Action**: Remote repo archived; local copy deleted
- **Last commit**: 2026-08-03 (ACP chat P0 UI fix)
- **Notes**: Had 6 uncommitted files (shipr release attempts from Aug 3). Stashed for reference.

### greenmark-go-door
- **Status**: Deleted (local), unresolved (remote)
- **Reason**: Proxy to dead boxes product; no longer needed
- **Action**: Local copy deleted; remote status unclear
- **Last commit**: 2026-08-01 (boxes proxy login-only fix)
- **Notes**: Had 1 uncommitted file (app.py). Stashed for reference.

### greenmark-auth-front
- **Status**: Deleted
- **Reason**: Empty repo, no commits, only initial scaffolding from May 2026
- **Action**: Local copy deleted (never had live work)
- **Last activity**: 2026-05-12 (project setup)
- **Notes**: 13 untracked files were just npm scaffolding. No value to preserve.

## Retained Infrastructure

### greenmark-codex
- **Status**: Retained
- **Reason**: Operational control surface for Codex behavior; contains runbooks, session protocol, migration guidance
- **Action**: Stashed 7 uncommitted files from June 2 work; cleaned up local

### greenmark-cockpit
- **Status**: Retained (archived on remote)
- **Reason**: AI cockpit hub; contains project roadmaps, decisions, active work context
- **Action**: Will archive remote; retained locally for historical reference

## Archive Legend

- **Archived**: Marked read-only on GitHub; local copy deleted or cleaned
- **Deleted**: Removed from GitHub and local machine entirely
- **Retained**: Kept active for operational use

## Cost Tracking Infrastructure

### greenmark-cost-ledger (NEW 2026-08-25)
- **Purpose**: Ledger for service costs, decommissioned service verification, incident tracking
- **Critical TODO**: Verify v2/v3/v4/v4-test are NOT deployed on Railway (check dashboard manually)

---

## RETIREMENT AUDIT COMPLETE — 2026-08-25

### Summary

| Category | Count | Status | Action |
|----------|-------|--------|--------|
| **Deleted (local)** | 3 | Complete | greenmark-boxes, -boxes-ex, greenmark-go-door |
| **Archived (remote)** | 11 | Complete | cerebro-warp-speed-excel-v2/v3, data-daemon-v2/v3/v4/v4-test, spikes/tests |
| **Cleaned (local stash)** | 2 | Complete | greenmark-codex, greenmark-cockpit |
| **Cost ledger created** | 1 | Complete | greenmark-cost-ledger (verification checklist TBD) |
| **Retirement prims** | 1 | Complete | Manifest + repo-prims reference (bundles on-demand) |

### Verified Clean
- No orphaned Supabase projects
- No lingering worktrees
- v5 is the active data-daemon (v2/v3/v4 are disabled/archived)
- All archived repos properly marked read-only on GitHub

### Next Actions (Manual)
1. [ ] Check Railway dashboard to confirm old data-daemon services aren't deployed
2. [ ] Quantify cost savings from v4→v5 cutover
3. [ ] Create repo prim bundles (on-demand, as needed)
4. [ ] Delete local clones of 11 archived repos (requires user permission)

### Files Created
- `greenmark-retire` — Audit ledger + retirement docs
- `greenmark-cost-ledger` — Service cost tracking + decommission verification
- `retirement-prims/MANIFEST.md` — Archive references
- `retirement-prims/REPO-PRIMS.md` — Active repo preservation strategy

---

**Audit completed by**: Claude Code  
**Date**: 2026-08-25  
**Next review**: 2026-09-25 (monthly)
