# First Codex Prompt

Læs først hele repository-dokumentationen før du foreslår kodeændringer:
- README.md
- AGENTS.md
- PLANS.md
- docs/product/prd.md
- docs/architecture/system-architecture.md
- docs/governance/change-control.md
- docs/governance/regression-strategy.md
- docs/backlog/feature-inventory-and-gap-analysis.md

Opgave:
1. Lav en plan-først analyse af GlimR med nul-regressionsfokus.
2. Opdatér PLANS.md med konkret status, afhængigheder og næste milepæl.
3. Kortlæg moduler, storage-paths, eksportfunktioner og PDF-flow.
4. Identificér hvilke ønskede funktioner der allerede findes, hvilke der mangler, og hvilke der er højrisko.
5. Foreslå en phased implementation plan i små reviewbare slices.
6. Udled de første konkrete testcases for:
   - PMB-validering
   - CPR-validering
   - backup/restore
   - PDF-generering
   - eksport af filtrerede elementer
7. Foreslå de første 5 ændringer som giver høj værdi og lav risiko.
8. Undgå store rewrites.
9. Bevar single-file output som distributionsmål.
10. Notér antagelser og risici eksplicit.

Outputformat:
- Assumptions
- Current architecture snapshot
- Verified vs unverified functionality
- Risks
- Dependency map
- Proposed slices
- Test plan
- Suggested next commit
