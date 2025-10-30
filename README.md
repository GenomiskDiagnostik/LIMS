# <img width="90" height="90" alt="GlimR logo" src="https://github.com/user-attachments/assets/cfdd5b73-d477-477d-9ba6-acba4826ea60" /> GlimR – Genetic LIMS Reporter

GlimR is a self-contained, browser-based LIMS for genetic diagnostics. The entire application lives in a single HTML file, runs offline on IndexedDB, and can optionally write to a local JSON file through the File System Access API for easy backup and sharing. 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L4139-L4162】

<img width="1179" height="1156" alt="Skærmbillede 2025-10-30 1056562" src="https://github.com/user-attachments/assets/107638c6-f161-4aba-b6d8-fd441eb5d2a7" />

## Overview
- **Full client application in one file** – no build or server dependencies; open `GlimR.html` directly in any modern Chromium-based browser (Chrome, Edge, Arc). Startup initializes the database, rebuilds caches, and presents the dashboard. 【F:GlimR.html†L15224-L15236】
- **Local persistence** – data is stored in IndexedDB. If the browser blocks IndexedDB, GlimR falls back to temporary in-memory storage and shows a clear warning. 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L14500-L14508】
- **File-based backup** – bind a JSON file and enable auto-save to continuously flush all tables to disk. Manual backups can be exported as JSON, SQL, or ZIP archives from the admin tab. 【F:GlimR.html†L4139-L4162】【F:GlimR.html†L4210-L4270】【F:GlimR.html†L14530-L14575】【F:GlimR.html†L15106-L15168】

## Core features
### Overview and scheduling
- Dashboard with KPIs, status cards, audit log, and quick tables of new, oldest, and assigned orders; includes a print-friendly report generator. 【F:GlimR.html†L4882-L5134】
- Kanban-style planner that derives tasks per requisition (QC, analysis, interpretation, approval, reporting, response) with due dates, notes, and ICS export to calendar tools. 【F:GlimR.html†L11770-L12344】

### Case creation and data management
- Guided workflow to create complete cases including patient, specimen, control, requisition, QC metrics, and variants—supports VarSeq import and dynamic validation based on variant type. 【F:GlimR.html†L5263-L5759】
- Tabular views for patients, specimens, and requisitions with advanced filters, CSV export, role and status summaries, plus shortcuts to related data. 【F:GlimR.html†L6237-L6337】【F:GlimR.html†L6628-L6707】【F:GlimR.html†L7166-L7726】

### Variant and report management
- Variant registry with full-text and faceted search, filtering on variant type/ACMG criteria, and export capabilities. The editor handles SNV, CNV, structural, and cytogenetic variants with specialized fields. 【F:GlimR.html†L7816-L8371】
- Variant library for curated findings with metadata about evidence, inheritance, frequency calculations, and CSV import/export. 【F:GlimR.html†L8701-L9099】
- Standard text library with placeholder guidance, report editor for inserting text blocks, selecting variants, managing report status, and copying variants into reports. 【F:GlimR.html†L9595-L9710】【F:GlimR.html†L9901-L9998】

### Quality, responses, and utilities
- QC module for recording laboratory measurements and filtering active samples. 【F:GlimR.html†L11464-L11634】
- FHIR/MedCom tab for importing external response bundles, generating outbound FHIR documents for selected requisitions, and previewing JSON payloads. 【F:GlimR.html†L14120-L14260】
- Extensive toolbox: ACMG/AMP criteria selector with strength adjustments, automatic calculations and storytelling, consanguinity calculator with pedigree diagrams, genetic lookup helpers (BLAST, genome browsers), GC calculator, sequence utilities, and more. 【F:GlimR.html†L12494-L13684】【F:GlimR.html†L13596-L13639】

### Administration and operations
- User and role management including PIN login, logout, and role-based write access. 【F:GlimR.html†L1983-L2006】【F:GlimR.html†L14351-L14515】
- Automatic audit trail of all CRUD actions and a reset function that first takes a backup before wiping data (except users). 【F:GlimR.html†L4100-L4123】【F:GlimR.html†L4215-L4275】
- Database tab handles binding to local files, auto-save, manual save, JSON backup, restore, and emergency reset. 【F:GlimR.html†L14530-L14575】
- Admin tab for demo data, SQL/ZIP export, and maintenance of patient groups referenced by requisitions. 【F:GlimR.html†L15145-L15168】【F:GlimR.html†L14554-L14640】
- Self-test tab that runs an automated sanity check and surfaces the results directly in the UI. 【F:GlimR.html†L14746-L14820】

## Getting started
1. **Fetch the repository** – clone or download the ZIP, and keep `GlimR.html` and the optional logo in the same folder. You can replace the logo by adding `logo.png` next to the HTML file. 【F:GlimR.html†L15184-L15218】
2. **Open the application** – double-click `GlimR.html` or open it via `File → Open` in your browser. On first launch, IndexedDB tables are created and caches are loaded. 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L15224-L15236】
3. **Log in** – create a user under *Users* or load demo data to get an administrator account (`Admin / admin`). 【F:GlimR.html†L14351-L14436】【F:GlimR.html†L15145-L15162】
4. **(Optional) Bind a data file** – go to *Database & Backup* and click **Bind/Open DB file...** to persist data to a chosen JSON file. Enable *Auto-save* to flush changes automatically. 【F:GlimR.html†L14530-L14547】
5. **Back up data** – use **Download backup (JSON)**, **Download glimr.sql**, or **Download ZIP** as needed. Restores accept the JSON export from the same tab. 【F:GlimR.html†L4210-L4243】【F:GlimR.html†L14548-L14575】【F:GlimR.html†L15106-L15135】
6. **Run the self-test** (optional) from the *Self-test* tab to verify CRUD operations and exports in your environment. 【F:GlimR.html†L14746-L14857】

## Browser requirements
GlimR relies on IndexedDB, modern ES2020 JavaScript, and the File System Access API. Use an up-to-date Chromium-based browser. Safari does not support file binding but can operate in in-memory mode (without persistent data). 【F:GlimR.html†L3911-L3993】【F:GlimR.html†L4139-L4162】

## License
This project is distributed under the MIT License. See `LICENSE` for details.

---







## Dansk beskrivelse

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
