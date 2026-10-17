# From Charts to Trends: How Has Song Popularity Changed Over Time?

**Status:** Analysis complete; dashboard planned.

## Project overview

This exploratory project examines Billboard Hot 100 chart history and the overlap between Billboard chart performance and TikTok music rankings. It asks whether songs with stronger TikTok ranks also improve on Billboard, what timing patterns appear in the observed data, and whether older tracks return to the chart. The analysis is descriptive; it does not establish that TikTok causes Billboard success.

## Research questions

1. Are better TikTok ranks associated with Billboard rank improvement?
2. Do TikTok observations precede Billboard movements, and what timing gaps appear in the available data?
3. Do older songs return to the Billboard Hot 100 after TikTok activity?
4. What do selected song timelines show about these patterns?

## Data

- **Billboard Hot 100:** [Billboard Hot 100 & more on Kaggle](https://www.kaggle.com/dsv/8544442), using `hot100.csv`. The local file covers 1958-07-30 through 2026-09-30.
- **TikTok Trending Music:** [lingbow/tiktok-trending-hashtags-music on Hugging Face](https://huggingface.co/datasets/lingbow/tiktok-trending-hashtags-music), using `trending_music.csv`. The local file covers 2024-05-23 through 2025-07-09 and contains US rankings for 7-, 30-, and 120-day windows. The primary comparison uses the seven-day window.

The notebooks expect the raw files at:

```text
data/raw/hot100.csv
data/raw/trending_music.csv
```

The cleaning notebook creates:

```text
data/cleaned/billboard_cleaned.csv
data/cleaned/tiktok_cleaned.csv
data/cleaned/tiktok_7day_cleaned.csv
```

If these files are not present in your copy, obtain the source datasets from the links above and place the CSVs in `data/raw/` before running the notebooks. Both dataset pages list a **CC BY-NC 4.0** license; credit the sources and check the license terms before redistributing data or derived materials.

## Methods and definitions

- Song matching uses normalized title-and-artist text. A title-only match is kept as unconfirmed because different songs can share a title.
- TikTok daily records are grouped into Thursday–Wednesday calendar weeks ending on the Billboard chart date. Same-week comparisons use only the 43 weeks with all seven TikTok dates observed.
- The weekly TikTok rank is the song's best (lowest) rank that week. Billboard rank changes are positive when a song moves closer to number 1.
- A historical chart run allows no more than seven days between chart records. The older-song return analysis uses a stricter rule: at least 26 missing chart weeks and at least ten years since the first observed Billboard appearance. The dataset has no song release dates, so this ten-year measure is only a proxy for age.

## Current findings

- Of 10,509 TikTok song IDs, 1,230 have an exact normalized title-and-artist match to Billboard history. Another 1,372 match by title only and remain unconfirmed.
- In 137 matched song-weeks appearing on both charts, the same-week Spearman rank correlation is 0.032, indicating little rank association in this sample.
- In the one-week movement comparison, Billboard improvement occurred in 49.6% of matched song-weeks with TikTok Top 100 presence in the starting week, compared with 36.9% without it. The groups contain 115 and 1,174 song-weeks, respectively; this is a descriptive comparison.
- For the rank-tier comparison, 115 song-weeks across 74 songs were available. The Spearman correlation between TikTok rank and next-week Billboard rank change is -0.131. Improvement shares range from 33.3% for TikTok ranks 51–100 to 52.9% and 54.8% for ranks 1–10 and 11–25; the pattern is modest and not perfectly stepwise.
- First observed dates put TikTok before Billboard for 124 of 206 matched songs. The 15-day median gap applies only to those TikTok-first observations; these dates are not confirmed trend starts or chart debuts.
- The stricter older-song rule identifies 15 return entries during the TikTok data period. Seven have exact TikTok title-and-artist matches, and six of those have TikTok Top 100 observations in the 30 days before the return. Several are recurring seasonal chart appearances. Case studies include “Bye Bye Bye,” “Ghostbusters,” and “All I Want For Christmas Is You.”
- Historical median chart weeks per song/artist credit within each period are 9 (1958–1992), 16 (1993–2008), 8 (2009–2019), and 2 (2020–2026). These are within-period counts; songs crossing period boundaries are truncated, and the last period is partial through September 2026.

These results describe the available charts and observation window. They do not show that TikTok caused a Billboard rank change or return. The first-observed-date comparison is especially limited by the datasets' time coverage, and the older-song measure is not based on release dates.

## Notebooks and run order

Install the notebook dependencies:

```bash
python -m pip install jupyter pandas matplotlib
```

The notebooks use paths relative to `notebooks/`. From the project root, start Jupyter there:

```bash
cd notebooks
jupyter notebook
```

Run the notebooks in this order:

1. `data_exploration.ipynb` — inspect the source datasets.
2. `data_cleaning.ipynb` — clean the CSVs and create files under `data/cleaned/`.
3. `data_analysis.ipynb` — match songs, align dates, compare ranks and movement, and inspect next-week appearances.
4. `historical_trends.ipynb` — compare historical chart persistence, identify return entries, and review case-study timelines.
