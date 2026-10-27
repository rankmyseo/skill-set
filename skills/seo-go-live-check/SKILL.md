---
name: seo-go-live-check
description: The first-weeks checklist after a website goes live. Confirms Google can find and read the site, the tracked keywords are checking, and the owner's numbers have started arriving. Use during the first month after a site first goes live, and before and after a redesign, a domain move, or a template change. For a batch of new pages, use seo-indexing.
---

# SEO go-live check

Goal: in the first week, confirm the basics work. In the first month, confirm the numbers are arriving.

Steps that read tracked rank need RankMySEO. If the owner does not use it, skip them and say so. Search Console and GA4 can be read directly or through RankMySEO.

Acceptance: the owner knows which of three states the site is in (crawling and indexing, waiting, or broken), and has one fix for each broken item.

## Days 0 to 2: the basics

1. Open the live homepage and one service page. Check the title, description, H1, canonical link, and that the URL form matches the sitemap.
2. Open `/sitemap.xml` and `/robots.txt`. The sitemap loads and lists the canonical URLs. The robots file points to the sitemap.
3. Submission and indexing requests follow `seo-indexing`. Do not repeat them here.
4. Call `project_overview`. A new site shows only the keywords the owner added.

Also check the Search generative AI control in Search Console (Settings, then Search generative AI). It should be set to include the site. If the owner has excluded the site, say so and ask before you change it.

Run the reference scan at isitagentready.com on the live homepage, and report the failing checks in priority order. Do not present an llms.txt failure as a Google problem.

Validate the schema on the live URLs again. Use the same two tools as in `seo-site-setup`. The target is zero errors.

Check the accessibility tree on the homepage and one service page. Every button, link, and form field needs a name. Report any that have none, since a missing name blocks both assistive technology and browser agents.

## Days 3 to 7: data starts

5. Read the last 28 days of Search Console, through `search_console` in RankMySEO or a direct connector. Few or no rows in the first days is normal. Say so, so the owner does not panic.
6. Once GA4 is connected, directly or through RankMySEO, check that the homepage appears in the pages report (`analytics_pages` in RankMySEO). If no pages appear, check the GA4 tag before anything else.
7. `list_keywords` shows new keywords with `position: null` and `outsideTop20: true`. That is normal. The first position arrives after the next rank check. Do not report it as a failure.

## Weeks 2 to 4: the first real read

8. Call `site_issues` once an audit has run. It says "not run yet" until one completes. Treat that as a wait, not a fault. When it has results, give the owner the top three issues by pages affected.
9. Use `keyword_history` on a keyword once it has a trend, meaning several points, not one.
10. Compare Search Console with the tracked rank. They measure different things. Say which one you quote.

## Three states

- **Crawling and indexing:** pages show impressions in `search_console`. Move on to `seo-maintenance-loop` after about four weeks.
- **Waiting:** the sitemap is submitted, there are no errors, and impressions are few or none. Tell the owner that new sites often take weeks to show search traffic. Set a date to check again.
- **Broken:** a key page returns 404 or redirects wrongly, the sitemap or robots file is missing, the homepage is set to `noindex`, or the host blocks crawlers. Name the one fix. Make the change in the builder only if the owner asks.

## Redesigns and releases

Use this before and after a redesign, a move to a new domain or platform, or a change to a shared template. A release can drop titles, canonicals, or the main text without anyone seeing it on screen.

**Before the release, take a snapshot.** Pick the pages that get the most Search Console clicks, plus every money page. For each one, record the URL, status code, title, description, H1, canonical, robots meta tag or `X-Robots-Tag` header, hreflang links, JSON-LD types, and whether the main text is in the first HTML response. Save a copy of `/robots.txt` and the list of URLs in the sitemap. Note each page's clicks for the last 28 days.

If any URL will change, write the redirect map first (`seo-existing-site`). Each old URL gets a server-side permanent redirect (`301` or `308`) to its closest new page.

**After the release, compare.** Check the staging site first if there is one, then the live site the same day. Flag:

- A status code that changed, or an old URL that does not redirect
- `noindex` or a robots.txt rule that was not there before
- A canonical that now points somewhere else
- A title or H1 that lost the page's keyword
- A JSON-LD type that disappeared
- Main text that is no longer in the first HTML response
- Sitemap URLs that redirect or return errors

Fix what broke before you request indexing. Then run the days 0 to 2 basics above, add a row to the change log (`seo-reporting`), and check the same pages in Search Console after one week and after four.

For a move to a new domain:

- The owner submits a Change of Address in Search Console for the old domain, for every verified version of it (with and without www, and subdomains).
- Keep the redirects for at least a year, as Google advises.
- Ranks can move around for a few weeks or more while Google recrawls. Tell the owner before the move, not after.

## What to tell the owner

- New sites take weeks to show search traffic, and some get none for a while.
- Early numbers are small. A single spike is not a trend.
- No plan can guarantee a ranking.
