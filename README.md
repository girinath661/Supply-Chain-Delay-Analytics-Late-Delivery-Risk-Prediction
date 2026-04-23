# Supply Chain Delay Analytics & Late Delivery Risk Prediction

A end-to-end data analysis and machine learning project on a global e-commerce supply chain dataset to identify delivery bottlenecks, quantify profit loss from delays, and predict late delivery risk using a Random Forest Classifier.

---

## Business Problem

A global e-commerce company managing order fulfillment across multiple regions was facing inconsistent delivery performance — actual shipping times frequently deviated from scheduled timelines, leading to late deliveries and unpredictable profitability.

**Goal:** Analyze delivery operations, identify bottlenecks, and build a predictive system to reduce delays, optimize shipping decisions, and improve overall profitability.

---

## Dataset

- **Source:** DataCo Supply Chain Dataset
- **Size:** 180,000+ orders
- **Features:** 53 columns including order dates, shipping mode, customer segment, department, region, profit, and delivery status

---

## Project Structure

```
Supply-Chain-Analysis/
│
├── Supply_Chain_Data_Analysis_Project.ipynb   # Main notebook
├── README.md                                  # Project documentation
└── DataCoSupplyChainDataset.csv               # Dataset (not uploaded due to size)
```

---

## Workflow

### 1. Data Cleaning & ETL
- Dropped 33 redundant, PII, and zero-variance columns
- Removed cancelled orders irrelevant to delivery analysis
- Parsed datetime columns and handled missing values
- Validated data quality via duplicate checks and null counts

### 2. Feature Engineering
Created 6 business-critical features from raw data:

| Feature | Description |
|---|---|
| `Order Processing Time` | Actual days from order to shipment |
| `Delay` | Actual processing time minus scheduled days |
| `Is_Delayed` | Boolean flag — True if Delay > 0 |
| `Profitability Flag` | Profit / Loss / Break-even per order |
| `order_month` | Month extracted from order date |
| `order_day` | Day of week extracted from order date |
| `order_hour` | Hour extracted from order date |

### 3. Business KPI Dashboard
Computed executive-level operational metrics:

- Total Orders
- Late Deliveries count and %
- On-Time Delivery %
- 90th Percentile Delay (days)
- Total Profit
- Total Loss attributed to delayed shipments

### 4. Profitability vs Delay Analysis
- Grouped profit metrics (mean, total, count) by delay day
- Visualized delay distribution and profit impact using dual-axis charts
- Identified the financial cost of each additional day of delay

### 5. Bottleneck Detection
Computed delay percentage across 6 operational dimensions:
- Order Region
- Customer Segment
- Shipping Mode
- Order Status
- Payment Type
- Department Name

### 6. Root Cause Analysis
Built a reusable function to identify **top 10 delay drivers** within any region by cross-analyzing multiple factors — enabling targeted, region-specific operational recommendations.

### 7. Time-Series Trend Analysis
Analyzed delay rates across:
- Month of year
- Day of week
- Hour of day

Annotated top 3 highest-risk periods to surface scheduling patterns.

### 8. Machine Learning — Late Delivery Risk Prediction

| Step | Detail |
|---|---|
| Features | Type, Scheduled Shipment Days, Category, Segment, Department, Region, Shipping Mode, Month, Hour |
| Encoding | Frequency encoding on 6 high-cardinality categorical columns |
| Class Imbalance | SMOTE oversampling on training data |
| Train-Test Split | 80/20 stratified split |
| Model | Random Forest Classifier |
| Evaluation | Accuracy, Precision, Recall, Classification Report |

---

## Key Results

- Identified that **54%+ of orders** were delivered late
- Quantified total revenue loss attributed to delayed shipments
- Pinpointed highest-risk regions, shipping modes, and customer segments
- Built a predictive model to flag late delivery risk before shipment

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| Data Wrangling | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-Learn, Imbalanced-learn (SMOTE) |
| Environment | Jupyter Notebook |

---

## How to Run

1. Clone the repository
```bash
git clone https://github.com/girinath661/supply-chain-analysis
cd supply-chain-analysis
```

2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
```

3. Download the dataset from [Kaggle — DataCo Supply Chain Dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) and place it in the project folder

4. Open and run the notebook
```bash
jupyter notebook Supply_Chain_Data_Analysis_Project.ipynb
```

---

## Author

**Girinath Reddy Pullalarevua**  
[LinkedIn](https://linkedin.com/in/pullalarevua-girinath-reddy) | [GitHub](https://github.com/girinath661)
