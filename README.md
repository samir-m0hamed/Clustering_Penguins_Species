# 🐧 Clustering Palmer Penguins Species using K-Means

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange.svg)
![Plotly](https://img.shields.io/badge/Visualization-Plotly-green.svg)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📌 Project Overview
This project implements an **Unsupervised Machine Learning pipeline** to identify patterns and groupings among Palmer Penguins based on their physical characteristics. Using the **K-Means Clustering** algorithm, the model segments the penguins into distinct clusters without relying on pre-existing species labels. 

The project emphasizes robust **Exploratory Data Analysis (EDA)**, rigorous **data preprocessing**, and mathematical validation techniques (Elbow Method & Silhouette Analysis) to determine the optimal number of clusters.

## 📂 Dataset
The dataset used is the **Palmer Archipelago (Antarctica) penguin data**.
* **Source:** [Kaggle - Clustering Penguins Species](https://www.kaggle.com/datasets/youssefaboelwafa/clustering-penguins-species)
* **Features Used:**
    * `culmen_length_mm`: Length of the dorsal ridge of the bird's bill.
    * `culmen_depth_mm`: Depth of the bill.
    * `flipper_length_mm`: Length of the flipper.
    * `body_mass_g`: Body mass in grams.
    * `sex`: Penguin gender (Mapped and encoded).

## 🛠️ Technologies & Tools
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn (KMeans, StandardScaler, Silhouette Score)
* **Visualization:** Plotly Express & Plotly Graph Objects (Interactive plots)

## ⚙️ Methodology

### 1. Exploratory Data Analysis (EDA)
* Conducted univariate analysis using **Plotly histograms** to understand the distribution of features.
* Identified potential outliers and missing values in the `sex` and `flipper_length_mm` columns.

### 2. Data Preprocessing & Cleaning
* **Handling Nulls:** Removed rows with missing values to ensure data integrity.
* **Outlier Removal:** Filtered out logical inconsistencies (e.g., specific rows where `sex` was undefined or flipper length was physically impossible/outliers).
* **Encoding:** Mapped categorical data (`sex`) to numerical format (`FEMALE: 0`, `MALE: 1`).
* **Feature Scaling:** Applied **StandardScaler** to normalize `culmen_length`, `culmen_depth`, `flipper_length`, and `body_mass`.
    * *Why?* K-Means relies on Euclidean distance; scaling prevents features with larger magnitudes (like body mass) from dominating the distance calculations.

### 3. Model Selection (Finding Optimal K)
Two methods were used to determine the best number of clusters (K):
1.  **The Elbow Method:** Plotted WCSS (Within-Cluster Sum of Square) against K. Observed the "elbow" point where inertia reduction slows down.
2.  **Silhouette Analysis:** Calculated silhouette scores for K ranges (2-15) to measure cluster cohesion and separation.
    * *Result:* Based on the analysis, **K=6** was selected to capture granular distinct groups (likely correlating to Species × Sex combinations).

### 4. Model Training
* **Algorithm:** K-Means Clustering.
* **Initialization:** Used `init='k-means++'` to ensure smart centroid initialization and avoid the random initialization trap.
* **Configuration:** `n_clusters=6`, `random_state=42` for reproducibility.

## 📊 Results & Visualization
The final model segmented the data into 6 distinct clusters. The results were visualized using **interactive scatter plots** mapping `culmen_length_mm` vs `culmen_depth_mm`, colored by the predicted cluster.

* **Silhouette Score:** Achieved a score of approx **0.43** for K=6, indicating reasonable separation given the overlapping nature of biological data.
* The clusters successfully differentiated penguins based on size and gender characteristics.

## 👨🏻‍💻 Author
**[Samir Mohamed]** *AI Engineer & Data Scientist* 
