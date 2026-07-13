# Network georeferencing — Bus / Thermal / Hydro

Case: PDE34 Caso Base SDDP. All coordinates in valid Brazil range; spot-checks (ITAIPU, FURNAS, ANGRA, GNA, Cubatão) verified.

## Buses (13,188) — 13185/13188 georeferenced

| Source / tier | Count |
|---|---:|
| topology interpolation (network neighbors) | 7212 |
| already in case | 5905 |
| PSRBus reference | 68 |
| none (isolated) | 3 |

## Thermal (255) — 255/255 georeferenced

| Source / tier | Count |
|---|---:|
| connection substation (real bus) | 121 |
| ANEEL SIGA by name (precise) | 67 |
| ANEEL SIGA fuzzy (former-name/capacity) | 33 |
| connection substation (interpolated bus) | 32 |
| subsystem centroid (fallback) | 2 |

## Hydro (176) — 176/176 georeferenced

| Source / tier | Count |
|---|---:|
| ANEEL SIGA by name (precise) | 122 |
| connection substation (real bus) | 40 |
| ANEEL SIGA fuzzy (former-name/capacity) | 6 |
| subsystem centroid (fallback) | 6 |
| connection substation (interpolated bus) | 2 |

## Method

- **Thermal & Hydro**: reference `PSR*Plant_SDDP.xlsx` coord columns were **empty**, so — ANEEL SIGA by normalized name (incl. former `ANTIGA` names, capacity-disambiguated) → connection-bus proxy → subsystem centroid.
- **Buses**: `PSRBus_SDDP.xlsx` + existing case coords as anchors (5,973), then **topology interpolation** through the 18,204-branch network (wave-fill + smoothing) for the rest. `interpolated` are approximate.
- Provenance is per-row in the `confidence` column so any tier can be refined later.
- Residuals (small/fictitious: NORTEFLU, JAGUATIRI II, VIGARIO, TOCOS, CALHA-CEDAE, Jordao Fic01…) sit at subsystem centroid.

Sources: ANEEL SIGA; EPE PSR*_SDDP.xlsx reference; case network topology.
