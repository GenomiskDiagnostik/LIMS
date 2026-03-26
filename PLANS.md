# PLANS.md

## Current objective
Carry the current validation and form slice through merge and release review without reopening migration, storage, or naming questions.

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

### Progress
- Governance package is locked on `fa6c55f`.
- The first technical regression-harness round now covers PMB validation, CPR validation, JSON roundtrip via `exportData()`/`replaceAllData()`, PDF blob generation, patient and order filtered-export row counts, UI logo-fallback state, and PDF SVG fallback behind `logo.png`.
- Bound-file/autosave flows, CSV/ZIP restore assertions, broader filtered-export coverage, and visual PDF verification remain open.

### Exit criteria
- Governance documents are merged and internally consistent
- Regression targets for PMB, CPR, backup/restore, PDF, filtered export, and bound-file flows are defined
- The next low-risk slices are ready to implement without re-opening baseline questions

## Phase 2 - Low-risk additive changes
**Status:** Active

### Progress
- Filtered export buttons now show the current filtered count across patients, samples, panels, orders, variants, reports, audit, and variant-library export entry points without changing export payloads.
- Orders now expose additive patient and family shortcuts alongside the existing sample and report shortcuts.
- Administration panels are now collapsible and default-minimized using the existing `tool-panel` pattern.
- Logo hover credits, an inline SVG fallback for missing `logo.png` in both UI and PDF export, and a safe subset of clickable KPI cards are in place without adding new filters or changing underlying data semantics.
- The embedded SVG fallback now hardens its filter extents to avoid cropped rendering in UI and PDF fallback serialization.
- Users can now store an optional per-user `organization_label` that drives presentation-only branding in the header, browser title, KPI print view, planner mail text, pedigree print, and the report PDF subtitle while technical names remain unchanged.
- The variant AI action now renders as an icon-only button with tooltip and `aria-label`, while the selected provider remains visible in the adjacent select and the underlying AI flow is unchanged.
- Admin datavalidering now stores configurable display labels for `pmb`, `mrn`, and `extraId`, with `Prøvenummer`, `MRN`, and `Ekstra ID` as presentation defaults.
- Orders now restrict new sample selection to non-control samples, show sample type in the dropdown, and keep historical control-linked orders editable as legacy references without mutating stored data.

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
- CSV-assisted PMB lookup
- Variant-library review interval behavior
- Any configurable uniqueness policy that does not escalate into migration

### Progress
- PMB validation is now hardened against decimal-like input while remaining string-based and preserving leading zeroes.
- `copy_number` and `size_bp` were intentionally not tightened in runtime behavior in this slice, because the current baseline still treats them as free-text/domain-text fields.
- Uniqueness policy remains analysis-only: PMB uniqueness is already hard-enforced in both UI save logic and the IndexedDB unique index on `samples.pmb_number`.

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
Complete manual validation and orders-form smoke plus merge/release evidence for the PMB/display-label/order-selector slice, then return to the remaining Phase 1 gaps around bound-file/autosave, CSV/ZIP restore assertions, and broader runtime verification.

## Next recommended commit
`fix(validation): harden integer fields and refine configurable id labels`
