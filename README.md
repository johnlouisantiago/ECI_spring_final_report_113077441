# Final Report for Experiments and Causal Inference (114 Spring)

## Replication — State Economic Freedom and Firm Size as Moderators of Paid Family Leave's Effect on Firm Risk-Taking

Replication materials for the class report extending Lin (2025) ("Pearl's" thesis) on how state Paid Family Leave (PFL) affects firm strategic risk-taking. The extension adds **state economic freedom** and **firm size** as connected moderators.

### Files

| File | Description |
|------|-------------|
| `final_panel_manufacturing.csv` | Manufacturing firm-year panel (has `factor_score`, `is_sme`, controls, `Effective_Year`). |
| `economic-freedom-of-north-america-2025-full-dataset.xlsx` | Fraser Institute EFNA subnational workbook. |

### How to run

1. Open `PFL_Extension_Replication.Rmd` in RStudio.
2. Place the two input files in the same folder, or edit the file paths in the `paths` chunk.
3. Knit. The first chunk installs any missing R packages: `dplyr`, `tidyr`, `readr`, `readxl`, `fixest`, `did`, `ggplot2`, `knitr`.

### Pipeline (two stages)

1. **Upstream preprocessing** — inherited from the original thesis (Lin 2025). These chunks build the panel (the risk-taking factor score, the SME indicator, and all controls) from the raw Compustat / Execucomp / BEA / BLS / SBA inputs. They are set to `eval = FALSE` because they need those raw inputs (`COMPUSTAT/`, `execucomp/`, `SAGDP/`, `SAINC/`, `Unemp/`, `SME_size_standards.xlsx`); running them end-to-end regenerates `final_panel_manufacturing.csv`.
2. **Extension analysis** — runs from `final_panel_manufacturing.csv` plus the EFNA workbook, and is fully executable.

### What it reproduces (and where each piece appears in the paper)

| Rmd output | In the paper |
|------------|--------------|
| Treated cohorts (Table 1) | Table 2 |
| Specification menu, TWFE/DDD (Table 2) | Table 3 |
| Implied PFL effect by state (Table 3) | Figure 1 |
| Callaway–Sant'Anna, combined + stratified (Table 4) | Table 4 |
| Robustness — post-COVID, movers, RI (Table 5) | Table 5 |
| Figures: RI pre-trend, firm-size stratification, implied effect by state | Figures 1–2 + Appendix B |
