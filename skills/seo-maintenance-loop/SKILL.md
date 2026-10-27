---
name: seo-maintenance-loop
description: The recurring check for a live website. Finds the few opportunities worth acting on this week (keywords near the top, pages with search demand but weak clicks, on-page issues, competitor gaps, link changes), ranks them, and gives the owner three actions. Use for weekly or monthly reviews, or when the owner asks what to fix or write next.
---

# SEO maintenance loop

Goal: each round gives the owner three actions. Each one has a reason, a page, and a way to tell whether it worked.

Acceptance: the owner can read the three actions, say which one to do first, and say what to check in two weeks.

## Cadence

- **Weekly review:** the normal period. One full round of this loop, ending in three actions.
- **Monthly summary:** the same loop over the last 28 days, compared with the 28 days before. It shows the trend and which of last month's actions worked.
- **Daily digest:** only when Google Analytics (GA4) or Search Console is connected, so the numbers are available. The digest reads the daily trend from `analytics_pages` and the daily series from `search_console`. It lists visits to the top pages and Search Console clicks and impressions, compared with the 7 days before. It flags a drop or spike only past a threshold the owner agrees to. It proposes no daily actions.
- If neither GA4 nor Search Console is connected, there is no daily digest. Say that once, and offer the weekly review.
- Recent days can still change as the data updates. Compare complete days only, and say so in the digest.
- Rank checks in RankMySEO are weekly on every plan. Growth and above also get a daily pass when there is room. Check `account_status` for `rankRefresh` before you describe any daily rank as available.

## One round, in order

Steps marked RankMySEO need the owner's RankMySEO account. If the owner does not use it, run the Search Console and GA4 steps with a direct connector, skip the rest, and say what is missing.

1. `account_status` (RankMySEO): confirm the plan and that nothing is refused.
2. `project_overview`: the headline numbers, average position, how many keywords moved, and `nextSteps`.
3. `next_actions`: the ranked to-do list from on-page issues, keywords close to the top, and page ideas. Starter and above. Read the top rows. Do not copy all of them.
4. Search Console for 28 days, compared with the previous window (`search_console` in RankMySEO, or a direct connector).
5. `list_keywords`. Run `keyword_history` on any keyword that dropped.
6. `site_issues` when `next_actions` shows on-page problems. Use `issue_pages` for the URLs behind one issue.
7. Rivals, when saved (Starter and above): `list_competitors` to see who is saved, `keyword_gap` for keywords they rank for that the site does not, and `competitor_traffic` for organic visits to the site and each rival. Use `competitor_traffic` when the owner asks how the site compares. It queues a collect for any domain not yet pulled, so call it again later.
8. `backlink_review` only when the owner asks about links, or when lost links point to important pages. Start with `linkStatus: "lost"` for pages that matter. For spam review, pass `spamScoreAbove: 20` and `limit: 20`. Use `savedOnly: true` to page through the same saved report without starting a new collection. Score filters exclude rows with no score, so say how many rows had none.
9. The GA4 pages report, to see what visitors do after they land (`analytics_pages` in RankMySEO, or a direct connector).

Do not run every step every round. Pick the steps the last round left open.

## Opportunity types and the first move

| Signal | What it usually means | First move |
| --- | --- | --- |
| Tracked keyword at positions 4 to 10 | Close to the top 3 | Strengthen the page that owns the keyword: answer the search in the first paragraph, add a section, link to it from related pages |
| Tracked keyword at positions 11 to 20 | Needs a larger push to reach the top 10 | Same as above, and check the title and H1 contain the keyword in plain words |
| Search Console query with impressions but few clicks, at a position that should earn clicks | The snippet does not earn the click | Rewrite the title and description with `seo-page-rewrite` |
| Search Console query with many impressions at position 30 or lower | The page may be the wrong owner, or too thin | Check that this page is the right owner. If not, decide whether a new page is needed |
| Tracked keyword that fell across several checks | A stale page, or a rival moved up | `keyword_history`, then `rank_compare` to see who passed the site |
| `site_issues` item that touches many pages | A template problem | Fix it once in the template, not page by page |
| `keyword_gap` keyword with clear buyer intent and no owner page | A missing page | Propose one page using the rules in `seo-launch-plan` |
| Not enough candidates for the next round | More keywords are needed | `research_site` (Starter and above) reads clusters from the site as it is. `start_auto_add` queues a fuller website review. It is a write, so it needs the owner's yes first. Nothing is tracked until the owner picks it |
| `backlink_review`: lost links to an important page | A moved or removed page | Check the page still exists. Redirect it if it moved |
| A pattern of spammy-looking new links | Possible bad links | Review the rows with `backlink_review`. Offer the disavow file only when the owner asks, using `disavow_export` (Starter and above). It returns the saved list as a text file and does not submit anything to Google. Never say a disavow is needed without evidence |

## Choosing the three

Rank the candidates by impact first, then effort:

- Pages that already get impressions or sit near the top beat new pages. A new page takes weeks to show.
- Issues that stop crawling or indexing beat cosmetic ones.
- One template fix that touches many pages beats many one-page fixes.
- Stop at three. Put the rest under a short backlog heading.

## Output for each action

- **Action:** one sentence, starting with the verb.
- **Page:** the URL.
- **Why:** the number you saw, its source, and its window.
- **Check:** what to look at, and when. Use two weekly checks or four weeks of Search Console data, whichever is later.

## When traffic or ranks drop

Use this when the owner says visits, clicks, or ranks fell, or when the weekly round shows a drop. Find where it fell before you guess why.

1. **Confirm it.** Use one source, complete days, and the same weekdays in both windows. Compare with the same weeks last year when Search Console has them, to rule out a seasonal dip.
2. **Find where.** In Search Console, split by page, query, country, device, and search type (web, image, video, news). One page, one section, and the whole site point to different causes.
3. **Check the tracking.** If GA4 visits fell and Search Console clicks did not, suspect the tag or the cookie banner before search.
4. **Check your own changes.** Read the change log (`seo-reporting`) for the window. A redesign, a move, or a template change points to the release check in `seo-go-live-check`.
5. **Check Google.** Open the Google Search Status Dashboard (status.search.google.com) for a ranking update or an incident in the window. If an update is still rolling out, wait. Google advises waiting at least a full week after it finishes, then comparing a week after with a week before it started.
6. **Check what Google sees.** On the pages that fell: status code, `noindex`, canonical, and robots.txt. Ask the owner to open the Page indexing, Manual actions, and Security issues reports in Search Console if you cannot reach them. In RankMySEO, run `site_issues`.
7. **Check rivals.** `keyword_history` on the keywords that fell, then `rank_compare` to see who passed the site.

How to act on it:

- A small drop on a page that still ranks well, such as position 2 to 4, needs no big change. Google advises against changing pages that already perform well.
- A large drop after a core update calls for the people-first checks in `seo-page-rewrite` on the pages that fell most, and on the site as a whole. Do not make quick fixes such as removing an element because someone said it hurts SEO.
- Deleting pages is a last resort. Propose it only for pages written for search and not for people, and only with the owner's yes.
- Recovery after a core update can take months. Say so, and set the next check date.

Report what fell, where, the most likely cause and the evidence for it, what you could not check, and at most three actions.

## Checking AI answers (optional)

Use this when the owner asks whether AI assistants mention the site.

- Test 10 to 20 prompts that matter to revenue, written the way buyers type them.
- Run each prompt 3 to 5 times per assistant. Record whether the site is mentioned.
- Report the rate with its sample size, for example "mentioned in 3 of 5 runs". One run is an anecdote. Compare rates over time.
- Agency and Scale plans can use `track_ai`. It checks the prompts the owner has ticked for ChatGPT and Gemini, weekly. Check the plan with `account_status` first.
- For Google's AI features, use the Generative AI performance report in Search Console, which shows impressions only.
- Do not rewrite a page to chase one run's result.

## Rules

- Say what the fix is meant to change. Do not promise it will raise a rank.
- Do not write the rewrite here. Hand the page to `seo-page-rewrite`.
- Do not add keywords or competitors without the owner's yes.
- `check_ranks` queues a fresh rank check. It is a write, so use it only when the owner asks, for example right after an approved change. Results land within minutes. Read them with `list_keywords`, not by calling `check_ranks` again.
- Apply an approved page change yourself, in the files or builder you can reach. Then add a row to the change log (see `seo-reporting`), with the date and the check date, so the check two weeks later has a baseline.
- If a plan limit blocks a step, say which limit and give the next window or the upgrade path.
