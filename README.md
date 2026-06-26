# Integrating Phytosociological Proxies to Improve Predictions of Tree Habitat Suitability: Potentials and Limitations

[![Status](https://img.shields.io/badge/Status-Submitted%202026-orange)]()
[![Journal](https://img.shields.io/badge/Journal-CJFR-darkgreen)]()
[![R](https://img.shields.io/badge/R-4.5.2-276DC3?logo=r)](https://www.r-project.org/)

## Overview

This repository contains the data and reproducible analysis code supporting the manuscript:

> **Czarnecki de Liz, J.P.**, Thiffault, N., D'Orangeville, L., Coops, N.C., & Achim, A. (*under review*). Integrating Phytosociological Proxies to Improve Predictions of Tree Habitat Suitability: Potentials and Limitations. *Canadian Journal of Forest Research*.

Intensifying disturbances and climate change are disrupting forest ecosystems globally, making science-based adaptation strategies essential in forest management. Species distribution models (SDMs) support this task, but their predictive accuracy is often limited by a primary reliance on abiotic variables. We evaluated whether the incorporation of tree species co-occurrence data — a proxy for biotic interactions and habitat filtering — can improve habitat suitability predictions (operationalized as Importance Value, IV) in the boreal-temperate ecotone of Quebec, Canada. Using Random Forest regression, we compared abiotic-only versus abiotic + co-occurrence models for seven ecologically important tree species. Co-occurrence predictors consistently improved generalization to independent test data (test R² from 0.01–0.44 to 0.07–0.73), reduced prediction bias, and frequently displaced broad climatic predictors in importance rankings. These findings suggest that forest-inventory co-occurrence data offers a scalable baseline for habitat suitability predictions supporting climate-adaptive forestry.

**Keywords:** Eltonian shortfall, community assembly, realized niche, forest inventory, model calibration

---

## Repository Structure

```
Integrating-Phytosociological-Proxies/
│
├── script/
│   └── 000_CzarneckiLiz_RForest_Phytosociological_Proxies_IV_prediction.Rmd   # Full reproducible analysis
│
├── database/
│   └── undisturbed_plots_sf_env_clim_4th_inv_study_area_PET.csv                # Plot-level dataset
│
├── 000_CzarneckiLiz_RForest_Phytosociological_Proxies_IV_prediction.html       # Rendered HTML output
└── 000_CzarneckiLiz_RForest_Phytosociological_Proxies_IV_prediction.pdf        # Rendered PDF output
```

---

## Data

The dataset (`undisturbed_plots_sf_env_clim_4th_inv_study_area_PET.csv`) contains plot-level observations from the 4th Quebec Forest Inventory, filtered to undisturbed stands within the study area. Variables include:

- **Response variable:** Importance Value (IV) for seven tree species — *Abies balsamea* (SAB), *Betula papyrifera* (BOP), *Betula alleghaniensis* (BOJ), *Picea mariana* (EPN), *Populus tremuloides* (EPB), *Acer rubrum* (ERR), and *Acer saccharum* (ERS)
- **Abiotic predictors:** bioclimatic variables (ClimateNA), topographic metrics (TWI, slope, aspect, curvature, wind exposition, insolation), and soil properties (CEC, clay, pH, organic matter)
- **Co-occurrence predictors:** Importance Value of co-occurring tree species derived from the same forest inventory plots
- **Spatial variables:** longitude, latitude, altitude

---

## Reproducible Analysis

The full analysis pipeline is documented in `000_CzarneckiLiz_RForest_Phytosociological_Proxies_IV_prediction.Rmd` and covers:

1. Data preparation and spatial filtering
2. Train/test spatial split (independent test set)
3. Random Forest regression — abiotic-only models
4. Random Forest regression — abiotic + co-occurrence models
5. Model evaluation: R², RMSE, MAE, prediction bias
6. Variable importance and partial dependence analysis
7. Spatial visualization of observed vs. predicted IV

The rendered outputs (`.html` and `.pdf`) provide fully navigable versions of the analysis with all results, figures, and code.

---

## Requirements

Analysis was conducted in **R 4.5.2**. Main packages:

| Package | Purpose |
|---|---|
| `caret` | Random Forest modelling and tuning |
| `CAST` | Spatial cross-validation |
| `sf` | Spatial data handling |
| `tidyverse` | Data manipulation and visualization |
| `iml` | Variable importance and partial dependence |
| `patchwork` | Multi-panel figure composition |
| `ggplot2` | Figures |

To reproduce the analysis, open the `.Rmd` file in RStudio and knit, or run sequentially in an R session.

---

## Citation

> Citation details will be updated upon acceptance and publication.

---

## Authors

- **João Paulo Czarnecki de Liz** — Faculté de foresterie, de géographie et de géomatique, Université Laval, Québec, Canada
- **Nelson Thiffault** — Canadian Forest Service, Natural Resources Canada, Québec, Canada
- **Loïc D'Orangeville** — Faculté de foresterie, de géographie et de géomatique, Université Laval, Québec, Canada
- **Nicholas C. Coops** — Department of Forest Resources Management, University of British Columbia, Vancouver, Canada
- **Alexis Achim** — Faculté de foresterie, de géographie et de géomatique, Université Laval, Québec, Canada

---

## License

Code is released under the [MIT License](LICENSE). Data use is subject to Quebec Forest Inventory data sharing policies.

---

## Acknowledgements

We thank the Direction des inventaires forestiers (Ministère des Ressources naturelles et des Forêts du Québec) for access to forest inventory data.
