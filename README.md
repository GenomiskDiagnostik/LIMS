# <img width="90" height="90" alt="GlimR logo" src="https://github.com/user-attachments/assets/cfdd5b73-d477-477d-9ba6-acba4826ea60" /> GlimR – Genetic LIMS Reporter

GlimR is a self-contained, browser-based LIMS for genetic diagnostics. The full application ships as a single HTML file, runs entirely offline on IndexedDB, and can optionally mirror every change into a user-selected JSON file via the File System Access API for straightforward backups and sharing.

## Overview
- **Single-file deployment** – open `GlimR.html` directly in any modern Chromium-based browser; no servers, build steps, or installers required.
- **Offline-first persistence** – IndexedDB stores all data locally, with graceful fallback to in-memory mode and clear warnings if the browser blocks durable storage.
- **Role-aware workspace** – PIN-based login, per-entity write protection, and rich audit trails keep laboratory actions accountable.
- **Comprehensive data domains** – manage patients, families, samples, requisitions, variants, curated libraries, QC runs, reports, and responses from one interface.
- **Interoperability tooling** – generate PDF reports, exchange MedCom/FHIR bundles, export CSV/SQL/ZIP backups, and feed case plans into calendar clients through ICS.
- **Laboratory utilities** – use integrated ACMG classifiers, pedigree and consanguinity calculators, genome browser jump-offs, GC calculators, and sequencing helpers without leaving the app.
- **Built-in validation** – automated self-tests, audit logs, and database reset/backup flows reduce onboarding friction and support regulated operations.

## Feature tour

### Dashboard and planning
- KPI dashboard summarising patient/sample/order volumes, response times, backlog composition, and assignments for the signed-in user.
- Timeline cards for newest, oldest, and assigned requisitions with shortcuts into the relevant tabs.
- Personal radar showing overdue items, upcoming milestones, and subscription alerts for requisitions you follow.
- Planner workspace that organises requisitions into swimlanes for intake, QC, analysis, interpretation, approval, reporting, and response. Track stage progression, flag blockers, add structured notes, bulk-adjust deadlines, export filtered boards to ICS/CSV, and trigger follow-up reminders.

### Case intake and registration
- **Create case wizard** – collapsible sections for patient, sample, control sample, requisition, QC metrics, and variant entry. Supports VarSeq CSV import, automatic status previews, dynamic validation based on variant type, and batch creation of QC rows or variants.
- **Patients tab** – advanced filters (MRN, family number, indication, birth year, gender), age calculations, family-number pickers, CSV export, and inline audit of who created each patient.
- **Family manager** – dedicated family menu that groups probands and relatives, displays relationship matrices, draws editable pedigrees, synchronises affection statuses, and pushes inheritance assumptions back into variant review.
- **Samples tab** – active-status toggle, PMB uniqueness checks, cross-links into Orders/Reports, auto-synchronisation of sample status back to linked requisitions, date filtering, and CSV export.
- **Panel registry** – maintain versioned gene panels with automatic version increments, gene counting, searchable descriptions, and text exports summarising gene lists for clinical communication.

### Order execution and interpretation
- **Orders tab** – multi-criteria filtering (assignment roles, patient groups, HPO terms, date ranges), quick shortcuts to related samples/reports, automatic propagation of sample statuses, and CSV export with creator metadata.
- **Variant tracking** – capture SNV, CNV, structural, mitochondrial, and cytogenetic variants with specialised fields; batch entry, library lookups, VarSeq ingestion, ACMG classification helpers, and promotion of curated evidence into the shared variant library.
- **Variant library** – curate findings with extensive metadata (genomic range, ISCN, inheritance, evidence, review dates). Includes CSV import/export, powerful faceted search, genome browser with hotspot overlays, and placeholder guides for reusing content in reports.
- **Conclusion library** – manage reusable text blocks with placeholder guidance so patient, sample, and variant details merge automatically during report drafting.
- **Reports workspace** – filter by requisition/sample/status, assemble narrative sections, insert standard texts, select variants, maintain publication history, preview outputs, and export polished PDFs with logos and section layouts.

### Quality, utilities, and interoperability
- **QC module** – register assay metrics per sample, filter active specimens, and keep laboratory performance notes alongside requisition data.
- **Toolbox** – ACMG/AMP criteria selector with strength adjustments, automated storytelling, consanguinity estimator with pedigree diagrams, population baselines, sequencing coverage planners, genome-browser launchers, GC and sequence utilities, BLAST shortcuts, and more.
- **MedCom/FHIR tab** – import external bundles to log responses (with optional conversion into variant library entries) and generate outbound diagnostic report bundles for any requisition, complete with preview/download controls.
- **Users & audit** – manage staff accounts, roles, and PINs; inspect chronological audit logs for every CRUD action across entities.
- **Database & backup** – bind to local files, toggle autosave, trigger manual writes, export JSON backups, restore from files, or perform safeguarded resets that first capture a backup.
- **Administration** – load demo data, download SQL schemas, assemble distributable ZIP archives, and maintain patient-group catalogues that feed into orders and reporting filters.
- **Self-test** – run automated smoke tests that create data, generate reports, build FHIR bundles, produce ZIP/SQL exports, and then restore the original dataset.

### Import and export options
- **Case intake** – load patients, samples, and variants via VarSeq CSV or curated library CSV templates.
- **Variant intelligence** – import hotspot lists and structural variant datasets; export filtered variant grids, hotspot definitions, and curated reviews as CSV/JSON for downstream tools.
- **Reporting** – generate PDF reports, MedCom/FHIR bundles, and shareable case summaries as HTML or Markdown snippets.
- **Planning** – export Planner boards, task lists, and ownership matrices as ICS, CSV, or JSON snapshots.
- **Data management** – perform incremental JSON writes, full JSON backups, SQL schema exports, ZIP archives, and per-entity CSV dumps across patients, samples, orders, QC rows, and audit logs.

## Getting started
1. **Clone or download** this repository and keep `GlimR.html` (plus the optional logo) together in the same folder. Replace the logo by placing a `logo.png` next to the HTML file.
2. **Open the application** by double-clicking `GlimR.html` or using *File → Open* in a supported browser. The first launch provisions IndexedDB tables, seeds caches, and displays the dashboard.
3. **Log in** by creating a user under *Users* or loading demo data to unlock the default administrator credentials (`Admin / admin`).
4. **(Optional) Bind a data file** from *Database & Backup* using **Bind/Open DB file...** to persist changes into a chosen JSON file. Enable **Auto-save** for continuous flushing.
5. **Back up your data** with **Download backup (JSON)**, **Download glimr.sql**, or **Download ZIP**. Restore by selecting a previous JSON export in the same tab.
6. **Run the self-test** from the *Self-test* tab to validate CRUD, reporting, FHIR exchange, and backup features in your environment.

## Browser requirements
GlimR relies on IndexedDB, modern ES2020 JavaScript, and the File System Access API. Use an up-to-date Chromium-based browser (Chrome, Edge, Arc, Brave). Safari can operate in in-memory mode but cannot bind to local files.

## License
This project is distributed under the MIT License. See `LICENSE` for details.

---

## Dansk beskrivelse

GlimR er et selvstændigt, browserbaseret LIMS til genetisk diagnostik. Hele applikationen lever i én HTML-fil, kører offline i IndexedDB og kan spejle alle ændringer til en valgfri JSON-fil via File System Access API'et for nem backup og deling.

## Oversigt
- **Udrulning i én fil** – åbn `GlimR.html` direkte i en moderne Chromium-browser uden servere, build-processer eller installationer.
- **Offline-første persistens** – IndexedDB gemmer alle data lokalt; hvis browseren blokerer lagring, falder GlimR tilbage til hukommelsestilstand og viser tydelige advarsler.
- **Rollebevidst arbejdsflade** – PIN-login, skrivebeskyttelse per entitet og udførlige revisionslogger sikrer sporbarhed i laboratoriet.
- **Dækkende datasæt** – håndter patienter, familier, prøver, ordinationer, varianter, kuraterede biblioteker, QC-målinger, rapporter og svar ét sted.
- **Interoperabilitet** – generér PDF-rapporter, udveksl MedCom/FHIR-bundter, eksportér CSV/SQL/ZIP-backups og læg arbejdsplaner i kalenderen via ICS.
- **Laboratorieværktøjer** – brug indbyggede ACMG-værktøjer, stamtræs- og konsangvinitetsberegner, genombrowser-genveje, GC-udregnere og sekvenshjælpere uden at forlade appen.
- **Indbygget validering** – selvtest, revisionslog og backup-/reset-flow understøtter onboarding og kvalitetskrav.

## Funktioner

### Dashboard og planlægning
- KPI-dashboard med overblik over volumener, svartider, backlog og personlige opgaver.
- Kort over nyeste, ældste og tildelte ordinationer med genveje til relevante faner.
- Personligt radaroverblik med forsinkede opgaver, kommende milepæle og abonnementer på ordinationer du følger.
- Planlægningsmodul der organiserer ordinationer i svømmeaner for modtagelse, QC, analyse, tolkning, godkendelse, rapportering og svar. Følg progression, marker blokeringer, tilføj strukturerede noter, masseopdater deadlines, eksportér filtrerede boards til ICS/CSV og udsend opfølgningspåmindelser.

### Sagsoprettelse og registrering
- **Sagswizard** – fold-ud sektioner til patient, prøve, kontrol, ordination, QC og varianter. Understøtter VarSeq-CSV, statusforhåndsvisning, dynamisk validering efter varianttype samt batch-oprettelse af QC-målinger og varianter.
- **Patientfane** – avancerede filtre (MRN, familienummer, indikation, fødselsår, køn), aldersberegning, familienummer-vælger, CSV-eksport og visning af hvem der har oprettet posten.
- **Familiefane** – samler probander og pårørende, viser relationsmatrix, tegner redigerbare stamtræer, synkroniserer affektionsstatus og sender arveantagelser videre til variantgennemgang.
- **Prøvefane** – filter for aktive prøver, kontrol af unikke PMB-numre, genveje til ordinationer/rapporter, automatisk synkronisering af status tilbage til ordinationer, datofilter og CSV-eksport.
- **Panelforvaltning** – vedligehold versionerede genpaneler med automatisk versionshåndtering, genoptælling, søgbare beskrivelser og teksteeksport til kommunikation.

### Analyse og tolkning
- **Ordinationsfane** – filtrering på roller, patientgrupper, HPO-termer og datoer, genveje til prøver/rapporter, automatisk opdatering af prøvestatus og CSV-eksport med historik for opretter.
- **Variantregistrering** – understøtter SNV, CNV, strukturelle, mitokondrielle og cytogenetiske varianter med specialfelter, batch-indtastning, biblioteksopslag, VarSeq-import, ACMG-hjælp og mulighed for at løfte varianter over i biblioteket.
- **Variantbibliotek** – kuratér fund med metadata (genom, ISCN, arvegang, evidens, reviewdato). Indeholder CSV-import/-eksport, kraftig filtrering, genombrowser med hotspot-overlays og pladsholder-guide til brug i rapporter.
- **Standardtekster** – administrér genbrugstekster med pladsholdere så patient-, prøve- og variantdata flettes automatisk under rapportudarbejdelse.
- **Rapportværksted** – filtrér på ordination/prøve/status, sammensæt afsnit, indsæt standardtekster, vælg varianter, styr publiceringsstatus, få forhåndsvisning og eksportér PDF med logo og layout.

### Kvalitet, værktøjer og interoperabilitet
- **QC-modul** – registrér målinger per prøve, filtrér aktive prøver og behold laboratorienoter sammen med ordinationsdata.
- **Værktøjskasse** – ACMG/AMP-kriterievælger, automatiske fortællinger, konsangvinitetsestimator med stamtræ, populationsbaseline, sekventeringsplanlægger, genome-browser-genveje, GC- og sekvensværktøjer, BLAST m.m.
- **MedCom/FHIR** – importér eksterne bundter (med mulighed for at overføre varianter til biblioteket) og generér udgående diagnostik-svar for enhver ordination med forhåndsvisning/download.
- **Brugere & revision** – håndtér brugerkonti, roller og PINs; inspicér kronologisk revisionslog for alle CRUD-handlinger.
- **Database & backup** – knyt lokale filer, slå autogem til/fra, gem manuelt, hent JSON-backups, gendan fra filer eller udfør sikker reset med automatisk backup først.
- **Administration** – indlæs demodata, download SQL-skema, lav distribuerbare ZIP-arkiver og vedligehold patientgrupper til ordinationer og rapportfiltre.
- **Selvtest** – kør automatiserede tests der opretter data, genererer rapporter, bygger FHIR-bundter, producerer ZIP/SQL-eksporter og genskaber udgangspunktet bagefter.

### Import og eksport
- **Sagsoprettelse** – indlæs patienter, prøver og varianter via VarSeq-CSV eller kuraterede biblioteksskabeloner.
- **Variantviden** – importér hotspot-lister og strukturelle variantdatasæt; eksportér filtrerede varianttabeller, hotspot-definitioner og kuraterede vurderinger som CSV/JSON til andre systemer.
- **Rapportering** – generér PDF-rapporter, MedCom/FHIR-bundter samt delbare sagsresuméer som HTML eller Markdown.
- **Planlægning** – eksportér planlægningsboards, opgavelister og ansvarsoversigter som ICS, CSV eller JSON.
- **Datastyring** – foretag inkrementelle JSON-skrivninger, komplette JSON-backups, SQL-skema-eksporter, ZIP-arkiver og CSV-dumps per entitet (patienter, prøver, ordinationer, QC, revisionslog).

## Kom godt i gang
1. **Hent repoet** og placér `GlimR.html` (samt evt. logo) i samme mappe. Udskift logoet ved at lægge `logo.png` ved siden af HTML-filen.
2. **Åbn applikationen** ved at dobbeltklikke `GlimR.html` eller via *File → Open* i en understøttet browser. Første opstart opretter IndexedDB-tabeller, indlæser caches og viser dashboardet.
3. **Log ind** ved at oprette en bruger under *Brugere* eller indlæse demodata for at få administratorlogin (`Admin / admin`).
4. **(Valgfrit) Knyt datafil** under *Database & Backup* med **Knyt/åbn DB-fil...** for at gemme ændringer i en selvvalgt JSON-fil. Aktivér **Autogem** for løbende skrivning.
5. **Tag backup** med **Hent backup (JSON)**, **Hent glimr.sql** eller **Hent ZIP**. Gendan ved at vælge en tidligere JSON-backup i samme fane.
6. **Kør selvtesten** fra *Selvtest*-fanen for at verificere CRUD, rapportering, FHIR og backup-flow i dit miljø.

## Browserkrav
GlimR kræver IndexedDB, moderne ES2020-JavaScript og File System Access API. Brug en opdateret Chromium-baseret browser (Chrome, Edge, Arc, Brave). Safari kan køre i hukommelsestilstand men understøtter ikke filbinding.

## Licens
Projektet distribueres under MIT-licensen. Se `LICENSE` for detaljer.
