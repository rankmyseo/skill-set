---
name: seo-keyword-selection
description: Choose the next keywords to target, for a new website from the owner's intake, or for an existing website from measured search demand. Sets a primary and alternate keywords, validates them with RankMySEO or Search Console, checks relevance to the business, and classifies each as money, tool, hub, or informational. Use before a plan is written for a new site, or when the owner asks what to target next on an existing one.
---

# Keyword selection

Goal: a short list of keywords, each with one owner page type, one reason, and a validation status. Keywords become tracked only after the owner's yes.

Acceptance: the owner can read the list and say which page answers each keyword, and why that keyword fits the business.

Use the evidence that exists. For a new site, the evidence is the owner's words and the research tools. For an existing site, the evidence is what people already search for.

## Path A: new website (no search data yet)

1. **Start from the intake.** Use the product, the place, the goal, the competitor, and the customers' own words. This gives a hypothesis, not data. Say so in the plan.
2. **Choose a primary keyword.** It is the phrase a buyer or reader would type for this product in this place. Choose by fit with the business, not by how large it sounds.
3. **Add alternates.** Three to five other phrasings: synonyms, category names, question forms, and the competitor's name when a buyer compares.
4. **Validate with RankMySEO.** Call `keyword_planner` with each seed (`q`), the country from the intake, and the saved `project`. The keyword tools need a saved site, so ask for the domain and add it with `add_project` after the owner's yes. Read until `status` is `ready`. Show volume and difficulty only where they appear. Unknown stays unknown.
5. **Check the competitor.** Once the competitor is saved and collected, `keyword_gap` lists keywords it ranks for that the site does not. Use it to find gaps, not to copy the competitor's whole list.
6. **Check other platforms.** For social platforms the owner uses, use `social_research` after the draft list exists. Check `social_lookups` first.

## Path B: existing website (search data exists)

1. **Start from what people already search.** `search_console` with `days: 28` gives the top queries, with clicks, impressions, CTR, and position. These beat any estimate.
2. **Read the tracked rank.** `list_keywords` and `keyword_history` show the current position and trend for tracked keywords.
3. **Rank the candidates.** Keywords that already show impressions and sit at positions 4 to 10 are the closest wins. Positions 11 to 20 need more work. A keyword at position 30 or lower with many impressions usually points to the wrong page or a thin one, not a quick win.
4. **Read the competitor gap.** `keyword_gap` (Starter and above) shows keywords rivals rank for that the site does not.
5. **Look at the site's content.** `research_site` returns clusters from the pages the site has. Use it to see what the site already covers. If no website review has run yet, the call starts one, which uses the daily research budget; ask the owner first.
6. **Separate brand queries.** Queries that contain the brand name measure brand demand. Keep them in their own group, and do not count them as new keyword targets.

## Relevance check (judgment, for both paths)

Keep a keyword only if it:

- describes what the owner sells or publishes,
- fits the country and language the owner serves, and
- can be answered by a page the owner will build or keep.

Drop a keyword when a different kind of page answers it. Show the owner the drop list, with a reason for each drop.

## Classify each keyword

Give each kept keyword one type, using the same rules as `seo-launch-plan`:

- **Money:** a buyer acts, with words like software, service, agency, or pricing.
- **Tool:** a free result, with words like checker, tool, or audit.
- **Hub:** a topic term with no product of its own.
- **Informational:** a question, with words like what is, how to, or meaning.

If a page already ranks for the keyword or gets impressions for it, that page stays the owner. A new page links to it and does not compete.

## Output

A table with these columns: keyword, type, owner page (existing or planned), source (Search Console, RankMySEO planner, competitor gap, or intake), volume and difficulty where available, relevance decision, and tracking status. Mark each keyword as validated, hypothesis, or dropped.

Then ask the owner which keywords to track. Track only the ones they pick, with `add_keyword`, after their yes.

## Do not

- Estimate volume, difficulty, or position.
- Track a keyword before the owner picks it.
- Pick a keyword only because a competitor ranks for it.
- Treat a brand query as a new keyword target.
