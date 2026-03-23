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
| PMB validation | `dataValidation.pmb`, `digits12` preset, `samples.pmb_number` unique index | Partial. Self-test now covers valid/invalid 12-digit PMB values plus duplicate create and edit behavior in sample flows. | Accept valid 12 digits, reject invalid shape when enabled, verify duplicate handling, verify create and edit flows. | Yes | No baseline suite yet for every PMB entry path, import path, or report/export surface. |
| CPR validation | `dataValidation.mrn`, `parseCprNumber()`, `applyCprAutofill()` | Partial. Self-test now covers valid/invalid CPR-like input, parser output, and autofill behavior. | Accept valid CPR-like input, reject invalid dates, verify century behavior, verify autofill and no unwanted overwrite of manual edits. | Yes | Current parser is heuristic, not a full CPR rules engine, and manual-override coverage is still missing. |
| CRUD smoke | Built-in self-test plus module CRUD flows | Present. Self-test exercises core create/update/delete paths. | Re-run self-test and targeted manual smoke for touched entities. | Yes | No formal external golden dataset harness yet. |
| Backup and restore roundtrip | `downloadBackup()`, `importData()`, `replaceAllData()`, `restoreFromFile()` | Partial. Self-test now covers `exportData()` plus `replaceAllData()` roundtrip with representative records and `validation_settings`. | Export representative data, restore it, verify counts and key settings, verify no silent loss. | Yes | Browser download, file-picker restore, and store-by-store roundtrip coverage remain incomplete. |
| JSON export and import | JSON backup and bound-file paths | Partial. Core JSON snapshot/restore contract is now covered through self-test. | Verify backup file creation, re-import, compatibility, and data integrity. | Yes | Bound-file and manual restore still need explicit regression coverage. |
| CSV and ZIP export and import | CSV backup, per-entity CSV export, ZIP export, CSV restore | Partial. Runtime paths exist, and patient filtered-export row counts are now covered through self-test. | Verify filtered export counts, CSV restore behavior, ZIP contents, and no cross-store corruption. | Yes | CSV restore, ZIP contents, and filtered-export assertions outside patients remain uncovered. |
| SQL export | `generateSqlDump()` and admin export UI | Present. Self-test exercises SQL export generation. | Verify export completes and output remains syntactically valid after touched changes. | No | Not an import path, but still sensitive to schema drift. |
| PDF generation | `createReportPdfBlob()`, custom PDF builder, report preview flow | Partial. Self-test now verifies PDF blob creation, MIME/signature, deterministic filename, and non-crash behavior when `logo.png` is unavailable. | Generate PDF with representative report data, verify blob creation, filename, logo fallback, and non-crash behavior. | Yes | No visual regression lock or snapshot baseline yet. |
| Filtered export | `exportFilteredCsv()` and module-specific filtered arrays | Partial. Self-test now verifies row-count correctness for patient filtered export. | Apply filters, export, and verify row count matches visible filtered rows. | Yes | Samples, orders, variants, and reports still lack formal filtered-export assertions. |
| AI-provider configuration | `ai_providers` store, admin provider UI, variant AI request flow | Partial. Configuration and request path exist. | Verify provider CRUD, secret persistence behavior, and no accidental hard dependency for core workflows. | Yes when touched | Live provider interoperability remains runtime-unverified. |
| Bound file and autosave | `bindDbFile()`, `saveBoundFile()`, autosave flags and settings | Partial. Full path exists. | Verify bind, save, reload, autosave on/off behavior, and no merge regression. | Yes | Long-running permission and conflict behavior is not yet locked. |
| Reset and restore | Reset, backup-first, import, replace-all flows | Partial. Paths exist. | Verify reset protections, backup creation, and successful restore to usable state. | Yes | Exact preservation semantics need formal assertions. |
| Audit logging | `audit` store and entity mutation flows | Present. Runtime audit path exists. | Verify create, update, delete, export, and restore-sensitive actions still log as expected when touched. | Yes when touched | No dedicated audit regression suite beyond runtime use. |
| Logo fallback | `loadReportLogoImage()` and PDF generation path | Partial. `logo.png` path exists and failure fallback is graceful. | Verify missing `logo.png` does not break PDF; verify present logo still renders. | Yes when PDF touched | SVG fallback is not implemented. |
| Family, patient, and order navigation | Existing cross-links in dashboard, families, samples, orders, reports | Partial. Cross-links exist, but not all requested shortcuts are present. | Verify touched navigation paths from orders to related entities and confirm no existing links break. | Yes when touched | Additive patient/family shortcuts in orders are still missing. |
| Self-test coverage and gaps | Admin self-test flow | Present and expanded. Self-test now covers PMB, CPR, JSON roundtrip, PDF blob generation, and patient filtered-export counts in addition to the earlier CRUD/FHIR/ZIP/SQL checks. | If touching covered areas, run self-test. If touching uncovered areas, add targeted tests or document why coverage remains manual. | Yes | CSV/ZIP restore, bound-file/autosave, visual PDF fidelity, and broader filtered-export coverage remain outside the current harness. |

## Matrix interpretation rule
If a change touches more than one row, the union of the required tests applies.
