## Data Analysis Summary

This summary records the first matching and integration work for the TikTok and Billboard datasets. The analysis uses the cleaned data and keeps the raw files unchanged.

### Song matching

- Created comparison versions of song titles and artist names by standardizing Unicode, ignoring case, and removing spaces and punctuation. Original names were kept.
- Checked TikTok metadata and found 44 song IDs with more than one normalized title/artist pair.
- Used exact normalized title and artist matches as the confirmed matching rule. A title match without an exact artist match remains a review candidate.
- Of 10,509 TikTok song IDs, 1,230 matched both title and artist (11.70%). Another 1,372 had a title match but no exact artist match (13.06%). In total, 2,602 IDs had a Billboard title match.
- The confirmed matches linked to one Billboard song per TikTok song ID in this check. Different artist credits may still cause legitimate matches to be missed.

### Weekly alignment

- Billboard dates in the dataset fall on Wednesday. TikTok daily records were grouped into Thursday–Wednesday calendar weeks ending on the Billboard date. This is a practical date-binning choice; it does not confirm that both charts use the same underlying tracking period.
- There are 59 Billboard chart dates in the shared data range. TikTok has complete seven-day coverage for 43 weeks; 16 weeks are partial or missing. Weeks without full TikTok coverage were excluded from the same-week comparison.
- The weekly summary keeps each TikTok song ID’s best rank that week and the number of days it appeared in TikTok’s Top 100.
- In complete weeks, the integrated table contains 1,859 matched TikTok song-weeks. Of these, 152 also appear on Billboard in the same week. This is an exploratory overlap count, not evidence that TikTok caused a chart change.

### TikTok and Billboard comparison

- For the 152 matched song-weeks that appeared on both charts in the same week, the Spearman rank correlation was 0.038, indicating little relationship between the two sets of ranks in this sample. The scatterplot shows the individual song-week comparisons.
- Compared first observed dates for 241 matched songs found on both charts during the shared dataset period. TikTok was observed first for 144 songs (59.8%), on the same date for 5 (2.1%), and Billboard was observed first for 92 (38.2%). For the 144 TikTok-first songs, the median gap was 12 days; the middle half of gaps was 4 to 37 days.
- These are first dates observed within the available dataset window, not confirmed release dates or Billboard entry dates. The timing comparison cannot establish that TikTok caused a Billboard appearance.
- For songs also found on TikTok, compared consecutive Billboard chart weeks only. Across 66 matched song-weeks, 31 (47.0%) improved, 6 (9.1%) stayed at the same rank, and 29 (43.9%) worsened. Median Billboard movement was +8 places for the improved group and -7 for the worsened group; positive movement means closer to number 1. A bar chart shows the counts.
- Song-weeks are the unit of analysis, so one song may contribute more than once. These results describe observed patterns and do not show causation.

### Limitations and current status

Exact text matching is conservative and can miss songs when artist credits differ. Title-only matches are not treated as confirmed because unrelated songs can share a title. The TikTok dataset covers a much shorter period than Billboard and has incomplete weekly coverage. The weekly alignment uses calendar date bins and does not establish identical tracking periods.

The historical Billboard analysis is documented in `notebooks/historical_trends.ipynb` and `summaries/historical_trends_summary.md`. The Day 5 TikTok and Billboard comparison is complete and documented in `notebooks/data_analysis.ipynb`. The next planned phase is Day 6: define and identify older-song comebacks, then examine matched TikTok records where available.
