# ADR-002 – i18n Strategy

## Status
Accepted

## Context
Der ønskes mange sprog, men dansk skal være sikker fallback, og formatering/PDF må ikke bryde.

## Decision
- Flyt brugerrettede tekster til sprogpakker.
- Dansk indlejres som fallback i runtime.
- Eksterne filer som `/lang/<locale>.json` kan overskrive eller supplere.
- Dato/tal formatteres via central locale service.
- PDF-generering må kun bruge oversættelser, der findes i valideret resource map.

## Consequences
### Positive
- Kontrolleret udvidelse af sprog
- Dansk kan altid fungere uden eksterne filer

### Negative
- Stor testbyrde ved PDF/layout pr. sprog
- Manglende translation kan give tomme labels hvis der ikke er fallbackdisciplin

## Follow-up
- Start med framework + 1 ekstra sprog før fuld sprogliste.
