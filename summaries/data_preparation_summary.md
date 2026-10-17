## Data Exploration and Cleaning Summary

This note combines the exploration and cleaning work for the Billboard Hot 100 and TikTok Trending Music datasets. The detailed steps are in `notebooks/data_exploration.ipynb` and `notebooks/data_cleaning.ipynb`.

### Data sources and coverage

- **Billboard Hot 100:** Kaggle's [Billboard Hot 100 & more](https://www.kaggle.com/dsv/8544442), source file `hot100.csv`. The local file contains 355,758 rows and 8 columns, covering 1958-07-30 through 2026-09-30.
- **TikTok Trending Music:** Hugging Face's [lingbow/tiktok-trending-hashtags-music](https://huggingface.co/datasets/lingbow/tiktok-trending-hashtags-music), source file `trending_music.csv`. The local file contains 104,886 rows and 14 columns, covering 2024-05-23 through 2025-07-09. It includes US rankings for 7-, 30-, and 120-day windows.

Both dataset pages list a **CC BY-NC 4.0** license. Credit the sources and check their terms before redistributing the data or derived materials.

### Exploration and data quality

#### Billboard

- The file has 3,558 distinct chart dates, with 97–100 records per date. Rank values range from 1 to 100.
- There are no exact duplicate rows. There are 13 repeated date/song/artist keys (26 rows), all for “Unchained Melody” by The Righteous Brothers in 1990, where the same credited song appears at two ranks on a chart date. The analysis keeps the best rank when aggregating by chart date.
- `Last Week` has 36,391 `-` placeholders; `Weeks in Charts` has 300. The latter occur on the final three chart dates in the file. `Image URL` is missing for 124,215 rows.

#### TikTok

- The seven-day subset contains 35,602 rows across 358 dates. Each date has 96–100 ranked entries, with ranks from 1 to 100; all records in this subset are US data.
- `rank_diff` has 27,241 missing values, and all are labeled `new_to_top100`. The missing values are retained. Interpret the numeric direction of `rank_diff` only according to the dataset documentation.
- There are no exact duplicate rows. Four rows (two repeated keys) share the same date, window, and song ID in the 30-day window on 2024-06-23. They are retained for review; they are outside the seven-day subset used for the main comparison.

### Cleaning decisions

- Original source CSVs are left unchanged. Column names, dates, and numeric fields are standardized in the cleaned Billboard file.
- Billboard `-` placeholders in numeric fields are converted to missing values; rows are retained.
- TikTok dates are parsed as dates, `song_id` and `clip_id` are treated as text identifiers, and `rank_diff` is stored as a nullable integer. Missing values and repeated keys are retained rather than silently removed.
- The seven-day TikTok data is saved as a separate subset for the primary comparison.

### Files and notebook order

The notebooks expect source files at `data/raw/hot100.csv` and `data/raw/trending_music.csv`. The cleaning notebook creates `data/cleaned/billboard_cleaned.csv`, `data/cleaned/tiktok_cleaned.csv`, and `data/cleaned/tiktok_7day_cleaned.csv`.

Run `data_exploration.ipynb` and then `data_cleaning.ipynb` from the `notebooks/` directory before running the analysis notebooks. The notebook paths are relative to that working directory.
