# Feature Inventory and Gap Analysis

## Metode
Listen herunder er afledt af bestillerens ønskeliste. Da `GlimR.html` ikke er inspiceret, er status **foreløbig**.

### Statuskoder
- **D** = dokumenteret i eksisterende README
- **V** = kræver kodeverifikation
- **N** = ny funktionalitet
- **HR** = høj-risiko / separat spor

## Backlog

### B-001 Ordinationsgenvej til Familie og Patient
- Status: N
- Prioritet: P1
- Risiko: Low
- Acceptance criteria:
  - Hvis patient på ordination har familienummer, vis ikon til Familie.
  - Vis ikon til Patient.
  - Ikoner placeres til højre for eksisterende Prøve- og Rapport-ikoner.

### B-002 Eksportknapper viser antal filtrerede elementer
- Status: V
- Prioritet: P1
- Risiko: Low

### B-003 Tooltip på Akut/Haster og klikbare KPI'er
- Status: V
- Prioritet: P1
- Risiko: Low

### B-004 PDF spacing og danske datoformater i rapporter
- Status: V
- Prioritet: P0
- Risiko: Medium

### B-005 Integer-håndhævelse for PMB, size_bp, copy_number
- Status: V
- Prioritet: P0
- Risiko: Medium

### B-006 Admin-indstilling: kræv unikke prøver og patienter
- Status: N
- Prioritet: P0
- Risiko: Medium

### B-007 Admin-indstilling: kræv inkognito-mode
- Status: N
- Prioritet: P2
- Risiko: HR

### B-008 Administration collapsible og default-minimeret
- Status: N
- Prioritet: P1
- Risiko: Low

### B-009 Mouse-over credits på logo
- Status: N
- Prioritet: P3
- Risiko: Low

### B-010 Autofill formular med admin-modul
- Status: V
- Prioritet: P2
- Risiko: Medium

### B-011 Få styr på AI udfyld
- Status: V
- Prioritet: P2
- Risiko: HR

### B-012 Simpel genome browser med tracks
- Status: N
- Prioritet: P2
- Risiko: HR

### B-013 Splice site tool og visualisering
- Status: N
- Prioritet: P2
- Risiko: HR

### B-014 SVG-logo fallback når `logo.png` mangler
- Status: N
- Prioritet: P1
- Risiko: Low

### B-015 AI provider management + variant autofill
- Status: N
- Prioritet: P2
- Risiko: HR

### B-016 FTP til databasen
- Status: N
- Prioritet: P3
- Risiko: HR
- Bemærkning: bør kun overvejes hvis der foreligger eksplicit driftsbehov.

### B-017 Sæson- og pinktemaer per bruger
- Status: N
- Prioritet: P3
- Risiko: Low/Medium

### B-018 Fuld sprogfunktion med mange sprog
- Status: N
- Prioritet: P2
- Risiko: HR

### B-019 Analyse-menupunkt med NGS designer og plate setup
- Status: N
- Prioritet: P2
- Risiko: HR

### B-020 Auto-indsæt `logo.png` i rapport-PDF
- Status: V
- Prioritet: P1
- Risiko: Medium

### B-021 Kryptering af pinkode i ekstern lokal DB
- Status: N
- Prioritet: P1
- Risiko: HR

### B-022 Auto-hent PMB fra CSV ved CPR-opslag
- Status: N
- Prioritet: P2
- Risiko: Medium

### B-023 Online SQL database som datalagring
- Status: N
- Prioritet: P3
- Risiko: HR

### B-024 Revurderingsinterval for variantbibliotek
- Status: N
- Prioritet: P2
- Risiko: Medium

### B-025 Fuld annotering af `GlimR.html`
- Status: N
- Prioritet: P0
- Risiko: Medium

### B-026 README-opdatering
- Status: N
- Prioritet: P0
- Risiko: Low

### B-027 Udbudsbeskrivelse
- Status: N
- Prioritet: P0
- Risiko: Low

### B-028 Autosave + ryd browserhukommelse / incognito research
- Status: N
- Prioritet: P1
- Risiko: HR

### B-029 PMB skal være 12-cifret heltal overalt
- Status: N
- Prioritet: P0
- Risiko: Medium

### B-030 MRN omdøbes til CPR med dansk CPR-validering
- Status: N
- Prioritet: P0
- Risiko: High

### B-031 PMB må ikke vises under Ordination på Varianter
- Status: N
- Prioritet: P1
- Risiko: Low

## Konklusion
De rigtige første leverancer er ikke de mest flashy. De er:
1. baseline-verifikation
2. domænevalidering (PMB/CPR)
3. dokumentation og annotation
4. regressionstest
5. derefter additive UX-forbedringer

Det er præcis sådan man undgår at et single-file laboratorieværktøj udvikler sig til en klinisk Jenga-tårn med dårlig rollback.
