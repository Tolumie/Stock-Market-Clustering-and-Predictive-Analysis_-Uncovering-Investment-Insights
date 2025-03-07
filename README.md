# **Stock Market Clustering and Predictive Analysis: Uncovering Investment Insights**  

## **Table of Contents**  
1. [Introduction](#introduction)  
2. [Data Description](#data-description)  
3. [Data Exploration and Preprocessing](#data-exploration-and-preprocessing)  
4. [Unsupervised Model Training and Evaluation](#unsupervised-model-training-and-evaluation)  
5. [Model Selection and Key Findings](#model-selection-and-key-findings)  
6. [Comparison with K-Means and Hierarchical Clustering](#comparison-with-k-means-and-hierarchical-clustering)  
7. [Investment Strategy Implications](#investment-strategy-implications)  
8. [Next Steps](#next-steps)  
9. [Final Takeaway](#final-takeaway)  

---

## **1. Introduction**  
This project applies **unsupervised learning** to segment S&P 500 stocks based on financial characteristics such as returns, volatility, P/E ratio, dividend yield, and market capitalization. The objective is to help investors and portfolio managers **optimize investment strategies** by identifying market patterns beyond traditional sector-based allocations.  

Using **DBSCAN, K-Means, and Hierarchical Clustering**, this analysis uncovers distinct stock clusters and high-risk outliers, offering **a deeper understanding of portfolio risks and opportunities**.  

---

## **2. Data Description**  
The dataset consists of **historical stock data (2021–2024) for ten major S&P 500 companies**:  
**AAPL, MSFT, GOOGL, AMZN, TSLA, NVDA, META, NFLX, JPM, XOM.**  

### **Key Features Used:**  
- **Daily Returns & Rolling Volatility** – Measures price fluctuations.  
- **P/E Ratio** – Evaluates stock valuation.  
- **Dividend Yield** – Identifies income-generating stocks.  
- **Market Capitalization** – Classifies stock sizes.  

---

## **3. Data Exploration and Preprocessing**  
- **Feature Engineering:**  
  - Computed **30-day rolling volatility** and average daily returns.  
  - Imputed missing fundamental data using **sector-based median values**.  
- **Feature Scaling & Dimensionality Reduction:**  
  - Applied **StandardScaler** to normalize data.  
  - Used **PCA (Principal Component Analysis)** to reduce features to **two components (PC1 & PC2), explaining 70.5% of the variance**.  

---

## **4. Unsupervised Model Training and Evaluation**  

Three clustering models were trained and evaluated:  

### **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)**  
- **Parameters:** eps = 0.9, min_samples = 3  
- **Findings:**  
  - Identified **27% of stocks as noise/outliers**, including **NVDA, TSLA, NFLX**.  
  - Captured **high-volatility, high-growth stocks** that standard clustering missed.  

### **K-Means Clustering**  
- **Optimal k = 3 (Silhouette Score: 0.5090)**  
- **Findings:**  
  - Assigned all stocks to clusters but **failed to detect outliers**.  

### **Hierarchical Clustering**  
- **Optimal k = 3 (Silhouette Score: 0.5133)**  
- **Findings:**  
  - Improved segmentation, but lacked DBSCAN’s ability to handle outliers.  

---

## **5. Model Selection and Key Findings**  

**DBSCAN provided the most insightful clustering results:**  
- Isolated **high-risk outliers (NVDA, TSLA, NFLX)** that traditional methods misclassified.  
- Grouped **stable, dividend-paying stocks (JPM, XOM, KO) into distinct low-risk clusters**.  
- Provided **a more flexible segmentation approach without forcing stocks into predefined clusters**.  

### **Cluster Insights**  
| Cluster | Stocks | Characteristics |
|---------|---------|----------------|
| **Cluster 0** | XOM, JPM | Low volatility, high stability, dividend-paying stocks. |
| **Cluster 1** | AAPL, AMZN, GOOGL, META, MSFT | Growth-oriented tech stocks, moderate risk. |
| **Outliers (-1)** | NVDA, TSLA, NFLX | High volatility, high-growth potential, risk-prone. |

---

## **6. Comparison with K-Means and Hierarchical Clustering**  

| Clustering Method | k | Silhouette Score | Outlier Detection | Insights |
|------------------|---|-----------------|-------------------|---------|
| **K-Means** | 3 | 0.5090 | ❌ No | Forced segmentation; grouped tech stocks together. |
| **Hierarchical** | 3 | 0.5133 | ❌ No | Better segmentation, but still lacked outlier detection. |
| **DBSCAN** | - | **N/A** | ✅ Yes | Identified **30% of stocks as outliers**, better capturing market nuances. |

---

## **7. Investment Strategy Implications**  

### **For General Investors:**  
- **Outliers (TSLA, NVDA, NFLX) require caution** due to extreme volatility.  

### **For Risk-Tolerant Investors:**  
- These stocks offer **high reward potential but need tailored risk management**.  

### **For Conservative Portfolios:**  
- **AAPL, AMZN, GOOGL, META, MSFT** provide stable growth with moderate risk.  
- **JPM, XOM** offer low volatility, making them **ideal for defensive strategies**.  

---

## **8. Next Steps**  

🔹 **Supervised Learning:** Build a classifier to **predict cluster membership** for new stocks.  
🔹 **Outlier Deep-Dive:** Analyze financial factors **driving outlier classification**.  
🔹 **Dynamic Clustering:** Assess **how stock clusters change over time**.  
🔹 **Feature Enrichment:** Incorporate **news sentiment, analyst ratings** for better predictions.  
🔹 **Parameter Optimization:** Fine-tune **DBSCAN’s eps and min_samples** for better segmentation.  

---

## **9. Final Takeaway**  
- **DBSCAN’s density-based clustering revealed key outliers** that traditional methods overlooked.  
- **It provides a powerful tool for portfolio diversification and risk-aware investing**.  
- This framework helps **investors refine their strategies based on real stock behavior** rather than predefined sector classifications.  

🚀 **Stay ahead of the market with data-driven insights!**  

---

### **📌 Repo Structure**  

```
📁 Stock-Market-Clustering-and-Predictive-Analysis  
│── 📄 README.md  
│── 📄 requirements.txt  
│── 📄 clustering_analysis.ipynb  
│── 📄 data_preprocessing.ipynb  
│── 📄 visualization.ipynb  
│── 📄 results_summary.md  
│── 📂 data/  
│     ├── historical_stock_data.csv  
│     ├── processed_data.csv  
│── 📂 models/  
│     ├── dbscan_model.pkl  
│     ├── kmeans_model.pkl  
│     ├── hierarchical_model.pkl  
```
