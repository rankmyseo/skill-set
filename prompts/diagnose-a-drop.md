# Diagnose a traffic drop

Find where clicks or ranks fell before guessing why. Skill: `seo-maintenance-loop`, section "When traffic or ranks drop".

## Workflow: Find where it fell

### Step 1: Confirm and locate

```text
My site [site] lost traffic around [date or "recently"].

1. Run search_console with days: 28. Read the totals against the previous window, and the daily series to see the day it started. Use complete days only.
2. For pages, use clicksChange if pagesComparable is true; otherwise run page_updates and read each row's search numbers. For queries, run search_console again with days: 56; a query's previous 28 days is its 56-day number minus its 28-day number.
3. If Analytics is connected, run analytics_pages for the same windows. If GA4 visits fell but Search Console clicks did not, say the tracking may be the cause and stop here.

Country, device, and search type splits are not in these answers. If I have Search Console open, tell me which compare view to check.

Return one table: Where (page or query) | Clicks before | Clicks now | Clicks lost.
Sort by clicks lost, largest first, not by percentage. Show up to 15 rows.

Then say in one sentence whether the drop is one page, one section, or the whole site. Name both windows with their dates.
```

### Step 2: Tracked ranks

```text
If the drop table from the previous step is in this conversation, use it. If not, run that step first.

Run list_keywords for [site], then keyword_history on each tracked keyword that fell.

Return one table: Keyword | Position before | Position now | Page | Date it started to fall.
Sort by position lost. Show up to 15 rows.

Search Console's average position is not the tracked rank; do not mix them.
```

## Workflow: Find why

### Step 1: Check the causes in order

```text
If the drop and rank tables from the workflow above are in this conversation, use them. If not, run those steps first.

Check each cause and say what you found:
1. My changes: ask me for redesigns, moves, template or plugin changes in the window.
2. Google: check the Google Search Status Dashboard (status.search.google.com) for a ranking update in the window. If one is still rolling out, say to wait a full week after it finishes.
3. What Google sees: run site_issues and issue_pages for the pages that fell. Check status code, noindex, canonical, and robots.txt.
4. Rivals: run rank_compare for the keywords that fell.
5. The market: run competitor_traffic and read each site's months series for the months of the drop. If saved rivals fell too, the drop is likely seasonal or market-wide.
6. Intent: look at what ranks now for the keywords that fell, or ask me to. Is it a different kind of page than mine?

Return one table: Cause | Checked (yes, no, could not) | Evidence | Likely (yes, no, maybe).
```

### Step 2: What to do

```text
If the causes table from the previous step is in this conversation, use it. If not, run that step first.

Give at most three actions, each with the page it affects, the evidence, and the date to check again.

Rules: a small drop on a page still in the top four needs no big change. Do not delete pages as a first fix. After a core update, recovery can take months; say so. Do not promise a recovery.
```
