# Analysis Findings Summary

This note consolidates the current findings from `notebooks/data_analysis.ipynb` and `notebooks/historical_trends.ipynb`. Results describe the available datasets; they do not establish that TikTok caused Billboard rank changes or returns.

## Matching and date alignment

- Song names are normalized by applying Unicode normalization, case folding, and removing spaces and punctuation. A confirmed match requires both normalized title and artist to match. A title-only match remains unconfirmed.
- Of 10,509 TikTok song IDs, 1,230 have an exact normalized title-and-artist match to Billboard history. Another 1,372 match by title only. Forty-four TikTok IDs have multiple normalized metadata pairs and were reviewed as variants.
- TikTok daily records are grouped into Thursday–Wednesday calendar weeks ending on the Billboard Wednesday chart date. This is a practical calendar alignment, not confirmation that the charts use the same tracking period.
- The datasets share 59 Billboard chart dates. TikTok has full seven-day coverage for 43 weeks; 16 weeks are partial or missing. Same-week comparisons use the complete weeks only.
- For each matched song and week, the TikTok measure is its best (lowest) daily rank. A song may appear in multiple song-weeks.

## TikTok and Billboard results

### Same-week ranks

Among 1,802 confirmed matched TikTok song-weeks in fully observed weeks, 137 also appear on Billboard that week. Across those 137 song-weeks, the Spearman rank correlation is **0.032**, indicating little same-week rank association in this sample.

### First observed dates

Among 206 matched song/artist credits observed on both charts in the shared period:

- TikTok was observed first for 124 (60.2%); Billboard was observed first for 77 (37.4%); 5 (2.4%) were first observed on the same date.
- For the 124 TikTok-first cases, the median gap was 15 days; the middle half ranged from 4 to 41.5 days.

These are first dates observed inside the available data window, not verified trend starts or Billboard debuts. They do not establish a typical lead time.

### Next-week Billboard movement

For matched songs already on Billboard in consecutive weeks, the share improving the following week was 49.6% when the song appeared in TikTok's Top 100 in the starting week (115 song-weeks), compared with 36.9% when no matched TikTok record was present that week (1,174 song-weeks). The corresponding unchanged/worsened shares were 8.7%/41.7% and 14.2%/48.9%. Median rank change was zero in both groups. These unequal groups support a descriptive comparison, not a causal or predictive conclusion.

Among TikTok-present song-weeks, the rank-tier comparison included 115 observations across 74 songs:

| Best TikTok rank | Song-weeks | Distinct songs | Billboard improved | Stayed same | Worsened | Median Billboard rank change |
|---|---:|---:|---:|---:|---:|---:|
| 1–10 | 51 | 36 | 52.9% | 7.8% | 39.2% | +1 |
| 11–25 | 31 | 24 | 54.8% | 9.7% | 35.5% | +2 |
| 26–50 | 15 | 14 | 46.7% | 6.7% | 46.7% | 0 |
| 51–100 | 18 | 16 | 33.3% | 11.1% | 55.6% | −1.5 |

The Spearman correlation between TikTok rank and next-week Billboard rank change is **−0.131**. Better TikTok ranks show a modest, imperfect pattern with next-week movement. Some songs contribute more than one observation, and the sample contains only songs already on Billboard in consecutive weeks.

A separate check found 31 next-week Billboard appearances among 1,665 matched TikTok song-weeks absent from Billboard in the starting week (1.9%). These are next-week appearances, not necessarily first-time debuts or returns.

## Historical Billboard context

- The dataset contains 355,758 chart rows for 32,688 distinct song/artist credits. With a chart run defined as consecutive weekly records allowing no more than seven days between dates, 2,784 credits have multiple runs, producing 3,715 later runs.
- Median chart weeks per credit within the four periods were 9 (1958–1992), 16 (1993–2008), 8 (2009–2019), and 2 (2020–2026). Period-boundary crossings truncate counts, and 2020–2026 is incomplete through September 2026. These values describe chart weeks within each period, not full song lifespans.
- Return counts depend on the chosen threshold. The general chart-run analysis finds 196 later runs at least ten years after first observed Billboard appearance. The stricter older-song analysis requires at least 26 missing chart weeks plus ten years since first observed appearance; it finds 194 return entries across 95 credits.

## Older-song returns and case studies

The stricter rule identifies 15 return entries during the TikTok dataset's date range. Seven have exact normalized title-and-artist TikTok matches; six of those have TikTok Top 100 records in the 30 days up to and including the Billboard return date. The dataset has no release dates, so the ten-year condition is only a proxy for age.

- **“Bye Bye Bye”** returned at Billboard rank 45 on 2024-08-14 after 1,258 missing chart weeks. TikTok ranked it 30 on two dates (2024-07-27 and 2024-07-28). It appeared on Billboard for one week in the following eight weeks; it did not chart in the same seasonal window in the three prior years.
- **“Ghostbusters”** returned at rank 28 on 2024-11-06 after 51 missing chart weeks. TikTok ranked it 63 once, on 2024-10-27. It also charted near Halloween in each of the three prior years, making this a recurring seasonal return rather than a novel comeback.
- **“All I Want For Christmas Is You”** returned at rank 16 on 2024-11-27 after 46 missing chart weeks. TikTok ranked it as high as 4 on nine dates in the prior 30 days. Billboard rank improved to number 1 by 2024-12-11, but the song also charted in the same season in each of the three prior years.

These examples illustrate timing and seasonal recurrence. They do not show that TikTok caused a Billboard return.

## Interpretation and limitations

- The rank associations are small and based on a limited number of matched song-weeks; repeated observations from the same songs are not independent.
- TikTok ranks represent Top 100 positions in one dataset and time window, not total platform popularity or all TikTok use.
- Weekly date bins are not verified chart-tracking periods. The TikTok data begins in May 2024 and ends in July 2025, so first-observed dates are left- and right-censored.
- Billboard artist/title text may differ across credits or versions. Conservative exact matching can miss valid matches, while title-only matches can be false positives.
- Billboard first appearance is not song release date. Seasonal re-entries and other events can explain observed chart returns; no causal attribution is supported.
