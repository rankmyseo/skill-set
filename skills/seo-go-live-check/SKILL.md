---
name: seo-go-live-check
description: The first-weeks checklist after a website goes live. Confirms Google can find and read the site, the tracked keywords are checking, and the owner's numbers have started arriving. Use during the first month after a site first goes live. For a batch of new pages, use seo-indexing.
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

## What to tell the owner

- New sites take weeks to show search traffic, and some get none for a while.
- Early numbers are small. A single spike is not a trend.
- No plan can guarantee a ranking.
