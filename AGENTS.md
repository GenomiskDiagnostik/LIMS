# AGENTS.md

## Mission
Videreudvikl GlimR sikkert, dokumenteret og reversibelt. Bevar produktets offline-first karakter, single-file distribution og kliniske anvendelighed.

## Non-negotiable product rules
1. Eksisterende funktionalitet må ikke brydes.
2. Ingen skjulte schemaændringer eller data-migrationer uden backup-strategi og rollback-plan.
3. Alle brugerrettede ændringer skal have acceptance criteria.
4. Alle høj-risiko ændringer skal være bag feature flag eller admin-indstilling, indtil de er verificeret.
5. AI-funktioner må ikke fremstille genererede svar som kliniske fakta uden tydelig markering og kildekrav.
6. Dansk er fallback-sprog.
7. Single-file build-output er obligatorisk, selv hvis kildetræet modulariseres.
8. PMB og CPR er domænekritiske felter og må ikke ændres uden tværgående konsekvensanalyse.

## Working style
- Plan-first.
- Små, reviewbare ændringer.
- Dokumentér før større refaktoreringer.
- Hold ændringer isolerede pr. featureområde.
- Opdater `PLANS.md` ved væsentlige beslutninger.
- Brug ADR'er ved arkitekturelle beslutninger.

## Clean-room rule
Ved udbud eller eventuel nyimplementering skal krav beskrives funktionsmæssigt og arkitektonisk. Der må ikke ske proprietær kloning uden eksplicit rettighedsafklaring.

## UX rules
- Ingen overraskende adfærd.
- Eksisterende flows må ikke ændres uden godkendt change request.
- Nye genveje, tooltips og klikbare KPI'er skal være additive og ikke fjerne eksisterende navigation.
- Validering skal være tydelig, lokal og forklarende.
- Sprogskift og temaer må ikke ødelægge layout, eksport eller PDF.

## Architecture rules
- Offline-first og local-first er førstevalg.
- IndexedDB er primær lokal persistence, men abstraheret bag repository/storage layer.
- Eksterne integrationspunkter (AI, SQL, FTP, lokale filer) skal ligge bag adaptere.
- PDF, eksport og backup skal være deterministiske nok til regressionstest.
- Ingen netværkskrævende funktion må blive hard dependency for kernedrift.

## Localization rules
- Alle brugerrettede tekster skal kunne flyttes til sprogpakker.
- Dansk fallback må aldrig bryde hvis en ekstern sprogfil mangler.
- Dato-, tal- og PDF-formattering skal testes pr. sprog.

## Testing rules
- Golden dataset er obligatorisk.
- Smoke tests for CRUD, søgning, eksport, PDF, backup/restore og login.
- Høj-risiko features kræver målrettet regressionstest.
- Acceptance tests skal skrives før implementering på større features.
- Ingen release uden dokumenteret teststatus.

## Change-control rules
- Hver ændring skal referere til backlog-ID eller change request.
- Hver ændring skal klassificeres: bugfix, forbedring, sikkerhed, refaktorering, arkitektur eller feature.
- Hver ændring skal have rollback-vurdering.
- Arkitekturskift kræver ADR.
- Releases kræver godkendelse jf. `docs/governance/release-governance.md`.

## Expected output format for Codex
Ved plan- eller implementeringsarbejde skal output som minimum indeholde:
1. antagelser
2. berørte filer/moduler
3. risici
4. testplan
5. konkret ændringssekvens
6. eventuelle dokumentopdateringer
