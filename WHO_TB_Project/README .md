# WHO Global TB Intelligence Pipeline
### CARB-X × Gates Foundation Strategic Initiative | 2026

**A nine-notebook data science pipeline that converts all 16 WHO tuberculosis datasets into a country-level precision intervention strategy for the 30 highest-burden nations.**

This project was developed to support competitive positioning for CARB-X diagnostic funding and Gates Foundation programme alignment. It moves from raw data audit to a grant-ready precision deployment brief — with every analytical claim traceable to a specific WHO source file.

---

## The Research Questions

The pipeline addresses one strategic question from nine different angles:

> *Where should CARB-X deploy its AI diagnostic platform, in what configuration, and why — given the biological, structural, and political constraints of each country?*

Each notebook sharpens the answer by adding a new analytical layer. By Notebook 09, the output is not a recommendation — it is a prescription.

---

## Repository Structure

```
WHO_TB_Project/
├── WHO_raw_csv/                    ← All 16 WHO source files (not versioned — see Data below)
├── figures/                        ← Chart outputs (auto-created on first run)
├── 01_Data_Ingestion.ipynb
├── 02_Data_Preprocessing.ipynb
├── 03_Clustering_and_Market_Segmentation.ipynb
├── 04_Gates_AI_Readiness.ipynb
├── 05_End_TB_2030_Trajectory.ipynb
├── 06_Computer_Vision_Clinical_Deployment_Logic.ipynb
├── 07_Drug_Resistance_Intelligence.ipynb
├── 08_Equity_Vulnerability_Prevention.ipynb
├── 09_Precision_Intervention_Strategy.ipynb
├── requirements.txt
└── README.md
```

**Before running:** open any notebook and update the `BASE_DIR` path in the configuration cell to point to your local project directory.

```python
BASE_DIR = Path('/your/path/to/WHO_TB_Project')
```

---

## The Nine Notebooks

| # | Title | Key Output | New Datasets |
|---|-------|-----------|--------------|
| 01 | **Data Audit & Ingestion** | Quality matrix, completeness heatmap, 16-file inventory | All 16 WHO files first loaded |
| 02 | **Feature Engineering** | CARB-X composite index, master country table | TB_burden, TB_outcomes, TB_laboratories |
| 03 | **Market Segmentation** | K-Means clustering into 4 deployment archetypes | TB_expenditure, TB_budget, Metadata GDP |
| 04 | **Gates AI Readiness** | Strategic AI Readiness Index (SARI), 2×2 priority matrix | TB_policies_services, TB_community_engagement |
| 05 | **End TB 2030 Trajectory** | BAU vs CARB-X intervention forecast to 2030 | TB_burden_countries (time series) |
| 06 | **Computer Vision** | ResNet50 chest X-ray triage, YOLOv8 AFB detection simulation | TB_laboratories (GeneXpert capacity) |
| 07 | **Drug Resistance Intelligence** | MDR/XDR gap analysis, DST capacity correction | TB_outcomes (drug-specific) |
| 08 | **Equity, Vulnerability & Prevention** | Equity vulnerability score, 5-dimension dashboard | TB_burden_age_sex, TB_outcomes_age_sex, TB_contact_tpt, TB_hiv_nonroutine_surveillance |
| 09 | **Precision Intervention Strategy** | Country-level prescription matrix, UNHLM accountability audit | **LTBI_estimates** *(first use)*, **TB_unhlm** *(first use)* |

All 16 WHO datasets are used. No file is left behind.

---

## Key Findings

**Biological driver (Notebook 09):** In 8 of 30 high-burden countries, undernutrition drives more than 35% of TB burden. In these markets — led by Central African Republic (53%), North Korea (48%), DRC (47%), Lesotho (44%), and Mozambique (42%) — deploying AI diagnostics without nutritional support is immunologically insufficient. The malnutrition degrades T-cell function before the diagnostic tool can intervene.

**AI blind spots (Notebook 09):** Five high-burden countries (Mozambique, Tanzania, Namibia, Uganda, Kenya) carry HIGH AI diagnostic reliability risk. HIV-positive TB patients present with paucibacillary disease — fewer bacteria, atypical X-ray appearances, and structurally lower sensitivity for chest X-ray AI. In these countries, the Notebook 06 computer vision model requires mandatory GeneXpert molecular confirmation.

**The pharmacy channel (Notebook 09):** In Nigeria (98% private), Pakistan (98%), and India (93%), the private sector accounts for the overwhelming majority of TB diagnoses. The gender treatment gap in these markets is a care-pathway problem, not a biological one. Men prefer private pharmacies over public TB clinics to avoid stigma. Pharmacy-linked AI triage is the structural solution.

**TPT pipeline leak (Notebook 08):** Globally, 75% of screened household contacts never start preventive therapy. Across the 30 high-burden countries, 8.95 million contacts were identified in 2022, 7.53 million were screened, and only 1.95 million started TPT. A digital longitudinal tracker is the intervention that closes this gap.

**Funding accountability (Notebook 09):** DRC (6.3% domestic funding), Zimbabwe (6.7%), Pakistan (6.9%), and Myanmar (9.7%) are allowing international donors to carry 90%+ of the TB programme cost. Where domestic co-investment is below 30%, grant conditionality is required for deployment sustainability.

---

## The Precision Intervention Matrix

The final output of the pipeline is a country-level prescription for each of the 30 WHO high-burden countries. Five intervention types are defined:

| Intervention | Trigger | Clinical Rationale |
|---|---|---|
| **NUTRITION-DX BUNDLE** | Undernutrition > 35% of TB burden | Diagnostic tools cannot compensate for immune failure driven by malnutrition |
| **DUAL HIV+TB MOLECULAR DX** | HIV surveillance undercount gap > 15pp | AI X-ray has systematic false-negative bias in paucibacillary HIV/TB presentations |
| **PHARMACY AI TRIAGE** | Private sector > 50% + gender gap > 3pp | Men seeking informal care require a diagnostic that goes to where they already are |
| **DIGITAL TPT TRACKER** | TPT efficiency < 30% | Three-quarters of screened contacts disappear before starting prevention |
| **EMERGENCY GRANT** | Domestic funding < 30% | Deployment will not survive grant end without domestic co-investment conditionality |

---

## Data Sources

All data is sourced from the **WHO Global Tuberculosis Programme** 2024 data release:

> *WHO Global Tuberculosis Report Dataset, 2024-03-21 release*
> https://www.who.int/teams/global-tuberculosis-programme/data

The 16 source files used across this pipeline:

```
TB_burden_countries          TB_outcomes               TB_burden_age_sex
TB_outcomes_age_sex          TB_contact_tpt            TB_hiv_nonroutine_surveillance
TB_laboratories              TB_budget                 TB_expenditure_utilisation
TB_policies_services         TB_community_engagement   TB_ppm
TB_unhlm                     LTBI_estimates            Metadata_Country_GDP
TB_data_dictionary
```

**The raw CSV files are not versioned in this repository** because they are publicly available from the WHO source above. Download the 2024-03-21 release and place all files in `WHO_raw_csv/` before running any notebook.

---

## Setup & Installation

**Python 3.9 or higher required.**

```bash
# 1. Clone the repository
git clone https://github.com/your-username/WHO-TB-Intelligence-Pipeline.git
cd WHO-TB-Intelligence-Pipeline

# 2. Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Download WHO data files
# Place all 16 CSV files in WHO_raw_csv/

# 5. Set your base directory
# Open any notebook and update BASE_DIR in the first configuration cell

# 6. Run notebooks in order (01 through 09)
jupyter notebook
```

**Notebooks must be run in order.** Several notebooks consume output variables and CSV files produced by earlier notebooks in the sequence.

---

## Computational Requirements

| Notebook | Compute Notes |
|---|---|
| 01–05, 07–09 | Standard CPU. No GPU required. Typical runtime 30–120 seconds per notebook. |
| 06 | Loads a pretrained ResNet50 model via PyTorch. CPU-only is supported but slower. A CUDA-capable GPU reduces runtime significantly. First run downloads ~100MB of model weights. |

---

## Outputs

Each notebook saves its figures to `figures/` and its primary data export to the project root:

| File | Produced by |
|---|---|
| `CARBX_Master_Table.csv` | Notebook 02 |
| `CARBX_Market_Segments.csv` | Notebook 03 |
| `CARBX_AI_Readiness_Index.csv` | Notebook 04 |
| `CARBX_2030_Trajectory.csv` | Notebook 05 |
| `CARBX_Equity_Adjusted_Final_2026.csv` | Notebook 08 |
| `CARBX_Precision_Intervention_Matrix_2026.csv` | Notebook 09 |

---

## Author

**Dr. Frida Arrey Takubetang**
CARB-X × Gates Foundation Strategic Initiative
Life Sciences & Global Health Technology | 2026

---

## Citation

If you use this pipeline or its outputs, please cite the underlying WHO data source:

> World Health Organization. *Global Tuberculosis Report 2024 — Data.* Geneva: WHO, 2024. https://www.who.int/teams/global-tuberculosis-programme/data

---

## Licence

This repository is shared for research and transparency purposes. The underlying WHO data is subject to WHO's own terms of use. Model weights used in Notebook 06 (ResNet50) are from PyTorch's pretrained model library and are subject to their respective licences.
