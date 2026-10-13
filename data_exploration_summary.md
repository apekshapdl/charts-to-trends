## Data exploration Summary

### 1. Datasets

#### Billboard Hot 100 and more (hot100.csv)
- Source: Kaggle billboard dataset
- 355758 rows and 8 columns
- Date range: July 1958 - September 2026
- Weekly rankings from 1 to 100
- No exact duplicate rows

#### Tiktok Trending Music (trending_music.csv)
- Source: Hugging Face, lingbow/tiktok-trending-hashtags-music
- 104886 rows and 14 columns
- Date range: May 23, 2024 - July 9, 2025
- US-only data with rankings from 1 to 100
- Ranking windows: 7-days, 30-days, 120-days
- No exact duplicate rows

### 2. Key Findings
- Billboard provides historical chart data, while Tiktok covers a shorter period. 
- The overlapping period is May 23, 2024 - July 9, 2025, containing 59 Billboard chart dates and 358 Tiktok ranking dates for the 7-day window
- The tiktok 7-day subset contains 35,602 rows, 10,509 unique song IDs and approximately 100 ranked entries per day
- rank_diff has 27,241 missing values, matching the number of new_to_top100 records
- 4 rows are involved in repeated records for the same date, ranking window, and song ID. These occur in 30-day window and require further investigation

### 3. Data Cleaning Decisions
- Preserve original datasets
- standardize column names and data types
- conver - values in billboard numeric columns to missing values without deleting rows
- investigate repeated records and missing values
- use the tiktok 7-day winfow for the primary comparison
- normalize song titles and artist names before matching the datasets

### 4. Next Steps
Clean both datasets, match songs between Tiktok and Billboard, analyze historical chart trends and potential song comebacks, and build the final power BI dashboard. 

##### Limitation: 
The analysis can identify relationships between Tiktok trends and Billboard performance but cannot prove that Tiktok caused changes in chart rankings. 
