# Bird Sightings at Sea 🐦

Exploratory analysis of 49,000+ seabird sightings logged from ships in New Zealand and Australian waters between 1969 and 1990. Data sourced from Te Papa Tongarewa via the New Zealand government open data catalogue.

---

## Dataset

| | |
|---|---|
| **Source** | [At-Sea Observations of Seabirds 1969 to 1990](https://catalogue.data.govt.nz/dataset/at-sea-observations-of-seabirds-1969-to-1990) |
| **Article** | [OBIS Dataset — Tasman Sea, NZ and Australian waters](https://obis.org/dataset/29ea15ed-8f76-40ca-bd14-58c62e10b2ef) |
| **Period** | July 1969 – December 1990 |
| **Records** | 49,019 bird observations across 12,310 ten-minute ship counts |
| **Geography** | Southern hemisphere, latitudes −19° to −69°, centred on New Zealand and subantarctic waters |

The data was recorded by hand in ship logbooks following the Australasian Seabird Mapping Scheme guidelines. Each record captures the species seen, bird counts, behaviours observed, and the ship's position, speed, weather, and sea conditions at the time.

---

## Files

```
seabird-sightings-nz/
├── analyse.ipynb        # Main analysis notebook
├── birds.csv            # Bird observation records
├── ships.csv            # Ship position and environmental records
├── beaufort_scale.csv   # Beaufort wind scale lookup
├── sea_states.csv       # Sea state class lookup
└── README.md
```

---

## Analysis

The notebook walks through six phases:

**Phase 1 — Load and join**
Read `birds.csv` and `ships.csv`, join on `record_id`, and inspect structure and coverage.

**Phase 2 — Data quality**
Audit whether the free-text `species_common_name` logbook entries were correctly parsed into structured columns (`species_scientific_name`, `age`, `wan_plumage_phase`, `sex`). Key finding: Te Papa's parsing was perfectly consistent — zero mismatches on name, age, or plumage across 48,328 sightings.

**Phase 3 — Species and behaviour EDA**
Top species, flock size distributions, and what birds were actually doing. Nearly half of all sightings involved birds actively following or accompanying the ship.

**Phase 4 — Environmental analysis**
How wind strength (Beaufort scale), sea state, and ship activity relate to bird counts. Trawling attracted nearly 5× more birds per sighting than ordinary steaming — the strongest signal in the dataset.

**Phase 5 — Geospatial and seasonal patterns**
Sighting locations mapped by season, species-level habitat preferences, and sightings over time. Survey effort varied significantly year to year — peaking in 1984–1987 — which must be accounted for in any temporal interpretation.

**Phase 6 — Summary**
Key findings written up with a four-panel summary figure.

---

## Key Findings

- **Wandering albatross dominated** — 11,293 sightings (23% of all records), the most ship-following of any species
- **Ships were wildlife attractors** — trawling averaged 146 birds per sighting vs 29.6 when steaming; only 3.5% of sightings captured naturally feeding birds
- **Spring was peak season** for most species, consistent with breeding returns to subantarctic islands
- **Survey effort drives trends** — the apparent decline after 1987 reflects fewer ship counts, not falling bird numbers
- **Coastal vs pelagic split** — Australasian gannets appeared in calmer inshore waters (avg sea state 3.29) while open-ocean species clustered in moderate-rough conditions (3.74–3.83)

---

## Setup

```bash
pip install pandas matplotlib seaborn
```

Then open `analyse.ipynb` in Jupyter and run all cells.

---

## Licence and attribution

This dataset is published by [CSIRO](https://www.marine.csiro.au/ipt/resource?r=asms_nz) and licensed under a **Creative Commons Attribution Non-Commercial (CC BY-NC) 4.0 International** licence. This project is for educational and non-commercial use only.

Attribution as required by Te Papa Tongarewa:

> This work uses data sourced from Te Papa.

Full Te Papa attribution for unmodified use:

> Source: Te Papa and licensed by Te Papa for re-use under the Creative Commons BY 4.0 International licence.

First registered: September 10, 2019 | Published: December 29, 2025
Dataset URL: https://www.marine.csiro.au/ipt/resource?r=asms_nz

---

## Credit

**Tarun Yadav** — [@whytarunishere](https://github.com/whytarunishere)

Original TidyTuesday framing by [Jon Harmon](https://github.com/jonthegeek), Data Science Learning Community.
