# Campaign Attribution Analysis

## Overview

This project analyzes how different marketing attribution models assign revenue to marketing channels using the **Online Retail II transaction dataset**.

The objective is to understand how attribution methodology influences channel-level revenue reporting and marketing performance evaluation. The project compares three commonly used attribution models:

- **First-Touch Attribution** — assigns all revenue credit to the first marketing channel in a customer's journey.
- **Last-Touch Attribution** — assigns all revenue credit to the last marketing channel before the conversion.
- **Linear Attribution** — distributes revenue credit equally across all marketing touchpoints in a customer's journey.

The analysis uses Python and pandas to construct customer journeys, simulate marketing touchpoints, calculate attribution credits, and compare channel-level performance.

**Important data limitation:** The original Online Retail II dataset contains transaction data but does not include actual marketing touchpoints or channel interactions. Therefore, marketing channels and customer journeys are simulated for analytical and educational purposes. The results should not be interpreted as actual marketing campaign performance.

## Business Objectives

This project addresses the following business questions:

1. How does revenue allocation change across first-touch, last-touch, and linear attribution models?
2. Which simulated marketing channels receive the most revenue credit under each model?
3. How does the choice of attribution model affect channel performance rankings?
4. How can customer purchase history and RFM segments provide additional context for marketing analysis?
5. Why should marketing teams avoid relying on a single attribution model when evaluating campaign performance?

## Attribution Models

| Model | Attribution logic | Business interpretation |
|---|---|---|
| First touch | 100% credit to the first touchpoint | Highlights channels associated with customer discovery |
| Last touch | 100% credit to the last touchpoint | Highlights channels associated with the final interaction |
| Linear | Equal credit across all touchpoints | Recognizes every recorded touchpoint equally |

These models provide different perspectives on the customer journey. None independently proves that a marketing channel caused a purchase.

## Dataset

The project uses prepared CSV files derived from the Online Retail II transaction data and an RFM segmentation workflow.

### Required files

| File | Purpose |
|---|---|
| `cleaned_online_retail_data.csv` | Cleaned transaction-level data used to construct customer journeys and calculate revenue attribution |
| `rfm_with_churn.csv` | Customer RFM segments used to enrich the analysis |

### Required columns

**Transaction dataset — `cleaned_online_retail_data.csv`**

- `Customer ID`
- `Invoice`
- `InvoiceDate`
- `TotalRevenue`

**RFM dataset — `rfm_with_churn.csv`**

- `Customer ID`
- `Segment`

The transaction dataset should contain valid customer identifiers, invoice identifiers, transaction dates, and revenue values. The RFM dataset should contain customer identifiers that can be matched to the transaction data.

The RFM file is used for customer segmentation context; the presence of a churn-related filename does not mean churn has been causally explained or validated by this attribution analysis.

## Technology Stack

- **Python** — data analysis and processing
- **pandas** — data cleaning, grouping, aggregation, and attribution calculations
- **JupyterLab / Jupyter Notebook** — interactive analysis
- **NumPy** — numerical operations, if used in the notebook
- **Matplotlib / Seaborn** — visualizations, if used in the notebook

Install the exact dependencies listed in `requirements.txt`.

## Project Structure

```text
campaign-attribution-analysis/
├── data/
│   ├── cleaned_online_retail_data.csv
│   └── rfm_with_churn.csv
├── notepads/
│   └── campaign_attribution.ipynb
├── requirements.txt
└── README.md
```

The CSV files are required inputs and may need to be prepared separately. Add them to the expected data directory before running the notebook. Do not commit sensitive or restricted data to a public repository.

## Setup and Installation

### 1. Clone the repository

```bash
git clone https://github.com/Uma-Obbani/campaign-attribution-analysis.git
cd campaign-attribution-analysis
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the virtual environment

**macOS / Linux**

```bash
source .venv/bin/activate
```

**Windows — Command Prompt**

```bat
.venv\Scripts\activate.bat
```

**Windows — PowerShell**

```powershell
.\.venv\Scripts\Activate.ps1
```

### 4. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 5. Prepare the data files

Place the required CSV files in the `data/` directory expected by the notebook.

The notebook currently resolves the data directory relative to the Jupyter working directory. When running from `notepads/`, it is configured to resolve to a `data/` directory three levels above that working directory.

If your files are stored elsewhere, update the `file_path` setup in `campaign_attribution.ipynb` to match your actual directory structure.

### 6. Launch JupyterLab

From the project root, run:

```bash
jupyter lab
```

Open `notepads/campaign_attribution.ipynb` and execute the cells in order.

## Analysis Workflow

The notebook follows this analytical workflow:

1. **Load prepared data** — read transaction records and RFM customer segments.
2. **Prepare transaction data** — use customer IDs, invoice IDs, invoice dates, and revenue to organize purchase events.
3. **Construct customer journeys** — group and order transactions by customer and date.
4. **Simulate marketing channels** — assign illustrative channels because actual marketing interaction data is unavailable.
5. **Apply attribution models** — calculate first-touch, last-touch, and linear revenue credit.
6. **Aggregate attribution results** — compare credited revenue across the simulated channels.
7. **Incorporate customer segments** — use RFM segments to explore differences in customer-level revenue patterns.
8. **Compare the models** — examine how channel rankings and revenue allocation change depending on the attribution method.

The exact calculations and visual outputs are defined in the notebook.

## Business Applications

The project demonstrates analytical approaches relevant to marketing analytics and business intelligence roles.

- **Marketing performance reporting:** Compare how attribution assumptions influence channel-level revenue reporting.
- **Budget allocation discussions:** Use attribution results as one input when evaluating marketing investment decisions, alongside costs, conversion rates, incrementality, and customer lifetime value.
- **Customer segmentation:** Explore how revenue attribution patterns vary across RFM segments.
- **Stakeholder communication:** Explain why channel performance can look different under different attribution rules.
- **Analytics engineering:** Transform transaction-level data into structured, aggregated reporting outputs.

## Limitations and Future Improvements

The current project is an educational demonstration rather than a production-ready marketing attribution system.

Potential improvements include:

- Integrating actual website sessions, ad clicks, campaign IDs, and conversion events.
- Implementing configurable attribution windows and touchpoint definitions.
- Adding time-decay and position-based attribution models.
- Comparing attributed revenue with marketing spend, ROAS, CAC, and conversion rates when reliable campaign cost and conversion data are available.
- Validating channel rankings against controlled experiments or incrementality tests.
- Building a dashboard to compare attribution models and customer segments.
- Adding automated data-quality checks for duplicate invoices, missing customer IDs, invalid revenue values, and inconsistent timestamps.

A production implementation should also distinguish between an invoice, an individual transaction line, and a marketing conversion, as these represent different analytical entities.

## Repository

GitHub: https://github.com/Uma-Obbani/campaign-attribution-analysis

## Author

**Uma Obbani**

This project is part of a data analytics portfolio focused on Python, customer behavior, marketing performance, and business decision-making.
