# Map your market

Find who you actually compete with in search, and how much demand there is for what you sell. Skill: `seo-competitors`, `seo-keyword-selection`.

## Workflow: Find your search rivals

### Step 1: List the candidates

```text
For my site [site], find who I compete with in search.

1. Run list_competitors for rivals already saved.
2. Run research_site and read the competitors it returns. If no website review has run yet, this call starts one, which uses my daily research budget, so ask me first. If it answers queued, wait a minute and ask again.
3. Look at the search results for my three main keywords: [keyword 1], [keyword 2], [keyword 3]. If you cannot search, ask me to paste them.

Return one table: Site | Found by (saved, website review, search results) | Direct rival (sells the same) or search rival (guide, directory, marketplace) | Why it counts.
Sort by how many sources found it, then by name. Show up to 10 rows.

Then suggest the five to save, and ask me before you run add_competitor; each one uses a plan slot. Write "not reported" for any number the tools do not return.
```

### Step 2: Benchmark the saved rivals

```text
Run list_competitors for [site]. Benchmarking works only on saved rivals; if none are saved, run the previous step first.

Run competitor_traffic and keyword_gap for [site]. If either answers queued, wait a minute and ask again. If rank_compare has data, run it too.

Return one table: Site | Visits from search (estimate) | Shared keywords | Keywords only they rank for | Where they lead.
Include my site as the first row. Sort the rest by visits from search, highest first.

Give the reading date. Rival visits are estimates; say so.
```

## Workflow: Size the demand

### Step 1: Demand for the core topics

```text
For my site [site], which sells [what you sell] in [country]:

1. Run keyword_planner for each of these seeds: [seed 1], [seed 2], [seed 3]. Poll each one until its status is ready.
2. Keep keywords that match what I sell. Drop other brands and unrelated topics.

Return one table: Keyword | Volume | Difficulty | Intent (buy, compare, learn, local) | Seed.
Sort by volume, highest first. Show up to 30 rows.

Do not add any keyword. Write "not reported" for missing numbers.
```

### Step 2: Group into topics

```text
If the demand table from the previous step is in this conversation, use it. If not, run that step first.

Group the keywords into topics, one topic per page a buyer would expect. Then run site_pages for [site] and mark which topics already have a page.

Return one table: Topic | Main keyword | Total volume | Intent | Page on my site today (or "none").
Sort money topics first, then by total volume. Show up to 15 topics.

End with the three topics you would build or improve first, each with one sentence of reasoning.
```
