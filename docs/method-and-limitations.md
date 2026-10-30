# Method, QA and limitations

[Back to the case study](../README.md)

This page summarises the method reported in Henry Briscoe's 2026 MSc thesis.
Page references refer to the supplied thesis's printed page numbers, which match
the PDF page positions for the passages cited here. The summary is not a new
analysis or an independent audit of the underlying model files.

## Study design

The study used a compact area of interest in central Graz and a 1,000 m context
buffer. High-resolution elevation and imagery inputs supported both model
branches. The common preparation included terrain, ground-factor regions,
transport sources and receiver locations.

The final building layers used the same footprint coverage and each contained
4,713 building/context obstacles. Identical completeness repairs were applied to
both branches. The main remaining difference was the height representation:
nDSM-supported baseline heights versus accepted Roofer-derived heights with
controlled fallbacks. See §§3.4.3–3.4.6, pp. 58–67.

## What survived reconstruction

Roofer produced LoD2.2-style CityJSON reconstructions upstream. These supported
visual inspection and the acceptance or rejection of reconstruction-derived
heights. The final acoustic input was a building layer with height and ground-level
fields; raw CityJSON, roof planes and BuildingPart structure were not retained as
the final acoustic input.

Fallbacks covered failed or missing reconstructions, implausible heights and
buildings outside the reconstruction candidate coverage. The enhanced branch
therefore did not use successful detailed reconstruction everywhere.

This is a test of a specific operational conversion workflow, not a general test
of the acoustic value of fully detailed 3D city models. See §§3.4.5–3.4.6,
pp. 61–66, Table 4.3, p. 83, and §5.3, pp. 86–87.

## Receiver layouts versus analysed outputs

The initial receiver layouts and the final analysis counts are different:

| Receiver set | Layout count | Valid paired outputs analysed |
| --- | ---: | ---: |
| 10 m area-of-interest grid | 1,634 | 898 |
| 1 m selected case-study grids | 9,006 | 9,005 |
| Façade-adjacent receivers | 150 | 150 |

Sources: Table 3.9, p. 69, and Table 4.1, p. 73.

Each receiver set was shared by the two branches, with receiver height kept at
4 m. The six calculation models formed three explicit pairs. A 1 m result was
compared with its matching 1 m counterpart, not with a 10 m output.

Receiver identifiers, coordinates and heights were checked before subtraction.
Missing or non-numeric paired values were excluded. The thesis reports that these
mainly arose at locations inside building footprints or otherwise without valid
paired acoustic outputs. This repository does not independently diagnose every
excluded receiver. See §§3.4.7–3.4.9, pp. 69–73.

## Quality controls reported in the thesis

- Separate raw, working, import and result data; preserve common master inputs.
- Use a consistent coordinate reference system and stable building identifiers.
- Repair geometry and check spatial completeness before the branch comparison.
- Check raster alignment and NoData handling when deriving relative heights.
- Review reconstruction failures and implausible heights before accepting them.
- Apply the same missing-obstacle repairs to both building branches.
- Check input parity before calculation and valid receiver pairing afterwards.

These controls are described in §§3.4.3–3.4.10, pp. 58–72. They are reported
research procedures, not executable tests supplied in this repository.

## Interpreting the findings

The reported broad-grid mean difference was −0.69 dB. The local-grid mean was
+0.08 dB, while individual local-grid differences ranged from −2.40 to +5.20 dB.
A mean near zero can coexist with local changes in both directions; it does not
mean that every receiver was unchanged.

The 1 m case-study grids sampled selected areas, whereas the 10 m grid covered
the broader area of interest. Their aggregate statistics should not be interpreted
as a clean isolation of resolution effects. Within each receiver set, the paired
branch comparison is the controlled comparison.

The nine local-grid receivers reaching an absolute difference of at least 3 dB
were all in case C031. This concentration is a reported descriptive finding;
it does not establish a general causal rule for all similar urban forms.
See Table 4.2, p. 74, and §§4.8–5.2, pp. 83–86.

## What the evidence does not establish

- **Greater real-world accuracy:** no independent measured receiver dataset was
  available. Official modelled outputs served as benchmark/plausibility context.
- **City-wide or general applicability:** the area was compact, and local cases
  were selected for interpretation rather than statistical representativeness.
- **The performance of fully architectural acoustic models:** detailed roof and
  façade geometry was not retained as raw final acoustic input.
- **Independent reproducibility from this repository:** source inputs, model
  files, scripts and receiver-level outputs are not included or re-executed here.
- **A quantified cost-benefit improvement:** the summary does not attach a time
  saving, prediction-error reduction or financial return to the workflow.

See §§4.6 and 5.4–5.7, pp. 82–89, and Chapter 6, pp. 90–92.

Independent measured validation, additional study areas and comparisons across
software implementations are future research directions identified by the thesis.
They are not completed extensions of the work described here.
