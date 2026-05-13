# 🛍️ Customer Shopping Behavior Analysis

An end-to-end data analytics project built on a retail customer behavior dataset. The goal was to answer a real business question: how can a company use its transaction data to improve customer engagement, reduce churn, and sharpen its marketing strategy?

The project follows a complete analytics workflow — raw data to cleaned insights to an executive-ready dashboard — covering Python, SQL, Power BI, and a formal project report.

---

## 📁 Repository Structure

```
Customer Behaviour Project/
├── problem-based-data-analysis.ipynb       # Data cleaning, EDA & feature engineering (Python)
├── customer_shopping_behavior.csv          # Raw dataset (3,900 rows, 18 features)
├── customer_behavior_dashboard.pbix        # Interactive Power BI dashboard
├── customer_shopping_behavior_report.pdf   # Full project report with findings & recommendations
└── Consumer-Shopping-Behavior-Analysis.pptx  # Presentation deck for stakeholders
```

---

## 🧩 Business Problem

> *"How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"*

A retail company noticed shifts in purchasing patterns across demographics, product categories, and sales channels. This project breaks down those patterns and offers concrete answers.

---

## 🔧 Tools & Technologies

| Layer | Tool |
|---|---|
| Data Cleaning & EDA | Python (pandas) |
| Database & Querying | PostgreSQL + SQLAlchemy |
| Visualization | Power BI |
| Documentation | PDF Report |
| Presentation | PowerPoint (Gamma AI) |

---

## 📊 Dataset Overview

- **Rows:** 3,900 customer transactions
- **Features:** 18 columns including age, gender, category, purchase amount, season, review rating, payment method, shipping type, subscription status, and purchase frequency

**Missing values:** Only `review_rating` had 37 nulls (~1%), handled using category-wise median imputation to avoid introducing bias.

---

## ⚙️ What Was Done

### 1. Data Preparation (Python)
- Loaded and inspected the raw CSV
- Imputed missing `review_rating` values using per-category median
- Renamed all columns to `snake_case` for clean SQL compatibility
- Discovered `discount_applied` and `promo_code_used` were perfectly identical — dropped the redundant column

### 2. Feature Engineering
- **`age_group`** — Bucketed customers into `Young Adult`, `Adult`, `Middle-aged`, and `Senior` using `pd.qcut()`
- **`purchase_frequency_days`** — Converted text frequency labels (e.g., "Fortnightly", "Every 3 Months") into numeric day values for SQL sorting and aggregation

### 3. SQL Integration (PostgreSQL)
- Loaded the cleaned dataframe into a local PostgreSQL database using SQLAlchemy
- Connected from Kaggle using **Bore** (a tunneling tool) to bridge the cloud-to-local network gap
- Used `chunksize=500` in `to_sql()` to prevent connection timeouts during upload

### 4. Power BI Dashboard
- Built an interactive dashboard visualizing key metrics across categories, seasons, demographics, and payment methods

### 5. Project Report & Presentation
- Wrote a structured PDF report covering methodology, key findings, and 5 business recommendations
- Prepared a stakeholder presentation deck

---

## 📌 Key Findings

- **Clothing dominates** at 44.5% of transactions, but average spend is nearly identical across all four categories (~$59–60), meaning the gap is about volume, not ticket size
- **43% of purchases used a promo code** — a high enough share to question whether discounts are driving incremental sales or just training customers to wait for deals
- **Only 27% of customers subscribe**, yet the average customer has 25 prior purchases — a clear opportunity to convert loyal buyers into subscribers
- **Purchase volume is flat across all four seasons** — either the product mix is well-diversified, or seasonal campaigns aren't creating demand peaks
- **Payment methods and shipping preferences are evenly distributed** across six options each — no dominant preference, which has infrastructure and UX implications

---

## 💡 Business Recommendations

1. **Grow the subscription base** — Target high-frequency non-subscribers with a first-month incentive
2. **Rethink the discount strategy** — A/B test discount-free campaigns to measure true incremental impact
3. **Run seasonal campaigns** — Use the flat seasonal data as a baseline and create deliberate peaks, especially for Outerwear (winter) and Footwear (spring)
4. **Segment by age group** — The `age_group` feature enables targeted campaigns; Young Adults and Seniors likely respond to very different messaging
5. **Streamline payment UX** — Analyze which payment methods correlate with higher order value or repeat purchases before investing further in all six equally

---

## 🚀 How to Run

**Python Notebook**
```bash
# Install dependencies
pip install pandas sqlalchemy psycopg2-binary

# Open the notebook
jupyter notebook problem-based-data-analysis.ipynb
```

**Power BI Dashboard**
Open `customer_behavior_dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/)

---

## 📄 Report

The full analysis, methodology, and recommendations are documented in `customer_shopping_behavior_report.pdf`.

---

## 🙏 Credits

Project built following the tutorial by **Amlan Mohanty** — [YouTube](https://youtu.be/5PrZvPeUw60) · [LinkedIn](https://www.linkedin.com/in/amlanmohanty1/)

---

## 📬 Connect

**Kingshuk Datta** — [GitHub](https://github.com/KingshukDatta)

---

*MIT License — see `LICENSE` for details*
