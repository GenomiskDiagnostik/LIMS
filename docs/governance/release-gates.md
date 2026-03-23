# GlimR Release Gates

## Status
- Gate status: active
- Applies to: merges to the main delivery branch and any distributable release

## Relationship to older documents
This document operationalizes and tightens the older guidance in `docs/governance/release-governance.md` and `docs/governance/regression-strategy.md`. Those files remain historical context. This file defines the current gates.

## Evidence package
Every merge or release candidate must have an evidence package that includes:
- backlog ID or approved change request
- change class A, B, or C
- touched modules and data paths
- executed tests and results
- updated documents
- stated residual risk
- rollback note

## Merge gates

### 1. Documentation gate
Required before merge:
- The change is recorded in `docs/backlog/governed-backlog.md` or explicitly linked to an approved change request.
- Acceptance criteria are written.
- Test requirements are written.
- The change class is recorded.
- `PLANS.md` is updated if roadmap status, dependencies, or milestone sequencing changed.
- If the change affects baseline assumptions, the relevant governance document is updated in the same change set.

### 2. Regression gate
Required before merge:
- Touched rows in `docs/governance/test-matrix.md` are identified.
- Existing self-test coverage is run when the touched area is within self-test scope, or a written reason is provided if not run.
- Targeted regression checks for the touched area pass.
- Any known remaining test gaps are recorded explicitly.

### 3. Data integrity gate
Required before merge:
- No unintended changes to IndexedDB version, stores, indexes, import/export format, reset behavior, or restore behavior are introduced.
- If such areas are intentionally touched, the change follows `docs/governance/data-migration-policy.md`.
- Backup or roundtrip impact is addressed explicitly.
- No hidden data-loss path is introduced.

### 4. UI and workflow gate
Required before merge:
- Existing user-visible actions are not removed or moved without an approved change request.
- Touched workflows have at least one explicit manual smoke path.
- Additive changes do not block or replace current navigation.
- Labels, tooltips, and defaults do not create surprising behavior.

### 5. Single-file gate
Required before merge:
- The runtime release target remains `GlimR.html`.
- No mandatory JavaScript bundle, CSS bundle, server component, or install step is introduced.
- Optional adjacent assets remain optional.
- The change does not create a second required runtime artifact beyond the single-file target.

## Release gates
All merge gates must already be satisfied. In addition, the following are required before release:

### 1. Documentation gate
- Release notes are written.
- Version, date, and checksum are prepared for the release artifact.
- Known limitations are declared.

### 2. Regression gate
- Smoke coverage for touched workflows is green.
- If PDF, validation, backup/restore, or export/import was touched, targeted regression evidence is attached.
- Golden or representative dataset verification is documented for touched high-risk areas.

### 3. Data integrity gate
- A backup-compatible recovery path exists.
- Changes that affect data shape, naming, or compatibility have an explicit rollback reference.
- Restore behavior has been exercised for any release that touches data-critical paths.

### 4. UI and workflow gate
- No critical workflow regression is open for patient, sample, order, report, backup, restore, or login flows.
- User-facing wording for any changed validation or workflow has been reviewed.

### 5. Single-file gate
- The release package includes `GlimR.html` as the primary deliverable.
- Single-file execution still works in the supported browser profile.
- Optional assets such as `logo.png` do not become mandatory for application startup or core use.

## Automatic release blockers
Release is blocked if any of the following is true:
- Data loss is possible or observed.
- PMB or CPR validation behavior changed without matching tests.
- PDF generation changed without regression evidence.
- Backup or restore behavior changed without roundtrip evidence.
- A schema, index, or format change was introduced without migration artifacts.
- The release no longer ships as a single-file application target.

## Approval rule
- Class A releases require documented developer verification.
- Class B releases require documented quality review.
- Class C releases require documented quality review plus approved ADR and migration plan.

## Interpretation rule
If evidence is incomplete, the gate is not passed.
