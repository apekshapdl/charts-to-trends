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

### Limitations and current status

Exact text matching is conservative and can miss songs when artist credits differ. Title-only matches are not treated as confirmed because unrelated songs can share a title. The TikTok dataset covers a much shorter period than Billboard and has incomplete weekly coverage.

The first historical Billboard analysis is documented in `notebooks/04_historical_trends.ipynb` and `summaries/historical_trends_summary.md`. The current project phase is the deeper TikTok and Billboard comparison; the same-week overlap count above is preliminary and does not measure whether one chart's rank changes alongside the other.
