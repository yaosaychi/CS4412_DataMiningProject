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

## Module 3 updates.
Customer-level clustering is then performed on RFM features (Recency, Frequency, Monetary) constructed for 3,920 customers, revealing four stable behavioral segments. A K-Means solution with k=4 achieves a silhouette score around 0.60 and is competitive with Ward hierarchical clustering, with segments interpretable as “Champions”, “Loyal Regulars”, “New Occasional” and “At-Risk/Lapsed”, where Champions are extremely high-value, very recent, frequent buyers and New Occasional customers are many low-frequency, lower-spend accounts.

# **Customer segmentation and RFM modeling
Using only customers with valid IDs, RFM features are computed with a reference date one day after the last transaction, summarizing each customer by their days since last purchase, number of distinct invoices, and total revenue in GBP. The resulting distribution shows a highly skewed Monetary dimension (mean ≈ 1,864 versus a max above 259,000), motivating log-transforms and robust scaling prior to clustering and classification.

The RFM-based K-Means clusters are profiled to compute segment sizes and segment-level revenue contributions, with the “New Occasional” group forming the largest share of customers while “Loyal Regulars” and “Champions” contribute disproportionately to total revenue. A decision tree classifier trained on the RFM features reproduces these unsupervised segment labels with macro-F1 around 0.84 in 5-fold cross-validation and shows that Monetary, Recency, and Frequency all contribute meaningfully and comparably to split decisions.

## PCA visualization and cluster validation
Principal Component Analysis (PCA) on scaled RFM features is used to project customers into a 2D space, enabling visual inspection of segment separation and density. In the PCA scatterplots, Champions and Loyal Regulars occupy compact regions at high Monetary/low Recency, while At-Risk/Lapsed and New Occasional customers spread into areas with higher Recency and lower spending, with DBSCAN highlighting a small number of noise points that fall between segments.

Internal validation metrics (silhouette, Davies–Bouldin, Calinski–Harabasz) are reported side-by-side for K-Means and Ward hierarchical clustering at k=4 and are very similar across methods, with K-Means slightly better on two of the three scores. This supports the conclusion that the cluster structure is robust to the choice of algorithm, and that either method can be used to derive actionable, interpretable customer segments for marketing and retention strategies.

## Dataset
The dataset used in this project is the **Online Retail Dataset** provided by the UCI Machine Learning Repository.

Dataset Source: https://archive.ics.uci.edu/dataset/352/online+retail
D. Chen. "Online Retail," UCI Machine Learning Repository, 2015. [Online]. Available: https://doi.org/10.24432/C5BW33.
