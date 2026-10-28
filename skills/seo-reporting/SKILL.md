---
name: seo-reporting
description: Standard formats for the change log and the owner report. The change log records every page change with its date, reason, and expected effect, so later checks have a baseline. The owner report is a short weekly or monthly summary the owner can read without SEO knowledge, and the executive summary is a one-page scorecard with the decisions a manager or client must make. Use after any change to a live site, and when writing the weekly, monthly, or executive report.
---

# Reporting

Goal: every change to a live site is recorded, and the owner gets a short, consistent report each week or month.

Acceptance: the owner can find any change by date, see why it was made, and read a report that says what moved, what did not, and what happens next.

## 1. The change log

Keep one log per site. Add one row for each change, on the day it is made.

| Date | Page or URL | What changed | Why | Expected effect | Metric to check | Check date | Result |
| --- | --- | --- | --- | --- | --- | --- | --- |

Rules:

- One row per change. Batch edits to one page on one day can share a row.
- "Why" names the evidence: the number, the issue, or the owner's request. "Looks better" is not a reason.
- "Expected effect" names one metric. Do not promise a rank.
- "Check date" is at least two weekly checks after the change, or four weeks of Search Console data, whichever is later.
- "Result" stays blank until the check date. Then write what happened, with the number and its source.
- Record owner-made changes too, such as a new page the owner published or a setting they changed.

## 2. The weekly owner report

Keep it under one page. Use this order:

1. **Summary:** one sentence on the main change this week.
2. **Numbers:** Search Console clicks and impressions for the last 28 days, against the 28 days before, with the source and the window named. Tracked ranks if RankMySEO is connected. Key events if conversion tracking is set up.
3. **Changes this week:** the rows from the change log for the week, with their check dates.
4. **Three actions:** the three actions from the maintenance loop, each with its reason and the page it affects.
5. **Waiting on the owner:** any fact, approval, or access you need.

Use plain words. Explain a term the first time you use it.

## 3. The monthly summary

Use the same order, over 28 days. Add:

- The trend across the month, not just the last week.
- Which of last month's actions had a result, and whether it was positive, negative, or too early to tell.
- Any change log row whose check date has passed, with its result filled in.

## 4. The executive summary

For a manager, a client, or the end of a quarter (`/seo report exec`). One page, read in two minutes. Use this order:

1. **Headline:** one sentence on what search did for the business in the period.
2. **Scorecard:** four to six numbers, each with this period, the period before, the change, the source, and the window. Pick from clicks and impressions (Search Console), visits from search and key events (GA4), tracked keywords in the top 3 and top 10 (RankMySEO), and rivals' visits from search (`competitor_traffic`, marked as estimates).
3. **What worked:** up to three changes from the change log whose check date has passed, with their result.
4. **What did not:** up to three, with the cause if it is known.
5. **Risks:** rivals closing in on money keywords, pages sliding, open technical problems.
6. **Decisions needed:** each one with the options, the evidence, and what you recommend.
7. **Next period:** the three to five priorities, from `seo-roadmap` when one exists.

Use the same numbers as the weekly reports, so the two never disagree. Leave out any metric without a source; write "not reported" instead of a guess.

## 5. Do not

- Put numbers in the report without a source and a window.
- Report a result before its check date.
- Add a daily report unless GA4 or Search Console is connected. See `seo-maintenance-loop`.
- Blame a number change on a page change without checking the change log first.
- Quote average position from Search Console as a tracked rank.
