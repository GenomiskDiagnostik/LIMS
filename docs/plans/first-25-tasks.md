# First 25 Tasks

1. Importér faktisk `GlimR.html` i repoet.
2. Opret versionsmærket baseline-release af nuværende fil.
3. Tag checksum af baseline build.
4. Kortlæg hovedfaner, modaler, eksportfunktioner og storage-touchpoints.
5. Opret golden dataset med patienter, familier, prøver, ordinationer, varianter og rapporter.
6. Beskriv de 20 vigtigste brugerflows.
7. Identificér alle steder hvor `MRN` optræder i UI, storage og eksport.
8. Identificér alle steder hvor `PMB` optræder i UI, storage og eksport.
9. Kortlæg felttyper for `PMB`, `size_bp` og `copy_number`.
10. Opret central validator for PMB (12 cifre, heltal).
11. Opret central validator for CPR (`DDMMYY-XXXX`) med parser for født/køn.
12. Design migrationsstrategi fra MRN til CPR uden datatab.
13. Design admin-setting for kræv unikke prøver og patienter.
14. Implementér test for dobbelt PMB/dobbelt CPR.
15. Implementér smoke tests for backup/restore og autosave.
16. Kortlæg PDF-generering og rapporttemplate-flow.
17. Implementér regressionstest for rapport-PDF med fixtures.
18. Implementér lav-risiko UI batch: eksportantal, tooltips, klikbare KPI'er.
19. Implementér ordinationsgenveje til Patient og Familie.
20. Gør adminbokse collapsible og default-minimerede.
21. Tilføj SVG fallback for logo samt hover credits.
22. Specificér AI-adapter interface og settings model uden netværkskode endnu.
23. Specificér i18n resource model med dansk fallback.
24. Skriv inline annotationsstandard for `GlimR.html`.
25. Forbered første change set og release note efter grøn regression.
