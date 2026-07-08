# Digital-Subscription-Churn-Conversion-Forecasting-Model
Simulated quantitative research project (ACHA-style dataset) linking digital consumption frequency, sleep quality, and stress level, then using those signals to forecast subscription churn and trial-to-paid conversion.

Data disclosure: All data in this project is synthetically generated (numpy/pandas,
seeded for reproducibility) to reflect realistic effect sizes reported in media-use / sleep /
stress literature. No real ACHA microdata was used or accessed.



Project Goals


Correlation analysis — isolate the relationships between consumption frequency, sleep
quality, and stress level.
Regression analysis — quantify how much each additional hour of weekly consumption
costs in sleep quality, and how stress responds to consumption and sleep independently.
Churn forecasting — a logistic regression model predicting subscription churn from
consumption, sleep, stress, and tenure.
Conversion forecasting — a companion model predicting trial-to-paid conversion from the
same wellbeing signals.


Key Results

AnalysisResultConsumption ↔ Sleep qualityNegative correlation, statistically significant (p < 0.001)Consumption ↔ Stress levelPositive correlation, statistically significant (p < 0.001)Churn modelLogistic regression, AUC ≈ 0.72Conversion modelLogistic regression on trial users, wellbeing signals predictive

Correlation Structure

Show Image

Churn Model Performance

Show Image

Methodology


Synthetic data generation — 2,500 simulated users with consumption frequency drawn from
a Gamma distribution; sleep quality and stress level generated as (noisy) linear functions
of consumption, so ground-truth relationships are known and recoverable.
Correlation + regression — Pearson correlation and scikit-learn LinearRegression to
quantify the strength and direction of each relationship.
Churn / conversion modeling — churn and conversion probabilities are generated via a
logistic function of standardized predictors (stress, sleep, tenure, consumption), then a
LogisticRegression classifier is trained/evaluated on a held-out test split (AUC, ROC,
classification report).


Repo Structure

.
├── notebooks/
│   └── churn_conversion_forecasting_model.ipynb   # full analysis, pre-executed with outputs
├── dashboard/
│   └── index.html                                 # standalone interactive dashboard (Chart.js)
├── reports/
│   └── Churn_Conversion_Forecasting_Report.docx   # formal written report
├── data/
│   └── subscriber_wellbeing_data.csv              # synthetic subscriber-level dataset
├── images/                                        # exported chart previews for this README
├── requirements.txt
└── README.md

Interactive Dashboard

dashboard/index.html is a standalone, no-build-step dashboard (HTML + Chart.js via CDN)
showing consumption/sleep/stress relationships, the churn model's ROC curve, churn rate by
stress quartile, and feature drivers. Open it directly in a browser, or enable GitHub Pages
on this repo (Settings → Pages → deploy from main /root or /dashboard) for a shareable link.

Written Report

reports/Churn_Conversion_Forecasting_Report.docx is a formal write-up (objectives,
methodology, results, limitations, recommendations) suitable for sharing with stakeholders who
want the findings without opening the notebook.

Running It

bashgit clone <this-repo-url>
cd digital-subscription-churn-forecasting
pip install -r requirements.txt
jupyter notebook notebooks/churn_conversion_forecasting_model.ipynb

The notebook is deterministic (np.random.seed), so re-running it reproduces the exact same
numbers and charts shown here.

Tools & Techniques

Python · pandas · NumPy · scikit-learn (LogisticRegression, LinearRegression,
StandardScaler, train_test_split, ROC/AUC) · scipy.stats (Pearson correlation) ·
matplotlib / seaborn

License

MIT — see LICENSE.
