# Build a 90-day roadmap

Turn what is known about the site into a plan for the next quarter. Skill: `seo-roadmap`.

## Workflow: Gather, prioritize, plan

### Step 1: Gather

```text
For my site [site], gather the current state. Reuse any table already in this conversation instead of calling the tool again.

Run account_status, project_overview, next_actions, page_updates, site_issues, and search_console with days: 28. If rivals are saved, run keyword_gap and rank_compare.

Return one table: Area (technical, existing pages, new pages, rivals) | Finding | Number and source | Date read.
Show up to 15 rows.

Then ask me two questions: my business goal for the quarter (leads, sales, bookings, sign-ups), and how many hours a week I or my team can give.
```

### Step 2: Prioritize

```text
If the findings table and my answers from the previous step are in this conversation, use them. If not, run that step first.

Turn the findings into initiatives under four themes: fix, win (pages near the top), build (new pages), protect (pages and keywords to defend).

Score each initiative low, medium, or high on impact, effort, and confidence. Fixes that stop pages being indexed come first.

Return one table: Initiative | Theme | Impact | Effort | Confidence | Reason (number and source).
Keep three to six. List what you left out and why.
```

### Step 3: The 90-day plan

```text
If the initiatives table from the previous step is in this conversation, use it. If not, run that step first.

Plan the next 90 days within the hours I gave.

Return one table: Days (1 to 30, 31 to 60, 61 to 90) | Initiative | Tasks | Who (you, me, my developer or writer) | Hours | Done when.

Then list:
- The metrics with today's baseline, date, and source: leading (pages indexed, issues fixed, impressions, tracked positions) and lagging (clicks, key events)
- What I must do myself
- The check-ins: weekly review, and reviews at day 30, 60, and 90

Do not promise rankings, traffic, or dates for results. Start nothing until I approve.
```
