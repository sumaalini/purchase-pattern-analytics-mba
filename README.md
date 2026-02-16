
# 🛒 Purchase Pattern Analytics – Market Basket Analysis (MBA)

## 📌 Overview

This project applies Market Basket Analysis (MBA) to uncover product associations and purchasing patterns from a large retail transaction dataset.

Using Exploratory Data Analysis, extensive data cleaning, and the Apriori algorithm, the project identifies:

* Frequently co-purchased product combinations
* High-value customers
* Seasonal sales trends
* Actionable bundling opportunities

The goal is to support data-driven decisions in cross-selling, inventory planning, and customer targeting.

---

## 🧩 Business Problem

Retail transactions often contain hidden co-purchase relationships that are not immediately visible.

This project aims to:

* Detect frequently bought-together product groups
* Generate association rules using Apriori
* Identify seasonal demand trends
* Recommend product bundling strategies

---

## 📊 Dataset Information

**Raw Dataset Size**

* 522,064 rows (original)
* 516,778 rows after duplicate removal
* 6,138 final transaction-level records (after grouping)

**Final Cleaned Dataset**

* 6,138 transactions
* 3,600 unique items

**Key Columns**

* BillNo
* ItemName
* Quantity
* Price
* CustomerID
* Country
* Present_Date

---

## 🛠 Tools & Technologies

### Data Cleaning & Transformation

* Power Query
* Power BI
* DAX

### Market Basket Analysis

* Python (Jupyter Notebook)
* Pandas
* mlxtend (Apriori, association_rules)

### Visualization

* Power BI Dashboards

---

## 🔄 Data Cleaning Process

Major issues handled:

* Removed missing or invalid ItemName values
* Standardized product names (case, spelling, special characters)
* Removed negative/zero Quantity and Price
* Replaced missing CustomerID with "Unknown"
* Grouped data to transaction level by BillNo
* Removed incomplete transactions

Duplicates removed: **5,286 rows**

Final dataset prepared specifically for Apriori analysis.

---

## 📈 Exploratory Data Analysis (EDA)

### Key Statistics

* Mean Quantity: 10.08
* Median Quantity: 3
* Mean Price: 3.82

### Observations

* United Kingdom dominates transactions
* Top customer purchased ~192,000 units
* Strong seasonal spikes in November–December
* Sales follow a long-tail distribution (few products drive majority of sales)

---

## 🤖 Apriori Implementation

```python
from mlxtend.frequent_patterns import apriori, association_rules

freq_itemsets = apriori(trans_df, min_support=0.01, use_colnames=True)
rules = association_rules(freq_itemsets, metric="confidence", min_threshold=0.3)
```

### Parameters

* min_support = 0.01
* metric = confidence
* min_threshold = 0.3

### Output

* 2,330 frequent itemsets
* 3,664 association rules

---

## 🔎 Key Findings

### 🔹 Strong Product Associations

HERB MARKER product combinations showed extremely high lift values (>80), indicating strong co-purchase behavior.

### 🔹 Seasonal Trends

Sales peak significantly during October–December (holiday season).

### 🔹 Customer Behavior

* Heavy dependency on UK customers
* Few high-value customers drive disproportionate sales
* Most baskets contain single items

### 🔹 Rule Strength

* Average Lift: 22.50
* Average Confidence: 0.59
* Most rules have low support (~0.01), so filtering is required for production use

---

## 💡 Business Recommendations

* Bundle strongly associated HERB MARKER products
* Increase marketing during peak seasonal months
* Focus loyalty programs on top customers
* Place associated products together in-store
* Improve ItemName standardization for better analytics

---

## ⚠ Limitations

* Low-support rules reduce reliability at scale
* Dataset heavily dominated by UK transactions
* Missing CustomerID limits deeper segmentation
* Apriori is computationally expensive for very large datasets

---

## 📊 Dashboard Highlights

The Power BI dashboard includes:

* Top 10 products by quantity
* Seasonal sales trends
* Lift vs Confidence scatter plot
* Association rule table
* KPI cards (Total Rules, Avg Confidence, Avg Lift)
* Interactive slicers for Date, Country, CustomerID, Items

---

## 🚀 Project Outcome

This project demonstrates:

* End-to-end data cleaning and transformation
* Transaction-level restructuring for MBA
* Association rule mining using Apriori
* Visualization of rule strength and seasonal demand
* Translation of analytical results into business recommendations

