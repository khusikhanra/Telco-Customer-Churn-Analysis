# 📉 Telco Customer Churn — Predictive Analytics & Retention Intelligence

**An end-to-end churn intelligence solution combining machine learning prediction with an executive-grade BI dashboard — built to turn raw customer data into retention revenue.**

![Python](https://img.shields.io/badge/Python-3.10-3776AB?logo=python&logoColor=white)
![Scikit--Learn](https://img.shields.io/badge/Scikit--Learn-ML%20Models-F7931E?logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-success)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

## 📌 Project Overview

Customer churn is the single most expensive problem in subscription-based businesses — acquiring a new customer costs **5–7x more** than retaining an existing one. This project tackles that problem head-on for a telecom provider, delivering two connected deliverables:

1. **A predictive ML pipeline** that flags customers likely to churn *before* they leave, achieving **94% accuracy** on held-out test data.
2. **An interactive Retention Command Center dashboard** that translates those predictions into prioritized, dollar-quantified business actions for retention teams.

This isn't just a model in a notebook — it's a decision-support system designed the way a BI consultant would hand it to a client: model → insight → dashboard → action.

---

## 💼 Business Impact

| Metric | Finding |
|---|---|
| 💰 Revenue at risk | **$1.67M annualized** revenue exposed to churn |
| 📊 Overall churn rate | **26.5%** of customers (1,869 of 7,043) churned |
| 🎯 Best model accuracy | **94%** (Random Forest + SMOTEENN) |
| 🔍 Churn recall (caught) | **97%** of actual churners correctly identified |
| ⏱️ Highest-risk window | First 12 months of tenure (**47.7% churn rate**) |

---

## 🔬 Key Insights from Exploratory Analysis

Data-driven patterns extracted from 7,043 customer records that directly shape the retention strategy:

| Driver | Churn Rate | Insight |
|---|---|---|
| **Contract type** | Month-to-month: 42.7% vs Two-year: 2.8% | Contract length is the single strongest churn lever — locking customers into longer terms cuts risk by ~15x |
| **Payment method** | Electronic check: 45.3% vs Credit card (auto): 15.2% | Manual payment methods correlate with disengagement; auto-pay customers are far stickier |
| **Internet service** | Fiber optic: 41.9% vs DSL: 19.0% | Fiber customers churn more — likely a pricing/service-quality gap worth investigating |
| **Tech support / online security** | No support: ~41.7% vs With support: ~14.9% | Customers without add-on support services are over 2.5x more likely to leave |
| **Tenure** | 0–12 months: 47.7% vs 61–72 months: 6.6% | Churn risk drops sharply with loyalty — the first year is the critical retention window |
| **Senior citizens** | 41.7% vs 23.6% (non-seniors) | Senior customers churn at nearly double the rate of the general base |
| **Monthly charges** | Churned avg: $74.44 vs Retained avg: $61.27 | Higher-paying customers are disproportionately at risk — these are also the most valuable to save |

---

## 🤖 Machine Learning Pipeline

### Workflow
```
Raw CSV → Data Cleaning → Feature Engineering (tenure binning, encoding)
        → Class Imbalance Handling (SMOTEENN) → Model Training & Comparison
        → Best Model Selection → Serialized Model (model.sav) → Dashboard Integration
```

### Models Evaluated

| Model | Accuracy | Churn Precision | Churn Recall | Churn F1-Score |
|---|---|---|---|---|
| Decision Tree (baseline) | 79% | 0.61 | 0.48 | 0.54 |
| Decision Tree + SMOTEENN | 92% | 0.92 | 0.94 | 0.93 |
| Random Forest + PCA | 81% | 0.69 | 0.47 | 0.56 |
| **Random Forest + SMOTEENN** ⭐ | **94%** | **0.93** | **0.97** | **0.95** |

The baseline models struggled with **class imbalance** (only 26.5% of customers churn), producing high accuracy but poor recall on the minority class — the exact customers the business needs to catch. Applying **SMOTEENN** (a combined over/under-sampling technique) corrected this, and the final **Random Forest classifier** was selected and serialized for production use, catching **97% of true churners** with strong precision.

---

## 📊 Interactive Dashboard — Retention Command Center

A self-contained, single-file HTML dashboard (`telco_churn_dashboard.html`) built for non-technical stakeholders to explore and act on the model's output without touching a notebook.

**Dashboard sections:**
- **Executive Overview** — headline revenue-at-risk figure, churn vs. retained split, early-tenure loss trends, and top churn-rate gaps vs. baseline
- **Customer Demographics & Segmentation** — churn rate by demographic combination, monthly charges vs. tenure relationship
- **Service & Contract Drivers** — churn rate across service dimensions, a drill-down path (Contract → Internet → Tech Support), and a key-influencers confirmation layer
- **Predictive Risk & Retention Action** — a retention campaign what-if simulator, a high-risk customer action table, and a model credibility panel for stakeholder trust

Built with synced cross-filtering slicers so any stakeholder can isolate a segment and instantly see its churn exposure — no SQL or Python required.

---

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| Data Processing | Python, Pandas, NumPy |
| Visualization (EDA) | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn (Decision Tree, Random Forest, PCA), imbalanced-learn (SMOTEENN) |
| Model Persistence | Pickle |
| BI Dashboard | HTML, CSS, JavaScript (interactive, no external dependencies) |
| Environment | Jupyter Notebook |

---

## 📁 Repository Structure

```
├── Telco_Churn_Prediction_Analysis.ipynb   # Full EDA + ML pipeline (data cleaning → model training)
├── telco_churn_dashboard.html              # Interactive BI dashboard (open directly in browser)
├── WA_Fn-UseC_-Telco-Customer-Churn.csv     # Source dataset (IBM Telco Customer Churn, 7,043 rows)
└── README.md                               # Project documentation
```

---

## 🚀 How to Run

**1. Clone the repository**
```bash
git clone https://github.com/khusikhanra/telco-churn-prediction.git
cd telco-churn-prediction
```

**2. Set up the environment**
```bash
pip install pandas numpy scikit-learn seaborn matplotlib imbalanced-learn jupyter
```

**3. Run the analysis**
```bash
jupyter notebook Telco_Churn_Prediction_Analysis.ipynb
```

**4. Explore the dashboard**
Simply open `telco_churn_dashboard.html` in any modern browser — no server or installation needed.

---

## 🔮 Future Enhancements

- Deploy the trained model as a REST API (Flask/FastAPI) for real-time scoring
- Add SHAP-based explainability so retention agents see *why* a customer is flagged
- Automate the pipeline with scheduled retraining as new customer data arrives
- A/B test retention offers against the model's risk segments to quantify ROI

---

## 👤 About the Author

**Khusi Khanra**
Business Intelligence & Automation Consultant

Building data-driven decision systems that bridge machine learning and business action — from predictive models to executive dashboards.

📫 Feel free to connect or reach out for collaboration opportunities.

---

⭐ If you found this project useful, consider giving it a star!
