# Presentation Script: Metro Manila AADT-Crash Analysis

> This is a speaker script — what you actually SAY during the presentation.
> Text in *italics* = stage directions. Text in **bold** = emphasis.

---

## [SLIDE 1: Title]

"Good day everyone. Our study is about **Metro Manila Road Crash Analysis** — specifically, we're investigating whether traffic volume increases crashes on major roads. We used data from 2019 to 2024 and applied both data analysis and forecasting to answer this question."

---

## [SLIDE 2: Introduction]

"So we all know Metro Manila is one of the most congested cities in the world. Millions of vehicles use its roads every day, and unfortunately, road crashes are a constant concern."

"Our main research question is simple: **Does more traffic mean more crashes?** It sounds obvious, but we wanted to find out using actual data — and if so, can we predict when and where crashes will happen?"

---

## [SLIDE 3: The Dataset]

"Our data comes from the **MMDA MMARAS Annual Reports** — these are the official crash records for Metro Manila."

"We studied **7 major roads** — EDSA, C-5, Commonwealth, Quezon Avenue, Roxas Boulevard, Marcos Highway, and Radial Road 10. We looked at **6 years** of monthly data, from 2019 to 2024 — that's **504 records** total."

"Each record contains the road name, the year and month, the **AADT** or traffic volume, and the number of crashes broken down by type — fatal, non-fatal injury, and property damage."

---

## [SLIDE 4: What is AADT?]

"Before we go further — what is AADT? It stands for **Average Annual Daily Traffic**. It's basically the average number of vehicles that pass through a road every day over the course of a year."

"So when we say a road has an AADT of 300,000 — that means about 300,000 vehicles use that road every single day on average. The higher the AADT, the more traffic."

---

## [SLIDE 5: AADT & Crash Trends]

*Point to chart*

"Here we can see the AADT and crash trends for each road across 6 years."

"You'll notice a **sharp dip in 2020** — that's the COVID-19 lockdowns. Traffic dropped dramatically, and so did crashes. But by 2022 to 2023, most roads recovered to pre-pandemic levels, and some even exceeded them by 2024."

"Consistently, **EDSA has the highest traffic volume and the most crashes** among all seven roads."

---

## [SLIDE 6: AADT vs Crashes Relationship]

"Now the key question — **does more traffic actually lead to more crashes?**"

*Point to correlation chart*

"When we compare roads side by side, we find a **positive correlation** — roads with higher AADT tend to have more crashes. That confirms our expectation."

"**But here's the interesting part.** When we normalize crashes by traffic volume — meaning we calculate the **crash rate per 100,000 vehicles** — the ranking changes. Some roads with lower traffic actually have **worse safety performance** per vehicle. This means raw crash numbers alone can be misleading."

---

## [SLIDE 7: Severity & Monthly Patterns]

"In terms of crash severity, **property damage** makes up the largest portion across all roads. Non-fatal injuries are next, and fatal crashes are the lowest in number — but still significant."

*Point to heatmap*

"This heatmap shows the average crashes per month for each road. You can see that **different roads peak in different months**. This is important because it means a one-size-fits-all approach to road safety won't work — each road needs its own schedule."

---

## [SLIDE 8: What is SARIMA?]

"Now let's move to the forecasting part. This is where we use a model called **SARIMA** to predict future crashes."

*Pause — this is the part to explain carefully*

"So what is SARIMA? Think of it this way. If you've been tracking your expenses every month for 6 years, you probably notice patterns — maybe you spend more in December because of the holidays, less in February. SARIMA does the same thing, but with crash data."

"It learns **two things** from the historical data:"
1. "**The overall trend** — are crashes going up or down over the years?"
2. "**Seasonal patterns** — do crashes spike every June? Every December? It finds those repeating cycles."

"On top of that, we also feed it the **AADT data** — the traffic volume — as an additional input, so it knows how traffic levels affect crashes."

"The result is: **based on 6 years of crash patterns and traffic data, SARIMA gives us a forecast for the next 2 years — January 2025 through December 2026.**"

> **If someone asks "how is this machine learning?":**
> "SARIMA is a statistical machine learning model — it automatically learns the parameters from the data rather than us manually defining the rules. It fits itself to the patterns in the data and then projects those patterns forward."

> **If someone asks "what does SARIMAX(1,1,1)(1,1,1,12) mean?":**
> "The numbers are the model's configuration. The first (1,1,1) controls short-term patterns — how today relates to yesterday. The second (1,1,1,12) controls seasonal patterns — the 12 means it looks for patterns that repeat every 12 months, which makes sense for monthly data."

---

## [SLIDE 9: Per-Road Forecasts]

*Show 2–3 forecast charts*

"Here are the SARIMA forecasts for individual roads. The **solid blue line** is the actual historical data. The **dashed red line** is our forecast. The **shaded area** is the 95% confidence interval — meaning we're 95% confident the actual crashes will fall within that range."

"You can see that the model captures the seasonal ups and downs quite well. For each road, we calculated the expected total crashes for 2025 and 2026, and whether that's an increase or decrease compared to 2024."

---

## [SLIDE 10: All Roads Combined]

"We also ran a forecast for **all 7 roads combined** — so this is basically the total Metro Manila picture."

*Point to the stats box on the chart*

"Here you can see the average monthly crashes across all roads, the total expected for 2025 and 2026, and the percentage change. This gives planners a big-picture view."

---

## [SLIDE 11: Crash Type Forecasts]

"We didn't just forecast total crashes — we also forecasted each **crash type separately**: fatal, non-fatal, and property damage."

"The red line is fatal, orange is non-fatal, and green is property damage. The solid lines are historical, dashed lines are forecast."

"Property damage remains the most common type. Fatal crashes are harder to predict because the numbers are small and more random, but the model still captures the general trend."

---

## [SLIDE 12: Safety Trends]

"This is one of the most insightful parts. Instead of just forecasting raw crash counts, we forecasted the **crash rate per 100,000 vehicles** for each road."

"Why does this matter? Because it tells us if a road is getting **safer or more dangerous independent of traffic growth**. A road might have more crashes simply because more cars are using it — but if the crash rate per vehicle is going down, that means safety is actually improving."

"The green box means improving safety, yellow means worsening. This helps prioritize which roads need the most urgent attention."

---

## [SLIDE 13: Peak Months & High-Risk Periods]

*Point to heatmaps*

"These heatmaps show the predicted crash counts for every road and every month in 2025 and 2026. The darker the color, the more crashes expected."

"We also identified the **top 10 riskiest month-road combinations** — these are the specific periods where MMDA should concentrate enforcement and monitoring."

---

## [SLIDE 14: Key Findings]

"To summarize our findings:"

1. "**Yes, more traffic does mean more crashes** — the positive correlation is confirmed."
2. "**But it's not the only factor.** Some roads with less traffic are actually more dangerous per vehicle."
3. "**COVID-19 significantly disrupted patterns** in 2020–2021, but things have returned to normal by 2023."
4. "**Peak crash months differ by road** — there's no single 'dangerous month' for all of Metro Manila."
5. "**SARIMA can forecast crashes effectively** and help authorities plan ahead."

---

## [SLIDE 15: Recommendations]

"Based on our analysis, we recommend:"

1. "**Deploy enforcement during peak crash months** — but road-specific, not blanket deployment."
2. "**Prioritize infrastructure improvements** on roads with high crash rates per vehicle."
3. "**Use forecasts for proactive planning** — allocate ambulances, enforcers, and resources to high-risk road-month combinations."
4. "**Collect more data** — daily data, weather, vehicle speed — to make future models even more accurate."

---

## [SLIDE 16: Conclusion]

"In conclusion, traffic volume is a meaningful but not sole predictor of road crashes. Our study combines comprehensive data analysis with SARIMA forecasting to give a complete picture of road safety in Metro Manila from 2019 to 2024, with actionable forecasts for 2025 and 2026. Thank you."

---

## [SLIDE 17: Q&A]

"We're now open for questions."

---

## Common Q&A Answers

**Q: Why SARIMA and not other models?**
> "SARIMA is specifically designed for time series data with seasonal patterns — which is exactly what crash data is. Monthly crashes follow seasonal cycles, and SARIMA is built to capture that. It's also interpretable and well-established in forecasting literature."

**Q: How accurate is the model?**
> "The model was trained on 2019–2023 and tested on 2024 data. It captures the seasonal patterns well. But like any forecast, it becomes less certain the further out you go — that's why we show confidence intervals."

**Q: Why not use AI / deep learning?**
> "Deep learning models like LSTMs need much larger datasets to be effective. With only 72 months per road, SARIMA is a better fit. Our dataset size favors classical statistical models."

**Q: What does the confidence interval mean?**
> "It means we're 95% confident the actual crash count will fall within that shaded range. It's like a weather forecast saying 'expect 28–32 degrees' instead of just saying '30 degrees.'"

**Q: Can this be used in real life?**
> "Absolutely. MMDA could use this approach to plan enforcement schedules, allocate emergency response resources, and prioritize road safety improvements based on predicted high-risk periods."
