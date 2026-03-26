# ADR-004 - User Logo Override

## Status
Accepted

## Context
GlimR skal kunne bruge et valgfrit per-bruger logo i UI-headeren og i rapport-PDF'er, og det skal virke stabilt, selv naar `GlimR.html` aabnes via `file://`.

Den eksisterende branding-kaede er:
- lokal `logo.png`
- indlejret SVG-fallback

Det loeser ikke brugerens behov for et eget logo, og lokal filadgang er ikke robust nok til PDF-rasterisering i alle browsermiljoeer.

## Decision
- Tilfoej et nyt valgfrit felt paa `users`-records: `organization_logo_data_url`.
- Feltet bruges kun som praesentation og branding, ikke som teknisk identifikator.
- Prioriteten for branding bliver:
  1. `state.currentUser.organization_logo_data_url`
  2. lokal `logo.png`
  3. indlejret SVG-fallback
- Feltet gemmes paa brugerrecorden, saa det bevares via JSON-backup, bound-file og `exportData()` / `replaceAllData()`.
- Der loeftes ikke `DB_VER`.
- Der oprettes ingen nye stores eller indexes.
- `organization_logo_data_url` tilfoejes ikke til `schemaFields.users`, saa CSV- og SQL-kontrakter forbliver uendrede.
- Audit skal ikke gemme logoindhold:
  - `organization_logo_data_url` fjernes fra audit-payloads for `users`
  - logo-only brugeropdateringer skal ikke oprette en tom audit-entry

## Consequences
### Positive
- Per-bruger branding virker i baade UI og PDF uden schema- eller migrationsspor.
- Single-file drift bevares, fordi den indlejrede SVG stadig er sidste fallback.
- JSON/bound-file bevarer brugerlogoet uden nye eksportformater.
- Audit undgaar store base64-payloads og meningsloese logo-only entries.

### Negative
- `users`-payloaden udvides, saa slicen skal behandles som en Class C-aendring under governance.
- CSV-import/export for brugere bevarer ikke logoet, fordi `schemaFields.users` bevidst er uaendret.
- Store PNG-filer kan bloate JSON-backups, saa upload holdes til PNG og max 1 MiB.

## Follow-up
- Bevar selvtest for header-prioritet, PDF-prioritet, backup/restore og audit-sanitization.
- Hold eventuelle fremtidige udvidelser af brugerlogo-format eller global branding i et separat ADR-spor.
