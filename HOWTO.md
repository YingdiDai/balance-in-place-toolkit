# HOWTO — Balance in Place Toolkit (v0.1)

Practical, step-by-step instructions to run a 1-week municipal pilot using the Balance in Place Toolkit (Five Elements for CPTED).

## Purpose
This document shows the minimum steps to (a) run quick diagnostics, (b) co-design and run a reversible pilot, (c) collect monitoring data, and (d) apply the scoring rubric and SLA to decide Keep / Adjust / Remove.

## Prerequisites
- QGIS >= 3.22 (desktop) with Processing toolbox.  
- Excel or LibreOffice (for `scoring_rubric.xlsx`) and a CSV editor.  
- Basic smartphone or camera for photo documentation.  
- Files from this repo: `operationalisation_matrix.pdf`, `SLA_template.pdf`, `templates/tally_template.csv`, `templates/intercept_template.csv`, `templates/scoring_rubric.xlsx`, `qgis/qgis_README.md`.

## Quick start (10–30 minutes)
1. Unzip `Balance_in_Place_Toolkit_v0.1.zip` and review `README.md`.  
2. Open `qgis/qgis_README.md` and load base layers (OpenStreetMap, building footprints, canopy).  
3. Run the **Diagnose** step (viewshed / shaded-path) for 1 target corridor.  
4. Run a 90-minute co-design workshop with 8–15 residents using `scampia_toolkit_appendix.pdf`.  
5. Implement up to three reversible micro-moves per site.  
6. Monitor for 1 week (15-minute tallies + intercepts) and enter data into the CSV templates.  
7. Open `scoring_rubric.xlsx`, fill raw values, and read the Recommendation (Keep / Adjust & Re-pilot / Remove).  
8. If Keep → prepare SLA using `SLA_template.pdf` and hand to procurement.

## Step-by-step — 1-week pilot protocol
### Day 0 — Preparation (½ day)
- Select 2–3 contiguous micro-places (corridor segments, thresholds).  
- Open the QGIS project or create a new one: add building footprints, street centreline, canopy polygons, and streetlight points. Save project as `pilot_{site}.qgz`.

### Day 1 — Diagnose (1 day)
- **Viewshed / LOS**: create observer points at 1.6 m height for walking lines. Run the QGIS Viewshed algorithm (Processing → GRASS / SAGA / native Viewshed) to detect blind spots. Export blind-corner flags as a point layer.
- **Shaded-path %**:
  - Digitise the main pedestrian path as a LineString.
  - Buffer the line by 1.5 m (walkable corridor).
  - Intersect buffer with canopy polygons, compute area of intersection, compute shaded-path % = (area_intersection / area_buffer) * 100.
- Save exports: `diagnostics_blindcorners.geojson`, `diagnostics_shade.csv`.

> See `qgis/qgis_README.md` for exact tool names and screenshots.

### Day 2 — Co-design (90 minutes)
- Use printed maps and `operationalisation_matrix.pdf`.  
- Ask residents to place sticky-dots on proposed micro-moves. Record design choices and costs.

### Day 3–4 — Pilot implementation (1–3 days)
- Install reversible micro-moves (planters, solar bollards, seating). Record installation notes and costs in `KPI_dashboard_example.csv`.

### Day 4–10 — Monitor (1 week)
- Run 15-minute tallies at matched timepoints (use `templates/tally_template.csv`).  
- Conduct intercepts (aim n≈30–50 per site; use `templates/intercept_template.csv`).  
- Logging: lighting uptime, watering/maintenance incidents.

### Day 11 — Decide
- Populate `scoring_rubric.xlsx` Raw values column (I). Scores and recommendation auto-calc.  
- If Recommendation = **Keep**, finalise SLA row(s) and prepare procurement package.

## How to use the `scoring_rubric.xlsx`
- Column I = enter measured values.  
- Columns J/K auto-calc Score & Weighted score.  
- Summary gives Total weighted score and Recommendation.  
- Edit thresholds or weights in E–H if your municipality prefers different tolerances.

## Minimal QGIS commands (short)
- Buffer: `Vector` → `Geoprocessing Tools` → `Buffer`  
- Intersect: `Vector` → `Geoprocessing Tools` → `Intersection`  
- Viewshed: `Processing Toolbox` → search “viewshed” → run with DEM/buildings as input or use SAGA/GRASS implementations.  
- Export CSV: right-click layer → `Export` → `Save Features As...` → CSV.

## File naming convention (recommended)
- `pilot_SITE_diagnostics_{type}.geojson`  
- `pilot_SITE_tally_YYYYMMDD.csv`  
- `pilot_SITE_intercepts_YYYYMMDD.csv`  
- `pilot_SITE_report_v0.1.pdf`

## Troubleshooting
- Shaded-path % too low: check canopy polygon CRS & units (meter vs degrees). Use projected CRS (e.g., UTM / local).  
- Viewshed failing: ensure you have a valid DEM or use building height attribute and use 2.5D viewshed approach.  
- Excel formulas not calculating: check Excel locale (comma vs semicolon). See `scoring_rubric.xlsx` sheet notes.

## How to cite the toolkit
> Dai, Yingdi (2025). *Balance in Place Toolkit — Five Elements for CPTED (Balance Toolkit) v0.1.* Zenodo. DOI: (to be added).

## Feedback & contributions
- Open issues or PRs on the GitHub repo. See `CONTRIBUTING.md` for pull request format and code of conduct.

