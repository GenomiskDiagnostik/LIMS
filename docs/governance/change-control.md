# Change Control

## Formål
Sikre at ændringer i GlimR er sporbare, reversible og risikovurderede.

## Roller
- **Product owner**: prioriterer og godkender scope
- **Technical lead**: vurderer arkitektur og implementeringsstrategi
- **Quality owner**: godkender test og release-gates
- **Developer/agent**: udfører ændringen og dokumenterer påvirkning

## Change classes
- C1 Bugfix
- C2 Additiv UX-forbedring
- C3 Domæne-/datavalidering
- C4 Integration
- C5 Arkitekturændring
- C6 Sikkerhedsændring

## Obligatorisk change request
Hver change request skal indeholde:
- problem
- ønsket outcome
- berørte områder
- risikoklasse
- rollback-idé
- acceptance criteria
- testplan
- dokumentopdateringer

## Risikoklasser
- **Low**: lokal UI-forbedring uden schema/dataændring
- **Medium**: ændring i validering, eksport eller PDF
- **High**: storage, auth, AI, online integrationer, migration, i18n, analysemoduler

## Change gates
### Før implementering
- backlog-ID findes
- acceptance criteria findes
- risikovurdering udført

### Før merge
- testplan gennemført
- dokumentopdateringer udført
- regression vurderet

### Før release
- release note klar
- rollback-plan klar
- godkendelse fra product owner + quality owner

## Forbudte ændringer
- skjult omdøbning af domænefelter uden migration
- direkte netværksafhængighed i kritisk offline flow
- AI-skrivning direkte til kliniske felter uden brugerreview
- breaking UI-ændringer uden ændringsgodkendelse
