# Metro Manila Road Crash Analysis: Traffic Volume vs Crashes
### A Data Analysis and Forecasting Study on AADT and Road Crash Relationships Across Major Metro Manila Roads (2019–2024)

**Authors:** Jerdan L. Gondayao, Johnmer M. Tanqui-on

---

## Abstract

This study investigates the relationship between Average Annual Daily Traffic (AADT) and road crash incidents across seven major Metro Manila roads from 2019 to 2024. Through comprehensive descriptive and analytical exploration—including trend analysis, correlation studies, crash severity breakdowns, seasonal pattern identification, and SARIMA-based time series forecasting—the research examines whether higher traffic volume leads to increased crash frequency. The data analysis reveals a moderate positive correlation between AADT and total crashes across roads, with distinct seasonal and monthly crash patterns varying by road. SARIMA models generate per-road, all-roads-combined, crash severity, and crash rate forecasts for 2025–2026, identifying peak crash months and roads requiring the most attention. The findings provide actionable insights for data-driven road safety policy in Metro Manila.

**Keywords:** AADT, road crash analysis, Metro Manila, SARIMA, traffic safety, time series forecasting, MMARAS

---

## I. Introduction

### Background

Metro Manila, the National Capital Region of the Philippines, is one of the most congested urban areas in the world. With a population exceeding 13 million and millions of vehicles traversing its roads daily, road crashes remain a persistent public safety concern. Major arterial roads such as EDSA, C-5 Road, Commonwealth Avenue, Quezon Avenue, Roxas Boulevard, Marcos Highway, and Radial Road 10 carry varying volumes of traffic and exhibit distinct crash patterns.

Understanding the relationship between traffic volume—measured as Average Annual Daily Traffic (AADT)—and crash frequency is critical for evidence-based road safety interventions. While it is intuitive to assume that more vehicles on the road lead to more crashes, the nature and strength of this relationship varies depending on road characteristics, traffic management infrastructure, and temporal factors such as weather and holiday seasons.

### Research Question

**Does traffic volume (AADT) increase the frequency and severity of crashes on major Metro Manila roads?**

### Objectives

1. Analyze traffic volume (AADT) trends across seven major Metro Manila roads from 2019 to 2024.
2. Examine crash trends by total count and severity (fatal, non-fatal injury, property damage).
3. Quantify the statistical relationship between AADT and crash frequency—both across roads and over time.
4. Identify seasonal and monthly crash patterns per road.
5. Forecast crash counts for 2025–2026 using SARIMA models (per road and all roads combined).
6. Identify high-risk periods and roads for targeted safety interventions.

### Significance

This study contributes to data-driven road safety policy by providing empirical evidence on the AADT–crash relationship, identifying which roads and months present the greatest risk, and offering forecasts that can guide enforcement scheduling and infrastructure investment.

---

## II. Methods

### 2.1 Dataset

| Attribute | Detail |
|---|---|
| **Source** | MMDA MMARAS Annual Reports |
| **Period** | January 2019 – December 2024 (72 months) |
| **Roads** | 7 major Metro Manila arterial roads |
| **Observations** | 504 monthly records (7 roads × 72 months) |
| **Variables** | `road_name`, `year`, `month`, `aadt`, `crashes_total`, `crashes_fatal`, `crashes_non_fatal`, `crashes_property` |

**Roads studied:** EDSA, C-5 Road, Commonwealth Avenue, Quezon Avenue, Roxas Boulevard, Marcos Highway, Radial Road 10.

### 2.2 Data Analysis

The data analysis phase employs the following techniques:

- **Descriptive Statistics:** Summary statistics per road (average AADT, total crashes, severity breakdown, monthly averages).
- **Trend Analysis:** Year-over-year AADT and crash count trends per road (2019–2024), visualized as individual line charts.
- **AADT vs. Crash Correlation:** Dual-axis plots overlaying AADT and crashes per road; Pearson correlation computed both across roads (comparing average AADT rankings to crash rankings) and over time within each road.
- **Crash Rate Normalization:** Crashes per 100,000 AADT computed to fairly compare roads with different traffic volumes and reveal which roads are disproportionately dangerous relative to their traffic.
- **Crash Severity Analysis:** Trends in fatal, non-fatal injury, and property damage crashes per road, with percentage breakdowns.
- **Monthly/Seasonal Patterns:** Average crash counts per calendar month per road, visualized as bar charts and a heatmap (roads × months) to identify peak crash periods.

### 2.3 Forecasting (SARIMA)

The forecasting phase uses the Seasonal Autoregressive Integrated Moving Average with Exogenous Regressors (SARIMAX) model:

- **Model specification:** SARIMAX(1,1,1)(1,1,1,12) — capturing both short-term and seasonal (12-month) crash patterns, with AADT as an exogenous variable.
- **Forecast horizon:** 24 months (January 2025 – December 2026).
**Forecasting tasks performed:**

| Forecast | Description |
|---|---|
| Per-road crash forecast | Total crashes per road for 2025–2026 |
| All roads combined forecast | Aggregate Metro Manila crash forecast |
| Crash severity type forecast | Fatal, non-fatal, and property damage forecasts (combined) |
| Crash rate per 100k AADT | Safety trend per road (improving vs. worsening) |
| Peak months & risk scoring | Heatmaps, top-10 riskiest month-road combinations, actionable insights |

---

## III. Results

### 3.1 Data Analysis Findings

#### Traffic Volume Trends (AADT)
- All seven roads experienced a significant AADT dip during 2020–2021 corresponding to COVID-19 lockdowns.
- Traffic recovered to pre-pandemic levels by 2022–2023 and continued growing into 2024.
- EDSA consistently recorded the highest AADT among all roads.

#### Crash Trends
- Total crashes dropped sharply in 2020 due to lockdowns, then gradually recovered through 2021–2022.
- By 2023–2024, most roads returned to or exceeded pre-pandemic crash levels.
- EDSA and C-5 Road recorded the highest total crash counts over the 6-year study period.

#### AADT vs. Crashes Relationship
- **Across roads:** A positive correlation was found between average AADT and total crashes—roads with higher traffic volume tend to experience more crashes overall.
- **Over time (per road):** The year-over-year correlation varies by road. Some roads show strong positive correlations (crashes rise with AADT), while others show weak or negative correlations, suggesting that factors such as infrastructure improvements and enforcement moderate the relationship.
- **Overall finding:** AADT is a meaningful but not sole predictor of crash frequency.

#### Crash Rate Normalization
- When crashes are normalized by AADT (per 100,000 vehicles), road rankings change. Some lower-volume roads have disproportionately high crash rates, revealing hidden safety risks that raw crash counts alone obscure.

#### Crash Severity
- Property damage constitutes the majority of crashes across all roads.
- Non-fatal injury crashes represent a significant share, particularly on high-volume roads.
- Fatal crash counts are relatively low but vary meaningfully between roads.

#### Monthly/Seasonal Patterns
- Each road exhibits distinct monthly crash patterns.
- The heatmap analysis reveals consistent high-risk months across multiple roads.
- Seasonal effects are influenced by weather (rainy season), holidays, and the school calendar.

### 3.2 Forecasting Results

#### Per-Road Forecasts
SARIMA models fitted per road generated 24-month crash forecasts with 95% confidence intervals. Each road received a dedicated forecast plot showing historical data, predicted values, and confidence bands.

#### All Roads Combined
The aggregate Metro Manila forecast provides an overall picture of expected crash trends across all roads, summarizing total expected crashes for 2025 and 2026.

#### Crash Severity Forecasts
SARIMA models were fitted separately for fatal, non-fatal, and property damage crashes across all roads combined, producing severity-specific forecasts and the expected severity distribution for 2025–2026.

#### Crash Rate Safety Trends
Crash rate per 100,000 AADT forecasts indicate whether each road's safety is improving or worsening, independent of traffic growth. Roads are classified as "improving" or "worsening" based on whether the forecasted crash rate is lower or higher than 2024 levels.

#### Peak Crash Months
- Peak crash months were identified per road for 2025 and 2026.
- Forecast heatmaps show predicted monthly crash patterns across all roads.
- The top 10 riskiest month-road combinations were identified for priority intervention.

---

## IV. Discussion

### 4.1 Key Findings

1. **AADT and crashes are positively correlated across roads.** Roads with higher traffic volume experience more crashes overall, confirming the expected relationship.

2. **The temporal relationship varies by road.** For some roads, AADT increases over time correspond to crash increases; for others, infrastructure or enforcement improvements moderate the effect.

3. **Crash rate normalization reveals hidden risks.** Some lower-volume roads are disproportionately dangerous per vehicle, suggesting these roads should receive targeted safety interventions despite lower absolute crash counts.

4. **COVID-19 created a structural break.** The 2020–2021 period caused anomalous drops in both traffic and crashes, affecting trend analysis and model performance.

5. **Monthly patterns are road-specific.** Peak crash months differ between roads, emphasizing the need for road-specific (rather than blanket) safety strategies.

6. **SARIMA captures seasonal patterns effectively.** The model leverages the 12-month seasonal component to reproduce the cyclical crash patterns observed in the data analysis.

### 4.2 Practical Implications

- **Enforcement scheduling:** Peak crash months per road can guide deployment of traffic enforcement during highest-risk periods.
- **Infrastructure investment:** Roads with high crash rates per 100k AADT should be prioritized for engineering improvements.
- **Forecasting for planning:** SARIMA forecasts enable proactive resource allocation for 2025–2026 based on predicted crash volumes.

### 4.3 Limitations

1. **Monthly granularity** may mask within-month patterns (day-of-week, rush hour).
2. **Limited features:** The dataset lacks road geometry, weather, speed, and enforcement data that could improve prediction.
3. **Short time series:** 72 months per road, with 2 years disrupted by COVID-19, limits SARIMA's training data.
4. **AADT constancy within year:** Annual AADT values do not capture within-year traffic variation.
5. **External validity:** Findings are specific to the 7 studied roads and may not generalize broadly.

### 4.4 Future Work

- Incorporate daily/hourly crash data for finer-grained analysis.
- Add weather, road condition, and enforcement data as predictive features.
- Extend the study to additional arterial roads in Metro Manila.
- Develop a real-time crash risk dashboard for MMDA operational use.

---

## V. Conclusion

This study demonstrates that traffic volume (AADT) is a meaningful but not sole predictor of road crash frequency across major Metro Manila roads. The comprehensive data analysis—spanning AADT trends, crash trends, cross-road and temporal correlations, crash rate normalization, severity breakdowns, and monthly pattern identification—provides a detailed empirical picture of road safety conditions from 2019 to 2024. SARIMA forecasting models successfully capture seasonal crash patterns and generate actionable per-road and combined forecasts for 2025–2026, identifying peak crash months, high-risk roads, and safety trends. Together, the data analysis and forecasting components offer a foundation for evidence-based traffic safety policy in Metro Manila.

---

## References

1. Metropolitan Manila Development Authority (MMDA). *MMARAS Annual Reports, 2019–2024.*
2. World Health Organization (WHO). *Global Status Report on Road Safety, 2023.*
3. Hyndman, R.J. & Athanasopoulos, G. *Forecasting: Principles and Practice.* 3rd Edition, OTexts, 2021.
4. Box, G.E.P., Jenkins, G.M., Reinsel, G.C., & Ljung, G.M. *Time Series Analysis: Forecasting and Control.* 5th Edition, Wiley, 2015.
