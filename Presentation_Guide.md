# Presentation Guide: Metro Manila AADT-Crash Analysis

## Recommended Slide Structure

---

### Slide 1: Title Slide
- **Title:** Metro Manila Road Crash Analysis: Does Traffic Volume Increase Crashes?
- **Subtitle:** A Data Analysis and SARIMA Forecasting Study on AADT vs Crashes (2019–2024)
- **Authors:** Jerdan L. Gondayao, Johnmer M. Tanqui-on
- **Course/Subject info**

---

### Slide 2: Introduction / Background
- Metro Manila = one of the most congested cities in the world
- Road crashes are a persistent public safety issue
- **Research Question:** Does traffic volume (AADT) increase crashes on major roads?
- 💡 *Keep it brief — just set the stage*

---

### Slide 3: The Dataset
- Source: MMDA MMARAS Annual Reports
- 7 major roads (EDSA, C-5, Commonwealth, Quezon Ave, Roxas Blvd, Marcos Highway, Radial Road 10)
- Period: 2019–2024 (6 years, 72 months)
- 504 monthly records
- Variables: road name, year, month, AADT, total crashes, fatal, non-fatal, property damage

---

### Slide 4: What is AADT?
- **Average Annual Daily Traffic** — the average number of vehicles passing a road per day over a year
- Higher AADT = more traffic
- We want to know: **more traffic = more crashes?**

---

### Slides 5–7: Data Analysis Findings
Show the key visualizations from the code:

**Slide 5 — AADT & Crash Trends**
- Show the per-road trend charts (AADT over time, crashes over time)
- Point out: COVID-19 dip in 2020, recovery by 2022–2023
- EDSA = highest traffic and most crashes

**Slide 6 — AADT vs Crashes Relationship**
- Show the dual-axis chart (AADT vs crashes on same plot)
- Mention the correlation: positive relationship across roads
- Show crash rate per 100k AADT → reveals hidden risks on lower-volume roads

**Slide 7 — Crash Severity & Monthly Patterns**
- Show crash severity breakdown (fatal, non-fatal, property)
- Show the monthly heatmap → different roads peak in different months
- Property damage = most common type

---

### Slide 8: What is SARIMA? (The Machine Learning Part)
**This is the key slide to make it understandable:**

- SARIMA = a forecasting model that learns from historical patterns
- It looks at: **trends** (are crashes going up or down?) + **seasonality** (do crashes spike in certain months every year?)
- We also feed it AADT data so it knows about traffic volume
- Think of it like this: *"Based on how crashes behaved in 2019–2024, what should we expect in 2025–2026?"*

**Visual suggestion:** Simple diagram:
```
Historical Data (2019-2024) → SARIMA Model → Forecast (2025-2026)
```

---

### Slide 9: Per-Road Forecasts
- Show 2–3 of the per-road forecast charts (pick the most interesting ones)
- Point out: historical line → forecast line → confidence interval (shaded area)
- Mention which roads are expected to see more/fewer crashes

---

### Slide 10: All Roads Combined Forecast
- Show the combined Metro Manila forecast chart
- Highlight: total expected crashes for 2025 and 2026
- Mention the percentage change vs 2024

---

### Slide 11: Crash Type Forecasts
- Show the severity forecast chart (fatal, non-fatal, property)
- Mention the expected distribution: property damage still dominant
- Fatal crashes forecast

---

### Slide 12: Safety Trends (Crash Rate per 100k AADT)
- Show 2–3 of the crash rate forecast charts
- Explain: this tells us if roads are getting *safer* or *more dangerous*, regardless of traffic growth
- List which roads are improving vs worsening

---

### Slide 13: Peak Crash Months & High-Risk Periods
- Show the 2025 and 2026 heatmaps
- Highlight the top 3 riskiest month-road combinations
- Show the most common peak month across all roads

---

### Slide 14: Key Findings / Insights
Summarize in bullet points:
1. AADT and crashes ARE positively correlated
2. But it's not the only factor — some roads are more dangerous per vehicle than others
3. COVID-19 disrupted patterns significantly
4. Monthly crash patterns are road-specific, not uniform
5. SARIMA forecasts can help plan enforcement and safety interventions

---

### Slide 15: Recommendations
- Deploy enforcement during peak crash months (road-specific)
- Prioritize infrastructure upgrades on roads with high crash rates per 100k AADT
- Use forecasts for proactive resource allocation
- Consider further data collection (weather, speed, daily data) for better models

---

### Slide 16: Conclusion
- AADT is a meaningful predictor of crashes but not the sole factor
- Data analysis + SARIMA forecasting = comprehensive road safety picture
- The study provides actionable, road-specific insights for Metro Manila

---

### Slide 17: Thank You / Q&A

---

## Presentation Tips

1. **Don't read slides** — use the script as your talking guide
2. **Show the visualizations** — the charts tell the story, you just narrate
3. **Keep ML explanation simple** — use analogies, avoid jargon
4. **Time allocation:** ~2 min for background, ~5 min for data analysis, ~5 min for forecasting, ~3 min for insights
5. **Anticipate questions about SARIMA** — see the script for how to handle them
