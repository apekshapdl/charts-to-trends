## Data Cleaning Summary

This note records the main cleaning decisions. The original CSV files remain unchanged. Cleaned files are saved locally in `data/cleaned/`.

### Billboard Hot 100
- Renamed columns to lowercase with underscores and converted `date` to a date type.
- Converted `rank`, `last_week`, `peak_position`, and `weeks_in_charts` to numeric columns. The `-` placeholders became missing values; no rows were removed.
- Kept all 355,758 rows. There are no exact duplicate rows. Missing values include 36,391 in `last_week`, 300 in `weeks_in_charts`, and 124,215 in `image_url`.

### TikTok Trending Music
- Column names were already lowercase with underscores. Converted `date` to a date type and `song_id` and `clip_id` to text because they are identifiers.
- Converted `rank_diff` to a nullable integer. Its 27,241 missing values were retained; all have the label `new_to_top100` in this dataset.
- Kept all 104,886 rows. There are no exact duplicate rows. Four rows share the same date, ranking window, and song ID; they occur in the 30-day window on June 23, 2024, and were retained for review.
- Saved a separate seven-day subset with 35,602 rows across 358 dates. It has 96 to 100 entries per date and rank values from 1 to 100.
- The dataset card describes rank movement as relative to the previous day and provides labels for the movement types. The numeric direction should not be inferred beyond the source definition.

### Cleaned files
- data/cleaned/billboard_cleaned.csv
- data/cleaned/tiktok_cleaned.csv
- data/cleaned/tiktok_7day_cleaned.csv

