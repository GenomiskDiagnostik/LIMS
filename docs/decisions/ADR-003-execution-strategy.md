# ADR-003 – Execution Strategy

## Status
Accepted

## Context
Ønskelisten spænder fra små UI-fixes til store integrations- og analysemoduler. Risikoen for regression er høj.

## Decision
- Kør discovery/baseline først.
- Implementér P0/P1 i små additive batches.
- Klassificér højriskoændringer som særskilte spor med feature flags.
- Kræv dokumentation, acceptance criteria og testplan før implementering.
- Undgå giant rewrites.

## Consequences
### Positive
- Højere leverancesikkerhed
- Lettere review og overtagelse
- Mindre risiko for at bryde eksisterende flows

### Negative
- Langsommere vej til flashy features
- Mere upfront dokumentationsarbejde

## Follow-up
- Brug `PLANS.md` som aktiv styringsfil.
