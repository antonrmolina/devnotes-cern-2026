---
title: Cytosolic Compartment Characterization in a Lipid Vesicle-Encapsulated PURE System
description: We characterize the biochemical composition and translational capacity of a minimal cytosol reconstituted from purified components and encapsulated within giant unilamellar vesicles.
date: 2026-06-01
authors:
  - name: Elisa Ramponi
    affiliation: European Molecular Biology Laboratory, Heidelberg
keywords: [PURE system, cell-free, synthetic cell, GUV, cytosol]
license: CERN-OHL-P-2.0
thumbnail: figures/key-result.png
collections:
  - nucleus-core
---

## Context

Constructing a synthetic cell requires encapsulating a functional cytosol within a lipid membrane. The PURE (Protein synthesis Using Recombinant Elements) system provides a fully defined, reconstituted translation machinery, making it an ideal cytosol surrogate for bottom-up synthetic cell research. However, the biochemical behavior of PURE system components changes substantially upon confinement in giant unilamellar vesicles (GUVs): molecular crowding increases, free Mg²⁺ is buffered differently, and volume fluctuations during electroformation can alter reagent concentrations unpredictably.

Prior work has demonstrated GFP expression inside GUVs using PURE system {cite}`Noireaux2004,Kuruma2015`, but systematic characterization of expression kinetics as a function of encapsulation efficiency and vesicle size is lacking. This DevNote documents a fluorescence-based characterization assay used to benchmark cytosol quality across GUV batches.

## Methods

**GUV preparation.** GUVs were prepared by the PVA gel-assisted swelling method. DOPC:DOPG (9:1 mol/mol) lipid films (2 mg/mL in chloroform) were spread on PVA-coated coverslips and dried under vacuum for 2 h. Swelling buffer (300 mOsm sucrose, 10 mM HEPES pH 7.4) was added and GUVs were harvested after 45 min at 37 °C.

**PURE system encapsulation.** PURExpress Δ(aa, tRNA) kit (NEB) was reconstituted on ice according to manufacturer instructions, supplemented with 20 µM purified eGFP-encoding linear DNA template (T7 promoter, pET backbone). Encapsulation was achieved by co-swelling: PURE system mix was introduced during the hydration step at a 1:1 (v/v) ratio with swelling buffer.

**Fluorescence kinetics.** Encapsulated GUVs were imaged by spinning-disk confocal microscopy (Nikon Ti2-E, 60× oil objective, 488 nm laser, 525/50 nm emission) at 37 °C. Single-vesicle fluorescence was measured from ROIs drawn on individual GUVs (n = 47 per timepoint). Background was subtracted using non-encapsulating vesicles from the same batch.

**Analysis.** Mean fluorescence intensity (MFI) per vesicle was extracted in FIJI and exported as CSV. Kinetic curves were fit to a Hill-modified exponential using `scipy.optimize`.

## Results

GFP expression was detectable in ~62% of GUVs within the first 20 minutes post-encapsulation, rising to a plateau at approximately 90 minutes. The mean peak fluorescence was 1,840 ± 310 AU (n = 47 vesicles), consistent with an estimated GFP concentration of ~0.8 µM assuming a calibration curve from solution-phase standards.

Expression kinetics followed a sigmoidal profile with a lag phase of approximately 8 minutes, attributed to ribosome assembly and mRNA transcription prior to translation initiation. Vesicles with diameters below 5 µm showed significantly reduced expression (p < 0.01, Wilcoxon rank-sum), likely due to volume exclusion limiting PURE system component availability.

```{figure} figures/key-result.png
:align: center
:width: 85%
GFP fluorescence kinetics in GUV-encapsulated PURE system (mean ± SEM, n = 47 vesicles). Dashed line marks the end of the ~8 min lag phase.
```

## Specification

| Parameter | Value |
|---|---|
| Lipid composition | DOPC:DOPG 9:1 mol/mol |
| Total lipid concentration | 2 mg/mL |
| Swelling buffer osmolarity | 300 mOsm |
| HEPES pH | 7.4 |
| Swelling temperature | 37 °C |
| Swelling duration | 45 min |
| PURE system kit | PURExpress Δ(aa, tRNA), NEB #E6840 |
| DNA template concentration | 20 µM (linear, T7 promoter) |
| Imaging objective | 60× oil, NA 1.4 |
| Excitation wavelength | 488 nm |
| Emission filter | 525/50 nm |
| Imaging interval | 5 min |
| Total imaging duration | 120 min |
| Vesicles analyzed | 47 |
| Temperature during imaging | 37 °C |

All reagents stored at -80 °C in single-use aliquots. PURE system reconstituted on ice and used within 30 min of thawing.
