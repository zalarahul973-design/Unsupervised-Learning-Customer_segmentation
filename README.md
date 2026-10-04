

<p align="center">
  <h1 align="center">🛍️ Mall Customer Segmentation</h1>
  <p align="center"><b>Unsupervised Learning • K-Means • Hierarchical Clustering • DBSCAN • Business Insights</b></p>
</p>

---
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b7915856-7690-4c59-9aaf-20c4e17da49a" />


### 🖱️ Click the Image Above
<p align="center">

<a href="#-project-objectives">🎯 <b>OBJECTIVES</b></a>
&nbsp; ➜ &nbsp;

<a href="#-k-means-clustering">🔵 <b>K-MEANS</b></a>
&nbsp; ➜ &nbsp;

<a href="#-hierarchical-clustering">🟣 <b>HIERARCHICAL</b></a>
&nbsp; ➜ &nbsp;

<a href="#-dbscan-clustering">🟢 <b>DBSCAN</b></a>
&nbsp; ➜ &nbsp;

<a href="#-algorithm-comparison">📊 <b>COMPARISON</b></a>
&nbsp; ➜ &nbsp;

<a href="#-business-insights">💼 <b>INSIGHTS</b></a>

</p>

---

## 🏷️ Skills Badges

<p align="center">

![Python](https://img.shields.io/badge/Python-3.13-blue?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-purple?style=for-the-badge&logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-blue?style=for-the-badge&logo=numpy)
![Scikit Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-orange?style=for-the-badge&logo=scikit-learn)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-green?style=for-the-badge&logo=matplotlib)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-teal?style=for-the-badge&logo=seaborn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=for-the-badge&logo=jupyter)
![K-Means](https://img.shields.io/badge/K--Means-Clustering-red?style=for-the-badge)
![Hierarchical](https://img.shields.io/badge/Hierarchical-Clustering-blue?style=for-the-badge)
![DBSCAN](https://img.shields.io/badge/DBSCAN-Density%20Clustering-purple?style=for-the-badge)

</p>

---
## 📌 Project Overview

This project performs **customer segmentation** on the Mall Customers dataset using unsupervised machine learning techniques.

The main goal is to group customers with similar behaviour based on:

- 💰 Annual Income
- 🛒 Spending Score
- 👤 Age

For the primary clustering analysis, **Annual Income** and **Spending Score** are used because they provide clearer visual separation between customer groups.

The project compares three clustering algorithms:

1. 🔵 K-Means Clustering
2. 🟣 Agglomerative Hierarchical Clustering
3. 🟢 DBSCAN

The final analysis is converted into practical business recommendations for targeted marketing.

---

## 🎯 Project Objectives

- Load and understand the Mall Customers dataset.
- Perform Exploratory Data Analysis (EDA).
- Clean and preprocess the data.
- Encode the Gender feature.
- Standardise numerical features using `StandardScaler`.
- Select Annual Income and Spending Score for primary clustering.
- Determine a suitable number of K-Means clusters using the Elbow Method and Silhouette Score.
- Apply K-Means clustering.
- Apply Agglomerative Hierarchical Clustering.
- Apply DBSCAN with parameter tuning.
- Compare clustering algorithms using Silhouette Score.
- Build customer cluster profiles.
- Translate clusters into business insights and marketing strategies.
- Save the trained K-Means model using Joblib.

---

# 📊 Dataset

The project uses the **Mall Customers** dataset.

### Dataset Details

| Item | Details |
|---|---|
| 👥 Total Customers | 200 |
| 🆔 Original ID | `CustomerID` |
| 👤 Gender | Male / Female |
| 🎂 Age | Customer age |
| 💰 Annual Income | Annual income in k$ |
| 🛒 Spending Score | Spending score from 1–100 |

### Main Clustering Features

```text
Annual_Income
Spending_Score
```

The notebook applies `StandardScaler` before distance-based clustering.

---

# 🔍 Exploratory Data Analysis

The notebook includes:

- Dataset structure and information
- Statistical summary
- Missing-value checking
- Feature distributions
- Pairplot
- Correlation heatmap

### EDA Insight

Annual Income and Spending Score provide clearer visual separation than the other feature combinations, so they are selected as the main two-feature clustering space.

---

# ⚙️ Data Preprocessing

The following preprocessing steps are performed:

### 1. Rename Columns

```text
Annual Income (k$) → Annual_Income
Spending Score (1-100) → Spending_Score
```

### 2. Remove CustomerID

`CustomerID` is an identifier and is not useful for customer similarity calculations.

### 3. Encode Gender

Gender is converted into numerical form using `LabelEncoder`.

### 4. Feature Scaling

`StandardScaler` is applied to the numerical features.

Scaling is important because K-Means and DBSCAN are distance-based algorithms and features with larger numerical ranges can otherwise have greater influence.

---

# 🔵 K-Means Clustering

## Elbow Method

The Elbow Method was used to test cluster counts from `k = 1` to `k = 10`.

The notebook selected:

```text
Elbow k = 5
```

## Silhouette Score

Silhouette Scores were calculated from `k = 2` to `k = 10`.

The best result was:

```text
Best k = 5
Silhouette Score = 0.5547
```

Therefore, the final K-Means model uses **5 clusters**.

---

## 📊 K-Means Cluster Profile

| Cluster | Avg Age | Avg Annual Income | Avg Spending Score | Customers | Segment |
|---:|---:|---:|---:|---:|---|
| 0 | 42.72 | 55.30 | 49.52 | 81 | Moderate Income / Moderate Spending |
| 1 | 32.69 | 86.54 | 82.13 | 39 | High Income / High Spending |
| 2 | 25.27 | 25.73 | 79.36 | 22 | Low Income / High Spending |
| 3 | 41.11 | 88.20 | 17.11 | 35 | High Income / Low Spending |
| 4 | 45.22 | 26.30 | 20.91 | 23 | Low Income / Low Spending |

> Note: Cluster numbers are model-generated labels. The business segment names are based on the average income and spending values.

---

# 🟣 Hierarchical Clustering

Agglomerative Hierarchical Clustering was performed using:

```text
Linkage: Ward
Number of Clusters: 5
```

A dendrogram was used to understand the hierarchical structure and select an appropriate cluster count.

Hierarchical clustering produced broadly similar customer segments to K-Means because both methods use Annual Income and Spending Score.

---

# 🟢 DBSCAN Clustering

DBSCAN was used as a density-based clustering method.

### Parameter Search

The notebook tested:

```text
eps = 0.2, 0.3, 0.4, 0.5, 0.6
min_samples = 3, 4, 5, 6
```

The final model used:

```text
eps = 0.5
min_samples = 4
```

### Final DBSCAN Result

```text
Cluster 0 → 157 customers
Cluster 1 → 35 customers
Noise (-1) → 8 customers
```

DBSCAN is useful because it can identify dense customer groups and classify isolated observations as noise.

---

# 📈 Algorithm Comparison

| Algorithm | Clusters | Silhouette Score |
|---|---:|---:|
| 🔵 K-Means | 5 | **0.5547** |
| 🟣 Hierarchical | 5 | **0.5538** |
| 🟢 DBSCAN | 2 | 0.3876 |

### 🏆 Best Algorithm

**K-Means** achieved the highest Silhouette Score:

```text
0.5547
```

Therefore, K-Means is the best-performing algorithm in this notebook based on the reported Silhouette Score.

It also provides simple and easy-to-communicate customer segments for business interpretation.

---

# 💼 Business Insights

## 🟡 Segment 1 — Moderate Income / Moderate Spending

**K-Means Cluster 0**

These customers have average income and spending behaviour.

### Recommended Actions

- Seasonal promotions
- Cross-selling
- Loyalty incentives
- Personalised offers

---

## 🟢 Segment 2 — High Income / High Spending

**K-Means Cluster 1**

These are valuable customers with high spending potential.

### Recommended Actions

- VIP membership
- Premium products
- Exclusive events
- Personalised recommendations
- Loyalty rewards

---

## 🔵 Segment 3 — Low Income / High Spending

**K-Means Cluster 2**

These customers have lower income but relatively high spending scores.

### Recommended Actions

- Loyalty rewards
- Frequent-buyer discounts
- Value offers
- Customer retention campaigns

---

## 🔴 Segment 4 — High Income / Low Spending

**K-Means Cluster 3**

These customers have high purchasing potential but currently spend less.

### Recommended Actions

- Personalised recommendations
- Premium product promotions
- Targeted coupons
- Exclusive benefits
- Engagement campaigns

---

## 🟠 Segment 5 — Low Income / Low Spending

**K-Means Cluster 4**

These customers have both lower income and lower spending.

### Recommended Actions

- Budget-friendly products
- Discounts
- Value bundles
- Seasonal sales
- Affordable promotional offers

---

# 📸 Project Screenshots

Create a `screenshots/` folder in the GitHub repository and add the main notebook outputs.

Recommended screenshots:

```text
screenshots/
├── 01_eda_pairplot.png
├── 02_correlation_heatmap.png
├── 03_elbow_method.png
├── 04_silhouette_score.png
├── 05_kmeans_clusters.png
├── 06_kmeans_profile.png
├── 07_hierarchical_dendrogram.png
├── 08_hierarchical_clusters.png
├── 09_dbscan_4nn.png
├── 10_dbscan_clusters.png
├── 11_algorithm_comparison.png
└── 12_business_insights.png
```
## 📊 EDA Pairplot

**Objective:** Explore relationships and distributions among the customer features.

**Expected Output:** A pairplot showing relationships between Age, Annual Income, and Spending Score.
<img width="985" height="1023" alt="image" src="https://github.com/user-attachments/assets/2c08b875-eb75-4812-8fe6-a8b02856d576" />



## 🔥 Correlation Heatmap

**Objective:** Analyze the correlation between numerical customer features.

**Expected Output:** A correlation heatmap showing the strength and direction of relationships between Age, Annual Income, and Spending Score.
<img width="985" height="1023" alt="image" src="https://github.com/user-attachments/assets/9db2d13a-55fe-4033-9dc7-2fc11cf2af9d" />



## 📉 Elbow Method

**Objective:** Determine the optimal number of clusters (K) for K-Means clustering.

**Expected Output:** An Elbow Method plot showing the relationship between the number of clusters (K) and within-cluster sum of squares (WCSS/Inertia).
<img width="773" height="547" alt="image" src="https://github.com/user-attachments/assets/e82e8cd3-05d6-4ae5-89d2-1292d443d2fd" />




## 📊 Silhouette Score

**Objective:** Evaluate the quality of K-Means clustering for different numbers of clusters (K) using the Silhouette Score.

**Expected Output:** A plot showing the Silhouette Score for different K values, with the highest score indicating the best K.
<img width="777" height="547" alt="image" src="https://github.com/user-attachments/assets/b1b2551c-9e25-41ab-b12e-7fa62fb3e8f7" />



## 👥 K-Means Clusters

**Objective:** Visualize the customer segments created using the K-Means clustering algorithm.

**Expected Output:** A scatter plot showing customers grouped into different K-Means clusters based on Annual Income and Spending Score.
### Example README image section



## 📊 K-Means Cluster Profile

**Objective:** Analyze the characteristics of each customer cluster using average Age, Annual Income, and Spending Score.

**Expected Output:** A cluster profile showing the average customer attributes and customer count for each K-Means cluster.



## 🌳 Hierarchical Dendrogram

**Objective:** Visualize the hierarchical relationships between customers and identify a suitable number of clusters.

**Expected Output:** A dendrogram showing how customer groups are merged at different distance levels.




## 👥 Hierarchical Clusters

**Objective:** Visualize customer segments created using Hierarchical Clustering.

**Expected Output:** A scatter plot showing customers grouped into hierarchical clusters based on Annual Income and Spending Score.




## 📍 DBSCAN 4-NN Distance Plot

**Objective:** Determine a suitable `eps` value for DBSCAN using the 4-nearest-neighbor distance plot.

**Expected Output:** A sorted 4-NN distance plot where the knee point helps identify an appropriate `eps` value.




## 🔵 DBSCAN Clusters

**Objective:** Visualize customer segments identified by the DBSCAN clustering algorithm.

**Expected Output:** A scatter plot showing DBSCAN clusters and noise points separately.





## 📊 Algorithm Comparison

**Objective:** Compare K-Means, Hierarchical Clustering, and DBSCAN using the same customer features.

**Expected Output:** A three-panel visualization showing the clustering results of all three algorithms.





## 💼 Business Insights

**Objective:** Translate customer segments into actionable business strategies for mall management.

**Expected Output:** Clear customer segment interpretations and targeted marketing recommendations for each segment.






```markdown
## 📸 Screenshots

### 🔵 K-Means Clustering
![K-Means Clustering](screenshots/05_kmeans_clusters.png)

### 🟣 Hierarchical Clustering
![Hierarchical Clustering](screenshots/08_hierarchical_clusters.png)

### 🟢 DBSCAN Clustering
![DBSCAN Clustering](screenshots/10_dbscan_clusters.png)

### 📊 Algorithm Comparison
![Algorithm Comparison](screenshots/11_algorithm_comparison.png)
```

---

# 📓 Jupyter Notebook

The complete project workflow is available in:

```text
Customer_segmentation.ipynb
```

The notebook covers:

```text
Data Loading
    ↓
Data Cleaning
    ↓
EDA
    ↓
Preprocessing
    ↓
Feature Scaling
    ↓
K-Means
    ↓
Hierarchical Clustering
    ↓
DBSCAN
    ↓
Algorithm Comparison
    ↓
Business Insights
```

---

# 🌐 HTML Report

Export the completed notebook as HTML and keep it in the repository:

```text
Customer_segmentation.html
```

### Recommended README link

```markdown
## 🌐 HTML Report

📄 [View the Complete HTML Report](Customer_segmentation.html)
```

The HTML version allows the project to be viewed without opening or executing the Jupyter Notebook.

---

# 🎥 Project Demo Video

Add your project demonstration video to YouTube, Google Drive, or another accessible platform.

Replace the placeholder below with your actual video URL:

```markdown
## 🎥 Project Demo Video

▶️ [Watch the Project Demo](PASTE_YOUR_VIDEO_LINK_HERE)
```

### Suggested video content

```text
1. Project introduction
2. Dataset overview
3. EDA
4. K-Means clustering
5. Hierarchical clustering
6. DBSCAN
7. Algorithm comparison
8. Business insights
9. Final conclusion
```

---

# 📁 Project Structure

Recommended GitHub structure:

```text
Mall-Customer-Segmentation/
│
├── README.md
├── Customer_segmentation.ipynb
├── Customer_segmentation.html
├── Mall_Customers.csv
├── customer_segmentation_model.pkl
├── rfm_scaler.pkl
├── requirements.txt
├── summary_report.md
│
└── screenshots/
    ├── 01_eda_pairplot.png
    ├── 02_correlation_heatmap.png
    ├── 03_elbow_method.png
    ├── 04_silhouette_score.png
    ├── 05_kmeans_clusters.png
    ├── 06_kmeans_profile.png
    ├── 07_hierarchical_dendrogram.png
    ├── 08_hierarchical_clusters.png
    ├── 09_dbscan_4nn.png
    ├── 10_dbscan_clusters.png
    └── 11_algorithm_comparison.png
```

---

# 🧰 Technologies Used

| Technology | Purpose |
|---|---|
| 🐍 Python | Programming |
| 🐼 Pandas | Data Analysis |
| 🔢 NumPy | Numerical Computing |
| 📊 Matplotlib | Visualization |
| 🎨 Seaborn | Statistical Visualization |
| 🤖 Scikit-learn | Clustering & Preprocessing |
| 🧪 SciPy | Hierarchical Clustering |
| 📓 Jupyter Notebook | Development |

The project's `requirements.txt` contains Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, SciPy, and Jupyter. 

---

# ⚙️ Installation

Clone or download the repository and open the project folder in VS Code.

Install dependencies:

```bash
pip install -r requirements.txt
```

Or install the libraries directly:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

---

# ▶️ How to Run

### Step 1 — Open the project

Open the project folder in VS Code.

### Step 2 — Install requirements

```bash
pip install -r requirements.txt
```

### Step 3 — Open the notebook

```text
Customer_segmentation.ipynb
```

### Step 4 — Select Python Kernel

Select your Python environment from the top-right of VS Code.

### Step 5 — Run the notebook

Use:

```text
Run All
```

or execute the cells from top to bottom.

### Step 6 — Check generated files

The project can contain:

```text
customer_segmentation_model.pkl
rfm_scaler.pkl
```

---

# 💾 Saved Model

The trained K-Means model is saved as:

```text
customer_segmentation_model.pkl
```

It can be loaded using Joblib:

```python
import joblib

model = joblib.load("customer_segmentation_model.pkl")
```

The notebook also creates:

```text
rfm_scaler.pkl
```

for the saved StandardScaler artifact.

---

# 📌 Key Learnings

Through this project, the following concepts were practiced:

- Unsupervised Learning
- Exploratory Data Analysis
- Feature Encoding
- Feature Scaling
- K-Means Clustering
- Elbow Method
- Silhouette Score
- Agglomerative Hierarchical Clustering
- Dendrogram
- DBSCAN
- Hyperparameter tuning
- Noise detection
- Cluster profiling
- Business segmentation
- Model persistence using Joblib

---

# 🚀 Future Improvements

- Add PCA-based visualisation.
- Test clustering using all available numerical features.
- Tune DBSCAN parameters further.
- Build an interactive Streamlit customer segmentation app.
- Create a customer segment prediction interface.
- Add automated model evaluation.
- Add dashboard visualisations for business users.
- Deploy the segmentation application online.

---

# 🏁 Conclusion

This project demonstrates an end-to-end **Unsupervised Learning workflow** for Mall Customer Segmentation.

K-Means achieved the highest reported Silhouette Score of **0.5547**, slightly higher than Hierarchical Clustering at **0.5538**, while DBSCAN achieved **0.3876**.

The analysis identifies five interpretable customer segments:

```text
🟡 Moderate Income / Moderate Spending
🟢 High Income / High Spending
🔵 Low Income / High Spending
🔴 High Income / Low Spending
🟠 Low Income / Low Spending
```

These segments can help mall management design targeted marketing campaigns, loyalty programs, personalised offers, and customer retention strategies.

---

# 👨‍💻 Author

## Rahul Zala

**Python • Data Analytics • Machine Learning • Unsupervised Learning**

---

<p align="center">
  <b>🛍️ Segment Customers • 📊 Analyze Behaviour • 🎯 Target Better • 🚀 Grow Business</b>
</p>

⭐ If you foun
