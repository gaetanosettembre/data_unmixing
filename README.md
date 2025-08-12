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
    -
    -
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

- ### Urban 5 (benchmark)
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

## Loading examples

```

### MATLAB
```matlab
load('data/benchmark/samson/samson_cube.mat'); % loads variable X (B×P or H×W×B)
E = readmatrix('data/benchmark/samson/endmembers_gt.csv');     % K×B
A = load('data/benchmark/samson/abundances_gt.mat').A;         % K×H×W
wl = readmatrix('data/benchmark/samson/wavelengths_nm.csv');   % B
```

---

## Evaluation metrics (for reproducibility)

> We provide ground truths so that third parties can evaluate their methods consistently.

- **Spectral Angle Distance (SAD)** for endmembers (lower is better):  
  $$ \operatorname{SAD}(e,\hat e) = \cos^{-1} \left( \frac{ e^{\top} \hat e }{ \lVert e \rVert_2 \, \lVert \hat e \rVert_2 } \right) $$

- **RMSE** for abundances (lower is better):  
  $$ \operatorname{RMSE}(A,\hat A) = \sqrt{\frac{1}{KHW} \sum_{k,h,w} (A_{k,h,w} - \hat A_{k,h,w})^2 } $$

> Exact protocols (band selection, normalization, K) are described per dataset in the subfolder `README.md` files.

---

## Licensing & usage

- **Benchmark data** (Samson, Urban, Jasper Ridge) are provided for **research and educational use**; please respect the original dataset terms where applicable.
- **PRISMA imagery** is **not redistributed** here due to licensing; this repo includes only derived metadata and expert-derived reference endmembers. For access to raw imagery, please contact the corresponding author listed in the manuscript or the data provider.

A repository-level `LICENSE` file is included. If you need a different license, please open an issue.

---

## How to cite

If this repository or the provided ground truths/metadata are useful to your work, please cite:

**Gaetano Settembre, Flavia Esposito, Nicoletta Del Buono**.  
*Advancing blind hyperspectral unmixing in remote sensing: comparing deep-inspired subspace learning methods*. Manuscript, 2025.

```bibtex
@misc{Settembre2025SubspaceHU,
  author  = {Settembre, Gaetano and Esposito, Flavia and Del Buono, Nicoletta},
  title   = {Advancing blind hyperspectral unmixing in remote sensing: comparing deep-inspired subspace learning methods},
  note    = {Datasets and ground truths repository},
  year    = {2025},
  howpublished = {GitHub repository}
}
```

Optionally, add a `CITATION.cff` file to enable one-click citation on GitHub.

---

## Git LFS (recommended)

For large `.npy` / `.mat` files, enable **Git LFS**:

```bash
git lfs install
git lfs track "*.npy" "*.mat" "*.h5"
git add .gitattributes
git add data/
git commit -m "Add datasets with Git LFS"
git push
```

---

## Acknowledgements

We acknowledge the providers of benchmark datasets widely used in HU research and PRISMA data courtesy of the Italian Space Agency (ASI). We also thank all collaborators acknowledged in the manuscript.

---

## Contact

For questions about the data or PRISMA access, please contact:  
**Gaetano Settembre** — gaetano.settembre@uniba.it
