# Regression Strategy

## Princip
GlimR må ikke regressere i klinisk eller driftskritisk funktionalitet.

## Testlag
### 1. Smoke tests
- login
- oprettelse/redigering/sletning
- filtrering
- eksport
- PDF
- backup/restore
- lokal filbinding
- audit log

### 2. Golden dataset tests
Et fast datasæt skal bruges til:
- visning af patienter/familier/prøver/ordinationer
- variantbibliotek
- rapportudkast
- PDF-output
- CSV/JSON/SQL-eksport

### 3. Domænevalidering
- PMB 12-cifret heltal
- CPR format
- afledning af født/køn
- unikhedskrav
- integerfelter på variantdata

### 4. UI regression
- nøgleskærmbilleder
- synlige genveje
- adminsektioner
- KPI-navigation

### 5. Dokumentregression
- README og PRD i sync med implementeret scope
- udbudsdokument matcher godkendt målarkitektur

## Kritiske flows
1. Opret patient
2. Opret prøve
3. Opret ordination
4. Registrér variant
5. Opret rapport
6. Eksportér PDF
7. Tag backup
8. Gendan backup
9. Bind lokal DB-fil
10. Kør selvtest hvis tilgængelig

## Særligt følsomme områder
- PDF-layout
- datomasker og lokaliseret formatering
- storage sync
- migration fra MRN til CPR
- per-bruger tema og sprog
- AI-assisteret udfyldning

## Release-stop kriterier
- data-tab
- forkert PMB/CPR validering
- fejl i rapport-PDF
- backup/restore fejl
- manglende adgang til eksisterende data
- UI-flow hvor tidligere handling ikke længere kan gennemføres
