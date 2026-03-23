# System Architecture – GlimR

## Arkitekturretning
GlimR bør fastholde **single-file runtime** som distributionsmål, men internt organiseres som logiske moduler, så videreudvikling bliver styrbar.

## 1. Målarkitektur
```text
UI Layer
├─ Navigation / Tabs
├─ Forms / Tables / Filters
├─ PDF / Export UI
└─ Admin / Settings UI

Application Services
├─ PatientsService
├─ FamiliesService
├─ SamplesService
├─ OrdersService
├─ VariantsService
├─ ReportsService
├─ AdminService
├─ BackupService
├─ AIService
├─ AnalysisToolsService
└─ LocalizationService

Infrastructure Adapters
├─ IndexedDbAdapter
├─ LocalJsonMirrorAdapter
├─ PdfAdapter
├─ CsvImportExportAdapter
├─ SqlExportAdapter
├─ FhirMedComAdapter
├─ AIProviderAdapter(OpenAI/Ollama/LM Studio)
├─ ExternalSqlAdapter
└─ FtpAdapter

Shared Domain
├─ Validation
├─ Formatting
├─ Audit
├─ FeatureFlags
├─ Settings
└─ SchemaVersioning
```

## 2. Runtime model
- **Primær drift**: lokal browser, offline-first
- **Primær persistence**: IndexedDB
- **Sekundær persistence**: bruger-valgt JSON-fil (mirror/write-through)
- **Valgfri integrationer**: AI, SQL, FTP, eksterne hjælpefiler
- **Output**: PDF, CSV, JSON, SQL, ZIP, FHIR/MedCom

## 3. Modulgrænser
### Domæner
- Patients
- Families
- Samples
- Orders / Ordinationer
- Variants
- Reports
- QC
- Admin
- Users / Auth
- Analysis
- Storage / Backup
- Interop

### Tværgående concern
- Validation
- Audit
- Formatting
- Localization
- Security
- Feature flags
- Migration

## 4. Kodeorganisering (anbefalet)
Selv hvis release fortsat er én HTML-fil, bør kilden organiseres således:
```text
src/
  app/
  domain/
  services/
  adapters/
  ui/
  pdf/
  i18n/
  tests/
dist/
  GlimR.html
```

## 5. Data flows
### Lokal drift
User action -> service -> validation -> IndexedDB -> audit -> UI refresh

### Lokal JSON mirror
User action -> service -> validation -> IndexedDB -> mirror writer -> success/failure banner -> audit

### AI-assistance
Variant form -> provider adapter -> provider response -> schema validation -> draft patch -> user review -> apply -> audit

### Rapport-PDF
Report selection -> template composition -> data formatting -> asset resolution (logo/svg) -> PDF render -> file save -> audit

## 6. Høj-risiko arkitekturpunkter
- Online SQL som write target
- FTP-baseret databasebrug
- Tvungen inkognito-mode
- Fuld multi-sprog med PDF-layoutgaranti
- AI-forslag der skriver direkte i kliniske felter
- Kryptering af lokal ekstern DB uden robust nøglemodel

## 7. Arkitekturregler
1. Nye integrationer går bag adaptere.
2. UI må ikke kende konkrete persistence-detaljer.
3. Alle formatregler skal samles i delte formattere.
4. PMB/CPR validering skal ligge centralt, ikke spredt i UI.
5. Alle exports skal kunne testes deterministisk så vidt praktisk muligt.
6. Hver ny feature skal klassificeres som additive, invasive eller architectural.

## 8. Overtagelighed
For at andre kan tage over, skal `GlimR.html` annoteres i sektioner:
- purpose
- dependencies
- side effects
- storage touchpoints
- feature flag relation
- known risks
