---
name: seo-quick-wins
description: A focused push on the pages and keywords closest to earning more clicks, run as a short sprint of up to ten items. Finds keywords at positions 4 to 20, pages shown often but rarely clicked, and pages sliding down, ranks them by impact and effort, plans the sprint with the owner, and compares before and after. Use when the owner wants faster results than the weekly three actions, or asks for quick wins.
---

# SEO quick wins

Goal: the owner gets a short list of changes that can move clicks within weeks, a sprint that fits the time they have, and a before-and-after check once it ends.

Acceptance: every sprint item has a page, a keyword, the number behind it, an effort estimate, and the date to check it.

The weekly review (`seo-maintenance-loop`) picks three actions. This skill is for a deliberate push of up to ten, when the owner has time to make them.

## 1. Find the candidates

RankMySEO steps need Starter or above. Without RankMySEO, use Search Console directly and skip the tracked-rank rows.

1. `page_updates`: read the rows marked `tune` (positions 4 to 10), `expand` (11 to 20), and `refresh` (a keyword slid over the last three checks). Skip `wait` rows, which changed in the last six weeks, and leave `keep` pages alone.
2. When Search Console is connected, `page_updates` also flags pages shown often but rarely clicked, and pages on page two with real impressions. Take those too.
3. `list_keywords`: tracked keywords at positions 4 to 20, with volume.
4. `search_console` for 28 days: queries with many impressions and few clicks at a position that should earn clicks.

Remove duplicates. One page can carry several keywords; keep it as one item. Read each `page_updates` row's `reasons`: a `may_compete` reason means another page may answer the keyword better, so check both pages with `seo-content-refresh` before editing either.

## 2. Rank them

Put each candidate in one table, sorted by impact first, then effort:

| Page | Keyword | Now | Signal | Why now (one sentence, with the number and its source) | Impact | Effort |
| --- | --- | --- | --- | --- | --- | --- |

- **Impact:** high when the keyword has real volume and sits at positions 4 to 10, or the page already gets many impressions. Use `page_updates` order as the starting point; its clicks are for ordering, not a forecast.
- **Effort:** low for a title, description, or internal link change. Medium for a new section. High for a rewrite or a merge.
- A money page beats an informational page at the same impact.
- Do not invent volume or difficulty. A missing number is "not reported".

These are working rules for ordering, not measured thresholds. Tell the owner they can change them.

## 3. Plan the sprint with the owner

Ask how many hours they or their team have, and over how many weeks. Default to two weeks.

- Fill week one with the high-impact, low-effort items. Put larger items in week two.
- Add the hours. If they exceed what the owner has, cut from the bottom and say what was cut.
- Stop at ten items.
- Get a yes on the list before any change.

## 4. The checklist for each item

For each item, list four to six short tasks. Typical tasks by signal:

- **Tune (4 to 10):** answer the search in the first paragraph, tighten the title and description (`seo-page-rewrite`), add two internal links from related pages with plain anchor text.
- **Expand (11 to 20):** add the section the reader is missing, check the title and H1 name the keyword in plain words, link to the page from the hub.
- **Refresh:** update facts and dates that changed, then follow `seo-content-refresh`.
- **Shown but rarely clicked:** rewrite the title and description only. Leave the body alone.

Each item gets one check: the keyword's tracked position, or the page's Search Console clicks, and the date to look again.

## 5. Make the changes and log them

Apply each approved change yourself where you can reach the site. Add one change log row per item (`seo-reporting`), with the check date two weekly checks or four weeks later, whichever is later. Ask before `check_ranks`; it is a write.

## 6. Before and after

On the check date:

1. `page_updates` `results` shows how edited pages moved, and `afterEdit` compares clicks over equal spans before and after the change.
2. `keyword_history` for each target keyword.
3. Search Console clicks for each page, the same number of days before and after.

| Page | Keyword | Before | After | Change | Verdict |
| --- | --- | --- | --- | --- | --- |

Verdict is improved, stable, declined, or too early. Then count each, and say in one sentence what the sprint did. Do not credit a change for a rise that started before it; check the change log dates.

## Do not

- Change pages in the `keep` list.
- Edit a page again inside six weeks of the last change unless something broke.
- Promise a position or a date.
- Run a second sprint before the first one has its check date.
