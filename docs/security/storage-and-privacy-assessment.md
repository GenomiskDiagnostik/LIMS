# Security and Privacy Storage Assessment

## Formål
Vurdér ønsket om at rydde browserens hukommelse ved autosave og alternative beskyttelser ved lokal drift.

## Arbejdskonklusion
Det bør **ikke** være standardstrategien at slette IndexedDB efter hver autosave som generel sikkerhedsmekanisme. Det kan underminere offline-first design, backup-flow og brugeroplevelse. Brug i stedet et eksplicit sikkert driftsmode.

## Realistiske designvalg
### Option A – Default local-first
- IndexedDB som primær store
- Valgfri mirror til lokal JSON-fil
- Tydelig backup/advarselstekst
- Anbefal dedikeret browserprofil eller inkognito for følsom brug

### Option B – Secure session mode
- Kræv privat/inkognito-session
- Brug session-lignende datahåndtering hvor muligt
- Gør bruger opmærksom på at data ikke forventes bevaret lokalt efter session

### Option C – Write-through mode (pilot)
- Skriv til valgt lokal fil
- Ryd lokal cache *efter* verificeret commit
- Kun hvis produktansvarlig accepterer reduceret offline-resiliens

## Anbefaling
1. Indfør admin-setting: “Anbefal privat/inkognito-tilstand”.
2. Indfør separat pilot-setting: “Kør i write-through mode uden varig lokal cache”.
3. Bevar default som nuværende offline-first, indtil risikoanalyse og brugerbehov er dokumenteret.
4. Krypter følsomme felter i eksternt lagrede metadata, men undgå falsk tryghed: nøglehåndtering skal være klar.

## Åbne spørgsmål
- Hvordan håndteres crash under write-through mode?
- Skal følsomme værdier overhovedet gemmes i ekstern lokal fil?
- Skal PIN erstattes af hash eller egentlig credential model?
- Skal file:// deployment fortsat være primær, eller bør IWA/PWA-hosting vurderes på sigt?
