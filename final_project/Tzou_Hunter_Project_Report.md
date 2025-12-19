# Three Years of Mental Health: Depression Trends Across U.S. Counties (2021-2023)

**Hunter Tzou | DATA 110 - Final Project**

---

## Executive Summary

This project analyzes depression prevalence trends across 2,874 U.S. counties from 2021-2023 using CDC PLACES data. Through six visualizations (two interactive, four static), I examine post-pandemic mental health trajectories and the evolving relationship between health behaviors and depression.

**Key Findings:**
- Depression **increased 1.36 percentage points** (23.04% → 24.06%), with **79% of counties worsening**
- **All behavioral predictors weakened substantially:** smoking (r: 0.52→0.38), physical inactivity (0.29→0.06), obesity (0.19→0.16)
- **Multicollinearity among behaviors persisted** (smoking-inactivity r>0.75), confirming health behaviors still cluster
- **Geographic disparities deepened:** Appalachian and Western states worsened most (SD +4.49, WV +4.04); only NJ/NY improved (-3.01, -2.29)
- **Critical implication:** Traditional health behavior interventions may be insufficient—economic and social factors likely now dominate depression patterns

---

## 1. Introduction and Connection to Previous Research

In a prior regression project, I analyzed 2021 county-level data and found smoking was the strongest predictor of depression (β=0.681, p<2e-16, r=0.52), with severe multicollinearity among behaviors (VIF=6.43). That model explained 35% of variance but raised questions: Are these patterns stable? Is the smoking-depression link consistent?

This project extends that analysis across three years (2021-2023) to examine: **How are depression and health behavior patterns evolving in the post-pandemic era?** By merging three CDC data releases and tracking 2,874 counties over time, I identify improvement/deterioration patterns and test whether behavioral relationships remain stable.

**Dataset:** CDC PLACES (Population Level Analysis and Community Estimates)
- 2,874 counties with complete data (2021: 3,076 counties; 2022: 3,144; 2023: 2,956)
- Age-adjusted prevalence rates for fair geographic comparison
- Variables: Depression (outcome); smoking, obesity, physical inactivity, insurance, checkups (predictors)

**Data Quality Note:** I verified all six measures existed in 2021-2023 data (2020 lacked these measures). Used age-adjusted prevalence only—my previous project incorrectly averaged crude and age-adjusted rates. Complete cases only ensures consistent geographic coverage.

---

## 2. Key Findings

### 2.1 Depression Worsened Dramatically

| Year | Mean Depression | Counties in Sample |
|------|----------------|-------------------|
| 2021 | 23.04% (SD=3.28) | 3,076 |
| 2022 | 24.29% (SD=3.45) | 3,144 |
| 2023 | 24.06% (SD=3.46) | 2,956 |

**Change (2021→2023):** +1.36 points average | Range: -5.50 to +6.40 points  
**Distribution:** 79% worsened (2,270 counties), 19% improved (553), 2% unchanged (51)

### 2.2 All Behavioral Predictors Weakened

**Correlation with Depression:**

| Predictor | 2021 | 2023 | % Change |
|-----------|------|------|----------|
| Smoking | 0.52 | 0.38 | **-27%** |
| Physical Inactivity | 0.29 | 0.06 | **-79%** |
| Obesity | 0.19 | 0.16 | -16% |
| Routine Checkup | 0.21 | 0.13 | -38% |
| No Insurance | -0.04 | -0.23 | Flipped negative |

**Multicollinearity Persisted:** Smoking-inactivity (0.81→0.76), smoking-obesity (0.69→0.71), obesity-inactivity (0.78→0.75) all remained >0.7, confirming behaviors still cluster at community level.

**Critical Insight:** Health behaviors still co-occur in the same communities, but they ALL became less predictive of depression. This strongly suggests economic stress, social isolation, and pandemic-specific aftermath factors now drive depression patterns more than traditional health behaviors.

### 2.3 Geographic Patterns Deepened

**State-Level Changes (Top/Bottom 5):**

**Largest Increases:** SD (+4.49), DE (+4.07), WV (+4.04), HI (+3.94), CA (+3.70)  
**Only Meaningful Decreases:** NJ (-3.01), NY (-2.29)

**Consistent High-Depression States:** West Virginia, Kentucky, Tennessee, Arkansas consistently rank in top 15 across all three years. Geographic concentration in Appalachia, Deep South, and rural West persisted but intensified.

---

## 3. Visualizations and Insights

### Interactive Visualization 1: Choropleth Map

**[View Interactive Map]()** | **File:** `viz1_depression_map.html`

The animated map shows depression prevalence by county across 2021-2023. The map visibly **darkens** from 2021→2023, with the most dramatic shift occurring 2021→2022. In 2021, the West Coast and Great Plains display lighter yellow/orange (15-20%), while Appalachia shows dark red (25-30%). By 2023, the West Coast has shifted to orange/red (20-25%), the Great Plains to orange/red (18-22%), and Appalachia remains at maximum dark red (27-30%). 

The geographic "belt" of high depression—stretching from Appalachia through the rural Midwest to the Northwest—becomes more pronounced and interconnected over time. California's dramatic worsening is visually obvious (light yellow → orange/red), confirming the +3.70 point increase. South Dakota's darkening from yellow to red illustrates its +4.49 point increase. Coastal metropolitan areas (Northeast corridor, San Francisco Bay) remain relatively lighter, with New Jersey and New York showing visible stability compared to surrounding regions.

**Hover format:** "Montgomery, MD" displays depression and smoking percentages, making county-level comparisons intuitive.

**Key Insight:** The widespread darkening contradicts expectations of post-pandemic mental health recovery. Geographic disparities that existed in 2021 didn't just persist—they deepened, with already-high-depression regions remaining at ceiling while moderate-depression regions caught up.

---

### Interactive Visualization 2: Smoking vs Depression Scatter

**[View Interactive Scatter Plot]()** | **File:** `viz2_smoking_depression_scatter.html`

Each point represents one county, sized by obesity prevalence, colored by depression level. The **weakening correlation** (0.52→0.38) is visually striking across the animation. In 2021, counties cluster tightly along a diagonal trend line; by 2023, substantial scatter emerges with dramatically increased vertical spread. 

**2021 pattern:** Counties with 25% smoking prevalence cluster narrowly at 24-28% depression (±2 points). The tight diagonal indicates smoking strongly predicts depression. High-smoking counties (>30%) uniformly cluster at 28-32% depression with minimal variability.

**2023 pattern:** Counties with 25% smoking now range from 20-32% depression (±6 points)—a **fourfold increase in variability**. High-smoking counties (>30%) "fan out" dramatically from 22-36% depression, showing that smoking alone no longer reliably predicts outcomes. The scatter plot has loosened considerably, with points spreading vertically rather than following the diagonal.

**Upward shift:** The entire point cloud shifts upward from 2021→2023, confirming universal depression increases. For any given smoking rate, depression is approximately 1-2 percentage points higher in 2023 than 2021.

**Persistent clustering:** Larger points (high obesity) still cluster with high smoking and high depression across all years, confirming behavioral multicollinearity persists. The legend box clarifies that point size represents obesity and color intensity represents depression level.

**Implication:** Smoking explained 27% of depression variance in 2021 (r²=0.52²); by 2023, only 14% (r²=0.38²). This halving of explanatory power is visually obvious in the scatter increase. The weakening is NOT because counties stopped smoking (x-axis range remains 5-45% across years), but because depression became **unpredictable from smoking alone**. Some high-smoking counties now have moderate depression, while some moderate-smoking counties have high depression—patterns that were rare in 2021.

Despite the weakening, some relationship remains: no counties have very high smoking (>35%) with very low depression (<15%), confirming the correlation hasn't disappeared entirely. However, smoking's utility as a **predictor** has substantially diminished.

---

### Static Visualization 3: State Comparison Bar Charts

**![State Comparison]()** | **File:** `viz3_state_comparison.png`

Side-by-side bar charts show top 15 states by depression for each year. Rankings barely shifted—KY, TN, WV dominate all three years. All bars lengthen slightly 2021→2023, showing universal increases even among "relatively low" states.

**Insight:** Structural factors (economic conditions, healthcare access, policy environments) drive patterns more than temporal trends.

---

### Static Visualization 4: Depression Change Diverging Bars

**![Depression Changes by State]()** | **File:** `viz4_depression_change.png`

Far more red bars (increases) than green (decreases) visually confirms 79% worsened. Only NJ (-3.01) and NY (-2.29) showed meaningful improvement. SD, DE, WV saw dramatic increases (>4 points).

**No clear regional pattern in improvers:** NJ, NY, MS, RI, GA span different regions, suggesting improvements are idiosyncratic rather than regional policy-driven.

---

### Static Visualization 5: Correlation Matrix Comparison

**![Correlation Matrix Comparison]()** | **File:** `viz5_correlation_comparison.png`

Side-by-side heatmaps reveal:
- **All depression correlations weakened** (top row lighter in 2023)
- **Multicollinearity among behaviors stayed high** (smoking-inactivity-obesity block still dark red/orange)
- **Physical inactivity correlation collapsed** from 0.29→0.06 (lightest change)

**Critical finding:** Behaviors cluster together (smoking, obesity, inactivity still highly correlated), but this clustering no longer predicts depression as strongly. External factors (economic stress, isolation) likely now dominate.

---

### Static Visualization 6: Distribution of Changes

**![Distribution of Depression Changes]()** | **File:** `viz6_depression_distribution.png`

Heavily right-skewed histogram shows most counties in +1 to +3 range. Mean (+1.36) well right of zero. Left tail (improvements) shorter than right tail (worsening), indicating counties that worsened did so more dramatically.

**19% that improved** (left of zero line) prove change is possible and should be studied intensively.

---

## 4. Discussion

### 4.1 Comparison to Regression Work

My 2021 regression found smoking dominant (β=0.68, r=0.52) with multicollinearity (VIF=6.43). This temporal analysis reveals:

**Continuities:**
- Geographic patterns stable (high-depression counties remained high)
- Behavioral clustering persists (smoking-obesity-inactivity correlations >0.7)

**Critical Departures:**
- **All behavioral predictors weakened**, not just smoking
- Physical inactivity correlation **collapsed 79%** (0.29→0.06)
- A regression model fit on 2021 data would likely perform poorly predicting 2023 outcomes

**Implication:** The β=0.68 smoking coefficient may have been specific to 2021 conditions. A 2023 regression would show smaller coefficients across all behaviors and likely <35% variance explained. The 65% unexplained variance in my 2021 model may be even larger now.

### 4.2 Why Did Relationships Weaken?

The visual evidence from the scatter plot animation provides critical insight: **the weakening is not because counties stopped smoking, but because depression became unpredictable from smoking**. The x-axis range (smoking prevalence) remains 5-45% across all three years, yet the vertical spread (depression variability for any given smoking rate) increased dramatically.

Since **all** behavioral predictors weakened while multicollinearity persisted, this suggests:

1. **Economic/social factors became dominant:** Inflation, housing costs, job insecurity may now drive depression regardless of smoking/obesity status. A high-smoking county that maintained economic stability may have avoided depression increases, while a low-smoking county facing economic hardship experienced sharp increases. This would produce the scatter pattern observed.

2. **Pandemic-specific aftermath effects:** Long COVID, isolation effects, healthcare disruption, loss/grief affected communities differently based on factors uncorrelated with health behaviors. Counties with stronger social capital or community support may have buffered against depression despite high smoking rates.

3. **Geographic/structural factors diverged from behaviors:** The map shows depression worsening universally but unevenly. The scatter plot shows that smoking no longer predicts which counties worsened most. This suggests place-based structural factors (local economy, healthcare access, policy responses) now dominate over behavioral patterns.

4. **Threshold or non-linear effects:** Perhaps the relationship between behaviors and depression is non-linear, and as average smoking rates declined nationally, the linear correlation weakened even though causation persists at individual levels.

The 2022 visualization serves as a "transition year"—visually intermediate between 2021's tightness and 2023's scatter—matching the stepwise correlation decline (0.52 → 0.46 → 0.38). This progressive loosening suggests a gradual shift in depression drivers rather than a sudden methodological change.

### 4.3 Public Health Implications

1. **Traditional behavioral interventions may be insufficient:** If health behaviors explain less variance, smoking cessation and obesity programs alone won't address the crisis
2. **Economic security and social connection likely matter more now:** Public health must shift focus to poverty, employment, housing, social isolation
3. **Learn from NJ/NY:** The only states that improved should be studied—what policies or conditions distinguished them?
4. **Target Western/Appalachian states:** SD, WV, HI, CA need urgent support
5. **Study the 19% that improved:** Counties with decreases up to -5.5 points offer replicable lessons

### 4.4 Limitations

- **Ecological fallacy:** County patterns may not reflect individual relationships
- **Causation unclear:** Observational data; depression and behaviors may share common causes
- **Missing variables:** Poverty, unemployment, education, housing costs not included
- **Short timeframe:** 3 years may not capture longer trends; 2021-2023 is unusual (pandemic aftermath)
- **Selection bias:** Requiring complete data reduced sample from 3,076→2,874 counties

---

## 5. Conclusion and Future Directions

Depression prevalence increased 1.36 points across 79% of U.S. counties from 2021-2023—**this is crisis, not recovery**. The interactive visualizations make this visually undeniable: the choropleth map progressively darkens year by year, and the scatter plot's tight diagonal clustering dissolves into scatter. More importantly, **all health behavior predictors weakened substantially** while behavioral clustering persisted. This strongly suggests the drivers of community-level depression shifted from health behaviors toward economic and social factors.

The scatter plot animation provides the clearest evidence: for counties with 25% smoking prevalence, depression ranged ±2 points in 2021 but ±6 points in 2023—a fourfold increase in unpredictability. Smoking didn't become less common (the range remained 5-45%), but it became far less predictive. High-smoking counties that were uniformly at 28-32% depression in 2021 now span 22-36%—a massive divergence suggesting other factors now dominate individual county trajectories.

This challenges my regression findings: a model showing smoking as "dominant" (β=0.68) in 2021 would likely underperform in 2023. **Relationships between behaviors and mental health are not static**—public health models must be regularly updated. The map's visible darkening from West to East, the scatter plot's loosening diagonal, and the correlation matrix's systematic weakening all point to the same conclusion: traditional health behavior interventions, while still valuable, are no longer sufficient to address the depression crisis.

The 553 counties that improved prove change is possible. Understanding what distinguished them from the 2,270 that worsened—whether economic resilience, social capital, policy interventions, or other structural factors—should be public health's top priority.

### Future Research

1. **Add socioeconomic variables:** Poverty, unemployment, education, housing costs to test if they now explain more variance
2. **Study improving counties:** Identify local policies, economic conditions, healthcare access distinguishing them
3. **Extend timeframe:** 5-10 years to separate pandemic-specific effects from longer trends
4. **Individual-level data:** Track same people over time to establish causation
5. **Policy analysis:** Compare states with different mental health policies, Medicaid expansion, telehealth access
6. **Test economic hypothesis:** Did counties with worse economic outcomes (inflation-adjusted wage decreases, housing cost increases) show larger depression increases?

---

## References

Centers for Disease Control and Prevention. (2023). *PLACES: Local Data for Better Health, County Data 2023 release*. Data.gov. https://catalog.data.gov/dataset/places-local-data-for-better-health-county-data-2023-release

Centers for Disease Control and Prevention. (2024). *PLACES: County Data 2024 release*. Data.gov.

Centers for Disease Control and Prevention. (2025). *PLACES: County Data 2025 release*. Data.gov.

---

## Appendix: Code and Reproducibility

**Software:** Python 3.x, pandas, plotly, matplotlib, seaborn  
**Code:** [View Jupyter Notebook]()  
**Visualizations Generated:**
- [viz1_depression_map.html]() (interactive choropleth)
- [viz2_smoking_depression_scatter.html]() (interactive scatter)
- [viz3_state_comparison.png]() (static bar charts)
- [viz4_depression_change.png]() (static diverging bars)
- [viz5_correlation_comparison.png]() (static heatmaps)
- [viz6_depression_distribution.png]() (static histogram)

To reproduce: Install dependencies (`pip install pandas plotly matplotlib seaborn`), update file paths in notebook, run cells sequentially.
