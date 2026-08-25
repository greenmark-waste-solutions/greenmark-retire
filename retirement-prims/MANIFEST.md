# Retirement Prims Manifest

This directory preserves references to retired repositories. Each repo listed below is:
- **Archived** on GitHub (read-only, not deleted)
- **Optionally bundled** here as a git bundle for offline reference
- **Documented** with reason for retirement and recovery instructions

## Archived Repos (11)

### Excel Variants
| Repo | Archived | Reason | Recovery |
|------|----------|--------|----------|
| cerebro-warp-speed-excel-v2 | 2026-05-09 | Superseded by v3→v4 migration | `git clone https://github.com/greenmark-waste-solutions/cerebro-warp-speed-excel-v2.git` |
| cerebro-warp-speed-excel-v3 | 2026-05-09 | Frozen variant; v4 active | `git clone ...` |

### Data-Daemon Versions
| Repo | Archived | Reason | Recovery |
|------|----------|--------|----------|
| data-daemon-v2 | 2026-04-27 | Hand-rolled predecessor | See disabled-gmw-539 |
| data-daemon-v3 | 2026-04-28 | dbt+Dagster spike | See disabled-gmw-539 |
| data-daemon-v4 | 2026-04-29 | Replaced by v5 (production Dagster) | See disabled-gmw-539 |
| data-daemon-v4-test | 2026-05-02 | Smoke test variant | See disabled-gmw-539 |

### Tests & Spikes
| Repo | Archived | Reason | Recovery |
|------|----------|--------|----------|
| cerebro-mcp-spike | 2026-04-14 | Auth-less test; throwaway | GitHub archive |
| data-daemon-testing | 2026-03-17 | Old integration test sandbox | GitHub archive |

### Research
| Repo | Archived | Reason | Recovery |
|------|----------|--------|----------|
| research-secrets-manager | 2026-03-18 | Research complete; decisions in infra | GitHub archive |
| research-cost-accounting | 2026-03-17 | Research complete; not active | GitHub archive |
| navusoft-api-testing | 2026-05-19 | Old API testing toolkit | GitHub archive |

---

## Prim Bundles

Bundles (if captured) are in this directory:
```bash
ls -lh *.bundle
git clone --bare <repo>.bundle <repo>
```

## Disabled Directory

Old v2/v3/v4 are also preserved in:
```
~/repos-greenmark-waste-solutions.disabled-gmw-539/
```

This is the "graveyard" for repos that were never fully active.

---

**Last updated**: 2026-08-25
**Audit**: Daniel
