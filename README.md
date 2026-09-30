# Online Retail Customer Segmentation

A consolidated portfolio version of two business analytics coursework notebooks: `clustering_bisdig.ipynb` and `bisdigkelompok_6.ipynb`. Both use the same Online Retail transactions and pursue the same customer segmentation question. This repo combines their shared **RFM → clustering → segment profiling** workflow into one reproducible notebook.

## What it does

1. Removes cancelled transactions, unknown customers, and nonpositive quantity/price rows.
2. Aggregates recency, frequency, and monetary value per customer.
3. Uses log scaling, standardization, K-Means, silhouette scores, and a minimum cluster-size check.
4. Profiles each cluster's size, average RFM, and share of transaction revenue.
5. Inspects DBSCAN cluster and noise counts across three nearby `eps` settings.

The original notebooks covered **541,909 transaction lines** before filtering and **4,338 customer records** in their saved outputs. They were exploratory and used different feature sets and numbers of clusters; their labels and numerical summaries should not be combined directly. One original K-Means result contained a cluster of only **two customers**. This rewritten notebook recalculates its own results and does not claim the original cluster assignments.

## Data source and attribution

Download `Online Retail.xlsx` from [UCI Machine Learning Repository — Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail) and place it at `data/Online Retail.xlsx`. The original dataset has 541,909 transaction records and is licensed **CC BY 4.0**. Citation: Chen, D. (2015). *Online Retail* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5BW33. The workbook is excluded from the ZIP; its source and license are documented here.

## Run

```bash
python -m venv .venv
# Activate the virtual environment
pip install -r requirements.txt
jupyter notebook online_retail_customer_segmentation.ipynb
```

Run cells top to bottom after placing the workbook in `data/`. Dataset download, package installation, and model execution have not been performed in this preparation environment; the notebook code was syntax-checked.

## Limits

Clusters are descriptive groups, not ground-truth customer categories. Segment names should be assigned only after checking cluster sizes, behavior, and business needs. DBSCAN group IDs are unrelated to K-Means IDs, and removing outliers after inspecting clusters can change conclusions.
