# GlimR

GlimR er et browserbaseret, offline-first LIMS til genetisk diagnostik med deployment som én HTML-fil. Denne governance-starter pack etablerer styring for sikker videreudvikling, dokumentation, leverancekontrol og udbud.

## Formål med denne pakke
Denne pakke er lavet for at sætte styring på videreudviklingen af GlimR uden at ødelægge eksisterende funktionalitet.

Den gør fire ting:

1. Definerer governance, change control og release-gates.
2. Samler en verificerbar backlog over ønsket funktionalitet.
3. Etablerer en plan for baseline-inventar, regressionstest og sikker videreudvikling.
4. Leverer et opdateret README-udkast og en udbudsbeskrivelse.

## Projektprincipper
- **Ingen regressioner**: eksisterende funktionalitet må ikke forringes.
- **Offline-first**: lokal drift uden backend er et førsteklassekrav.
- **Single-file delivery**: produktet skal fortsat kunne leveres som én HTML-fil, også hvis kildekoden internt opdeles i moduler.
- **Sporbarhed**: alle ændringer skal kunne spores til backlog, plan og test.
- **Klinisk konservativ AI**: AI må kun være støttefunktion, aldrig skjult beslutningstager.
- **Dansk som fallback**: dansk er default sprog, med kontrolleret ekstern i18n.

## Governance-filer
- `AGENTS.md` – arbejdsregler for udviklere og AI-agenter
- `PLANS.md` – aktiv plan og milepæle
- `docs/governance/change-control.md` – formel ændringsstyring
- `docs/governance/release-governance.md` – release- og godkendelsesmodel
- `docs/governance/regression-strategy.md` – teststrategi med nul-regressionsfokus

## Centrale produktdokumenter
- `docs/product/prd.md`
- `docs/architecture/system-architecture.md`
- `docs/backlog/feature-inventory-and-gap-analysis.md`
- `docs/procurement/udbudsbeskrivelse.md`

## Status
Denne pakke er udarbejdet **uden adgang til `GlimR.html`-kildekoden**. Derfor er alle ønsker klassificeret som:
- dokumenteret i README
- sandsynligvis eksisterende, men kræver verifikation
- ny funktionalitet
- høj-risiko ændring

Ingen påstand i denne pakke om eksisterende implementering må læses som kodeverificeret sandhed.

## Foreslået næste skridt
1. Tilføj `GlimR.html` til repoet.
2. Kør fase 0 i `PLANS.md`.
3. Etabler golden dataset og smoke-test suite.
4. Først derefter: begynd featurearbejde.

## Repo-struktur
```text
.
├── README.md
├── AGENTS.md
├── PLANS.md
└── docs/
    ├── architecture/
    ├── backlog/
    ├── decisions/
    ├── governance/
    ├── plans/
    ├── procurement/
    ├── product/
    └── security/
```

## Drift og release
Releases skal versionsstyres, have checksums, changelog, testresultater og en eksplicit godkendelse fra både produktansvarlig og kvalitetsejer før distribution.

## Bemærkning om dette README
Dette README er et **governance-orienteret README-udkast**. Når `GlimR.html` er tilgængelig, skal det sammenholdes med faktisk kode og opdateres linje for linje.
