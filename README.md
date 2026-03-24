# Metro Manila Road Crash Analysis: Traffic Volume vs Crashes
### An IMRAD Study on AADT and Road Crash Relationships Across Major Metro Manila Roads (2019–2024)

**Authors:** Jerdan L. Gondayao, Johnmer M. Tanqui-on

---

## Abstract

This study investigates the relationship between Average Annual Daily Traffic (AADT) and road crash incidents across seven major Metro Manila roads from 2019 to 2024. Using descriptive statistics, correlation analysis, and machine learning models (Random Forest, Gradient Boosting, and SARIMA), the research examines whether higher traffic volume leads to increased crash frequency and severity. The analysis reveals a moderate positive correlation between AADT and crash totals across roads. Machine learning models trained per road demonstrate strong predictive capability for monthly crash counts, with feature importance analysis identifying AADT and historical crash lags as the most significant predictors. SARIMA-based forecasts for 2025–2026 identify peak crash months and high-risk road-month combinations, providing actionable insights for traffic management and road safety planning.

**Keywords:** AADT, road crash analysis, Metro Manila, SARIMA, Random Forest, Gradient Boosting, traffic safety, time series forecasting

---

## I. Introduction

### Background

Metro Manila, the National Capital Region of the Philippines, is one of the most congested urban areas in the world. With a population exceeding 13 million and a road network shared by millions of vehicles daily, road crashes remain a persistent public safety concern. Major arterial roads such as EDSA, C-5 Road, Commonwealth Avenue, Quezon Avenue, Roxas Boulevard, Marcos Highway, and Radial Road 10 carry varying volumes of traffic and exhibit distinct crash patterns.

Understanding the relationship between traffic volume—measured as Average Annual Daily Traffic (AADT)—and crash frequency is critical for evidence-based road safety interventions. While it is intuitive to assume that more vehicles on the road lead to more crashes, the nature and strength of this relationship varies by road characteristics, traffic management infrastructure, and temporal factors.

### Research Question

**Does traffic volume (AADT) increase the frequency and severity of crashes on major Metro Manila roads?**

### Objectives

1. Analyze traffic volume (AADT) trends across seven major Metro Manila roads from 2019 to 2024.
2. Examine crash trends by total count and severity (fatal, non-fatal, property damage).
3. Quantify the statistical relationship between AADT and crash frequency, both across roads and over time.
4. Identify seasonal and monthly crash patterns per road.
5. Build per-road machine learning models to predict crash frequency using traffic and temporal features.
6. Generate 2025–2026 crash forecasts and identify high-risk periods for targeted safety interventions.

### Significance

This study contributes to data-driven road safety policy in Metro Manila by:
- Providing empirical evidence on the AADT–crash relationship
- Identifying which roads and months present the greatest crash risk
- Comparing statistical (SARIMA) and machine learning (Random Forest, Gradient Boosting) approaches for crash prediction
- Offering actionable insights for resource allocation and enforcement scheduling

---

## II. Methods

### 2.1 Dataset Description

| Attribute | Detail |
|---|---|
| **Source** | MMDA MMARAS Annual Reports |
| **Period** | January 2019 – December 2024 (72 months) |
| **Roads** | 7 major Metro Manila arterial roads |
| **Observations** | 504 monthly records (7 roads × 72 months) |
| **Variables** | `road_name`, `year`, `month`, `aadt`, `crashes_total`, `crashes_fatal`, `crashes_non_fatal`, `crashes_property` |

**Roads studied:**
1. EDSA
2. C-5 Road
3. Commonwealth Avenue
4. Quezon Avenue
5. Roxas Boulevard
6. Marcos Highway
7. Radial Road 10

### 2.2 Data Analysis Techniques

#### Descriptive Statistics
- Summary statistics per road: average AADT, total crashes, severity breakdown
- Year-over-year trend analysis for both AADT and crash counts
- Monthly averages and crash seasonality patterns

#### Correlation Analysis
- **Across roads:** Pearson correlation between average AADT and total crashes to determine if higher-volume roads experience more crashes
- **Over time (per road):** Year-over-year correlation between AADT changes and crash changes for each road
- Crash rate normalization: crashes per 100,000 AADT to enable fair cross-road comparison

#### Visualization
- Per-road line charts for AADT and crash trends (2019–2024)
- Dual-axis plots showing AADT vs. crashes over time
- Crash severity stacked trends per road
- Monthly crash heatmaps (roads × months)

### 2.3 Machine Learning Models

#### Feature Engineering

The following features were engineered from the raw dataset:

| Feature | Description |
|---|---|
| `month_sin`, `month_cos` | Cyclical encoding of month (captures seasonality) |
| `crashes_lag_1`, `_3`, `_6`, `_12` | Lagged crash counts (1, 3, 6, and 12 months prior) |
| `crashes_rolling_3`, `_6` | Rolling mean of crashes (3-month and 6-month windows) |
| `crash_rate_per_100k` | Crashes normalized by AADT (per 100k vehicles) |
| `is_pandemic` | Binary flag for 2020–2021 (COVID-19 impact period) |
| `yoy_change` | Year-over-year percentage change in crashes |
| `fatal_ratio`, `nonfatal_ratio` | Proportion of fatal/non-fatal crashes to total |

#### Model Training

**Train/Test Split:** Temporal split — 2019–2023 for training, 2024 for testing (no data leakage).

**Models applied per road:**

1. **Random Forest Regressor** — 200 estimators, max depth 8, random state 42
2. **Gradient Boosting Regressor** — 200 estimators, max depth 5, learning rate 0.1
3. **SARIMAX (1,1,1)(1,1,1,12)** — Seasonal ARIMA with AADT as exogenous variable

**Target variable:** `crashes_total` (monthly crash count per road)

**Evaluation Metrics:**
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score (Coefficient of Determination)

#### Crash Severity Prediction

Gradient Boosting models were trained separately for each severity type (`crashes_fatal`, `crashes_non_fatal`, `crashes_property`) per road, using AADT and temporal features.

#### Time Series Forecasting

SARIMA models were fitted per road to generate 24-month forecasts (January 2025 – December 2026) with 95% confidence intervals, using AADT as an exogenous predictor.

---

## III. Results

### 3.1 Traffic Volume Trends

AADT analysis across all seven roads from 2019 to 2024 revealed:
- A significant dip in traffic volume during 2020–2021 corresponding to COVID-19 lockdowns
- Recovery to pre-pandemic levels by 2022–2023, with most roads showing continued growth into 2024
- EDSA consistently recorded the highest AADT among all roads studied

### 3.2 Crash Trends

Total crash trends showed:
- A sharp decline during 2020 (lockdown effect), with gradual recovery through 2021–2022
- By 2023–2024, most roads returned to or exceeded pre-pandemic crash levels
- EDSA and C-5 Road recorded the highest total crash counts across the study period

### 3.3 AADT–Crash Relationship

#### Across Roads
The Pearson correlation between average AADT and total crashes (6-year aggregate) across the seven roads was calculated. This analysis determines whether roads with higher traffic volume systematically experience more crashes.

#### Over Time (Per Road)
Year-over-year correlations between AADT and crashes were computed for each road individually. This reveals whether increases in traffic volume on a specific road are associated with increases in crashes on that same road.

#### Crash Rate Normalization
When crashes are normalized by AADT (crashes per 100,000 vehicles), the ranking of roads changes, indicating that raw crash counts alone may be misleading. Roads with lower AADT but proportionally high crashes emerge as having worse safety performance.

### 3.4 Crash Severity Patterns

Severity analysis revealed:
- Property damage incidents constitute the largest share of total crashes across all roads
- Non-fatal injury crashes represent a significant portion, particularly on high-volume roads
- Fatal crash counts are relatively low in absolute numbers but vary meaningfully between roads
- Some roads show improving fatal crash trends while others show worsening trends

### 3.5 Monthly and Seasonal Patterns

The crash heatmap analysis (roads × months) identified:
- Distinct monthly patterns varying by road
- Certain months consistently emerge as high-risk across multiple roads
- Seasonal patterns influenced by weather (rainy season), holidays, and school calendar

### 3.6 Machine Learning Results

#### Per-Road Crash Prediction (2024 Test Set)

Random Forest and Gradient Boosting models were trained for each road and evaluated on the 2024 holdout year. Results were compared against SARIMA baselines.

**Key findings:**
- Machine learning models (RF and GB) generally achieved competitive or superior performance compared to SARIMA on the 2024 test set
- The best model varies by road — some roads are better predicted by SARIMA (capturing seasonal patterns), while others benefit from the feature-rich ML approach
- MAE-based model selection identified the optimal approach per road

#### Feature Importance

Random Forest feature importance analysis revealed:
- `aadt` and `crashes_lag_1` (previous month's crashes) are consistently the most important predictors
- Rolling averages (`crashes_rolling_3`, `crashes_rolling_6`) provide strong predictive signal
- Cyclical month features (`month_sin`, `month_cos`) capture seasonal crash patterns
- The `is_pandemic` flag was important for roads with large COVID-era disruptions

#### Crash Severity Prediction

Gradient Boosting models trained for each severity type showed that:
- Property damage crashes are the most predictable (highest R² values)
- Fatal crash prediction is challenging due to low counts and high variance
- Non-fatal injury predictions show moderate accuracy

### 3.7 Forecasts (2025–2026)

SARIMA forecasts with 95% confidence intervals were generated for each road:
- Peak crash months were identified per road for both 2025 and 2026
- Heatmap visualizations show the predicted monthly crash distribution across all roads
- Top 10 riskiest month-road combinations were identified for priority intervention planning

---

## IV. Discussion

### 4.1 Key Findings

1. **AADT and crashes are positively correlated across roads** — roads carrying higher traffic volumes do tend to experience more crashes, confirming the expected relationship.

2. **The relationship varies over time** — for some roads, increases in AADT do not correspond to proportional crash increases, suggesting that infrastructure improvements, speed management, or enforcement may moderate the effect.

3. **Crash rate normalization reveals hidden risks** — when controlling for traffic volume, some lower-AADT roads show disproportionately high crash rates, indicating that these roads may benefit most from targeted interventions despite having lower raw crash totals.

4. **Machine learning models outperform or match SARIMA** — Random Forest and Gradient Boosting models leveraging lagged features, rolling means, and AADT achieve competitive performance, demonstrating that crash prediction benefits from a richer feature set beyond simple time series patterns.

5. **Monthly patterns are road-specific** — peak crash months differ by road, emphasizing the need for road-specific (rather than blanket) safety strategies.

6. **COVID-19 created a structural break** — the 2020–2021 pandemic period caused anomalous traffic and crash patterns that complicate modeling. The `is_pandemic` feature helps models account for this disruption.

### 4.2 Practical Implications

- **Enforcement scheduling:** Peak crash months identified per road can guide the deployment of traffic enforcement personnel during the highest-risk periods.
- **Infrastructure investment:** Roads with high crash rates per 100k AADT (poor safety performance despite moderate traffic) should be prioritized for engineering improvements (e.g., road design, signage, lighting).
- **Predictive monitoring:** The machine learning pipeline can be operationalized to generate monthly crash risk scores, alerting traffic authorities to emerging high-risk conditions.

### 4.3 Limitations

1. **Data granularity:** Monthly aggregation may mask within-month patterns (e.g., day-of-week, rush hour effects).
2. **Limited features:** The dataset lacks road geometry, weather data, speed data, and enforcement activity data that could improve model performance.
3. **Sample size:** With only 72 months per road (and 6 years), the time series are relatively short for SARIMA modeling, particularly given the COVID-19 disruption consuming 2 of 6 years.
4. **AADT constancy within year:** AADT values appear constant within each year, limiting the within-year predictive power of traffic volume as a feature.
5. **External validity:** Findings are specific to the seven roads studied and may not generalize to all Metro Manila roads or other cities.

### 4.4 Future Work

- Incorporate daily or hourly crash data for finer-grained analysis
- Add weather, road condition, and enforcement data as predictive features
- Extend the model to additional Metro Manila roads
- Explore deep learning approaches (LSTM, Transformer) for time series prediction
- Develop a real-time crash risk dashboard for MMDA operational use

---

## V. Conclusion

This study demonstrates that traffic volume (AADT) is a meaningful but not sole predictor of road crash frequency across major Metro Manila roads. While higher AADT is generally associated with more crashes, the strength of this relationship varies by road and over time. Machine learning models incorporating lagged crash data, rolling averages, seasonal features, and AADT achieve strong predictive performance for monthly crash counts, outperforming or matching traditional SARIMA models on multiple roads. The forecasts and risk scores produced offer practical value for traffic safety planning, enabling targeted enforcement, infrastructure prioritization, and data-driven decision-making for Metro Manila's road safety challenges.

---

## References

1. Metropolitan Manila Development Authority (MMDA). *MMARAS Annual Reports, 2019–2024.*
2. World Health Organization (WHO). *Global Status Report on Road Safety, 2023.*
3. Hyndman, R.J. & Athanasopoulos, G. *Forecasting: Principles and Practice.* 3rd Edition, OTexts, 2021.
4. Breiman, L. "Random Forests." *Machine Learning*, 45(1), 5–32, 2001.
5. Friedman, J.H. "Greedy Function Approximation: A Gradient Boosting Machine." *Annals of Statistics*, 29(5), 1189–1232, 2001.
6. Box, G.E.P., Jenkins, G.M., Reinsel, G.C., & Ljung, G.M. *Time Series Analysis: Forecasting and Control.* 5th Edition, Wiley, 2015.
