# PLANS.md

## Current objective
Lock governance and the regression baseline around the verified GlimR codebase before new feature work continues.

## Ground rules
- Baseline before behavior changes.
- Tests before risky changes.
- Additive slices before invasive slices.
- No hidden schema or naming changes.
- Single-file delivery remains mandatory.

## Phase 0 - Baseline locked
**Status:** Locked

### Completed deliverables
- Verified code-based baseline captured in `docs/governance/baseline-2026-03-23.md`
- Governed backlog established in `docs/backlog/governed-backlog.md`
- Architecture, storage paths, export paths, and PDF flow mapped against actual code
- High-risk areas and runtime-unverified areas explicitly documented

### Exit criteria
- Verified architecture snapshot exists
- Key data paths and stores are identified
- Existing versus missing functionality is classified

## Phase 1 - Governance and regression harness
**Status:** Active

### Scope
- Lock change policy, release gates, test matrix, data migration policy, and security/storage policy
- Use the governed backlog as the planning source of truth
- Extend the regression harness around the highest-risk existing paths before new feature behavior is changed

### Dependencies
- Phase 0 baseline stays authoritative until intentionally superseded
- No Class B or Class C implementation starts without explicit test requirements

### Exit criteria
- Governance documents are merged and internally consistent
- Regression targets for PMB, CPR, backup/restore, PDF, filtered export, and bound-file flows are defined
- The next low-risk slices are ready to implement without re-opening baseline questions

## Phase 2 - Low-risk additive changes
**Status:** Queued

### Candidate slices
- Orders shortcuts to patient and family
- Filtered counts on export buttons
- Admin panels as collapsible/default-minimized
- Tooltip and KPI polish where already partially present
- Targeted UI hiding such as PMB removal in the requested context
- Documentation-only annotation of `GlimR.html`

### Exit criteria
- Changes are additive
- Existing workflows remain available
- UI smoke checks are green

## Phase 3 - Medium-risk validation and PDF improvements
**Status:** Blocked by Phase 1

### Candidate slices
- Integer enforcement hardening for selected fields
- PDF spacing and report formatting hardening
- SVG logo fallback
- CSV-assisted PMB lookup
- Variant-library review interval behavior
- Any configurable uniqueness policy that does not escalate into migration

### Exit criteria
- Targeted validation and PDF tests are green
- No hidden data-shape change is introduced
- Rollback impact is documented

## Phase 4 - High-risk migration and integration tracks
**Status:** Blocked by ADR and migration planning

### Candidate tracks
- `MRN -> CPR` migration
- PMB normalization across all paths
- Unique-constraint redesign
- Storage-model changes including private-mode or memory-clearing proposals
- AI workflow hardening that affects persisted data or user trust boundaries
- Online SQL, FTP, or other network-backed persistence
- Larger i18n or theme architecture changes
- New analysis modules

### Exit criteria
- ADR approved
- Migration plan approved where required
- Compatibility and rollback are documented
- Release-gate evidence exists for the affected risk class

## Prioritization rules
- P0: data integrity, security, backup/restore, validation, critical reporting defects
- P1: low-risk additive UX and documentation improvements
- P2: medium-risk validation, PDF, and bounded workflow enhancements
- P3: high-risk integrations, migrations, and new modules

## Next milestone
Merge the governance lock package and begin Phase 1 regression-harness work, starting with explicit tests for PMB, CPR, backup/restore, PDF generation, and filtered export counts.

## Next recommended commit
`docs(governance): lock 2026-03-23 baseline and formalize change gates`
