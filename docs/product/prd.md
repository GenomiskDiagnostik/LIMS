# PRD – GlimR Governance and Controlled Evolution

## 1. Problem
GlimR er allerede et omfattende, browserbaseret genetic diagnostics LIMS. Videreudviklingen er i risiko for at blive opportunistisk og regressionstung, fordi ønskelisten spænder fra små UI-forbedringer til nye integrations- og analysemoduler uden formaliseret governance.

## 2. Formål
Etabler en videreudviklingsmodel hvor:
- eksisterende funktionalitet bevares
- ønsket funktionalitet verificeres før ændring
- højriskoændringer kontrolleres
- nye leverancer kan overtages af andre udviklere
- et eventuelt udbud kan gennemføres på et klart kravgrundlag

## 3. Primære brugergrupper
- Laboratoriepersonale
- Kliniske genetikere / variantfortolkere
- Administratorer
- Kvalitetsansvarlige
- Eksterne leverandører / udviklingsteam
- Revisorer / governance reviewers

## 4. Produktmål
1. Sikre nul-regressionsorienteret udvikling.
2. Gøre systemet overtageligt af nyt team.
3. Etablere backlog og acceptance criteria for ønskelisten.
4. Forberede teknisk og kontraktligt grundlag for evt. genudvikling/udbud.
5. Bevare enkel lokal drift med tydelig backup- og restore-model.

## 5. Dokumenteret nuværende funktionalitet (fra README, kræver stadig kodeverifikation)
- Single-file deployment
- Offline-first persistence via IndexedDB
- Lokal filbinding til JSON
- PDF-rapporter
- Variantbibliotek
- MedCom/FHIR
- Audit logs
- SQL/ZIP/JSON-eksport
- Toolbox og genom-relaterede hjælpeværktøjer

## 6. Ønsket funktionalitet i scope
### 6.1 Høj prioritet
- PMB som 12-cifret heltal overalt
- MRN omdøbes til CPR med validering
- Unikhedskrav for PMB/CPR (admin-indstilling)
- Regression-sikker PDF-justering
- Ordinationsgenveje til Familie og Patient
- Eksportknapper med filtreret antal
- Annotation af kodebase
- Opdateret README
- Governance og udbudsgrundlag

### 6.2 Mellem prioritet
- Klikbare KPI'er og tooltips
- Collapsible admin panels
- SVG logo fallback
- Sæson- og pinktemaer pr. bruger
- Revurderingsintervaller i variantbibliotek
- Auto-PMB lookup via CSV

### 6.3 Høj-risiko / særskilt spor
- AI-provider integrationer
- FTP til databasebrug
- Online SQL-lagring
- Tvungen inkognito-mode
- Kryptering af PIN i lokal ekstern DB
- Analyse-modul med NGS designer / genome browser / splice tools
- Fuld i18n på mange sprog

## 7. Ikke-funktionelle krav
- Offline-first
- Browserbaseret
- Reproducerbar backup og restore
- Klinisk konservativ AI
- Klar audit trail
- Testbar PDF- og eksportpipeline
- Tydelige feature flags for pilotfunktioner
- Ingen data-tab ved autosave eller restore
- Overtagelig kodebase med dokumenterede moduler

## 8. Definition of success
Projektet er succesfuldt når:
- governance-pakken er aktivt brugt
- baseline/regression suite findes
- P0/P1 backlog er verificeret og prioriteret
- første sikre feature-release er leveret uden regression
- README, udbudsbeskrivelse og arkitekturdokument er i sync med koden

## 9. Risici
- Manglende adgang til faktisk kode
- Uafklaret domænelogik for PMB/CPR migration
- Browserbegrænsninger ved file:// deployment
- Kompleksitet i multi-sprog + PDF-eksport
- Uoverensstemmelse mellem dokumenteret og faktisk funktionalitet
- Sikkerheds- og compliance-krav ved AI og online datalagring

## 10. Antagelser
- GlimR skal fortsat kunne bruges lokalt i moderne Chromium-browser.
- Dansk er baseline-sprog.
- Klinisk brug kræver konservativ fejlprofil.
- Single-file output ønskes bevaret.
