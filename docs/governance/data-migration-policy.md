# GlimR Data Migration Policy

## Status
- Policy status: active
- Scope: any change that can alter stored data, schema compatibility, export/import formats, or domain-field semantics

## Relationship to other governance documents
This policy works together with:
- `docs/governance/baseline-2026-03-23.md`
- `docs/governance/change-policy.md`
- `docs/governance/release-gates.md`
- `docs/governance/test-matrix.md`

## Baseline assumptions
- Current IndexedDB baseline is `DB_VER = 15`.
- Current storage includes named stores and indexes defined in `GlimR.html`.
- Current domain field usage still relies on `mrn` and `pmb_number` in multiple modules, exports, and workflows.
- Current import/export paths include JSON, CSV, ZIP, SQL, FHIR, and bound-file JSON.

## Migration triggers
The following always count as migration-sensitive work:
- `MRN -> CPR`
- PMB format or semantics changes
- Unique constraint changes
- New stores or indexes
- Store renames
- Export or import payload changes
- Reset or restore semantic changes
- Changes to bound-file compatibility

## Hard rules
- No migration-sensitive change may be implemented as a hidden refactor.
- No migration-sensitive change may ship without a documented compatibility strategy.
- No migration-sensitive change may ship without backup and rollback instructions.
- Any change that can invalidate old data or exports is Class C.

## Required migration package
Before implementation begins for a migration-sensitive change, all of the following are required:
- Approved ADR
- Approved migration plan
- Impact inventory across UI, storage, export/import, PDF, FHIR, audit, and tests
- Compatibility strategy
- Rollback strategy
- Targeted test requirements
- Release note draft for operator-facing impact

## MRN to CPR policy
`MRN -> CPR` is not a text substitution. It is a controlled migration program.

It affects:
- field naming in forms and filters
- validation behavior
- autofill behavior
- stored data payloads
- export/import files
- report templates and PDF content
- FHIR mapping
- search and filtering
- documentation and training material

Minimum requirements before implementation:
- ADR approved
- migration plan approved
- field inventory completed
- compatibility plan defined, including dual-read and dual-write where needed
- representative migration dataset prepared
- restore and rollback procedure documented
- test cases defined before code changes start

## PMB format policy
Changing PMB rules is migration-sensitive because PMB is already used in validation, uniqueness checks, and persisted records.

Minimum requirements:
- confirm current PMB entry paths and export paths
- define exact accepted formats and normalization rules
- verify compatibility with existing records
- verify duplicate behavior after normalization
- add roundtrip tests before rollout

## Unique constraints policy
Adding or changing uniqueness requirements is migration-sensitive when:
- a unique index already exists
- duplicates may already exist in stored data
- import or restore paths can receive older data

Required steps:
- inventory current indexes and runtime duplicate checks
- define duplicate handling strategy
- test old-data import and restore behavior
- provide rollback path if deployment causes false-positive conflicts

## New stores and indexes policy
New stores or indexes require:
- ADR if they affect compatibility or operational behavior
- explicit `DB_VER` strategy
- upgrade-path test coverage
- restore compatibility review
- export/import impact review

## Export and import format policy
Changing JSON, CSV, ZIP, SQL, or FHIR payloads requires:
- format inventory
- backward compatibility statement
- import behavior for older files
- export behavior for existing consumers
- representative roundtrip tests

## Backward compatibility rule
Preferred order of operations:
1. Add compatibility readers.
2. Add dual-write or compatibility export behavior if needed.
3. Migrate existing data in a controlled way.
4. Remove legacy behavior only after a separately approved cleanup step.

## Rollback rule
Every migration-sensitive release must have:
- previous release artifact retained
- backup guidance retained
- known-good restore path
- explicit note on whether rollback is data-compatible or requires restore-from-backup

## Interpretation rule
If a change touches naming, schema, or compatibility and there is doubt about whether it is a migration, treat it as one.
