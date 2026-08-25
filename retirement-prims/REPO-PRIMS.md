# Repo Prims

Reference bundles of **working, active repos** preserved for:
- Quick offline access (bundle cloning)
- Future research ("how did we solve this?")
- Disaster recovery snapshot

## Key Repos to Preserve

### Data Infrastructure
- `data-daemon-v5` — Production Dagster pipeline (ACTIVE)
- `data-daemon` — YAML-driven vendor connectors (ACTIVE)
- `cerebro-warehouse-postgres` — Bronze/silver/gold warehouse schema (ACTIVE)

### Dashboard & Metrics
- `cerebro` — Executive dashboard + Sage data (ACTIVE)
- `cerebro-registry-workbench` — Metrics reconciliation (ACTIVE)
- `cerebro-odwf-v1` — Metrics proof pack (ACTIVE)

### Infrastructure & Ops
- `infra` — Vendor API research, integration specs (ACTIVE)
- `greenmark-codex` — Codex operational control surface (ACTIVE)
- `cerebro-clis` — Cross-cutting CLIs for Cerebro (ACTIVE)

## Bundle Strategy

For each repo, create a prim:
```bash
# Clone into retirement-prims/
git clone --bare https://github.com/greenmark-waste-solutions/REPO.git REPO.bundle

# Recover if needed:
git clone --bare REPO.bundle recovered-REPO
```

**Status**: Pending (bundle creation on-demand)

---

**Purpose**: If GitHub ever goes down or a repo is accidentally deleted, we have local snapshots.
