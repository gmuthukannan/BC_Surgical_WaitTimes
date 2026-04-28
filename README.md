# BC Surgical Wait Times Analysis

> **A Comparative Study of Health Authority Performance Normalized by Population and Procedure-Specific Demand**

---

## Overview

This capstone project investigates surgical wait time disparities across British Columbia's regional Health Authorities (HAs). Rather than comparing raw wait-time counts, the analysis **normalizes** performance metrics by population size and procedure-specific demand, producing a fairer, apples-to-apples view of how each HA is managing its surgical backlog.

The work spans data from the BC Ministry of Health's open surgical wait-times catalogue (fiscal years 2009/10 to present) and is structured as a reproducible, notebook-driven analysis supported by two presentation decks.

---

## Repository Structure

```
BC_Surgical_WaitTimes/
├── 00_data/                          # Raw and processed datasets
├── 01_notebooks/                     # Jupyter analysis notebooks
├── BC Surgical Wait Times_Data Driven Analysis.pptx              # Capstone 1 presentation
└── BC Surgical Wait Times_Data Driven Analysis_CapStone 2&3.pptx # Capstone 2 & 3 presentation
```

---

## Data Source

Data is sourced from the **BC Open Government Data Catalogue**:

- **Dataset:** [BC Surgical Wait Times](https://catalogue.data.gov.bc.ca/dataset/bc-surgical-wait-times)
- **Publisher:** BC Ministry of Health
- **Coverage:** Fiscal years 2009/10 → current (quarterly & annual files)
- **Licence:** Open Government Licence – British Columbia

### Key Fields

| Field | Description |
|---|---|
| `Health Authority` | One of BC's six regional HAs (e.g. Fraser, Interior, Island, Northern, Vancouver Coastal, PHSA) |
| `Procedure Group` | Surgical procedure type (~83 unique procedures) |
| `Waiting` | Number of cases on the wait list at a point in time |
| `Completed` | Number of procedures completed in the period |
| `Completed 50th Percentile` | Median wait time in weeks for completed cases |
| `Completed 90th Percentile` | Wait time (weeks) below which 90 % of patients were served |

> Data covers **scheduled elective inpatient and day-surgery cases only** — unscheduled procedures are excluded. Records are aggregated quarterly (Q1: Apr–Jun · Q2: Jul–Sep · Q3: Oct–Dec · Q4: Jan–Mar).

---

## Methodology

1. **Data ingestion & cleaning** — Load quarterly and annual CSV files, standardise column names, and handle missing/restated values.
2. **Population normalisation** — Scale waiting and completed case counts by HA population estimates to produce per-capita metrics.
3. **Demand normalisation** — Weight procedure-level metrics by relative procedure-specific demand, accounting for the fact that some HAs naturally receive more referrals for complex or specialised surgeries.
4. **Comparative analysis** — Rank HAs on normalised performance indicators (completion rate, 50th/90th percentile wait times) and visualise trends over time.
5. **COVID-19 impact assessment** — Examine the 2020 disruption (an estimated 30,000+ elective surgeries were postponed in BC between March–May 2020) and the subsequent recovery trajectory.

---

## Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook / JupyterLab

### Installation

```bash
# Clone the repository
git clone https://github.com/gmuthukannan/BC_Surgical_WaitTimes.git
cd BC_Surgical_WaitTimes

# (Recommended) Create a virtual environment
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt   # add this file if not present — see note below
```

> **Note:** If a `requirements.txt` is not yet included, the core libraries used are likely:
> `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, and `jupyter`.

### Running the Notebooks

```bash
jupyter notebook 01_notebooks/
```

Open and run notebooks in order if they are numbered, or follow the logical flow of data loading → cleaning → analysis → visualisation.

---

## Key Findings

The presentation decks (`.pptx` files) summarise the capstone findings. At a high level, this analysis seeks to answer:

- Which Health Authorities are performing above or below expectation when caseload and population are held constant?
- How did the COVID-19 pandemic affect each HA differently, and how quickly did they recover?
- Are certain procedure groups systematically under-served in specific regions?

---

## Project Context

This project was completed as part of a **Data Science Capstone** (Phases 1, 2, and 3). The accompanying presentation files document the iterative evolution of the analysis across capstone milestones.

---

## Acknowledgements

- **Data:** BC Ministry of Health via the [BC Data Catalogue](https://catalogue.data.gov.bc.ca/)
- **Licence:** [Open Government Licence – British Columbia](https://www2.gov.bc.ca/gov/content/data/open-data/open-government-licence-bc)

---

## Licence

This project is for academic/research purposes. The underlying data is published under the **Open Government Licence – British Columbia**. Please review that licence before any commercial use of the data.
