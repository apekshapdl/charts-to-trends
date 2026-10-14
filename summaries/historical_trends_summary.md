# Historical Billboard Trends Summary

This is the first pass of the historical Billboard analysis in `notebooks/04_historical_trends.ipynb`. It uses `data/cleaned/billboard_cleaned.csv` and does not modify the source data.

## Definitions

- A song identity is the exact `(song, artist)` pair in the cleaned dataset.
- A continuous chart run permits no more than seven days between weekly chart records. A subsequent run after a longer gap is counted as a return.
- “Chart weeks” are distinct chart dates on which a credit appears.
- Release dates are not available. Time from first observed chart date is only a proxy and cannot be interpreted as song age.

## Initial findings

- The dataset contains 355,758 chart rows for 32,688 distinct song/artist credits, spanning July 1958 through September 2026.
- This run rule identifies 36,403 continuous chart runs. 2,784 credits have more than one run, for 3,715 later runs after a gap.
- Descriptive period comparison (chart weeks represented per song/artist credit within each period):

| Period | Chart rows | Credits | Median chart weeks | One-week share |
|---|---:|---:|---:|---:|
| 1958–1992 | 179,658 | 18,306 | 9 | 3.1% |
| 1993–2008 | 83,500 | 5,403 | 16 | 4.1% |
| 2009–2019 | 57,300 | 5,001 | 8 | 27.1% |
| 2020–2026* | 35,300 | 4,418 | 2 | 38.8% |

`*` The data ends in September 2026, so this is a partial period. Period counts are descriptive: songs that cross boundaries are truncated, and chart methodology and market conditions may differ between eras.

## Interpretation and next work

The broad shift toward shorter chart presence in recent periods is visible in these summaries, but needs careful interpretation because the method counts chart dates within each era and the latest period is incomplete. Time since first observed chart appearance is not release age, so these results identify possible returns rather than prove that a song is old.

As a preliminary cross-check, 15 of the long-gap returns began during the TikTok dataset's date range; 7 had an exact normalized title-and-artist match in TikTok. This does not yet compare rank changes or establish that TikTok caused a chart return. The next project phase is the broader TikTok and Billboard comparison.
