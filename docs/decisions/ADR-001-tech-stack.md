# ADR-001 – Tech Stack Direction

## Status
Accepted

## Context
GlimR leveres som én HTML-fil og bruges offline. Projektet skal gøres overtageligt uden at miste distributionsmodellen.

## Decision
- Bevar browserbaseret runtime og single-file distribution som ydre kontrakt.
- Tillad intern modularisering af kildekoden.
- Brug adaptermønster omkring storage, AI, eksport og integrationer.
- Bevar vanilla web stack som default, med mindst mulig runtime-kompleksitet.

## Consequences
### Positive
- Minimal driftsbarriere
- Let distribution
- God alignment med nuværende produktform

### Negative
- Stor HTML-fil kan være svær at vedligeholde uden god struktur
- Test og modulgrænser kræver disciplin

## Follow-up
- Etabler build-pipeline der kan samle modulær kilde til én `GlimR.html`.
