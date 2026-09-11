# # Ride-Hailing Trip Fare Analysis

A statistical analysis of 200 ride-hailing trips to test common assumptions about
fare pricing — whether distance, ride category, surge pricing, and time of day
actually drive fare amount and customer satisfaction, and whether the pricing
data contains anomalies.

## 📊 Project Overview

Ride-hailing platforms assume fares scale with distance, that premium tiers cost
more, and that surge pricing affects how customers rate their trips. This project
puts those assumptions to the test using hypothesis testing, correlation analysis,
probability theory, and confidence intervals on a real trip-level dataset.

**Dataset:** `Trip_Analysis.xlsx` — 200 rides, 6 features
(`Trip_Distance`, `Fare_Amount`, `Ride_Category`, `Surge_Multiplier`,
`Customer_Rating`, `Ride_Time`)

## ❓ Questions Answered

| # | Question | Method |
|---|---|---|
| 1 | Does trip distance significantly affect fare amount? | Pearson correlation, covariance, linear algebra (vector) interpretation |
| 2 | Are premium rides statistically more expensive than economy rides? | Independent t-test, one-way ANOVA |
| 3 | Is there a relationship between surge pricing and customer ratings? | Spearman rank correlation |
| 4 | Do peak-hour rides differ in revenue compared to non-peak rides? | Independent t-test / z-test |
| 5 | Are there unusual fare values indicating anomalies or pricing errors? | IQR method, z-score, percentiles |
| 6 | Can ride demand probabilities be estimated for different ride categories? | Basic probability, conditional probability, Bayes' theorem |
| 7 | How do trip factors correlate with each other overall? | Pearson & Spearman correlation matrix |
| 8 | Can statistical evidence support pricing or service improvements? | Confidence intervals, bootstrapping, hypothesis-test synthesis |

## 🔑 Key Findings

- **No significant relationship** between trip distance and fare amount
  (r = 0.017, p = 0.813) — fare does not scale with distance in this dataset.
- **No significant fare difference** between Economy, Premium, and Shared rides
  (t-test p = 0.685; ANOVA p = 0.397).
- **No significant relationship** between surge multiplier and customer rating
  (Spearman ρ = -0.047, p = 0.508).
- **No significant fare difference** between peak and non-peak rides
  (t-test p = 0.550).
- **One clear pricing anomaly**: a ₹37.59 fare on a 12-unit Economy trip falls
  outside the IQR bound — flagged as a likely data/pricing error.
- **Economy is the dominant ride category** (41% of all rides, and the most
  probable category even conditional on peak-hour timing, via Bayes' theorem).
- All correlation coefficients among distance, fare, surge, and rating stay
  close to zero — no strong pairwise relationships in the dataset.
- 95% confidence intervals (both t-distribution and 10,000-sample bootstrap)
  confirm the group differences above are not just a sampling artifact — they
  are genuinely small.

## 🛠️ Tools & Libraries

- **Python** — `pandas`, `numpy`
- **Statistics** — `scipy.stats` (Pearson, Spearman, t-test, ANOVA, Shapiro-Wilk, Levene's test)
- **Visualization** — `matplotlib`
- **Environment** — Jupyter Notebook

## 📁 Repository Structure

```
├── statistical_analysis.ipynb   # Full analysis notebook (all 8 questions)
├── Trip_Analysis.xlsx           # Source dataset
└── README.md                    # Project documentation
```

## ▶️ How to Run

```bash
pip install pandas numpy scipy matplotlib openpyxl
jupyter notebook statistical_analysis.ipynb
```

## 📌 Methodology Notes

- Normality was checked with the Shapiro-Wilk test and equal variance with
  Levene's test before choosing between Student's and Welch's t-test.
- Significance level (α) used throughout: **0.05**.
- Outliers were cross-checked using both the 1.5×IQR rule and z-score
  thresholds (|z| > 2 and |z| > 3) for robustness.
- Bootstrap resampling (10,000 iterations) was used to validate parametric
  confidence intervals non-parametrically.

## 👤 Author

**Nivetha B.**
Data Analytics | Python · SQL · Power BI · Tableau
[LinkedIn](https://www.linkedin.com/in/nivetha-b-822545318) · [GitHub](https://github.com/Nivetha-B93)
