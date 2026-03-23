# GlimR – governance-opdateret README-udkast

> Dette README-udkast afspejler dokumenteret funktionalitet fra eksisterende INFO.md samt den aktuelle governance-retning. Det er \*\*ikke\*\* en kodeverificeret feature-liste og skal opdateres igen, når `GlimR.html` er analyseret.

## Kort fortalt

GlimR er et browserbaseret, offline-first LIMS til genetisk diagnostik. Produktet er designet til at kunne leveres som én HTML-fil, bruge lokal persistence og understøtte centrale laboratorieflows omkring patienter, familier, prøver, ordinationer, varianter, rapporter, audit og eksport.

## Dokumenteret produktretning

* single-file deployment
* offline-first lokal persistence
* lokal filbinding / backup-arbejde
* rapport-PDF og andre eksportformer
* variantbibliotek og rapportarbejdsflade
* administrative funktioner, audit og selvtest
* laboratorienære hjælpeværktøjer

## Governance-retning

Videreudvikling af GlimR styres efter følgende principper:

* ingen regressioner
* baseline før featureudvikling
* små, reviewbare ændringer
* feature flags på højriskoændringer
* dokumentation og test som obligatoriske leverancer
* dansk fallback i sprogarkitekturen
* single-file release som ydre kontrakt

## Prioriteret udviklingsretning

### Først

* kodeinventar
* regressionstest
* PMB/CPR validering
* dokumentation og annotation

### Derefter

* additive UX-forbedringer
* sikre eksport-/PDF-forbedringer
* kontrollerede integrationsspor
* analysemoduler

## Kendte ønskede videreudviklingsspor

* bedre ordinationsgenveje
* eksportknapper med antal
* PDF-layoutforbedringer
* unikhedskrav for PMB/CPR
* collapsible administration
* SVG logo fallback
* temaer pr. bruger
* sprogpakker
* AI provider management
* analysefane med NGS/plate-design
* revurderingslogik i variantbibliotek
* annotation af kodebasen

## Release- og kvalitetspolitik

Ingen release må sendes ud uden:

* smoke tests
* backup/restore verificering
* PDF-regression vurdering
* changelog
* checksum
* godkendelse fra produkt- og kvalitetsejer

## Dokumenter

Se:

* `AGENTS.md`
* `PLANS.md`
* `docs/product/prd.md`
* `docs/architecture/system-architecture.md`
* `docs/governance/\*`
* `docs/backlog/feature-inventory-and-gap-analysis.md`
* `docs/procurement/udbudsbeskrivelse.md`

