# 📊 A/B Testing — Recommender System

## 📌 Overview

This project analyzes the results of an A/B test conducted by an international online store to evaluate the impact of an improved recommendation system on user behavior.

The analysis combines **data preprocessing, exploratory data analysis, conversion funnel analysis, and statistical hypothesis testing** to identify differences in user behavior between experiment groups.

---

## 🎯 Business Objective

The main objectives of this project are to:

* Evaluate the impact of an improved recommendation system.
* Validate the quality and structure of the experiment data.
* Analyze user behavior throughout the conversion funnel.
* Compare user activity between A/B test groups.
* Determine whether observed differences are statistically significant.
* Translate experimental results into product-related insights.

---

## 📂 Dataset

The project uses several datasets containing:

* Marketing campaign periods
* New user information
* User event activity
* A/B test participant assignments

### Main Event Data

The event dataset contains **423,761 event records** with the following variables:

| Column       | Description                                          |
| ------------ | ---------------------------------------------------- |
| `user_id`    | Unique user identifier                               |
| `event_dt`   | Date and time of the event                           |
| `event_name` | Type of user event                                   |
| `details`    | Additional event information, such as purchase value |

The recorded events include:

* `login`
* `product_page`
* `product_cart`
* `purchase`

The event data covers **December 7–30, 2020** before applying the analysis filters.

---

## 🛠️ Tools & Technologies

* Python
* Pandas
* NumPy
* SciPy
* Matplotlib
* Seaborn
* Plotly
* Statistical Hypothesis Testing
* Z-Test

---

## 🔍 Data Preparation

Several preprocessing steps were performed before the analysis:

* Converted date and timestamp columns into `datetime` format.
* Checked missing values and duplicate records.
* Investigated the `details` column.
* Filled missing `details` values with `0`.
* Created date-based variables for temporal analysis.
* Joined user, event, and experiment participant data.
* Restricted the analysis to users from the EU region.
* Limited user activity to a 14-day period from the user's first activity.
* Removed activity after December 25 based on the analysis period.

---

## 📈 Exploratory Data Analysis

The analysis examined the distribution of events over time.

Daily event activity increased throughout the period and reached its highest observed volume around **December 21**, followed by a decline.

This temporal analysis was used to understand user activity patterns before conducting the funnel and A/B testing analysis.

---

## 🔄 Conversion Funnel Analysis

The user journey was modeled as the following funnel:

```text
Login
  ↓
Product Page
  ↓
Product Cart
  ↓
Purchase
```

The funnel was calculated based on user activity across the different stages.

### Funnel Results

| Funnel Stage |  Users | Total Conversion |
| ------------ | -----: | ---------------: |
| Login        | 43,381 |             100% |
| Product Page | 16,311 |              38% |
| Product Cart |    981 |               6% |
| Purchase     |      5 |               1% |

### Key Funnel Insight

The largest decline occurred between **Login → Product Page**, where approximately 38% of users continued to the next stage.

The analysis also identified substantial drop-off between **Product Page → Product Cart**, providing an area for further investigation into user behavior and the recommendation journey.

---

## 🧪 A/B Testing

The A/B experiment analyzed was:

```text
recommender_system_test
```

The experiment contained two groups:

* **Group A**
* **Group B**

After filtering and merging the participant and event datasets:

| Group     |     Users |
| --------- | --------: |
| A         |     2,604 |
| B         |       877 |
| **Total** | **3,481** |

The analysis also checked whether users appeared in both experiment groups.

---

## 📊 A/B Test Metrics

User activity was compared across the following events:

| Event        | Group A | Group B |
| ------------ | ------: | ------: |
| Login        |   2,604 |     876 |
| Product Page |   1,685 |     493 |
| Product Cart |     782 |     244 |
| Purchase     |     833 |     249 |

The analysis calculated the proportion of users performing each event within their respective experiment groups.

---

## 📐 Statistical Hypothesis Testing

The experiment used a **two-proportion z-test** with:

* **Significance level (α): 5%**
* **H₀:** The proportions of users between Group A and Group B are statistically equal.
* **H₁:** The proportions of users between Group A and Group B are statistically different.

The z-test was implemented using the pooled proportion to calculate the test statistic and p-value.

### Statistical Results

| Event        | Group A | Group B | p-value |
| ------------ | ------: | ------: | ------: |
| Login        | 100.00% |  99.89% |  0.0848 |
| Product Page |  64.71% |  56.21% | <0.0001 |
| Purchase     |  31.99% |  28.39% |  0.0465 |
| Product Cart |  30.03% |  27.82% |  0.2147 |

Using **α = 0.05**, the reported results indicate statistically significant differences for:

* **Product Page**
* **Purchase**

The differences for:

* **Login**
* **Product Cart**

do not meet the 5% significance threshold based on the reported p-values.

---

## 💡 Key Findings

1. The conversion funnel shows substantial user drop-off between **Login → Product Page**.

2. The A/B test consisted of **2,604 users in Group A and 877 users in Group B**.

3. The largest observed difference between groups occurred at the **Product Page** stage:

   * Group A: **64.71%**
   * Group B: **56.21%**
   * p-value: **<0.0001**

4. The **Purchase** event also showed a statistically significant difference at the 5% level:

   * Group A: **31.99%**
   * Group B: **28.39%**
   * p-value: **0.0465**

5. The **Product Cart** event did not show a statistically significant difference:

   * p-value: **0.2147**

6. The analysis demonstrates how statistical testing can be used to distinguish observed differences in user behavior from differences supported by statistical evidence.

---

## 💼 Business Value

This project demonstrates how product and behavioral data can be used to:

* Evaluate product experiments.
* Measure conversion funnel performance.
* Identify user drop-off points.
* Compare behavioral metrics between experiment groups.
* Apply statistical testing to product decisions.
* Translate analytical results into product insights.

---

## 🔄 Analytical Workflow

```text
Raw Data
   ↓
Data Quality Checks
   ↓
Data Type & Missing Value Handling
   ↓
Data Filtering
   ↓
User & Event Data Integration
   ↓
Exploratory Data Analysis
   ↓
Conversion Funnel Analysis
   ↓
A/B Test Group Validation
   ↓
Conversion Comparison
   ↓
Z-Test / Hypothesis Testing
   ↓
Business Insights
```

---

## 📁 Project Structure

```text
├── README.md
├── AB Testing.ipynb
└── dataset/
    ├── ab_project_marketing_events_us.csv
    ├── final_ab_new_users_upd_us.csv
    ├── final_ab_events_upd_us.csv
    └── final_ab_participants_upd_us.csv
```

---

## 👤 Author

**I Putu Darma Ruswara**

Data Analyst | Business Analytics & Data Governance

* GitHub: [I Putu Darma Ruswara](github.com/darmaputu)
* LinkedIn: [I Putu Darma Ruswara](linkedin.com/in/i-putu-darma-ruswara-329366148/)
* Upwork: [I Putu Darma Ruswara](upwork.com/freelancers/~01299ccc7efce03dea)
