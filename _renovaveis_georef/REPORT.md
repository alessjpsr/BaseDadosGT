# Renewable georeferencing — coverage report

Case: PDE34 Caso Base SDDP (D:\Modelos\BaseDadosGT\BaseDados) — 9,398 RenewablePlant objects.

## 1. Coordinates (`renewable_coordinates.csv`)

All 9,398 plants assigned a coordinate. Precision tiers:

| Tier | Meaning | Plants |
|---|---|---:|
| `plant` | Plant-precise (reference / ANEEL SIGA) | 3,104 |
| `bus-proxy` | Connection-bus proxy (case network) | 1,623 |
| `aggregate-centroid` | State centroid (DG aggregate) | 4,515 |
| `uf-centroid` | State centroid (fallback) | 6 |
| `system-centroid` | Subsystem centroid (fallback) | 150 |
| | **Total** | **9,398** |

**3,104** are plant-precise (actual plant location); **1,623** use the connection substation; the rest are regional centroids for DG aggregates / generic future blocks.

### By technology

| Tech | plant | bus-proxy | centroid | total |
|---|---:|---:|---:|---:|
| Biomass | 351 | 391 | 4 | 746 |
| General | 0 | 0 | 2216 | 2216 |
| SmallHydro | 855 | 410 | 0 | 1265 |
| Solar | 741 | 245 | 2343 | 3329 |
| Wind | 1157 | 577 | 108 | 1842 |

## 2. Wind turbines (`wind_turbines.csv`)

- Wind plants: **1,842** = 1,158 identifiable EOL farms + 684 generic `ENE` expansion blocks.
- Turbine specs matched (ANEEL SIGEL Aerogeradores): **1,151/1,158 (99%)** of identifiable farms.
- Hub height (`hub_height_m`): min 44 / mean 100 / max 135 m.
- Rotor diameter: min 40 / mean 124 / max 170 m.
- Per farm: turbine count, unit power (MW), hub height, rotor diameter, total height. No commercial model/manufacturer field exists in the source; physical turbine parameters are provided.
- The 684 `ENE` blocks are year-duplicated capacity placeholders (no specific farm) → left blank; a representative modern turbine can be assigned if desired.

## 3. Sources

- Reference registry: `PSRGndPlant_SDDP.xlsx` (your PDE34 _Manual/C12 tree).
- ANEEL SIGA (empreendimentos de geração) — CEG + coordinates.
- ANEEL SIGEL `Parques_Eólicos/Aerogeradores` — per-turbine hub height, rotor, power (17,012 turbines → 1,631 farms).
- Case network: connection-bus coordinates for future/generic blocks.
