# Udbudsbeskrivelse – GlimR eller identisk funktionelt produkt

## 1. Formål
Ordregiver ønsker at anskaffe videreudvikling, overtagelse eller eventuel nyimplementering af et browserbaseret, offline-first LIMS til genetisk diagnostik med funktionel paritet til GlimR.

## 2. Overordnet produktbeskrivelse
Løsningen skal:
- kunne anvendes i moderne browser
- kunne drives lokalt uden server som minimumsdrift
- kunne lagre data lokalt
- understøtte patienter, familier, prøver, ordinationer, varianter, rapporter og audit
- understøtte eksport, backup og rapport-PDF
- have stærk fokus på sporbarhed og kontrolleret videreudvikling

## 3. Minimumskrav (skal-krav)
### Drift
- Offline-first drift
- Browserbaseret UI
- Single-file deployment som minimum understøttet leveranceform
- Lokal persistence med backup/restore

### Domæne
- Patient-, familie-, prøve-, ordinations-, variant- og rapportmoduler
- Audit log
- Brugeradministration
- Lokal eksport/import
- PDF-rapportering

### Datavalidering
- PMB skal kunne håndhæves som 12-cifret heltal
- CPR-format skal valideres
- Unikhedskrav for nøglefelter skal kunne konfigureres

### Governance
- Leverandør skal levere dokumentation, teststrategi og release-proces
- Koden skal være overtagningsvenlig
- Kritiske ændringer skal kunne feature-flages
- Leverandør skal levere annoteret kode eller tilsvarende systematisk dokumentation

## 4. Bør-krav
- Lokale AI-integrationer (fx Ollama/LM Studio)
- Online AI-provider integration
- Sprogpakker
- Per-bruger temaer
- Analyse-modul med NGS-opsætning
- Genome browser-funktioner
- Revurderingsadvarsler i variantbibliotek
- CSV-lookup til hjælpefelter

## 5. Høj-risiko optioner (skal prissættes separat)
- Online SQL persistence
- FTP-baseret databaseanvendelse
- Tvungen inkognito/private mode
- Kryptering af ekstern lokal database
- Fuld multilanguage-leverance for 15+ sprog
- Analyse-modul med visualisering og splice-vurdering

## 6. Leverancer
### Basisleverance
- Kildekode
- Bygbar release-proces
- Produktionsklar `GlimR.html` eller funktionelt identisk leverance
- Dokumentation
- Testpakke
- Changelog
- Arkitekturdiagram
- Overtagelsesdokumentation

### Dokumentpakke
- README
- PRD
- arkitekturdokument
- teststrategi
- release-proces
- backlog/gap-analyse
- administratorvejledning
- brugervejledning

## 7. Acceptance criteria
Tilbudsgiver skal beskrive hvordan følgende verificeres:
1. eksisterende funktionalitet bevares
2. backup/restore virker
3. PDF-generering virker
4. PMB/CPR validering virker
5. filtrering og eksport virker
6. audit trail virker
7. lokal drift uden backend virker

## 8. Kompetencekrav til leverandør
- dokumenteret erfaring med browserbaserede forretningssystemer
- erfaring med offline/local-first arkitektur
- erfaring med test og change governance
- gerne erfaring med medicoteknisk eller laboratorienær software
- kompetence inden for datasikkerhed og integrationsdesign

## 9. Estimeret prisramme (planlægningsestimat, ikke bindende markedspris)
### Model A – Sikker videreudvikling af eksisterende løsning
- Discovery, baseline, governance, testgrundlag: **DKK 180.000 – 350.000**
- P0/P1 forbedringer og datavalidering: **DKK 250.000 – 550.000**
- Dokumentation, annotation og releasehåndværk: **DKK 120.000 – 250.000**
- Samlet realistisk startpakke: **DKK 550.000 – 1.150.000**

### Model B – Videreudvikling inkl. integrationsspor
- Model A plus AI, i18n-pilot, CSV lookup, sikkerhedsspor: **DKK 1.100.000 – 2.200.000**

### Model C – Funktionelt identisk nyimplementering
- Kravafklaring og discovery: **DKK 300.000 – 700.000**
- Kernesystem med parity på centrale moduler: **DKK 2.000.000 – 4.500.000**
- Integrationsspor, analysemodul og bred i18n: **DKK 1.500.000 – 3.500.000**
- Samlet nyimplementering: **DKK 3.800.000 – 8.700.000**

## 10. Prisforudsætninger bag estimat
Estimatet forudsætter:
- dansk/europæisk senior profil-mix
- governance, test og dokumentation er reelle leverancer
- klinisk konservativ udviklingsstil
- små releases fremfor cowboykodning fredag kl. 16:57

## 11. Evalueringskriterier
- funktionel forståelse
- governance og testmodenhed
- overtagningsvenlighed
- leveranceplan
- totaløkonomi
- risikoforståelse
- dokumentationskvalitet

## 12. Anbefalet udbudsstrategi
Del leverancen i 2 trin:
1. **Discovery + baseline + governance**
2. **Efterfølgende implementeringsaftale**

Det reducerer risikoen markant og gør det muligt at verificere faktisk produktomfang før der loves guld og grønne genome browsers.
