## Data Exploration and Cleaning

This summary covers the two source datasets and the preparation steps in `notebooks/data_exploration.ipynb` and `notebooks/data_cleaning.ipynb`.

### Sources

- **Billboard Hot 100:** Kaggle's [Billboard Hot 100 & more](https://www.kaggle.com/dsv/8544442), using `hot100.csv`. The local copy has 355,758 rows, from July 1958 to September 2026.
- **TikTok Trending Music:** [lingbow/tiktok-trending-hashtags-music](https://huggingface.co/datasets/lingbow/tiktok-trending-hashtags-music), using `trending_music.csv`. The local copy has 104,886 rows, from May 2024 to July 2025, with 7-, 30-, and 120-day US rankings.

Both dataset pages list a CC BY-NC 4.0 license.

### What needed attention

Billboard has no exact duplicate rows, though 13 date/title/artist keys repeat. These are entries for “Unchained Melody” at two ranks in 1990; the analysis keeps the best rank when aggregating. Placeholder dashes in numeric columns are converted to missing values. Missing image URLs are not used in the analysis.

The TikTok seven-day subset has 35,602 rows across 358 dates. Its missing `rank_diff` values are labeled `new_to_top100`, so they are retained. Four repeated-key rows occur in the 30-day data, outside the main comparison subset.

### Prepared files

The original CSVs remain unchanged. The cleaning notebook creates:

- `data/cleaned/billboard_cleaned.csv`
- `data/cleaned/tiktok_cleaned.csv`
- `data/cleaned/tiktok_7day_cleaned.csv`

Run exploration, then cleaning, from the `notebooks/` directory. The notebooks expect the source files in `data/raw/`.
