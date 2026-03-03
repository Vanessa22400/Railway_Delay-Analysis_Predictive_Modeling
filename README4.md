# Railway Delay Analysis – Tübingen (Germany)
From commuter experience to data-driven insights on punctuality, risk and reliability in the Deutsche Bahn network

---

## Business Context

Reliable public transportation is essential in Germany, especially for commuters and students who depend on trains for work, study, and daily life. Even small disruptions can affect connections, productivity, and passenger trust.

While living in the Tübingen region (Baden-Württemberg), I experienced frequent delays that were constantly discussed among passengers. However, official numbers often summarize performance using averages, which can hide daily friction and rare high-impact events.

This project uses one full year of operational data from Tübingen Hbf to assess how delays behave over time, across services, and by destination, and to translate passenger perception into measurable, decision-oriented insights.

---

## Problem Statement

How reliable is the railway service at Tübingen Hbf, and which operational factors are most associated with delays and higher delay risk?

---

## Objectives

- Identify key drivers behind delay patterns and delay risk
- Perform structured exploratory data analysis (EDA)
- Validate common commuter perceptions using hypothesis testing
- Engineer features aligned with operational context
- Build and evaluate predictive models (regression and classification)
- Translate findings into actionable insights for planning and communication

---

## Methodology

1. Data Cleaning and Preprocessing  
   Handling missing values, outliers, inconsistencies and data normalization when required.

2. Exploratory Data Analysis (EDA)  
   Identification of patterns, correlations, structural behaviors and potential risks.

3. Hypothesis Testing  
   Statistical testing of recurring patterns (weekday effects, service-type differences).

4. Feature Engineering  
   Creation of variables based on domain logic and contextual interpretation.

5. Model Selection and Validation  
   Comparison of models using cross-validation and performance metrics.

6. Insight Generation  
   Translation of statistical results into operational or strategic recommendations.

---

## Tools & Technologies

- Python (Pandas, NumPy)
- Scikit-learn
- SciPy (Hypothesis Testing)
- Statsmodels (Time Series Decomposition)
- Matplotlib, Seaborn
- Folium (Geospatial Visualization)
- Data Source: Deutsche Bahn data (Hugging Face public repository)
- Modeling: Random Forest Regressor, Random Forest Classifier

---

## Exploratory Data Analysis Highlights

The exploratory analysis revealed consistent patterns with direct operational implications:

- **Perception gap:** 67.6% of services had some delay, even though the average delay was 3.23 minutes. This helps explain why everyday experience can feel worse than summary statistics.
- **Tail risk:** delays are mostly small, but the distribution is strongly right-skewed (extreme events up to 331 minutes). Severe delays above 30 minutes represent 1.24% of delayed services, but drive disproportionate disruption.
- **Monday fragility:** Mondays show the highest average delays and the highest concentration of cancellations, indicating a structurally more vulnerable start of the week.
- **Service differences:** express services have higher average delays than regional services (longer routes, exposure to network-wide disruptions).
- **Directional bottlenecks:** several southern and southeastern routes show higher average delays, while major hubs like Stuttgart appear comparatively more stable.

These findings guided formal hypothesis testing and the modeling strategy.

---

## Modeling Approach

This project uses two complementary predictive tasks aligned with practical decision needs:

**Regression Task**  
Focused on estimating expected delay minutes under typical operating conditions. To avoid extreme values distorting minute-level prediction, outliers are excluded from the regression training set.

**Classification Task**  
Focused on identifying higher-risk scenarios using a critical delay definition (delay above 5 minutes). This framing is more actionable for planning and passenger communication, and better reflects operational risk management.

Model choice prioritized **interpretability**, non-linear pattern capture, and alignment with real-world constraints.

---

## Model Performance

**Regression (Predicting Delay Minutes)**
- Mean Absolute Error (MAE): 3.20 minutes
- R² Score: -0.0426
 
Minute-level prediction is unstable because severe disruptions are often driven by external factors not present in the dataset (weather events, infrastructure incidents, technical failures). The low MAE reflects typical small delays, but the negative R² highlights the limits of predicting exact delay duration in a complex network.

**Classification (Predicting Critical Delays > 5 minutes)**
- Accuracy: 0.82
- On-time precision (Class 0): 0.86
- Critical delay recall (Class 1): 0.27
 
The model is strong at confirming lower-risk situations (useful for passenger trust and baseline planning). Critical delays remain harder to capture due to unobserved drivers and the nature of rare disruptions. This is a data limitation more than a modeling limitation, and it is a realistic finding for operational systems.

![Feature Importance – Critical Delay Prediction](Images/6.Feature Importance.png)

---

## Key Insights

- Summary metrics can be misleading: the average delay looks moderate, but the majority of services experience some delay, which matches passenger perception.
- **Mondays are consistently riskier:** both delay averages and cancellations peak early in the week, suggesting lower operational resilience.
- **Rush hour amplifies disruption:** overall mean delay rises during peak times (3.83 vs. 2.77 minutes), and delayed services are more severe during rush hour (5.20 vs. 4.39 minutes).
- Delay risk is more seasonal than hourly: month and weekday patterns carry more signal than the departure hour alone.
- Reliability is not evenly distributed: certain directions and destinations show recurring bottlenecks, suggesting localized infrastructure constraints.

---

## Business Impact & Applications

**Operational optimization**  
Support targeted actions on high-risk days and periods, especially early-week operations.

**Resource allocation**  
Improve staffing, maintenance planning and contingency readiness where risk concentrates (weekday patterns, seasonal peaks, and bottleneck routes).

**Risk mitigation**  
Use risk-based classification outputs to flag likely critical delays and reduce cascading effects.

**Strategic planning**  
Identify structural vulnerabilities (seasonality, destination-level risk) to inform longer-term network improvements.

**KPI monitoring**  
Track stability beyond averages, using metrics such as delay incidence, cancellation rate, and critical delay risk rate over time.

---

## Next Steps

- Integrate weather variables to quantify seasonal effects and improve critical-delay detection
- Merge maintenance and construction logs (Baustellen) to separate planned vs. unexpected disruption
- Test alternative models (boosting methods) and add explainability for stakeholder communication
- Build a lightweight API for delay-risk alerts
- Create a dashboard for monitoring weekday and route-level reliability trends

---

## Repository Structure
├── data
├── notebooks
├── images
├── requirements.txt
└── README.md  

---

## Strategic Perspective 
I intentionally framed this project around the gap between what passengers feel and what official averages show. Instead of assuming perfect predictability, I tested where prediction breaks, why it breaks, and what can still be useful for decision-making.

Living in different countries shaped how I approach analysis: I tend to question assumptions, pay attention to context, and connect patterns to real operational constraints. This project reflects that approach by combining technical modeling with practical interpretation and clear limitations.

---

## Conclusion

This project turns everyday commuter experience in Baden-Württemberg into a structured end-to-end analysis of railway reliability at Tübingen Hbf.

The results validate patterns passengers often discuss, quantify where risk concentrates, and show why predicting exact delay minutes is limited in complex networks. A risk-based approach provides more actionable value for planning, communication and monitoring.

---


