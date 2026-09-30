# Online Retail Customer Segmentation

A customer segmentation project using the Online Retail transaction dataset. The analysis builds **RFM features**, compares clustering choices, and profiles customer groups to support clearer business decisions.

## What it does

1. Removes cancelled transactions, unknown customers, and nonpositive quantity/price rows.
2. Aggregates recency, frequency, and monetary value per customer.
3. Uses log scaling, standardization, K-Means, silhouette scores, and a minimum cluster-size check.
4. Profiles each cluster's size, average RFM, and share of transaction revenue.
5. Inspects DBSCAN cluster and noise counts across three nearby `eps` settings.

The source dataset contains **541,909 transaction records**. The notebook filters invalid transactions and calculates customer-level features before clustering. Cluster counts and scores are generated when the notebook runs; the README does not claim results from a different experiment.

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
