# <img width="90" height="90" alt="GlimR logo" src="https://github.com/user-attachments/assets/cfdd5b73-d477-477d-9ba6-acba4826ea60" /> GlimR – Genetic LIMS Reporter

GlimR er et selvstændigt, browserbaseret LIMS til genetisk diagnostik. Hele applikationen lever i én HTML-fil, kører offline i browserens IndexedDB og kan valgfrit skrive til en lokal JSON-fil via File System Access API'et for nem backup og deling. 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L4139-L4162】

## Oversigt
- **Fuld klientapplikation i én fil** – ingen build- eller serverafhængigheder; åbn `GlimR.html` direkte i en moderne Chromium-baseret browser (Chrome, Edge eller Arc). Initialisering laster databasen, rekonstruerer caches og viser dashboardet. 【F:GlimR.html†L15224-L15236】
- **Lokal persistens** – data gemmes i IndexedDB. Hvis browseren blokerer IndexedDB, falder GlimR tilbage til midlertidig in-memory-lagring og viser en tydelig advarsel. 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L14500-L14508】
- **Filbaseret backup** – bind en JSON-fil og aktiver autogem for løbende at skrive alle datatabeller til fil. Manuelle backups kan downloades som JSON, SQL eller ZIP-arkiv via adminfanen. 【F:GlimR.html†L4139-L4162】【F:GlimR.html†L4210-L4270】【F:GlimR.html†L14530-L14575】【F:GlimR.html†L15106-L15168】

## Hovedfunktioner
### Overblik og planlægning
- Dashboard med KPI'er, statuskort, revisionslog og hurtige tabeller over nye, ældste og egne ordrer; indeholder også en udskriftsvenlig rapportgenerator. 【F:GlimR.html†L4882-L5134】
- Kanban-lignende planlægningsværktøj, der udleder opgaver per ordination (QC, analyse, tolkning, godkendelse, rapportering, svar) med deadlines, noter og ICS-eksport til kalender. 【F:GlimR.html†L11770-L12344】

### Sagsoprettelse og datahåndtering
- Guidet formular til at oprette komplette sager inkl. patient, prøve, kontrolprøve, ordination, QC-målinger og varianter – understøtter bl.a. VarSeq-import og dynamiske krav baseret på varianttype. 【F:GlimR.html†L5263-L5759】
- Fanevisninger for patienter, prøver og ordinationer med avancerede filtre, eksport til CSV, rolle- og statusoversigter samt hurtige genveje til relaterede data. 【F:GlimR.html†L6237-L6337】【F:GlimR.html†L6628-L6707】【F:GlimR.html†L7166-L7726】

### Variant- og rapportstyring
- Variantregister med fuldtekst- og facetteret søgning, filtrering på varianttype/ACMG-kriterier samt eksport. Formularen håndterer SNV, CNV, strukturelle og cytogenetiske varianter med relevante felter. 【F:GlimR.html†L7816-L8371】
- Variantbibliotek til kuraterede fund med metadata om evidens, nedarvning, frekvensberegninger og CSV-import/-eksport. 【F:GlimR.html†L8701-L9099】
- Bibliotek over standardtekster med placeholder-guide, rapporteditor der kan indsætte tekstblokke, vælge varianter og styre rapportstatus samt variantkopiering til rapporter. 【F:GlimR.html†L9595-L9710】【F:GlimR.html†L9901-L9998】

### Kvalitet, svar og hjælpeværktøjer
- QC-modul til registrering af laboratoriemålinger og filtrering på aktive prøver. 【F:GlimR.html†L11464-L11634】
- FHIR/MedCom-fane til at importere eksterne svarbundter, generere outbound FHIR-dokumenter for valgte ordinationer og forhåndsvise JSON. 【F:GlimR.html†L14120-L14260】
- Omfattende værktøjskasse: ACMG/AMP-kriterievælger med styrkemodificering, automatiske beregninger og storytelling, konsangvinitetsberegner med pedigree-diagrammer, genetiske opslagsværktøjer (BLAST, genom-browsere), GC-beregner, sekvensværktøjer m.m. 【F:GlimR.html†L12494-L13684】【F:GlimR.html†L13596-L13639】

### Administration og drift
- Bruger- og rolleadministration, inklusive PIN-login, logud og rollebaseret skriveadgang. 【F:GlimR.html†L1983-L2006】【F:GlimR.html†L14351-L14515】
- Automatisk revisionslog af alle CRUD-handlinger og reset-funktion, der først tager backup og derefter rydder data (undtagen brugere). 【F:GlimR.html†L4100-L4123】【F:GlimR.html†L4215-L4275】
- Databasefanen håndterer binding til lokal fil, autogem, manuelt gem, JSON-backup, restore og nødrens. 【F:GlimR.html†L14530-L14575】
- Adminfane til demo-data, SQL/ZIP-eksport og vedligehold af patientgrupper, som bruges i ordinationer. 【F:GlimR.html†L15145-L15168】【F:GlimR.html†L14554-L14640】
- Selvtest-fane, der kan køre en automatiseret sanity check og rapporterer resultatet i UI'et. 【F:GlimR.html†L14746-L14820】

## Kom godt i gang
1. **Hent repoet** – klon eller download ZIP, og placer `GlimR.html` og logo (valgfrit) i samme mappe. Logoet kan udskiftes ved at lægge `logo.png` ved siden af filen. 【F:GlimR.html†L15184-L15218】
2. **Åbn applikationen** – dobbeltklik `GlimR.html` eller åbn filen via `File → Open` i browseren. Første opstart opretter IndexedDB-tabeller og loader alle caches. 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L15224-L15236】
3. **Log ind** – opret en bruger under *Brugere*, eller indlæs demodata for at få en administratorkonto (`Admin / admin`). 【F:GlimR.html†L14351-L14436】【F:GlimR.html†L15145-L15162】
4. **(Valgfrit) Bind datafil** – gå til *Database & Backup* og tryk **Knyt/åbn DB-fil...** for at gemme data i en selvvalgt JSON-fil. Aktivér *Autogem* for automatisk skrivning efter ændringer. 【F:GlimR.html†L14530-L14547】
5. **Tag backup** – brug **Hent backup (JSON)**, **Hent glimr.sql** eller **Hent ZIP** efter behov. Restore understøtter JSON-eksporten fra samme fane. 【F:GlimR.html†L4210-L4243】【F:GlimR.html†L14548-L14575】【F:GlimR.html†L15106-L15135】
6. **Kør selvtest** (valgfrit) via *Selvtest*-fanen for at bekræfte, at CRUD-operationer og exports fungerer i miljøet. 【F:GlimR.html†L14746-L14857】

## Browserkrav
GlimR udnytter IndexedDB, moderne ES2020-JavaScript og File System Access API. Anvend derfor en opdateret Chromium-baseret browser. Safari understøtter ikke filbinding, men kan køre i in-memory-tilstand (uden persistente data). 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L4139-L4162】

## Licens
Projektet distribueres under MIT-licensen. Se `LICENSE` for detaljer.
