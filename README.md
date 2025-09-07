# Customer Churn Analysis

![Churn Distribution](https://img.shields.io/badge/Python-3.13-blue) ![License](https://img.shields.io/badge/License-MIT-green) ![Status](https://img.shields.io/badge/Status-Completed-success)

## Project Overview
This repository contains an Exploratory Data Analysis (EDA) on a customer churn dataset. The analysis is performed in a Jupyter Notebook (`Training Data -.ipynb`) using Python libraries like Pandas, NumPy, Matplotlib, Seaborn, and Plotly. The goal is to understand factors influencing customer churn, calculate churn rates, and visualize patterns across various features such as gender, age, support calls, payment delays, subscription types, and contract lengths.

The dataset used is `customer_churn_dataset-training-master.csv`, which includes customer details like Age, Gender, Tenure, Usage Frequency, Support Calls, Payment Delay, Subscription Type, Contract Length, Total Spend, Last Interaction, and Churn (binary: 0 for no churn, 1 for churn).

### Key Objectives
- Calculate overall churn percentage.
- Analyze churn rates by demographic and behavioral features.
- Visualize distributions and correlations to identify high-risk customer segments.
- Provide actionable insights for reducing churn (e.g., targeting high-support-call customers or monthly contract holders).

## Dataset
- **Source:** Loaded from local path (`C:\Users\Asus\OneDrive\Desktop\sewa\customer\customer_churn_dataset_ task\customer_churn_dataset-training-master.csv`).
- **Shape:** 440,833 rows × 12 columns.
- **Features:**
  - **CustomerID:** Unique identifier (float).
  - **Age:** Customer age (float, range: 18–65).
  - **Gender:** Male/Female (object).
  - **Tenure:** Months with the service (float, range: 1–60).
  - **Usage Frequency:** Usage count (float, range: 1–30).
  - **Support Calls:** Number of support interactions (float, range: 0–10).
  - **Payment Delay:** Days delayed in payment (float, range: 0–30).
  - **Subscription Type:** Basic/Standard/Premium (object).
  - **Contract Length:** Monthly/Quarterly/Annual (object).
  - **Total Spend:** Total amount spent (float, range: 100–1000).
  - **Last Interaction:** Days since last interaction (float, range: 1–30).
  - **Churn:** Target variable (float, 0 or 1; ~56.71% churn rate).
- **Data Issues Noted:**
  - One null row (dropped implicitly in analysis).
  - Monthly contracts show 100% churn—potential data anomaly or strong indicator.
  - No preprocessing (e.g., handling missing values or outliers) beyond basic loading.

**Summary Statistics (from `data.describe()`):**
| Statistic | CustomerID | Age | Tenure | Usage Frequency | Support Calls | Payment Delay | Total Spend | Last Interaction | Churn |
|-----------|------------|-----|--------|-----------------|---------------|---------------|-------------|------------------|-------|
| **Count** | 440,832 | 440,832 | 440,832 | 440,832 | 440,832 | 440,832 | 440,832 | 440,832 | 440,832 |
| **Mean**  | 225,398.67 | 39.37 | 31.26 | 15.81 | 3.60 | 12.97 | 631.62 | 14.48 | 0.57 |
| **Std**   | 129,531.92 | 12.44 | 17.26 | 8.59 | 3.07 | 8.26 | 240.80 | 8.60 | 0.50 |
| **Min**   | 2.00 | 18.00 | 1.00 | 1.00 | 0.00 | 0.00 | 100.00 | 1.00 | 0.00 |
| **25%**   | 113,621.75 | 29.00 | 16.00 | 9.00 | 1.00 | 6.00 | 480.00 | 7.00 | 0.00 |
| **50%**   | 226,125.50 | 39.00 | 32.00 | 16.00 | 3.00 | 12.00 | 661.00 | 14.00 | 1.00 |
| **75%**   | 337,739.25 | 48.00 | 46.00 | 23.00 | 6.00 | 19.00 | 830.00 | 22.00 | 1.00 |
| **Max**   | 449,999.00 | 65.00 | 60.00 | 30.00 | 10.00 | 30.00 | 1,000.00 | 30.00 | 1.00 |

## Analysis Performed
The Jupyter Notebook performs the following steps:
1. **Data Loading & Inspection:**
   - Import libraries: Pandas, NumPy, Matplotlib, Seaborn, Plotly.
   - Load CSV and display head, info, describe, shape.
   
2. **Overall Churn Calculation:**
   - Churn percentage: 56.71%.
   - Visualization: Bar chart showing No Churn (43.3%) vs. Churn (56.7%).

3. **Churn by Gender:**
   - Females: 66.67% churn.
   - Males: 49.13% churn.
   - Visualization: Bar chart highlighting higher churn among females.

4. **Churn by Age:**
   - Older customers show slightly higher churn tendency.
   - Visualization: Violin plot comparing age distributions for churned vs. retained customers.

5. **Churn by Payment Delay:**
   - Higher delays correlate with higher churn (e.g., delays >20 days approach 100% churn).
   - Visualization: Line chart of churn rate vs. payment delay.

6. **Churn by Total Spend:**
   - Lower spenders have higher churn.
   - Visualization: Box plot comparing total spend for churned vs. retained.

7. **Churn by Support Calls:**
   - More calls indicate higher churn (e.g., 10 calls: ~100% churn).
   - Visualization: Line chart of churn rate vs. number of support calls.

8. **Churn by Subscription Type:**
   - Basic: 58.18%.
   - Premium: 55.94%.
   - Standard: 56.07%.
   - Visualization: Bar chart showing minor variations.

9. **Churn by Contract Length:**
   - Annual: 46.08%.
   - Monthly: 100.00% (notable insight—suggests monthly contracts are high-risk).
   - Quarterly: 46.03%.
   - Visualization: Bar chart emphasizing monthly contract risks.

## Key Findings & Insights
- **High Overall Churn:** Over half (56.71%) of customers churn, indicating potential issues in retention strategies.
- **Demographic Patterns:** Females and older customers (>50 years) are more likely to churn. Target retention campaigns accordingly.
- **Behavioral Indicators:** 
  - Customers with >5 support calls or payment delays >15 days have churn rates nearing 100%.
  - Lower total spend (<$500) correlates with higher churn—possibly due to perceived low value.
- **Product-Related Factors:**
  - Monthly contracts have 100% churn: Recommend shifting to longer-term contracts with incentives.
  - Subscription types show balanced churn, but Basic users churn slightly more—upsell to Premium for better retention.
- **Recommendations:**
  - Improve support efficiency to reduce calls.
  - Implement payment reminders to minimize delays.
  - Focus on high-risk segments (e.g., monthly subscribers, high-delay customers) with personalized offers.

## Requirements
- Python 3.13+
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly` (install via `pip install -r requirements.txt`).
- Jupyter Notebook for interactive viewing.

**requirements.txt:**
