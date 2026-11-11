# Workflow notes

## Provenance

Based on Dr Tomasz Pirowski's AGH exercise "Podstawy Systemow Informacji Przestrzennej: Analizy rastrowe, cz. 2: analizy na NMT". The teaching PDF remains in the student's original study folder and is not redistributed here.

## Course procedure

1. Inspect the supplied terrain model (`nmt_dol_pradn_10m`), CLC raster and OPN protected-area raster in EPSG:2180.
2. Calculate slope in degrees and aspect in degrees clockwise from north.
3. Create a south-facing mask for aspect 135-225 degrees, and a slope mask for 5-20 degrees. Combine the two using Boolean raster operations.
4. Apply the land-cover and protected-area criteria. In the supplied class-number scheme, permitted CLC classes are 12, 18, 20, 21 and 29 (211, 231, 242, 243 and 324 in the CLC nomenclature). Do not confuse class indices with official CLC codes.
5. Apply a modal filter with a 7 x 7 neighbourhood, then remove small contiguous areas. The exercise requires at least 10 ha, equivalent to 1,000 cells at 10 x 10 m, and specifies 4-connected cells for this step.
6. Group contiguous candidate cells with GRASS `r.clump`, remove background from subsequent statistics, and calculate terrain / aspect statistics by candidate group.
7. Style the selected areas and produce an attributed map.

These are the exercise's prescribed steps, not a recovered execution log proving that each setting was used in the student's saved results. Check NoData, threshold boundary inclusion, land-cover recoding, filter and connectivity settings before claiming a fully reproduced analysis. Modal filtering can alter local threshold compliance, so final polygons need checking against the original terrain criteria.

## Inspect saved results

Open `project.qgz`, review the saved rasters and statistics layers and compare the `vineyards` layout with `outputs/map.png`. Inputs, retained intermediate files and results are distinguished in `data/manifest.csv`. The lecturer's example output was deliberately not copied into this student's portfolio package.

## Validation scope

The package was checked for valid local QGIS layers, relative file paths, successful loading after relocation and layout rendering. That is not a validation of agricultural suitability, per-polygon area thresholds or the student's calculation choices.
