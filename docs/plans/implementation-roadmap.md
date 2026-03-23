# Implementation Roadmap

## Fase A – Discovery og baseline
**Varighed:** 1–2 uger  
**Mål:** Fjern blindflyvning.

### Leverancer
- Kodeimport
- Modulkortlægning
- Gap-analyse mod ønskeliste
- Golden dataset
- Smoke tests
- Release checkliste

## Fase B – Datadisciplin
**Varighed:** 1–2 uger  
**Mål:** Luk domænefejl først.

### Leverancer
- PMB 12-cifret validering
- MRN -> CPR refaktorering
- CPR parser og manuel override for født/køn
- Unikhedskrav som admin-indstilling
- Integer-håndhævelse på relevante felter

## Fase C – Lavrisiko UX-forbedringer
**Varighed:** 1 uge

### Leverancer
- Nye ordinationsgenveje
- Eksportknapper med antal
- Tooltips
- Klikbare KPI'er
- Collapsible admin-sektioner
- Logo credits hover
- PDF-spacing/date-fix

## Fase D – Drift og sikkerhed
**Varighed:** 2–3 uger

### Leverancer
- Sikkerhedsvurdering af lokal storage og autosave
- Incognito advisory / optional enforcement setting
- Kryptering af følsomme lokale metadata hvor realistisk
- SVG-logo fallback
- Write-through policy for lokal DB

## Fase E – Kontrollerede integrationspiloter
**Varighed:** 3–6 uger

### Leverancer
- AI provider registry og adaptere
- CSV PMB lookup
- I18n framework
- Pilot for online persistence (kun hvis godkendt)
- Pilot for theme packs pr. bruger

## Fase F – Analysemodul
**Varighed:** 4–8 uger

### Leverancer
- Analyse menu
- NGS library designer
- Plate setup
- Genome browser tracks
- Splice site helper
- Re-evaluation alerting

## Go/no-go gates
- Gate 1: baseline eksisterer
- Gate 2: P0 datavalidering grøn
- Gate 3: UX batch grøn uden regression
- Gate 4: integrationspilot særskilt godkendt
- Gate 5: analysemodul har defineret MVP
