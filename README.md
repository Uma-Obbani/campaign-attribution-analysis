# Campaign Attribution Analysis

This project compares three revenue attribution models—first touch, last touch, and linear—using the Online Retail II transaction data. The notebook assigns simulated marketing channels to customer transactions because the source transaction data does not include marketing touchpoints.

## Project files

- `notepads/campaign_attribution.ipynb` — analysis notebook
- `requirements.txt` — Python packages used by the notebook

## Data files

The notebook requires these prepared CSV files in the same `data/` directory:

- `cleaned_online_retail_data.csv`
- `rfm_with_churn.csv`

The notebook currently builds the data directory from the Jupyter working directory. For a working directory of `notepads/`, it resolves to the `data/` directory three levels above `notepads/`. If your files are stored elsewhere, update the `file_path` setup in the notebook to point to their location.

The transaction CSV needs at least `Customer ID`, `Invoice`, `InvoiceDate`, and `TotalRevenue` columns. The RFM CSV needs `Customer ID` and `Segment` columns.

## Setup and run

From the project root, create and activate a virtual environment, then install the dependencies:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Start Jupyter and open `notepads/campaign_attribution.ipynb`:

```bash
jupyter lab
```

Run the notebook cells from top to bottom. The notebook prints attribution summaries and displays a comparison chart.
