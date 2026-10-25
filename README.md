# Spotify User Churn Prediction

### SQL | Python | Machine Learning | Product Analytics

## Project Overview

This project analyzes user engagement and subscription behavior to predict 14-day user churn and identify opportunities for improving retention.

Using a course-provided Spotify-like dataset containing 50,000 users, I developed an end-to-end analytics workflow covering SQL-based feature engineering, exploratory data analysis, machine learning, and business recommendations.

## Objectives

- Identify behavioral patterns associated with user churn.
- Build user-level features from listening, advertising, and subscription events.
- Compare Logistic Regression and Random Forest models.
- Segment users by churn risk to inform retention strategies.

## Methodology

**1. SQL Analysis & Feature Engineering**

- Analyzed engagement, subscription, advertising, and churn metrics using SQLite.
- Aggregated event-level data into a user-level feature table containing 50,000 users and 37 columns.
- Used a 30-day observation window (March 2–31, 2026) to predict inactivity during the following 14 days (April 1–14, 2026).
- Validated user uniqueness and checked data quality.

**2. Exploratory Data Analysis**

- Examined listening behavior and subscription segments.
- Compared churn rates with each segment's contribution to total churn.
- Analyzed signup cohorts and user engagement distributions.

**3. Machine Learning**

- Selected 14 numerical and categorical input features.
- Applied standardization and one-hot encoding.
- Trained Logistic Regression and Random Forest classifiers.
- Evaluated models using Accuracy, Precision, Recall, F1-score, ROC-AUC, and PR-AUC.
- Explored classification thresholds and Random Forest hyperparameters.

## Model Performance

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Accuracy | 71.38% | 70.49% |
| Precision | 67.00% | 65.71% |
| Recall | 78.47% | 79.35% |
| F1-score | 0.7228 | 0.7189 |
| ROC-AUC | 0.7842 | 0.7806 |
| PR-AUC | 0.7294 | 0.7235 |

Logistic Regression achieved slightly stronger overall performance, while Random Forest produced marginally higher recall.

## Key Findings

**Engagement predicts churn.** Listening sessions, active days, and listening minutes were the three most important Random Forest features, accounting for approximately 62.85% of total feature importance.

**High churn risk does not imply the largest churn contribution.** Inactive users had the highest observed churn rate (77.09%), while low-activity users accounted for the largest share of churn cases (42.71%).

**Risk segmentation can inform retention prioritization.** The Random Forest high-risk group had a 78.08% observed churn rate, compared with 17.46% for the low-risk group.

## Business Recommendations

- Test personalized re-engagement campaigns for high-risk users.
- Explore scalable playlist discovery and content recommendations for low- and medium-activity users.
- Evaluate retention strategies through randomized A/B testing before deployment.

## Project Structure

```text
Spotify-churn-model-prediction/
├── data/
├── 01_sql_analysis.ipynb
├── 02_sql_feature_engineering.ipynb
├── 03_churn_analysis_model.ipynb
└── README.md
```

## Data Availability

The dataset was provided for educational purposes and is not
included in this repository.

To reproduce the analysis, the original CSV files must be
placed in the `data/` directory before running the notebooks.

## Limitations

- The dataset is educational and should not be represented as official Spotify internal user data.
- The paid-conversion label derived from future events contains no positive cases and was excluded from churn model inputs.
- Threshold and hyperparameter comparisons were exploratory and used the test set; independently validated optimization would require a separate validation procedure.
- Feature importance identifies predictive associations, not causal effects.
- Model probabilities have not been formally calibrated.

## Tools & Technologies

Python, pandas, NumPy, SQLite, Matplotlib, scikit-learn, Jupyter Notebook, and VS Code.