---
name: seo-roadmap
description: Turn everything known about a site into a 90-day SEO plan the owner can follow. Sets the goals and how they are measured, picks a few initiatives by impact, effort, and confidence, splits them into 30, 60, and 90 day milestones, and says who does each task. Use when the owner asks for a strategy, a plan for the next quarter, or what to focus on first.
---

# 90-day roadmap

Goal: the owner has one page that says what will be done in the next 90 days, why, in what order, and how they will know it worked.

Acceptance: each initiative has a reason with its number and source, an owner, a milestone date, and one metric; the owner has approved the plan.

## 1. Gather what is already known

Reuse what exists in this conversation or the site's files before calling any tool: the baseline (`seo-existing-site`), the launch plan (`seo-launch-plan`), the keyword list, the change log, and the last owner report.

Fill the gaps with read-only calls:

- `project_overview` and `account_status`: headline numbers and plan.
- `next_actions` and `page_updates`: the ranked fixes and page actions.
- `site_issues`: technical problems.
- `search_console` with `days: 28`: clicks, impressions, and the previous window.
- `keyword_gap` and `rank_compare`, when rivals are saved: where rivals lead.

Ask the owner two things: the business goal for the quarter (leads, sales, bookings, sign-ups) and the hours per week they or their team can give.

## 2. Set goals and metrics

One business goal, then two kinds of search metrics:

- **Leading metrics** move first: issues fixed (`site_issues`), impressions, tracked positions, and pages indexed (Search Console's Page indexing report, which the owner reads if no tool can).
- **Lagging metrics** move later: clicks from search, and key events when conversion tracking is set up (`seo-conversion-tracking`).

Write the baseline for each metric with its date and source. A target is the owner's choice; do not promise a position or a traffic number.

## 3. Pick the initiatives

List candidates under four themes:

| Theme | Where candidates come from |
| --- | --- |
| Fix | `site_issues`, `next_actions`, indexing problems, Core Web Vitals |
| Win | `seo-quick-wins`: positions 4 to 20, pages shown often but rarely clicked |
| Build | New pages from gaps (`seo-competitors`), trends (`seo-trends`), or the page map |
| Protect | Pages in `page_updates` `keep`, money keywords in the top three, rivals closing in |

Score each one low, medium, or high on impact, effort, and confidence (how strong the evidence is). Keep three to six initiatives. Fixes that block indexing come first regardless of score. More than six spreads the hours too thin; say what was left out and why.

## 4. Milestones

| Days | Focus | Initiatives | Done when |
| --- | --- | --- | --- |
| 1 to 30 | Fix and quick wins | | |
| 31 to 60 | Build | | |
| 61 to 90 | Measure and adjust | | |

- Each initiative gets tasks, an owner (the agent, the owner, or the owner's developer or writer), and hours.
- The hours per week must fit what the owner said. If they do not, move work to the next milestone or cut it.
- Owner-only steps are named as such: Business Profile, Search Console settings, approvals, and facts only the owner knows.

## 5. Check-ins

- Weekly: the review in `seo-maintenance-loop` and the owner report in `seo-reporting`.
- At day 30 and day 60: compare each metric with its baseline, mark each initiative on track, behind, or blocked, and adjust the next milestone.
- At day 90: the executive summary in `seo-reporting`, and the next roadmap.

## 6. Report back

One page, in this order: the goal, the metrics with baselines, the initiatives with reasons, the 30/60/90 table, what the owner must do, and what was left out. Get the owner's yes before starting.

## Do not

- Promise rankings, traffic, or dates for results.
- Fill the plan with every possible task.
- Start work on any initiative before the owner approves the plan.
