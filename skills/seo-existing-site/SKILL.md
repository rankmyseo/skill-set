---
name: seo-existing-site
description: Baseline audit for a website that is already live. Builds a page inventory, reads what ranks and what is broken, decides keep, refresh, merge, or redirect for each page, checks for competing pages, and plans redirects for any URL that moves. Use the first time you take on an existing site, or when the owner asks for a full review.
---

# Existing site baseline

Goal: by the end, the owner knows every public page on the site, what each one does for search, and what to do with it. Nothing changes until the owner approves the decisions.

Acceptance: every URL in the inventory has one decision and one reason, and the owner has approved the list.

## 1. Connect the data

- RankMySEO: `list_projects` to find the site, then `account_status` for the plan. Without RankMySEO, use a direct Search Console connection, and say that tracked rank is not available.
- Confirm the site is in the account. If it is not, ask for the domain and add it with `add_project` after the owner's yes.

## 2. Read the headline state

- `project_overview`: tracked keywords, average position, buckets, and `nextSteps`.
- `search_console` with `days: 28`: clicks, impressions, the previous window, top queries, and top pages.
- `site_issues`: on-page problems from the last audit. It says "not run yet" until one completes. Treat that as a wait.
- `next_actions` (Starter and above): the ranked to-do list.

## 3. Build the page inventory

One row per URL. Sources, in order:

1. The sitemap, if one exists. Read it and list every URL.
2. Search Console pages, for URLs that already earn impressions. Include ones the sitemap does not list.
3. The homepage and its main navigation, for pages linked from the site.

For each URL, record: the title, the H1, the status code, the Search Console clicks and impressions, the page's job (money, tool, hub, informational, or support), and the owner's notes.

Say what the inventory does not cover. A page that is neither in the sitemap nor in Search Console, and is not linked from the navigation, is unknown until the owner says it exists.

## 4. Decide each page

| Decision | When it applies |
| --- | --- |
| Keep | The page has the right job, clean basics, and earns clicks or leads |
| Refresh | The page has the right job but the copy is thin, stale, or off-intent. Rewrite with `seo-page-rewrite` |
| Merge | Two or more pages answer one question. Keep the stronger one, fold in the useful parts of the others, and redirect the rest |
| Redirect | The page is retired and a better page owns its topic. Use a 301 redirect |
| Remove | The page has no job, no traffic, and no links. Confirm with the owner before you remove it |

Each decision needs a reason in one sentence, with the number that supports it. "Keep: 240 impressions, position 6 for the main query" is a reason. "Keep: looks fine" is not.

## 5. Check for competing pages

Search Console's query data and page data come back separately in RankMySEO, so it cannot show which page ranks for which query. Use this heuristic:

- Group the inventory by primary keyword, taken from the title and H1.
- Where two or more pages share a primary keyword, mark them as competing. Name the one that should own it, and make the others merge or redirect.
- Where a direct Search Console connection returns query and page together, use that to confirm. Say which method you used.

## 6. Plan redirects for every URL that moves

- Map each old URL to one new URL. Do not map to the homepage unless the topic is the homepage.
- Use 301 (permanent) redirects. Avoid chains: old, then intermediate, then new.
- Keep the old URLs in the redirect file until Search Console shows no traffic to them for several weeks.
- Update internal links to point at the new URL, so the redirect is a fallback, not the route.
- Remove the old URLs from the sitemap once they redirect.
- For a domain move, use Search Console's Change of Address tool, and read Google's move guidance before you change anything.

## 7. Write the baseline

Save one file the owner keeps:

- The inventory table with each decision and reason
- The competing-page groups and the owner for each
- The redirect map
- The headline numbers and the date they were read
- Open questions for the owner
- Next steps: `seo-keyword-selection` for the next targets, then `seo-maintenance-loop`

## Do not

- Change, remove, or redirect any page before the owner approves the decision list.
- Quote Search Console average position as a tracked rank.
- Treat a high average position with many impressions as a win.
- Estimate traffic for a page with no data. Write "not reported".
