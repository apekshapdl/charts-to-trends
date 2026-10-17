# From Charts to Trends: How Has Song Popularity Changed Over Time?

## About the project

Songs can become popular again years after their release. A TikTok trend may coincide with a song returning to the Billboard Hot 100, but the timing alone does not tell us why it happened. This project explores the relationship between TikTok music rankings and Billboard chart performance, including cases where older songs reappear on the chart.

The work is exploratory and descriptive. It looks for patterns in the available data; it does not claim that TikTok causes a song to chart or rise in rank.

## Questions

- Are better TikTok rankings associated with Billboard rank improvement?
- Do TikTok records appear before Billboard movements, and what timing gaps are visible?
- Do older songs return to the Hot 100 during periods of TikTok popularity?
- What can selected song timelines show about these patterns?

## Data

The project combines two public datasets:

- **Billboard Hot 100:** [Billboard Hot 100 & more on Kaggle](https://www.kaggle.com/dsv/8544442). The local file, `hot100.csv`, contains weekly chart history from July 1958 to September 2026.
- **TikTok Trending Music:** [lingbow/tiktok-trending-hashtags-music on Hugging Face](https://huggingface.co/datasets/lingbow/tiktok-trending-hashtags-music). The local file, `trending_music.csv`, covers May 2024 to July 2025 and includes US rankings for 7-, 30-, and 120-day windows. The main chart comparison uses the seven-day data.

Put the source files here:

```text
data/raw/hot100.csv
data/raw/trending_music.csv
```

Both source pages list a CC BY-NC 4.0 license. Please check the dataset terms before redistributing the data.

## Tools and methods

The project uses **Python, Jupyter Notebook, pandas, and Matplotlib**. Pandas is used to inspect and clean the data, normalize song and artist text, match records, and align dates. Matplotlib is used for the charts.

Matches require normalized song title and artist text; title-only matches are kept unconfirmed. TikTok dates are grouped into Thursday–Wednesday weeks to line up with Billboard chart dates. The primary weekly comparisons use only weeks with complete TikTok coverage. For older-song returns, first observed Billboard appearance is used as an age proxy because the data does not include release dates.

The analysis includes same-week rank comparisons, next-week Billboard movement, timing of first observed appearances, historical chart runs, older-song returns, and three case studies: “Bye Bye Bye,” “Ghostbusters,” and “All I Want For Christmas Is You.”

## Findings so far

- Same-week TikTok and Billboard ranks showed little association in the matched sample (Spearman correlation **0.032**, based on 137 song-weeks).
- Billboard improvement was more common the following week among songs in TikTok's Top 100 than among songs without a matched TikTok record. The groups were uneven, so this is a descriptive comparison.
- TikTok was observed first for 124 of 206 matched songs. These dates mark the first records in the datasets, not verified trend starts or chart debuts.
- The older-song return analysis found 15 return entries during the TikTok data period under its selected definition. The case studies include both seasonal returns and a less regular return.

These results are limited by the short TikTok observation period, incomplete weekly coverage, and uncertainty in matching song credits across sources. Some songs contribute more than one observation.

## Run the notebooks

Install the main dependencies:

```bash
python -m pip install jupyter pandas matplotlib
```

Start Jupyter from the `notebooks/` directory so the relative data paths work, then run the notebooks in order:

1. `data_exploration.ipynb` — inspect the source data.
2. `data_cleaning.ipynb` — prepare the analysis files in `data/cleaned/`.
3. `data_analysis.ipynb` — match the datasets and compare ranks, timing, and movement.
4. `historical_trends.ipynb` — examine chart runs, returns, and case studies.

The dashboard is planned as a next project step.
