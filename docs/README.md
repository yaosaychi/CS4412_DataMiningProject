# CS4412-Data-Mining-Project.

## Project Description
This project explores the Online Retail dataset from the UCI Machine Learning Repository using discovery-driven data mining methods. The dataset contains transactional records from a UK-based online retailer and captures detailed information about customer purchases over time. Rather than focusing on predictive modeling, the goal of this project is to discover, analyze, and interpret meaningful patterns in purchasing behavior.

The analysis applies multiple unsupervised and exploratory techniques, including association rule mining to identify frequently co-purchased products, clustering to uncover natural customer segments, and temporal pattern analysis to examine seasonal and time-based trends in transactions. Dimensionality reduction is used as a supporting technique to improve interpretability and visualization of high-dimensional behavioral data. The project follows the Knowledge Discovery in Databases (KDD) process, emphasizing careful data preprocessing, feature engineering, and critical interpretation of discovered patterns.

## Module 2 update.
The module presents a summary of findings from the
initial implementation phase of a data mining project applied
to an Online Retail Dataset. The analysis covers exploratory
data analysis, data preprocessing and cleaning, transformation
into transactional form, and the application of the Apriori
algorithm for association rule mining. Key findings reveal strong
co-purchasing patterns among herb marker products, with confidence values exceeding 85% and lift values of approximately 74,
indicating highly structured and intentional purchasing behavior
among customers.Module three would involve clustering algorithms and other findings from the use of fp-growth algorithm

## Module 3 update.
Module 3 completes the end-to-end implementation of the data mining pipeline, extending the analysis beyond association rules to full customer modeling, anomaly detection, and seasonal behavior analysis. All preprocessing, feature engineering, and mining components are fully operational, including data cleaning, RFM construction, clustering, classification, anomaly detection, and temporal pattern analysis on UK customer transactions.

The Apriori and FP-Growth algorithms were compared on a sparse basket matrix of 18,019 invoices and 4,007 products using identical thresholds (min_support = 0.01, min_confidence = 0.80), each generating 177 rules and nearly identical frequent itemsets, with Apriori performing slightly faster and thus preferred for future runs. Association rules ultimately highlight three key co-purchasing product families (Herb Markers, Jumbo Bag collection, and Regency Teacup sets), reinforcing strong bundling and display opportunities observed in Module 2.

Customer-level RFM features (Recency, Frequency, Monetary) were engineered for 3,920 customers and used as input to K-Means and hierarchical clustering with k = 4, producing well-separated segments with silhouette scores of approximately 0.595 and 0.606, respectively. Four segments emerge—Champions, At-Risk/Lapsed, Loyal Regulars, and New/Occasional customers—with New/Occasional customers constituting about 73.4% of the base and Champions a small but high-value group.

Using the cluster assignments as labels, a Decision Tree and Gaussian Naïve Bayes classifier were trained to interpret which RFM features distinguish segments, both achieving strong macro-averaged F1 scores. The Decision Tree indicates that Monetary is the most important splitter (importance ≈ 0.368), followed by Recency (0.331) and Frequency (0.301), aligning with the retail context where spending level is a primary differentiator.

For anomaly detection, DBSCAN and Local Outlier Factor (LOF) identify a small set of customers with unusual purchasing behavior: DBSCAN flags around 52 noise points (about 1.3% of customers), while LOF marks roughly 5% as anomalous, with both methods agreeing on approximately 38 anomalous customers. These anomalies occur across all segments but are concentrated in the At-Risk and New/Occasional groups, and customers with unusually high Monetary values relative to peers are especially likely to be marked as anomalies.

Seasonal analysis maps transactions to seasons and customer segments, computing per-season revenue and invoice counts for each segment. All segments peak in the autumn, with about half of Champions' purchases ocurring in that season and overall transaction volume increasing from September through November, revealing a pronounced and shared seasonal purchasing pattern across the customer base.


## Dataset
The dataset used in this project is the **Online Retail Dataset** provided by the UCI Machine Learning Repository.

Dataset Source: https://archive.ics.uci.edu/dataset/352/online+retail
D. Chen. "Online Retail," UCI Machine Learning Repository, 2015. [Online]. Available: https://doi.org/10.24432/C5BW33.

## How To Run 
Download the file from the notebook files folder.
Open in pycharm jupyter notebook or Google Colab.
Select Run all.


