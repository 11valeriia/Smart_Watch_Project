<div class='tableauPlaceholder' id='viz1761156893850' style='position: relative'><noscript><a href='#'><img alt='A Deep Dive into Personal Wellness ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;pe&#47;petprojectmifit&#47;ADeepDiveintoPersonalWellness&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='petprojectmifit&#47;ADeepDiveintoPersonalWellness' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;pe&#47;petprojectmifit&#47;ADeepDiveintoPersonalWellness&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-US' /><param name='filter' value='publish=yes' /></object></div>                <script type='text/javascript'>                    var divElement = document.getElementById('viz1761156893850');                    var vizElement = divElement.getElementsByTagName('object')[0];                    if ( divElement.offsetWidth > 800 ) { vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} else if ( divElement.offsetWidth > 500 ) { vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} else { vizElement.style.width='100%';vizElement.style.height='1927px';}                     var scriptElement = document.createElement('script');                    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';                    vizElement.parentNode.insertBefore(scriptElement, vizElement);                </script>
# Executive Summary

This comprehensive analytics project examines personal health data collected from smartwatch technology, spanning from January 2023 to August 2025. The analysis encompasses three key dimensions of personal wellness: physical activity, sleep patterns, and cardiovascular health. Through exploratory data analysis, hypothesis testing, and interactive visualization, this project reveals meaningful insights about behavioral patterns, health trends, and the interconnections between different wellness metrics.

**Key Findings:**

- Average daily step count of 6355 falls below the recommended 10000 steps target
- Sleep duration of 8.77 hours exceeds recommended guidelines, indicating good rest habits
- Significant weekend vs. weekday behavioral differences detected
- Insignificant correlation observed between activity levels and sleep quality
- Resting heart rate of 85 bpm suggests potential for cardiovascular improvement

---

## 1. Project Overview

### 1.1 Objectives

- Demonstrate proficiency in the data analytics workflow from raw data to insights
- Apply statistical hypothesis testing to real-world personal health data
- Create interactive visualizations that tell a data-driven story

### 1.2 Data Sources & Structure

**Dataset Coverage:** January 2, 2023 - August 24, 2025 (965 days)

**Three Primary Tables:**

1. **Sleep Data**
    - Metrics: Date, deep sleep duration, shallow sleep duration, wake time, start/end times, total minutes/hours
    - Temporal features: Weekday, is_weekend (Boolean)
    - Purpose: Analyze sleep quality and patterns
2. **Activity Data**
    - Metrics: Date, steps, distance, run distance, calories burned
    - Temporal features: Weekday, is_weekend (Boolean)
    - Purpose: Track physical activity levels and exercise habits
3. **Heart Rate Data**
    - Metrics: Date, time of day period, average heart rate
    - Purpose: Monitor cardiovascular health indicators

### 1.3 Technical Stack

- **Data Cleaning & EDA:** Python (Pandas, NumPy)
- **Statistical Analysis:** Scipy
- **Visualization:** Tableau Desktop, Python matplotlib, Seaborn
- **Development Environment:** Jupyter Notebook

---

## 2. Data Processing & Quality

**SLEEP**

- Rows with total sleep time less than **180 minutes (3 hours)** were filtered out to ensure the analysis focused on valid, primary sleep sessions.
- The final cleaned `sleep` dataset contains **655** records.
- Calculated total sleep duration from component stages

**ACTIVITY**

- The Activity table was cleaned to include key physical metrics: `steps`, `distance`, `run_distance`, and `calories`.
- Similar to the sleep data, categorical time columns (`weekday`, `is_weekend`) were added to facilitate comparisons and pattern analysis.
- The final cleaned dataset contains **680** records.

**HEART RATE**

- Aggregated heart rate by day parts for pattern detection
- Made sure to use the right formats (date)

---

## 3. Exploratory Data Analysis (EDA) and Insights

### 3.1 Physical Activity Analysis

**Overall Activity Profile:**

- **Average Daily Steps:** 6355
- **Average Calories Burned:** 168.2 per day
- **Activity Status:** Below the recommended 10000 steps/day threshold

The histogram reveals a right-skewed distribution of daily step counts, indicating varied activity levels:

- The highest frequency (70+ days) occurs in the lowest step count range (0-2000 steps), suggesting sedentary days
- The majority of active days cluster between 2000-10000 steps, with relatively consistent frequencies (50-60 days per range)
- **Bimodal Pattern:** Two distinct peaks suggest two primary activity patterns - low activity days (0-2,000) and moderate activity days (4000-8000)

**Temporal Patterns:**

*Monthly Trends (Jan-Dec):*
The Activity & Sleep Trends visualization reveals significant seasonal variation:

- **Winter months (Jan-Feb):** Moderate activity levels (~5000-6000 steps)
- **Spring plateau (Mar-May):** Consistent activity around 6000 steps
- **Summer surge (Jun-Aug):** Peak activity period with the highest step counts (8413)
- **Fall decline (Sep-Dec):** Gradual decrease returning to baseline

**Key Insight:** Activity levels show a clear seasonal pattern, with warmer months correlating to increased physical activity. The summer peak suggests outdoor activities or specific lifestyle factors during this period.

*Weekday vs. Weekend Comparison:*

- **Weekday Performance:** 5102 average daily steps
- **Weekend Performance:** 9448 average daily steps
- **Differential:** +97% increase on weekends

**Key Insight:** Weekend activity nearly doubles compared to weekdays, suggesting a sedentary work lifestyle during the week. This represents a major opportunity for intervention to increase weekday movement.

### 3.2 Sleep Analysis

**Sleep Duration Profile:**

- **Average Sleep:** 8.77 hours per night
- **Health Context:** Within recommended 7-9 hours, indicating prioritization of rest
- **Consistency:** Relatively stable across the observation period  

The histogram reveals a normal distribution centered at 8-9 hours

- **Highest Peak:** 210 nights within 8-9 hours (optimal range)
- **Secondary Peak:** 200 nights within 9-10 hours
- **Tight Clustering:** 84% of the dataset falls within 7-10 hours

**Sleep Architecture:**

*Weekday Sleep Composition:*

- Shallow sleep: 6.4 hours (72%)
- Deep sleep: 2.33 hours (27%)
- Wake time: 0.07 hours (1%)

*Weekend Sleep Composition:*

- Shallow sleep: 6.2 hours (70%)
- Deep sleep: 2.43 hours (29%)
- Wake time: 0.08 hours (1%)

**Key Insight:** Sleep stage distributions remain remarkably consistent between weekdays and weekends, with a slight improvement in deep sleep percentage on weekends. The deep sleep duration (2.3-2.5 hours) falls within healthy ranges (1.5-2.5 hours typical).

**Sleep Quality Observations:**

- Minimal wake time indicates good sleep continuity
- Consistent bedtime routine (evidenced by stable stage distributions)
- Good sleep habits are maintained throughout the week

### 3.3 Cardiovascular Health

**Resting Heart Rate:**

- **Average:** 85.40 bpm
- **Clinical Context:** Upper end of normal range (60-100 bpm)
- **Consideration:** Opportunity for cardiovascular fitness improvement
**Key Insight:** While within normal limits, the resting heart rate suggests moderate cardiovascular fitness. Regular aerobic exercise could lower this metric, which is associated with better long-term health outcomes.

---

## 4. Hypothesis Testing Results

### 4.1 Test 1: Sleep Duration

**Hypothesis:**

- H₀: The average total hours of sleep on weekends is equal to the average total hours of sleep on weekdays
- H₁: The average total hours of sleep on weekends is different from the average total hours of sleep on weekdays.

**Method:** Welch’s t-test (checked if assumptions are satisfied)

**Results:**

- **Weekend Mean:** 8.73 hours
- **Weekday Mean:** 8.78 hours
- **Difference:** -0.05 hours (weekday slightly higher)

**Results:**

- p-value `0.71` > 0.05
- **Conclusion:** Do not reject the null hypothesis

**Interpretation:**
The minimal difference of 0.05 hours (3 minutes) between weekend and weekday sleep suggests highly consistent sleep patterns regardless of day type. This indicates strong sleep discipline and potentially a well-established sleep routine that doesn't significantly vary based on work/non-work days.

**Business/Health Insight:**
This finding is noteworthy as many individuals typically exhibit "social jet lag" - sleeping significantly more on weekends to compensate for weekday sleep debt. The absence of this pattern suggests:

1. Adequate sleep was obtained throughout the week
2. Consistent sleep-wake schedule maintained
3. Good sleep hygiene practices
4. Minimal sleep debt accumulation

### 4.2 Test 2: Physical Activity

**Hypothesis:**

- H₀: The average number of daily steps on weekdays is equal to the average number of daily steps on weekends.
- H₁: The average number of daily steps on weekdays is not equal to the average number of daily steps on weekends.

**Method:** Welch’s t-test

**Results:**

- Average steps on weekday **5102**
- Average steps on weekend **9448**
- Difference: **4346**
- p-value: **6.82 × 10⁻²⁰**
- **Conclusion:** There is a significant statistical difference between physical activity on weekend and weekday.

**Interpretation:** The person takes substantially more steps on weekends than on weekdays. The large mean difference suggests that the effect is not only statistically significant but also practically meaningful, reflecting a clear behavioral pattern of increased physical activity during weekends.

### 4.3 Test 3: Activity's Impact on Sleep Duration

**Hypothesis:**

- H₀: There is no correlation between the number of steps taken in a day and the hours of sleep during the following night.
- H₁: There is a positive correlation between the number of steps taken in a day and the hours of sleep during the following night.

**Method:** Spearman correlation coefficient (data is not normally distributed)

**Results:**

- Correlation coefficient: -0.14
- p-value: 0.0005
- **Conclusion:** Weak negative correlation

**Interpretation:** While statistically detectable, the weak correlation suggests activity is one of many factors influencing sleep duration.

### 4.4 Test 4: Activity's Impact on Heart Rate

**Hypothesis:**

- H₀: There is no correlation between the running distance for a given day and the average heart rate for that day.
- H₁: There is a positive correlation between running distance and the average daily heart rate.

**Method:** Spearman correlation coefficient (data is not normally distributed)

**Results:**

- Correlation coefficient: -0.1
- p-value: 0.24
- **Conclusion:** The results are not statistically detectable; there is no correlation between the running distance for a given day and the average heart rate for that day.

---

## 5. Patterns and Recommendations

### 5.1 Lifestyle Segmentation

**Weekday Behavior Pattern:**

- Sedentary professional lifestyle (5102 steps)
- Adequate sleep (8.79 hours)
- Consistent routine and schedule

**Weekend Behavior Pattern:**

- Active lifestyle (9448 steps)
- Slightly decreased sleep (8.72 hours)
- Greater variability in daily patterns

### 5.2 Seasonal Variations

**Activity Seasonality:**

- Clear weather-dependent activity patterns
- 20-30% variation between winter lows and summer peaks
- Suggests outdoor preference for physical activity

**Sleep Stability:**

- Sleep duration remains consistent year-round
- Indicates strong circadian rhythm regulation
- Not significantly impacted by seasonal changes

### 5.3 Health Risk Assessment

**Positive Indicators:**

- Adequate sleep duration
- Good sleep architecture
- Consistent health monitoring habits
- Above-average weekend activity

**Areas for Improvement:**

- Below-target weekday activity levels
- Elevated resting heart rate
- Large weekday/weekend activity disparity
- Overall average steps below 10,000 target

---

## 6. Actionable Recommendations

### 6.1 Immediate Actions

**Increase Weekday Movement**

- Target: 7500 steps on weekdays (50% increase)
- Strategies: Walking meetings, lunch walks, parking further
- Expected impact: 15% increase in overall weekly activity

**Cardiovascular Focus**

- Add 20 minutes of moderate cardio 3x/week (jogging or skipping rope before work)
- Goal: Reduce resting heart rate to 75-80 bpm
- Monitor weekly using existing tracking

### 6.2 Medium-term Goals

**Eliminate Weekend/Weekday Gap**

- Gradually increase weekday baseline
- Maintain weekend activity levels
- Target: <3,000 step difference between day types

**Activity Consistency**

- Reduce day-to-day variability
- Establish minimum daily movement floor
- Build sustainable habits vs. sporadic effort

---

## 7. Methodology & Technical Approach

### 7.1 Analytical Techniques Applied

**Exploratory Data Analysis:**

- Univariate distributions for metrics
- Bivariate correlation analysis
- Temporal trend decomposition
- Outlier detection and treatment

**Statistical Testing:**

- Parametric tests (t-tests for normally distributed data)
- Non-parametric alternatives where appropriate
- Correlation analysis (Spearman)
- Significance level: α = 0.05

**Visualization Design:**

- User-centric dashboard layout
- Consistent color scheme (green for activity/health)
- Interactive filtering for exploratory analysis
- Clear labeling and contextual information

### 7.2 Dashboard Features

**Interactivity:**

- Date range selector (entire period or custom)
- Weekend/weekday toggle filters
- Month-specific filtering
- Cross-filtering across all visualizations

**Key Performance Indicators:**

- High-level summary metrics at top
- Color-coded for quick assessment
- Contextual comparisons included

**Multi-dimensional Analysis:**

- Comparative analysis (grouped bars)
- Correlation exploration (scatter plots)
- Categorical breakdowns (segmented visualizations)

---

## 8. Project Value & Portfolio Impact

### 8.1 Demonstrated Skills

**Data Wrangling:**

- Multi-table integration
- Date/time manipulation
- Feature engineering
- Data quality assurance

**Statistical Analysis:**

- Hypothesis formulation and testing
- Appropriate test selection
- Result interpretation
- Statistical significance assessment

**Visualization & Communication:**

- Dashboard design principles
- Storytelling with data
- Interactive visual analytics
- Professional presentation

**Domain Knowledge:**

- Health metrics understanding
- Behavioral science application
- Actionable insight generation
- Real-world problem solving

### 9.2 Business Relevance

This project demonstrates capabilities directly applicable to:

- **Healthcare analytics:** Patient monitoring, population health
- **Product analytics:** User behavior, engagement metrics
- **Marketing analytics:** Campaign effectiveness, customer segmentation
- **Operations analytics:** Process optimization, efficiency tracking

---

## 10. Conclusion

This personal wellness analytics project successfully demonstrates a complete data analytics workflow, from raw sensor data to actionable insights. The analysis reveals clear behavioral patterns, significant lifestyle differences between weekdays and weekends, and opportunities for health optimization.

**Key Takeaways:**

1. **Data quality matters:** Thorough cleaning and validation enabled reliable analysis
2. **Context is crucial:** Domain knowledge enhanced interpretation beyond statistical results
3. **Visualization drives understanding:** Interactive dashboard makes complex patterns accessible
4. **Statistics inform decisions:** Hypothesis testing confirmed behavioral patterns weren't due to chance
5. **Analytics enable action:** Insights translated to specific, measurable recommendations

The project showcases technical proficiency while addressing a personally meaningful question: "What do my health data reveal about my lifestyle, and how can I optimize it?" This combination of technical rigor and practical relevance exemplifies the power of data analytics to drive real-world decision-making.

---

## Dashboard Navigation Guide

### Filter Usage:

1. **Date Range Slider:** Narrow analysis to specific time periods
2. **Weekend/Weekday Toggle:** Compare day-type specific patterns
3. **Month Filter:** Examine seasonal variations
4. **Interactive Selection:** Click any chart element to cross-filter entire dashboard

### Metric Definitions:

- **Average Daily Steps:** Mean step count across selected period
- **Average Sleep (Hrs):** Mean total sleep duration in hours
- **Average Calories Burned:** Mean daily caloric expenditure
- **Average Resting Heart Rate:** Mean RHR in beats per minute
- **Deep Sleep:** Sleep stage with delta wave brain activity (most restorative)
- **Shallow Sleep:** Light and REM sleep stages

---

**Project Author:** [Valeriia Lazar]
**Analysis Period:** January 2023 - August 2025
**Last Updated:** October 2025
**Tools Used:** Python, Pandas, Jupyter Notebook, Tableau Desktop
