# Release Governance

## Release-typer
- **Patch**: fejlretning uden bevidst adfærdsændring
- **Minor**: additive features og valideringsforbedringer
- **Major**: arkitekturændringer, større migrationer eller nye hovedmoduler

## Releasepakke
Hver release skal mindst indeholde:
- `GlimR.html`
- version
- checksum
- changelog
- teststatus
- kendte begrænsninger
- rollback-reference
- dato og godkender

## Obligatoriske gates
1. Smoke tests grøn
2. Golden dataset gennemløbet
3. PDF-regression vurderet
4. Backup/restore testet
5. Eksport af mindst én filtreret liste verificeret
6. Kvalitetsejer godkendelse
7. Produktansvarlig godkendelse

## Pilotregler
Følgende må kun frigives som pilot eller bag feature flag:
- AI-autofill
- online SQL storage
- FTP databasebrug
- tvungen inkognito-mode
- Analyse-modul første version
- i18n ud over dansk + få pilot-sprog

## Rollback
Rollback skal være muligt ved:
- bevaret forrige release-fil
- bevaret kompatibel backup
- dokumenteret kendt schema-version

## Dokumentpligt
Efter hver release opdateres:
- README.md
- PLANS.md
- changelog
- relevante ADR'er ved arkitekturelle konsekvenser
