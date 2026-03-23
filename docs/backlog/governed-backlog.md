# Governed Backlog

## Status
- Backlog status: active
- Scope: authoritative backlog register after the 2026-03-23 baseline lock

## Relationship to older documents
This file supersedes `docs/backlog/feature-inventory-and-gap-analysis.md` as the active planning register.

The older file remains the intake history. This file is the governed tracker tied to the verified code baseline.

## Status legend
- `verified`: substantively present in the current codebase
- `partial`: partially present, partially governed, or present with important gaps
- `missing`: not substantively present in the current baseline

## Risk class legend
- `A`: low-risk additive UI or documentation work
- `B`: medium-risk validation, PDF, or domain-rule work
- `C`: high-risk schema, storage, naming, migration, or integration work

## Summary
- Verified: 4
- Partial: 10
- Missing: 17
- Class A: 9
- Class B: 7
- Class C: 15

| ID | Feature / oenske | Status | Risk class | Paavirkede moduler | Paavirker dataformat | Kraever ADR | Kraever migration | Foreslaaet slice | Acceptkriterier | Testkrav | Noter |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| B-001 | Ordinationsgenvej til Familie og Patient | missing | A | Orders, Patients, Families | No | No | No | Phase 2 / Slice A1 | Additive patient and family shortcuts appear in orders without removing existing shortcuts. | Manual navigation smoke from order to patient and family. | Current orders already link to related sample/report paths. |
| B-002 | Eksportknapper viser antal filtrerede elementer | missing | A | Patients, Samples, Orders, Reports, Variants | No | No | No | Phase 2 / Slice A2 | Export buttons show the current filtered count and still export the same filtered set. | Filtered export row-count checks. | Pure UI if implemented by reusing existing filtered arrays. |
| B-003 | Tooltip paa Akut/Haster og klikbare KPI'er | partial | A | Dashboard, Orders, Planner | No | No | No | Phase 2 / Slice A3 | Tooltips and KPI navigation are additive and consistent. | Manual UI smoke for tooltip visibility and KPI click-through. | Urgency tooltip behavior exists in part; KPI behavior needs runtime confirmation. |
| B-004 | PDF spacing og danske datoformater i rapporter | partial | B | Reports, PDF flow | No | No | No | Phase 3 / Slice B1 | PDF spacing remains readable and Danish date formatting stays correct. | PDF blob generation plus visual regression checks. | Date formatting exists; visual regression is not locked. |
| B-005 | Integer-haandhaevelse for PMB, size_bp, copy_number | partial | B | Create case, Samples, Variants, Validation settings | Yes | No | Yes | Phase 3 / Slice B2 | Integer rules are explicit and non-breaking across create and edit flows. | Validation tests for affected fields and regression smoke for save flows. | Some coercion exists, but not as a formal cross-field guarantee. |
| B-006 | Admin-indstilling: kraev unikke prover og patienter | missing | B | Admin, Patients, Samples, IndexedDB schema | Yes | No | Yes | Phase 3 / Slice B3 | Admin can express uniqueness policy without breaking existing data. | Duplicate, import, restore, and settings tests. | PMB uniqueness already exists in UI and DB, so this is not a trivial toggle. |
| B-007 | Admin-indstilling: kraev inkognito-mode | missing | C | Admin, Storage, Runtime policy | Yes | Yes | Yes | Phase 4 / Slice C1 | Any private-mode requirement is explicit, pilot-only, and operationally understood. | Browser-mode compatibility tests and storage behavior review. | High risk because browser private-mode behavior is inconsistent. |
| B-008 | Administration collapsible og default-minimeret | missing | A | Admin | No | No | No | Phase 2 / Slice A4 | Admin sections are collapsible and default state is predictable without hiding critical actions. | Manual admin workflow smoke. | Additive UI only. |
| B-009 | Mouse-over credits paa logo | missing | A | Header, Branding | No | No | No | Phase 2 / Slice A5 | Credits appear on hover and do not interfere with navigation. | Manual UI smoke. | Low-risk branding enhancement. |
| B-010 | Autofill formular med admin-modul | verified | C | Admin, Variants, AI providers | Yes | Yes | Yes | Baseline only | Existing provider-configured autofill remains accessible and optional. | Any future change requires AI config and no-hard-dependency tests. | Overlaps strongly with B-015. Treat future changes as governed integration work. |
| B-011 | Faa styr paa AI udfyld | partial | C | Variants, Admin, Audit | Yes | Yes | Yes | Phase 4 / Slice C2 | AI assistance stays optional, reviewable, and clearly marked as assistance. | Provider CRUD, request-path, audit, and failure-mode tests. | Runtime and governance hardening are incomplete. |
| B-012 | Simpel genome browser med tracks | missing | C | Tools, Variant library, New module surface | Yes | Yes | Yes | Phase 4 / Slice C3 | Scope, data model, and runtime dependencies are explicitly approved before buildout. | ADR-driven module and integration tests. | Not present as a governed productized feature. |
| B-013 | Splice site tool og visualisering | missing | C | Tools, Variants, New module surface | Yes | Yes | Yes | Phase 4 / Slice C4 | Tool is scoped, additive, and does not alter core workflows. | ADR-driven domain and UI tests. | New analysis-domain work, not baseline functionality. |
| B-014 | SVG-logo fallback naar `logo.png` mangler | missing | B | Reports, PDF flow | No | No | No | Phase 3 / Slice B4 | Missing `logo.png` still produces a valid report, and optional SVG fallback works without new runtime dependency. | PDF generation with and without branding asset. | Current fallback is "no logo", not SVG. |
| B-015 | AI provider management + variant autofill | verified | C | Admin, Variants, AI providers | Yes | Yes | Yes | Baseline only | Existing provider configuration and variant autofill remain optional and non-blocking. | Any future change requires provider, persistence, and failure-path tests. | Verified in substantial form. Overlaps with B-010. |
| B-016 | FTP til databasen | missing | C | Storage, Export, Integration | Yes | Yes | Yes | Phase 4 / Slice C5 | FTP use is treated as a separate integration pilot, never as an ad hoc storage patch. | ADR, threat review, compatibility tests. | Out of baseline scope and high risk. |
| B-017 | Saeson- og pinktemaer per bruger | partial | C | Theme, Users, localStorage | Yes | Yes | Yes | Phase 4 / Slice C6 | Per-user theme behavior is explicit and does not break layout, PDF, or exports. | Theme persistence and layout smoke tests. | Theme support exists, but requested per-user themed variants are not complete. |
| B-018 | Fuld sprogfunktion med mange sprog | missing | C | All UI text, Reports, PDF, Exports | Yes | Yes | Yes | Phase 4 / Slice C7 | I18n strategy must preserve Danish fallback and not break layout or PDFs. | ADR plus locale, PDF, and export regression coverage. | High-risk cross-cutting change. |
| B-019 | Analyse-menupunkt med NGS designer og plate setup | missing | C | New analysis module, Planner, Tools | Yes | Yes | Yes | Phase 4 / Slice C8 | New module is scoped as a separate governed track with no hidden impact on core flows. | ADR plus module-specific workflow tests. | New module area, not an additive tweak. |
| B-020 | Auto-indsaet `logo.png` i rapport-PDF | verified | B | Reports, PDF flow | No | No | No | Baseline hardening only | Existing optional `logo.png` loading continues to work, and missing file does not break PDF generation. | PDF generation with present and missing `logo.png`. | Present in code, but still runtime-sensitive across environments. |
| B-021 | Kryptering af pinkode i ekstern lokal DB | missing | C | Users, Storage, Bound file, Export | Yes | Yes | Yes | Phase 4 / Slice C9 | Security model, compatibility, and operator handling are explicit before implementation. | ADR, compatibility tests, backup/restore tests. | Current local model stores PIN data without dedicated encryption. |
| B-022 | Auto-hent PMB fra CSV ved CPR-opslag | missing | B | Create case, Patients, Samples, Import helpers | Yes | No | No | Phase 3 / Slice B5 | CSV-driven PMB lookup is optional, traceable, and does not overwrite data unexpectedly. | Validation, CSV parsing, and manual override tests. | Medium risk because it touches domain data entry. |
| B-023 | Online SQL database som datalagring | missing | C | Storage, Runtime architecture, Export/import | Yes | Yes | Yes | Phase 4 / Slice C10 | Any online SQL path remains a separate integration track and does not replace offline-first baseline by accident. | ADR, threat review, migration and offline-fallback tests. | Explicitly high risk and out of baseline scope. |
| B-024 | Revurderingsinterval for variantbibliotek | partial | B | Variant library, Alerts, Reports | No | No | No | Phase 3 / Slice B6 | Review interval behavior is explicit, testable, and does not corrupt existing library records. | Variant library CRUD plus date/alert tests. | Review metadata exists, but interval policy and warnings are not complete. |
| B-025 | Fuld annotering af `GlimR.html` | missing | A | Documentation, Code map | No | No | No | Phase 2 / Slice A6 | Documentation maps the actual code modules without changing logic. | Documentation review only. | Valuable for maintainability and review safety. |
| B-026 | README-opdatering | verified | A | README, Documentation | No | No | No | Baseline only | README remains aligned to the verified product surface. | Documentation review only. | README already reflects large parts of the codebase. |
| B-027 | Udbudsbeskrivelse | partial | A | Procurement docs, Governance | No | No | No | Phase 2 / Slice A7 | Procurement material is aligned to the locked baseline and does not overclaim unverified features. | Documentation review against baseline. | Artifact exists, but was not previously locked to verified code. |
| B-028 | Autosave + ryd browserhukommelse / incognito research | partial | C | Database, Storage, localStorage, Bound file | Yes | Yes | Yes | Phase 4 / Slice C11 | Autosave behavior remains safe, and any retention change is treated as governed storage design. | Autosave, bind, reload, and private-mode behavior tests. | Autosave exists; "clear memory" and incognito policy do not. |
| B-029 | PMB skal vaere 12-cifret heltal overalt | partial | C | Samples, Validation, Imports, Exports, Reports | Yes | Yes | Yes | Phase 4 / Slice C12 | PMB behavior is consistent across UI, storage, imports, exports, and restore flows. | Validation plus roundtrip import/export tests. | Current support is partial and migration-sensitive. |
| B-030 | MRN omdoebes til CPR med dansk CPR-validering | partial | C | Patients, Create case, Orders, Reports, FHIR, Exports | Yes | Yes | Yes | Phase 4 / Slice C13 | CPR model is introduced through a controlled migration and compatibility strategy. | ADR, migration dataset, validation, PDF, export/import, and search tests. | Not a rename. This is a full migration program. |
| B-031 | PMB maa ikke vises under Ordination paa Varianter | missing | A | Variants, Orders UI | No | No | No | Phase 2 / Slice A8 | PMB is hidden in the targeted context without removing needed identifiers elsewhere. | Manual UI regression around variant and order context. | UI-only request if implemented narrowly. |

## Interpretation rule
If a backlog item touches multiple risk domains, keep the highest assigned risk class unless a newer governance decision explicitly reclassifies it.
