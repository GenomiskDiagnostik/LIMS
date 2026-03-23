# GlimR Change Policy

## Status
- Policy status: active
- Governs: all code, documentation, schema, workflow, and release-affecting changes after the 2026-03-23 baseline lock

## Relationship to older documents
This document operationalizes and supersedes the older classification model in `docs/governance/change-control.md` for day-to-day delivery decisions. The older document remains historical context.

## Core rules
- Zero regression has priority over feature velocity.
- Single-file output remains mandatory.
- Additive changes are preferred over invasive changes.
- No large rewrites.
- No hidden schema changes.
- No feature implementation without accepted test requirements.
- Changes to persistence, PDF, export/import, key fields, or validation rules require tests to be defined before implementation.
- Class C changes require ADR and migration planning before implementation begins.

## Change classes

| Class | Risk level | Typical scope | Examples |
| --- | --- | --- | --- |
| A | Low | Additive UI or UX, docs, navigation, non-breaking quality-of-life changes | Extra shortcuts, visible counts, copy changes, collapsible admin panels |
| B | Medium | Validation behavior, PDF behavior, domain rules, controlled reporting changes | PMB validation hardening, PDF spacing, logo fallback, domain-specific field rules |
| C | High | Schema, storage, import/export formats, naming migrations, integrations, security model changes | `MRN -> CPR`, new stores or indexes, unique constraints, online SQL, FTP, AI write paths |

## Mandatory classification rules
- Every change must be assigned one class: A, B, or C.
- Mixed-scope changes inherit the highest applicable class.
- If a change affects data persistence, import/export, reset/restore, PDF generation, or core validation, it is never Class A.
- If a change affects schema, naming, compatibility, or external integrations, it is Class C.

## Required artifacts by class

| Artifact | Class A | Class B | Class C |
| --- | --- | --- | --- |
| Backlog entry in governed backlog | Required | Required | Required |
| Acceptance criteria | Required | Required | Required |
| Explicit test requirements | Required for touched UX or workflow | Required before implementation | Required before implementation |
| Rollback note | Required | Required | Required |
| PLANS.md update if roadmap impact exists | Required | Required | Required |
| ADR | Not required | Only if architecture impact exists | Required |
| Migration plan | Not required | Required if compatibility changes | Required |
| Release-gate evidence | Required | Required | Required |

## Test-first triggers
The following changes must have accepted test requirements before code is written:

- Persistence changes
- Reset or restore changes
- Bound-file or autosave changes
- Import/export changes
- PDF/report generation changes
- Validation changes for PMB, CPR, or equivalent key domain fields
- Audit logging behavior changes

## Prohibited implementation patterns
- Hidden schema or index changes
- Search-and-replace renames of key fields without cross-module analysis
- Replacing existing workflows without an approved change request
- Making network access a hard dependency for core operation
- Direct AI write-back into clinical fields without explicit user review
- Large rewrites bundled together with behavior changes

## Minimum delivery sequence
1. Link the work to a backlog ID or approved change request.
2. Assign Class A, B, or C.
3. Define acceptance criteria.
4. Define required tests.
5. If Class C, produce ADR and migration plan before implementation.
6. Update `PLANS.md` if milestone or dependency changes.
7. Implement in a small, reviewable slice.
8. Verify release-gate evidence before merge and before release.

## Interpretation rule
When there is doubt, classify upward. A wrongly conservative Class B or C decision is acceptable. A wrongly optimistic Class A decision is not.
