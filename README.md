# MSc Thesis — Strategic Noise Mapping

## Integrating Enhanced Building Representations into the CNOSSOS-EU Method for Strategic Noise Mapping

**Case study: Graz, Austria**

MSc (CE) Geographical Information Science & Systems (UNIGIS)  
University of Salzburg, 2026

## 30-second summary

This thesis investigated whether richer building representations derived from high-resolution airborne LiDAR and aerial imagery produce materially different strategic noise-mapping results from a strong conventional 2.5D building model.

I built two matched CNOSSOS-EU modelling workflows for central Graz, keeping terrain, ground conditions, traffic sources, receivers and calculation settings consistent so that the effect of building representation could be isolated.

The enhanced-building workflow produced measurable differences, but broad-area effects were generally modest and differences of 3 dB or more were rare and highly localised. The results suggest that richer 3D source data are most useful for targeted local analysis rather than as a wholesale replacement for a strong 2.5D strategic-noise model.

## Research question

Can an enhanced building representation derived from high-resolution geospatial data retain useful additional geometric information through an operational CNOSSOS-EU / iNoise workflow, and does that retained information materially change predicted noise levels compared with a conventional 2.5D baseline?

## What I did

- Processed high-resolution Vexcel UltraCam Dragon LiDAR and aerial-imagery data for central Graz.
- Prepared Digital Terrain Model (DTM), Digital Surface Model (DSM) and normalised DSM (nDSM) products.
- Cleaned and classified point-cloud data and used it to support building reconstruction and height extraction.
- Built a strong conventional 2.5D baseline using cleaned building footprints and LiDAR-derived building heights.
- Used Roofer to generate LoD2.2-style CityJSON building reconstructions as part of an enhanced-building workflow.
- Converted the enhanced building information into an iNoise-ready representation suitable for CNOSSOS-EU calculations.
- Prepared and quality-checked road, bus and tram noise-source data.
- Built matched 2.5D and enhanced-building iNoise models with identical non-building inputs.
- Compared results using a broad 10 m receiver grid, detailed 1 m case-study grids and façade-adjacent receivers.
- Used spatial QA, plausibility checks and reproducible data preparation to identify errors and maintain comparability between the two modelling branches.

## Key findings

- Enhanced building information did survive into the operational modelling workflow, but not all of the richer upstream geometry was retained.
- Detailed CityJSON and roof-plane information was simplified before the final acoustic calculation.
- The enhanced-building model produced different predicted noise levels from the 2.5D baseline, but the differences were generally modest and localised.
- Detailed 1 m and façade-adjacent receiver analysis revealed local effects that were less visible in the broad 10 m comparison.
- A strong 2.5D baseline remains an efficient and defensible default for broad strategic noise mapping.
- Enhanced-building workflows appear most useful as a targeted refinement for locations where complex building geometry, courtyards, façades or source-receiver relationships justify additional analysis.

## Technical stack

**GIS and spatial analysis**
- ArcGIS Pro
- raster and vector geoprocessing
- coordinate-reference-system management
- spatial joins and attribute processing
- map production and spatial QA

**Point clouds and 3D geodata**
- airborne LiDAR
- LAS point-cloud processing
- CloudCompare
- Roofer / 3DGI
- CityJSON
- LoD building representations
- Blender for visual QA

**Noise modelling**
- CNOSSOS-EU
- iNoise 2026
- strategic environmental-noise modelling
- multi-scale receiver analysis

**Data and formats**
- Vexcel UltraCam Dragon data
- OpenStreetMap
- GeoTIFF
- LAS
- vector GIS datasets
- public and official transport/noise data

## Workflow

The core comparison followed this structure:

`LiDAR / imagery / spatial data`
→ `point-cloud and GIS preprocessing`
→ `DTM / DSM / nDSM`
→ `2.5D baseline + enhanced-building workflow`
→ `QA and controlled input preparation`
→ `matched CNOSSOS-EU models`
→ `receiver-level comparison`
→ `spatial interpretation`

The important methodological principle was controlled comparability: both model branches used the same terrain, ground regions, source interpretation, receiver locations and calculation settings. Building representation was the intended difference between the paired models.

## Quality assurance and reproducibility

QA was an important part of the workflow rather than a final visual check.

The work included:

- geometry repair and completeness checking;
- stable building identifiers;
- checking coordinate reference systems;
- detection of implausible or missing building heights;
- documented fallback rules where high-resolution height information was unavailable;
- matched feature counts between the two model branches;
- point-for-point matching of receiver outputs;
- separation of raw, working, model-input and result data;
- explicit distinction between measured validation data and modelled benchmark data.

This was particularly important because differences between the two model branches needed to reflect building representation rather than accidental differences in the underlying datasets.

## Main conclusion

High-resolution LiDAR and richer 3D building data do not automatically produce substantially different strategic noise maps.

The limiting factor can be the operational modelling chain itself: detailed information may exist upstream but be simplified before the final calculation.

For the workflow tested here, enhanced building representation was most valuable for selective local analysis rather than blanket replacement of established 2.5D modelling.

## Limitations

This study did not have an independent measured receiver dataset.

Official noise-model outputs were therefore used only for benchmarking and plausibility assessment, not as measured validation data. The thesis can establish where the two modelling approaches diverge, but it cannot demonstrate that one model is more accurate than the other.

The study also covers a deliberately compact area of central Graz and tests an enhanced-building representation within the constraints of CNOSSOS-EU and iNoise. It is not a fully architectural 3D acoustic model.

## Data and publication note

Some source datasets and software used in this research were supplied by or associated with third parties and may be subject to licensing, copyright or redistribution restrictions.

This repository will therefore contain only material that can appropriately be shared. Proprietary source data, licensed software, restricted datasets and other third-party material will not be redistributed without permission.

## Thesis

**Henry Briscoe (2026)**  
*Integrating Enhanced Building Representations into the CNOSSOS-EU Method for Strategic Noise Mapping: Case Study: Graz, Austria*

Master's thesis, University of Salzburg, UNIGIS MSc (CE).