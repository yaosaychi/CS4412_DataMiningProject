# CS4412-Data-Mining-Project.

## Project Description
This project explores the Online Retail dataset from the UCI Machine Learning Repository using discovery-driven data mining methods. The dataset contains transactional records from a UK-based online retailer and captures detailed information about customer purchases over time. Rather than focusing on predictive modeling, the goal of this project is to discover, analyze, and interpret meaningful patterns in purchasing behavior.

The analysis applies multiple unsupervised and exploratory techniques, including association rule mining to identify frequently co-purchased products, clustering to uncover natural customer segments, and temporal pattern analysis to examine seasonal and time-based trends in transactions. Dimensionality reduction is used as a supporting technique to improve interpretability and visualization of high-dimensional behavioral data. The project follows the Knowledge Discovery in Databases (KDD) process, emphasizing careful data preprocessing, feature engineering, and critical interpretation of discovered patterns.

The analysis was designed to answer three business questions:

-	What products are frequently purchased together?
-	What natural customer segments exist within the data?
-	What distinct purchasing patterns emerge among the segments by season?


## Overview

The original dataset contained **541,909 transactions** across **8 attributes**. After preprocessing and filtering to valid United Kingdom records, the final working dataset contained **485,123 transactions**, **3,920 customers**, **18,019 invoices**, and **4,007 products**.

The project combines association rule mining, RFM-based customer segmentation, clustering, classification, anomaly detection, PCA, and seasonal analysis to generate actionable retail insights.

## Research Questions

1. What products are frequently purchased together?
2. What natural customer segments exist in the customer base?
3. What distinct purchasing patterns emerge among customer segments by season?

# Outline Flow

## Data Preprocessing

Before analysis, the dataset was cleaned by:

- Removing cancellations.
- Restricting transactions to the United Kingdom.
- Dropping rows with negative or zero quantities.
- Dropping rows with negative or zero unit prices.
- Excluding rows with null or empty product descriptions.
- Parsing invoice dates into datetime format.
- Adding `Month` and `TotalPrice` columns.
- Removing customers without valid `CustomerID` values.

These steps reduced noise and produced a cleaner transactional dataset for further analysis.

## Methods

### Association Rule Mining

Apriori and FP-Growth were run on the same sparse basket matrix using a minimum support of `0.01` and minimum confidence of `0.80`. Both algorithms were tested on invoice-product transactions to identify frequent itemsets and co-purchase rules.

### RFM Feature Engineering

Each customer was summarized using three behavioral features:

- **Recency** — number of days since last purchase, using December 10, 2011 as the reference date.
- **Frequency** — number of invoices per customer.
- **Monetary** — total customer spending in GBP.

### Clustering

K-Means and Hierarchical Clustering were applied to standardized RFM features. Although `k = 2` produced the strongest raw clustering score, `k = 4` was selected to create more actionable business segments.

### Classification

K-Means cluster labels were used as class labels for:

- Decision Tree (`max_depth = 4`, `random_state = 42`)
- Gaussian Naive Bayes

Both models were evaluated with 5-fold stratified cross-validation using macro-F1.

### Anomaly Detection

Two anomaly detection methods were applied to the standardized RFM data:

- DBSCAN (`eps = 0.5`, `min_samples = 5`)
- Local Outlier Factor (`n_neighbors = 20`, `contamination = 0.05`)

Customers flagged by both methods were treated as high-confidence anomalies.

### PCA and Seasonal Analysis

Principal Component Analysis was used to measure variance captured by the RFM features. Seasonal analysis grouped months into Winter, Spring, Summer, and Autumn, then cross-tabulated revenue and invoice counts by customer segment.


# Dataset Access.
The dataset used in this project is the **Online Retail Dataset** provided by the UCI Machine Learning Repository.

Dataset Source: https://archive.ics.uci.edu/dataset/352/online+retail
D. Chen. "Online Retail," UCI Machine Learning Repository, 2015. [Online]. Available: https://doi.org/10.24432/C5BW33.

# Requirements.
* Computer or Laptop with `PyCharm` installed and running.
  <br> OR <br>
* Computer or Laptop with internet access to `Google CoLab` online platform.

# How To Run 
* For a simple and straight forward implementation:
    * Download the `organized data notebook` file from the /notebookFiles folder directory.
    * Open the file in Pycharm in a jupyter notebook environment.
    * Select Run all at the top of the jupyter notebook interface (double play icon).
    * Results should then populate the output interface.

* To run in Google CoLab: 
    * Download the `organized data notebook` file from the /notebookFiles folder directory.
    * In the CoLab interface, Click `File`.
    * In the drop down menu, select `Upload Notebook`.
    * In cell 2 with the comment "Paste Copied Instruction Here If Using Google CoLab", copy and paste the following instruction: <br>
            !pip install ucimlrepo
    * On the top-right section on the CoLab interface, select `Connect`.
    * Wait for the on-screen actions to complete then select `Run all`.
    * Results should then populate the output interface.

# Reproducability Instructions.
* Set throughout all random_state = `42`.
* For K-Means: n_clusters=4, random_state=42, n_init=10.
* For DBSCAN intialization values: eps=0.5, min_samples=5.
* For LOCALOUTLIERFACTOR initialization values: n_neighbors=20, contamination=0.05.

# AI usage.
- AI was used in syntax comprehension and debugging.
  

