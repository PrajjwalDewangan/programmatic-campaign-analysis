# Digital Ad Campaign Analysis
## Overview
This project analyzes a digital advertising campaign across Canadian provinces covering CTV, Desktop, and Mobile devices.
The objective of the analysis is to evaluate key campaign performance metrics such as:
- CTR (Click Through Rate)
- VCR (View Completion Rate)

The insights generated from this analysis help identify patterns and opportunities to improve campaign performance and optimization strategies.

# Dataset
A synthetic dataset was generated to simulate real-world advertising log data.
- Rows: ~200,000
- Unique Users: ~40,000

## Data Generation
- A Python script was used to generate the dataset.
- A prompt was created using Gemini and then used in ChatGPT to generate the dataset generation script.
- The prompt instructed the model to generate log-style advertising data similar to real campaign logs.

### Data Simulation Assumptions
The dataset simulates realistic campaign behavior:

Devices included:

- CTV
- Desktop
- Mobile

Higher impression volumes during:

- Weekends
- Lunch hours
- Prime time

Demographic and geographic attributes were included to allow deeper analysis.

# Dataset Columns
- `log_id`
- `user_id`
- `session_id`
- `timestamp`
- `day_of_week`
- `campaign_id`
- `campaign_objective`
- `creative_id`
- `creative_type`
- `device_type`
- `fsa`
- `age_group`
- `impression_count`
- `is_click`
- `is_conversion`
- `vcr_percent`
- `bid_price_usd`

# Data Processing Architecture

The project follows a Medallion Architecture approach for structured data processing.

### 🥉 Bronze Layer
Raw dataset ingestion.

### 🥈 Silver Layer
Data cleaning and validation:

- Null value checks
- Duplicate removal
- Exploration of categorical variables such as:
  - `campaign_objective`
  - `creative_type`
  - `device_type`
  - `age_group`

### 🥇 Gold Layer

The cleaned dataset is split by **device type** for deeper analysis:

- `df_golden_ctv`
- `df_golden_desktop`
- `df_golden_mobile`

# Key Performance Metrics

## CTV Campaigns

The primary KPI for CTV campaigns is VCR (View Completion Rate).
VCR = Video Completions / Total Impressions

A video completion is defined as:
vcr_percent > 95%


This represents users who watched almost the entire advertisement.

## Desktop & Mobile Campaigns

The primary KPI for Desktop and Mobile campaigns is CTR (Click Through Rate).
CTR = Total Clicks / Total Impressions


CTR measures how effectively the advertisement drives **user engagement through clicks**.


# Levels of Analysis

Campaign performance was analyzed across multiple dimensions:

1. Time of Day
2. Day of Week
3. Age Group
4. Creative Type
5. Province
6. City

These analyses help uncover:

- Peak engagement periods
- High-performing demographics
- Best performing creatives
- Geographic performance differences


# Insights Explored

## CTV
### Time of Day
-	Observation: Impressions and VCR peak during 7–10 PM; 12–1 PM has good impressions but lower VCR.
-	Insight: Evening audiences are more engaged with CTV ads.
-	Action: Prioritize delivery during 7–10 PM.
### Day of Week
-	Observation: Weekends (Sat–Sun) show higher VCR; Friday has the highest impressions.
-	Insight: Engagement is stronger on weekends than weekdays.
-	Action: Increase delivery on weekends.
### Age
-	Observation: 25–34 has the highest VCR; 18–24 performs the worst.
-	Insight: Adults respond better to CTV ads.
-	Action: Focus targeting on 25–34 and reduce 18–24.
### Ad Duration
-	Observation: 30s and 15s ads show similar performance.
-	Insight: Ad length has minimal impact on VCR.
-	Action: Either format can be used interchangeably.

## Desktop
### Time of Day
-	Observation: Highest CTR at 8 PM on weekends; impressions peak 7–10 PM (Wed–Fri) but CTR is lower.
-	Insight: Evening weekday traffic is high but less engaged.
-	Action: Increase delivery during weekend evenings.
### Age
-	Observation: 45–54 has the highest impressions and CTR.
-	Insight: Middle-aged users respond best on desktop.
-	Action: Increase targeting for 45–54.

## Mobile
### Time of Day
-	Observation: Impressions peak 7–10 PM, but CTR is higher at 12–1 PM.
-	Insight: Users are more likely to click ads during lunchtime.
-	Action: Shift delivery toward 12–1 PM.
### Day of Week
-	Observation: Weekends and Tuesday show the best CTR; Wed–Fri have higher impressions.
-	Insight: Higher impressions on midweek days are not translating into engagement.
-	Action: Shift impressions from Wed–Fri to Sat, Sun, and Tue.
### Age
-	Observation: Adults and middle-aged groups lead in impressions and CTR.
-	Insight: Current targeting across all age groups reduces efficiency.
-	Action: Focus targeting on adult and middle-aged segments.

# Geographical Analysis
## CTV
### City
-	Observation: Calgary has the highest VCR, though differences across cities are minimal.
-	Insight: Performance is fairly consistent across cities.
-	Action: No major location shift required.
### Province
-	Observation: Alberta has the highest VCR (61.04%), with minimal variation across provinces.
-	Insight: Provincial performance differences are small.
-	Action: Maintain current distribution.
  
## Desktop
### City
-	Observation: Toronto has the highest CTR (0.82) with similar impressions across cities.
-	Insight: Toronto generates better engagement.
-	Action: Increase impressions in Toronto.
### Province
-	Observation: Ontario has the highest CTR (0.78), followed by BC (0.77), though BC has significantly fewer impressions (~15k difference).
-	Insight: BC performs similarly but is under-delivered.
-	Action: Increase impressions in BC.

## Mobile
### City
-	Observation: Calgary and Toronto show the highest CTR.
-	Insight: These cities generate stronger engagement.
-	Action: Increase impressions in Calgary and Toronto.
### Province
-	Observation: Alberta has the highest CTR (1.95).
-	Insight: Alberta users respond best to mobile ads.
- Action: Increase delivery in Alberta.


# Tech Stack

- Python
- PySpark
- SQL
- Databricks
- Data Visualization

# Dashboard

View the interactive Tableau Dashboard here: [Programmatic Campaign Analysis](https://public.tableau.com/app/profile/prajjwal.dewangan/viz/AdCampaignAnalysis_17747953153400/DesktopDashboard
)
