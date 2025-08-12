# Datasets & Ground Truths for
**Advancing blind hyperspectral unmixing in remote sensing: comparing deep-inspired subspace learning methods**

> This repository hosts the datasets, ground truths, and metadata used in the manuscript above.  
> **No training or evaluation code is included** — the repo focuses *solely* on data distribution.

If you use these data, please **cite the paper** (see [How to cite](#how-to-cite)).

---

## At a glance

- **Scope:** benchmark cubes and real-scene metadata/annotations for hyperspectral unmixing (HU).
- **Included:** data cubes, endmember spectra, abundance maps.
- **Excluded:** model implementations, training scripts, evaluation pipelines.
- **Format:** `.mat`, plus `.fig` metadata files.

---

## Repository structure

```
Datasets/
  Cuprite/
    - Cuprite_GT_nEnd12.mat
    - Cuprite_data_R188.mat
  Jasper/
    - jasperRidge2_R198.mat
    - Jasper_GT.mat
    - end4_Materials.fig
    - end4_Abundance.fig
  Samson/
    - Samson.mat
    - Samson_GT.mat
    - end3_Abundances.fig
    - end3_Materials.fig
  Urban/
    - Urban.mat
    - end4_groundTruth.mat
    - end5_groundTruth.mat
    - end6_groundTruth.mat
    - Figures of endmembers and abundance maps

README.md
```


---

## Dataset cards

Below we summarize **typical** configurations used in HU literature. Exact shapes may differ slightly depending on band-selection and pre-processing; the per-folder `README.md` specifies what is provided here.

### Cuprite (benchmark)
- **Dims:** `250 × 191 × 188` (H × W × B)
- **Materials (K):** 12 ("#1 Alunite", "#2 Andradite", "#3 Buddingtonite", "#4 Dumortierite", "#5 Kaolinite1", "#6 Kaolinite2", "#7 Muscovite", "#8 Montmorillonite", "#9 Nontronite", "#10 Pyrope", "#11 Sphene", "#12 Chalcedony")
  
### Samson (benchmark)
- **Dims:** `95 × 95 × 156` (H × W × B)
- **Materials (K):** 3 ("#1 Soil", "#2 Tree" and "#3 Water")

### Urban 4 (benchmark)
- **Dims:** `307 × 307 × 162`
- **Materials (K):** 4 ("#1 Asphalt", "#2 Grass", "#3 Tree" and "#4 Roof")

### Urban 5 (benchmark)
- **Dims:** `307 × 307 × 162`
- **Materials (K):** 5 ("#1 Asphalt", "#2 Grass", "#3 Tree", "#4 Roof" and "#5 Dirt")
  
### Urban 6 (benchmark)
- **Dims:** `307 × 307 × 162`
- **Materials (K):** 6 ("#1 Asphalt", "#2 Grass", "#3 Tree", "#4 Roof", "#5 Metal", and "6 Dirt")

### Jasper Ridge (benchmark)
- **Dims:** `100 × 100 × 198`
- **Materials (K):** 4 ("#1 Road", "#2 Soil", "#3 Water" and "#4 Tree")

### PRISMA – Alimini (real scene)
- **Dims:** typically large swaths (subsetted to `1000 × 1000`, ~230 valid bands after removal)
- **Materials (K):** 4 ("#1 Water", "#2 Soil", "#3 Clouds", "#4 Vegetation")
  > **Redistribution notice:** raw PRISMA imagery is not included here.

### PRISMA – Limassol Fire (real scene)
- **Dims:** similar to Alimini (subsetted), ~230 valid bands after removal
- **Materials (K):** 4 ("#1 Water", "#2 Clouds", "#3 Vegetation", "#4 Burned area")
  > **Redistribution notice:** raw PRISMA imagery is not included here.

---

## File formats & conventions

- **Cubes:** `H × W × B`  
  - `.mat` (MATLAB) with variable name `Y`.  
- **Endmembers ground truth:** `K × B` matrix (materials × bands).  
- **Abundances ground truth:** `K × H × W` tensor (materials × height × width).  

---


## Licensing & usage

- **Benchmark data** (Cuprite, Samson, Urban, Jasper Ridge) are provided for **research and educational use**; please respect the original dataset terms where applicable.
- **PRISMA imagery** is **not redistributed** here due to licensing; this repo includes only derived metadata and expert-derived reference endmembers. For access to raw imagery, please contact the corresponding author listed in the manuscript or the data provider.

A repository-level `LICENSE` file is included. If you need a different license, please open an issue.

---

## How to cite

If this repository or the provided ground truths/metadata are useful to your work, please cite:

**Gaetano Settembre, Flavia Esposito, Nicoletta Del Buono**.  
*Advancing blind hyperspectral unmixing in remote sensing: comparing deep-inspired subspace learning methods*. Manuscript, 2025.

```bibtex
@article{Settembre2025,
  author  = {Settembre, Gaetano and Esposito, Flavia and Del Buono, Nicoletta},
  title   = {Advancing blind hyperspectral unmixing in remote sensing: comparing deep-inspired subspace learning methods},
  journal = {Advanced Modeling and Simulation in Engineering Sciences},
  volume = {},
  publisher = {Springer Science and Business Media LLC},
  ISSN = {},
  DOI = {},
  url = {},
  year    = {2025},
  month = 
}
```

---

## Acknowledgements

We acknowledge the providers of benchmark datasets widely used in HU research and PRISMA data courtesy of the Italian Space Agency (ASI) and Planetek Italia S.r.l. We also thank all collaborators acknowledged in the manuscript.

---

## Contact

For questions about the data or PRISMA access, please contact:  
**Gaetano Settembre** — gaetano.settembre@uniba.it
