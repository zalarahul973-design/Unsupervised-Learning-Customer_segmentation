# Customer Segmentation — Summary Report

## Project Overview

This project performs customer segmentation using unsupervised learning techniques on the Mall Customers dataset.

## Dataset

- Dataset: Mall Customers
- Total Customers: 200
- Features used for clustering:
  - Annual Income
  - Spending Score
- StandardScaler was used for feature scaling.

## Algorithms Used

1. K-Means Clustering
2. Hierarchical Clustering
3. DBSCAN

## K-Means Clustering

K-Means was used to divide customers into meaningful groups based on Annual Income and Spending Score.

The Elbow Method and Silhouette Score were used to determine the suitable number of clusters.

## Hierarchical Clustering

Hierarchical clustering was performed using Ward linkage.

A dendrogram was used to understand the hierarchical structure and determine an appropriate number of clusters.

## DBSCAN Clustering

DBSCAN was applied using density-based clustering.

It can identify clusters of different shapes and classify low-density observations as noise.

## Model Comparison

The three clustering algorithms were compared using:

- Number of clusters
- Silhouette Score
- Cluster separation
- Business interpretability

The algorithm with the highest meaningful Silhouette Score was considered the best-performing model.

## Business Insights

The customer segments can help the business create targeted marketing strategies.

### High Income — High Spending

These customers are valuable customers and can be targeted with premium products, VIP offers, and loyalty programs.

### High Income — Low Spending

These customers have high purchasing potential but low spending. Personalized offers and recommendations can help increase their spending.

### Low Income — High Spending

These customers spend frequently despite lower income. Discounts, loyalty rewards, and value offers can help retain them.

### Low Income — Low Spending

Budget-friendly products, discounts, and promotional campaigns can be used for this segment.

### Moderate Customers

Personalized promotions, seasonal campaigns, and cross-selling strategies can be used.

## Conclusion

Customer segmentation helps the business understand different customer groups and design targeted marketing strategies.

K-Means provides a simple and interpretable segmentation approach, while Hierarchical Clustering provides a hierarchical view and DBSCAN helps identify density-based groups and noise.

The final model and scaler files can be used for future customer segmentation predictions.