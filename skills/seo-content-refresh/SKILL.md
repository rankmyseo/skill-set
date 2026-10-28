---
name: seo-content-refresh
description: Fix pages that are losing clicks and clean up pages that earn nothing. Finds declining and underperforming pages, works out why each one slipped, writes a refresh plan per page, and decides for pages with no search visibility whether to refresh, merge, redirect, or remove them. Use when the owner asks to refresh old content, when pages are sliding, or when the site has many pages no one finds.
---

# Content refresh and cleanup

Goal: every slipping page has a reason and a plan, and every page that earns nothing has a decision the owner approved.

Acceptance: each page in scope has one decision, one reason with its number and source, and a check date.

## 1. Find pages that are slipping

RankMySEO steps need Starter or above.

1. `page_updates`: rows marked `refresh` (a keyword slid over the last three checks), `rewrite` (positions 21 to 50 with real search volume), and `merge` or `split` (two of the site's pages compete for one keyword). With Search Console connected, rows whose `search` shows clicks falling against the 28 days before.
2. `search_console` with `days: 28`: each page carries `clicksChange` against the previous window when `pagesComparable` is true. When it is false, use the `search` numbers on `page_updates` rows instead.
3. `analytics_pages`, when Analytics is connected: pages whose visits fell.

Sort by the absolute number of clicks lost, not by percentage. A page that went from 400 clicks to 300 matters more than one that went from 4 to 1.

## 2. Find out why each page slipped

Check these in order, and stop at the first that holds:

1. **Own change:** the change log (`seo-reporting`) shows an edit, a URL change, or a template change near the date.
2. **Broken basics:** `site_issues` or `issue_pages` shows the page with an error, a noindex, or a wrong canonical.
3. **Competing page:** `page_updates` marks it `merge` or `split`, a row's `reasons` include `may_compete` (another page may answer the keyword better; read both before changing either), or `site_pages` shows two pages with the same biggest keyword.
4. **Stale:** prices, dates, steps, or screenshots on the page are out of date.
5. **Rivals:** `rank_compare` shows a saved rival passing it on the page's keywords. See `seo-competitors`.
6. **Demand:** the keyword's searches fell for everyone. See `seo-trends`.

If none holds, say the cause is unknown and wait another check before rewriting.

## 3. The refresh plan per page

| Page | Keyword | Clicks before | Clicks now | Cause | Fix | Effort |
| --- | --- | --- | --- | --- | --- | --- |

Fixes by cause:

- **Stale:** update facts, prices, steps, and dates. Change the visible "updated" date only when the content changed.
- **Off-intent:** reshape the page for what the searcher wants now, with `seo-page-rewrite`.
- **Thin:** add the missing sections a reader needs, from the owner's facts. Do not pad for length.
- **Competing page:** pick one owner page, fold the useful parts of the other in, and 301 the other to it.
- **Broken basics:** fix the issue first, then wait for a recrawl before judging the content.

Keep the URL when you refresh. A new URL resets nothing and adds a redirect.

## 4. Pages that earn nothing

A page earns nothing when, over the full window the plan allows:

- Search Console shows no impressions for it (`search_console` with `days` up to `allowedDays`; a page missing from the `pages` list had none, unless `pagesLimited` is true), and
- Analytics shows no visits from search, when connected, and
- `site_pages` shows it ranks for no keywords.

Search Console decides. `site_pages` counts only the keywords RankMySEO has collected (`rankingKeywords`), so a zero there is common for pages that do earn impressions. Without Search Console, do not call any page one that earns nothing; ask the owner to connect it first.

Then leave out pages with a job outside search: contact, legal, sign-in, thank-you, and pages linked from ads, email, or print. Ask the owner which pages those are. Pages published in the last three months are too new to judge.

Removing old pages in bulk does not make a site look fresh to Google; Google says so directly. Clean up a page because it has no job, not to lift the rest of the site.

## 5. Decide each one

| Decision | When it applies | How |
| --- | --- | --- |
| Refresh | The topic matters to the business and people search for it | Section 3 |
| Merge | Another page covers the same topic better | Fold in the useful parts, then 301 to that page |
| Redirect | The page is retired and another page is a clear replacement | 301 to the replacement, not to the homepage |
| Remove | No replacement exists and the page has no other job | Return 404 or 410. Google treats both as "page does not exist" |
| Keep | The page serves users outside search | Leave it |

Before you remove or redirect a page, check whether other sites link to it. Use Search Console's Links report, top linked pages, or ask the owner. A page with real links is better redirected to a clear replacement than removed.

A removed page should return a real 404 or 410 status. A "not found" message with a 200 status is a soft 404, which Google reports as an error.

## 6. Get the owner's yes, then act

Show the decision table. Nothing is removed, merged, or redirected before the owner approves each row. Then:

- Make the changes, update internal links to the kept URL, and drop retired URLs from the sitemap.
- Log each change (`seo-reporting`) with a check date at least four weeks out.
- For redirects, follow the redirect rules in `seo-existing-site` section 6.

## Do not

- Delete a page as the first fix for a slipping page.
- Redirect every retired page to the homepage.
- Remove or pad a page because of a word count. Google has no preferred word count.
- Change the published date to make a page look fresh without changing the content.
