---
name: seo-competitors
description: Find who the site actually competes with in search, benchmark against them, watch what they change, and turn the keywords and topics they win into a plan. Covers search rivals (which may differ from business rivals), keyword and content gaps, a monthly watch with alert rules, and an optional look at the ads a rival runs. Use when the owner asks who they compete with, what rivals are doing, or what topics they are missing.
---

# Competitors and gaps

Goal: the owner knows the three to five sites they compete with in search, where those sites are ahead, and which gaps are worth closing first.

Acceptance: every gap in the plan has a keyword or topic, the rival that wins it, the number behind it, and a decision: new page, refresh an existing page, or skip.

RankMySEO steps need Starter or above. The number of saved rivals per site follows the plan; `account_status` shows it.

## 1. Find the search rivals

Business rivals and search rivals are often different sites. A guide, directory, or marketplace can take the clicks a local rival never sees.

1. `list_competitors`: rivals already saved on the site.
2. `research_site`: the competitors the last website review found. If no review has run yet, the call starts one, which uses the daily research budget; ask the owner first.
3. The search results for the site's main keywords, if you can search, or ask the owner to paste them: which sites keep showing up.
4. Ask the owner which businesses they lose deals to. One question.

`rank_compare`, `competitor_traffic`, and `keyword_gap` cover only rivals already saved, so they cannot find new ones.

List each candidate with why it counts: found by the website review, seen in the results, or the owner's word. Mark each one as a direct rival (sells the same thing) or a search rival (takes the same clicks but sells something else, like a guide or directory).

Suggest three to five. Save them with `add_competitor` only after the owner's yes; it uses plan slots. The benchmark below needs them saved.

## 2. Benchmark

| Site | Visits from search | Shared keywords | Keywords only they rank for | Where they lead |
| --- | --- | --- | --- | --- |

- `competitor_traffic`: visits from search, ranking keywords, authority, and backlinks for the site and each saved rival, plus a monthly series. Say these are estimates from the data source, not the rival's own analytics.
- `keyword_gap`: overlap and the keywords rivals rank for that the site does not.
- `rank_compare`: on tracked keywords, which rival is ahead and by how much.

`keyword_gap` and `competitor_traffic` queue a collect for each domain not pulled yet. If they answer `queued`, ask again later instead of calling in a loop. The answer still carries the sites that are ready; use those. A rival listed in `noData`, or marked `unavailable`, gets "not reported" in the table.

## 3. Keyword gaps

From `keyword_gap`, keep keywords that match what the business sells or knows. Drop topics the owner would never write about. Set rival brand names aside; they fit only a comparison page, which follows the rule in `seo-launch-plan` "Watch for" and needs the owner's yes.

Group the rest into topics. For each topic:

| Topic | Keywords | Volume | Rival that wins it | Intent | Site page today | Decision |
| --- | --- | --- | --- | --- | --- | --- |

- **Site page today:** check `site_pages`. If a page already covers the topic, the decision is refresh, not a new page.
- **Decision:** new page (`seo-page-brief`), refresh (`seo-content-refresh`), or skip, with a one-sentence reason.
- Use `keyword_planner` for volume and difficulty on a topic's main keyword when the gap data has none. A missing number is "not reported".

Rank topics by volume and intent, money topics first. Picking which keywords to track follows `seo-keyword-selection`.

## 4. Content gaps

A content gap is a question rivals answer and the site does not, even when no single keyword shows it.

- Read the rival pages that win the top topics. Note the format (guide, tool, comparison, category, local page), the sections, and what proof they show.
- Note what the owner can say that the rivals cannot: first-hand detail, prices, cases, local knowledge. That is the angle, not a copy of the rival page.
- Do not copy or closely rewrite a rival's page. Google's guidance asks for original value beyond what other pages say.

## 5. The monthly watch

Once a month, or when the owner asks what changed:

1. `rank_compare`: tracked keywords where a rival moved past the site, or the site passed a rival.
2. `competitor_traffic`: each site's `months` series holds monthly visits and keyword counts. Compare the latest month with the month before and the same month last year.
3. `keyword_gap`: keywords a rival ranks for in the site's topics that were not in last month's list.
4. Read the rival's homepage, pricing, and new pages for launches or offers, when a rival jumps.

`keyword_gap` returns the current list only, so save each month's gap list with its date in the owner report. The first run sets that baseline.

Agree on alert rules with the owner, for example "a rival passes us on a money keyword" or "a rival's visits double". Treat the numbers as working rules the owner can change. Report only what crosses a rule, with the reading date.

Name what to protect: pages in `page_updates` `keep` and money keywords in the top three, when a rival closes in on them.

## 6. Optional: the ads a rival runs

When the owner wants to know what a rival thinks sells, `social_research` with tool `advertiser` on `googleads`, the rival's domain as the query, and the two-letter `country` of the market, lists ads that rival runs. It costs everyday lookups from the account's monthly allowance, so ask first. Call it once; if it answers `queued`, call again with the same arguments about a minute later, which costs nothing. Use `social_lookups` to reuse a saved answer.

This shows ad copy and offers. It does not show bids, spend, or cost per click; do not estimate them.

## 7. Report back

- The rival list with direct or search rival, and why each counts.
- The benchmark table with the reading date.
- The top gap topics with decisions.
- What changed this month, if this is a watch run.
- Hand-offs: briefs to `seo-page-brief`, refreshes to `seo-content-refresh`, keywords to `seo-keyword-selection`.

## Do not

- Add a rival or a keyword without the owner's yes.
- Call a rival's traffic exact; it is an estimate.
- Target a rival's brand name outside a comparison page the owner approved.
- Report a rival's ranking change as the cause of the site's drop without checking `seo-maintenance-loop` "When traffic or ranks drop".
