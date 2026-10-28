# Refresh and clean up pages

Fix pages that are losing clicks, and decide what to do with pages that earn nothing. Skill: `seo-content-refresh`.

## Workflow: Refresh slipping pages

### Step 1: Find them

```text
For my site [site]:
1. Run page_updates. Keep rows marked refresh, rewrite, merge, and split, rows with a may_compete reason, and rows whose search numbers (clicks against prevClicks) show clicks falling.
2. Run search_console with days: 28. If pagesComparable is true, use each page's clicksChange; if not, rely on the page_updates search numbers.

Return one table: Page | Main keyword | Clicks before | Clicks now | Clicks lost | Signal | Last changed (from my change log, if you have it).
Sort by clicks lost, largest first, not by percentage. Show up to 15 rows.

Name both windows. Write "not reported" for missing numbers.
```

### Step 2: Find the cause

```text
If the slipping pages table from the previous step is in this conversation, use it. If not, run that step first.

For each of the top five pages, check in this order and stop at the first that holds:
1. My change log shows an edit near the date.
2. site_issues or issue_pages shows an error, a noindex, or a wrong canonical on the page.
3. page_updates marks it merge or split, or site_pages shows another page with the same main keyword.
4. The page has out-of-date prices, dates, or steps. Read it.
5. rank_compare shows a rival passing it.
6. Searches for the keyword fell for everyone.

Return one table: Page | Cause | Evidence | Fix | Effort.
If no cause holds, write "unknown, check again next week". Do not change the published date unless the content changes.
```

## Workflow: Pages that earn nothing

### Step 1: Find them

```text
For my site [site]:
This needs Search Console connected. If it is not, stop and tell me to connect it.

1. Run site_pages for the full page list.
2. Run search_console with days set to its allowedDays (the longest my plan reads). Keep only pages that do not appear in its pages list. If pagesLimited is true, the list is cut short; say so and stop.
3. If Analytics is connected, run analytics_pages and drop any page that had visits from search.

A page with 0 keywords in site_pages is not proof of anything; site_pages counts only keywords RankMySEO has collected. Search Console decides.

Then ask me which of the remaining pages have a job outside search (contact, legal, sign-in, thank-you, ads, email, print), and leave those out. Leave out pages published in the last three months.

Return one table: Page | Words | Role | Published (if known) | Topic.
Sort by topic.
```

### Step 2: Decide each one

```text
If the earns-nothing table from the previous step is in this conversation, use it. If not, run that step first.

For each page, pick one decision:
- Refresh: the topic matters to my business and people search for it.
- Merge: another page covers the topic better. Name it.
- Redirect: retired, with a clear replacement. 301 to that page, never to the homepage by default.
- Remove: no replacement and no job. Return 404 or 410; Google treats both as "page does not exist".
- Keep: it serves people outside search.

Before Redirect or Remove, ask me to check Search Console's Links report (top linked pages) for links from other sites.

Return one table: Page | Decision | Target page (for merge or redirect) | Reason in one sentence.
Change nothing until I approve each row. Removing pages in bulk does not make a site look fresh to Google; only remove a page that has no job.
```
