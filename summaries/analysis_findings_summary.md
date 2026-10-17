## Analysis Findings

This summary brings together the results in `notebooks/data_analysis.ipynb` and `notebooks/historical_trends.ipynb`. They describe patterns in these datasets and do not establish that TikTok causes Billboard movement.

### TikTok and Billboard

Songs are matched on normalized title and artist. Title-only matches are not treated as confirmed. Of 10,509 TikTok song IDs, 1,230 have an exact match to Billboard history. The two datasets share 59 Billboard chart dates; 43 have full seven-day TikTok coverage. TikTok's best daily rank is used for each Thursday–Wednesday week.

Among 137 confirmed song-weeks present on both charts in complete weeks, the same-week Spearman rank correlation is **0.032**, indicating little association in this sample.

For songs already on Billboard in consecutive weeks, 49.6% improved the following week when they were in TikTok's Top 100, compared with 36.9% when they were not. The groups were unequal (115 versus 1,174 song-weeks), so this is a descriptive comparison. The rank-tier pattern was modest and not perfectly consistent.

TikTok was first observed before Billboard for 124 of 206 matched songs. The 15-day median gap applies to those cases only. These are first observations within the datasets, not confirmed trend starts or chart debuts.

### Older-song returns

The return analysis treats a song as older if its first observed Billboard appearance was at least ten years earlier, and as a return after at least 26 missing chart weeks. This is only a proxy for age because the data has no release dates. The rule identifies 15 returns during the TikTok data period; seven have exact TikTok matches, and six of those had TikTok Top 100 records in the prior 30 days.

- **“Bye Bye Bye”** returned at #45 on August 14, 2024, after 1,258 missing chart weeks. It had TikTok ranks on two dates shortly before the return.
- **“Ghostbusters”** returned at #28 on November 6, 2024, after 51 missing weeks. It also charted around Halloween in each of the previous three years.
- **“All I Want For Christmas Is You”** returned at #16 on November 27, 2024, after 46 missing weeks. It reached Billboard #1 in December and had returned in the same season in each of the prior three years.

The examples show different return patterns, including regular seasonal charting. They do not demonstrate that TikTok caused the returns.

### Limits to keep in mind

The TikTok data covers only May 2024 to July 2025 and includes Top 100 rankings, not all platform activity. Weekly bins are a practical alignment, not verified chart-tracking periods. Song title and artist differences can also lead to missed or uncertain matches. The samples are small, and some songs appear more than once.
