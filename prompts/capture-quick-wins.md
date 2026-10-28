# Capture quick wins

Find the keywords and pages closest to more clicks, run a two-week sprint on them, and measure what changed. Skill: `seo-quick-wins`.

## Workflow: Find quick wins

### Step 1: The candidates

```text
For my site [site]:
1. Run page_updates. Read the rows marked tune, expand, and refresh. Skip rows marked wait, and leave pages in keep alone.
2. Run list_keywords and keep tracked keywords at positions 4 to 20.
3. Run search_console with days: 28 and find queries with many impressions and few clicks.

Merge duplicates so each page appears once.

Return one table: Page | Keyword | Position now | Signal (tune, expand, refresh, shown but rarely clicked) | Why now (the number and its source) | Impact (high, medium, low) | Effort (low, medium, high).
Sort by impact, then effort (low first). Show up to 15 rows.

page_updates clicks are for ordering, not a forecast; do not present them as expected traffic. Write "not reported" for missing numbers.
```

## Workflow: Plan a two-week sprint

### Step 1: The sprint

```text
If the quick wins table from the previous step is in this conversation, use it. If not, run that step first.

I have [hours] hours over the next [two] weeks. Pick up to ten items that fit. Put high-impact, low-effort items in week one.

Return one table per week: Page | Keyword | Tasks (four to six short tasks) | Hours | Metric to check | Check date.
Add the hours. If they exceed what I have, cut from the bottom and say what you cut.

Do not change any page until I approve the list.
```

### Step 2: The changes

```text
If my approved sprint list is in this conversation, use it. If not, run the sprint prompt first.

For each item, write the exact change: the new title and description, the section to add, or the internal links to add with their anchor text. Show the current text next to the new text.

Return one block per item. After I approve each one, add a change log row: Date | Page | What changed | Why | Metric to check | Check date.
```

## Workflow: Measure the sprint

### Step 1: Before and after

```text
If the sprint change log is in this conversation, use it. If not, ask me for the pages and the dates they changed.

For my site [site]:
1. Run page_updates and read results and afterEdit for the edited pages.
2. Run keyword_history for each target keyword.
3. Run search_console with days: 28 for the pages.

Return one table: Page | Keyword | Before | After | Change | Verdict (improved, stable, declined, too early).
Sort by verdict, improved first.

Count each verdict and say in one sentence what the sprint did. Do not credit a change for a rise that started before it.
```
