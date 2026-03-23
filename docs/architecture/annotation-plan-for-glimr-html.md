# Annotation Plan for GlimR.html

## Status
Kildekoden er ikke tilgængelig i denne pakke. Derfor leveres her en konkret annoteringsstandard i stedet for direkte annotation af filen.

## Mål
Gøre `GlimR.html` overtagelig uden at ændre funktionalitet.

## Annoteringsregler
Hver større funktion/sektion skal have:
- formål
- input/output
- afhængigheder
- storage side effects
- eksport/PDF side effects
- kendte begrænsninger
- relaterede feature flags
- relaterede backlog-ID'er

## Eksempel på kommentarskabelon
```html
<!--
Module: OrdersQuickLinks
Purpose: Render shortcut icons from Orders rows to related Sample, Report, Patient, Family.
Inputs: order record, linked patient/sample/report/family ids
Outputs: clickable icon buttons
Storage side effects: none
Risks: broken navigation if linked IDs are missing
Backlog: B-001
-->
```

## Prioriteret annoteringsrækkefølge
1. bootstrap/init
2. storage/indexeddb/file-mirror
3. auth/users/pin
4. orders/patients/samples/families
5. variants/report/pdf
6. admin/settings
7. imports/exports
8. AI/integration points
9. analysis/toolbox modules

## Definition of done
- alle hovedfaner annoteret
- alle storage-write paths annoteret
- alle eksportpunkter annoteret
- alle integrationspunkter annoteret
- top 20 flows kan forstås uden mundtlig overlevering
