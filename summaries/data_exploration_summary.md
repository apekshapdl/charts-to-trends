## Data Exploration Summary

### 1. Datasets

#### Billboard Hot 100 and more (hot100.csv)
- Source: Kaggle billboard dataset
- 355758 rows and 8 columns
- Date range: July 1958 - September 2026
- Weekly rankings from 1 to 100
- No exact duplicate rows

#### TikTok Trending Music (trending_music.csv)
- Source: Hugging Face, `lingbow/tiktok-trending-hashtags-music`
- 104886 rows and 14 columns
- Date range: May 23, 2024 - July 9, 2025
- US-only data with rankings from 1 to 100
- Ranking windows: 7-days, 30-days, 120-days
- No exact duplicate rows

### 2. Key Findings
- Billboard provides historical chart data, while TikTok covers a shorter period.
- The overlapping period is May 23, 2024–July 9, 2025, containing 59 Billboard chart dates and 358 TikTok ranking dates for the seven-day window.
- The TikTok seven-day subset contains 35,602 rows, 10,509 unique song IDs, and approximately 100 ranked entries per day.
- rank_diff has 27,241 missing values, matching the number of new_to_top100 records
- 4 rows are involved in repeated records for the same date, ranking window, and song ID. These occur in 30-day window and require further investigation

### 3. Data Cleaning Decisions
- Preserve the original datasets.
- Standardize column names and data types.
- Convert `-` values in Billboard numeric columns to missing values without deleting rows.
- Investigate repeated records and missing values.
- Use the TikTok seven-day window for the primary comparison.
- Normalize song titles and artist names before matching the datasets.

### 4. Project Status
Exploration, cleaning, matching and integration, and the first historical Billboard analysis are complete. The current phase is the TikTok and Billboard comparison. Dashboard work follows the analysis.

##### Limitation:
The analysis can identify relationships between TikTok trends and Billboard performance but cannot prove that TikTok caused changes in chart rankings.
