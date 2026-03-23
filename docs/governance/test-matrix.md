# GlimR Test Matrix

## Status
- Matrix status: active
- Purpose: define the minimum test expectations that must be referenced before changes are implemented or released

## How to use this matrix
- Identify the touched rows before implementation.
- Treat rows marked "Yes" under release blocker as mandatory for release when the area is changed.
- If current coverage is partial, document the exact gap before changing behavior.

| Area | Code evidence | Current coverage | Required tests before change | Release blocker | Known gaps |
| --- | --- | --- | --- | --- | --- |
| PMB validation | `dataValidation.pmb`, `digits12` preset, `samples.pmb_number` unique index | Partial. Preset exists and uniqueness exists, but global behavior is not regression-locked. | Accept valid 12 digits, reject invalid shape when enabled, verify duplicate handling, verify create and edit flows. | Yes | No baseline roundtrip suite for all PMB entry paths. |
| CPR validation | `dataValidation.mrn`, `parseCprNumber()`, `applyCprAutofill()` | Partial. Parser and autofill exist, but field naming and domain coverage remain incomplete. | Accept valid CPR-like input, reject invalid dates, verify century behavior, verify autofill and no unwanted overwrite of manual edits. | Yes | Current parser is heuristic, not a full CPR rules engine. |
| CRUD smoke | Built-in self-test plus module CRUD flows | Present. Self-test exercises core create/update/delete paths. | Re-run self-test and targeted manual smoke for touched entities. | Yes | No formal external golden dataset harness yet. |
| Backup and restore roundtrip | `downloadBackup()`, `importData()`, `replaceAllData()`, `restoreFromFile()` | Partial. Flows exist, but roundtrip assertions are not fully formalized. | Export representative data, restore it, verify counts and key settings, verify no silent loss. | Yes | No locked roundtrip suite for every store. |
| JSON export and import | JSON backup and bound-file paths | Partial. Runtime path exists. | Verify backup file creation, re-import, compatibility, and data integrity. | Yes | Bound-file and manual restore need explicit regression coverage. |
| CSV and ZIP export and import | CSV backup, per-entity CSV export, ZIP export, CSV restore | Partial. Runtime paths exist. | Verify filtered export counts, CSV restore behavior, ZIP contents, and no cross-store corruption. | Yes | No formal assertion that filtered exports match visible rows. |
| SQL export | `generateSqlDump()` and admin export UI | Present. Self-test exercises SQL export generation. | Verify export completes and output remains syntactically valid after touched changes. | No | Not an import path, but still sensitive to schema drift. |
| PDF generation | `createReportPdfBlob()`, custom PDF builder, report preview flow | Partial. PDF path exists and logo loading exists. | Generate PDF with representative report data, verify blob creation, filename, logo fallback, and non-crash behavior. | Yes | No visual regression lock or snapshot baseline yet. |
| Filtered export | `exportFilteredCsv()` and module-specific filtered arrays | Partial. Export exists but count correctness is not locked. | Apply filters, export, and verify row count matches visible filtered rows. | Yes | Missing formal regression for filtered counts. |
| AI-provider configuration | `ai_providers` store, admin provider UI, variant AI request flow | Partial. Configuration and request path exist. | Verify provider CRUD, secret persistence behavior, and no accidental hard dependency for core workflows. | Yes when touched | Live provider interoperability remains runtime-unverified. |
| Bound file and autosave | `bindDbFile()`, `saveBoundFile()`, autosave flags and settings | Partial. Full path exists. | Verify bind, save, reload, autosave on/off behavior, and no merge regression. | Yes | Long-running permission and conflict behavior is not yet locked. |
| Reset and restore | Reset, backup-first, import, replace-all flows | Partial. Paths exist. | Verify reset protections, backup creation, and successful restore to usable state. | Yes | Exact preservation semantics need formal assertions. |
| Audit logging | `audit` store and entity mutation flows | Present. Runtime audit path exists. | Verify create, update, delete, export, and restore-sensitive actions still log as expected when touched. | Yes when touched | No dedicated audit regression suite beyond runtime use. |
| Logo fallback | `loadReportLogoImage()` and PDF generation path | Partial. `logo.png` path exists and failure fallback is graceful. | Verify missing `logo.png` does not break PDF; verify present logo still renders. | Yes when PDF touched | SVG fallback is not implemented. |
| Family, patient, and order navigation | Existing cross-links in dashboard, families, samples, orders, reports | Partial. Cross-links exist, but not all requested shortcuts are present. | Verify touched navigation paths from orders to related entities and confirm no existing links break. | Yes when touched | Additive patient/family shortcuts in orders are still missing. |
| Self-test coverage and gaps | Admin self-test flow | Present but incomplete. | If touching covered areas, run self-test. If touching uncovered areas, add targeted tests or document why coverage remains manual. | Yes | Self-test does not yet explicitly cover PDF blob assertions, backup roundtrip, CSV restore, or filtered export counts. |

## Matrix interpretation rule
If a change touches more than one row, the union of the required tests applies.
