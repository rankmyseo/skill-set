# agent-skills

Skills that teach an agent to take a site owner who may not know SEO from "I want a website" to a live, measured site, then keep it improving.

Built for Grok Bot and any agent with the RankMySEO MCP connected. Status: **draft**. Tool names and gates were checked against the live RankMySEO MCP catalog and two read-only calls on a real account. The skills have not yet been run end to end on a fresh customer account.

## Skills

| Skill | Phase | Use when |
| --- | --- | --- |
| `rankmyseo-seo-agent` | All | Start here. Routes to the right phase and sets the rules. |
| `seo-launch-plan` | Create | No site yet, or the site is not built. Plan pages and keywords first. |
| `seo-site-setup` | Create | Building or fixing the technical and on-page basics. |
| `seo-go-live-check` | Launch | The first weeks after the site goes live. |
| `seo-indexing` | Launch | Submitting a finished batch of pages to Google, Bing, and IndexNow, then checking on set dates. |
| `seo-existing-site` | Baseline | First review of a live site: page inventory, keep, refresh, merge, or redirect, and competing pages. |
| `seo-keyword-selection` | Keywords | Choosing the next keywords for a new site (from intake) or an existing one (from search data). |
| `seo-page-brief` | Build | A brief for each new page, and the owner facts that must arrive first. |
| `seo-conversion-tracking` | Measure | Turning the owner's lead definition into GA4 key events, without personal data. |
| `seo-reporting` | Report | The change log and the weekly and monthly owner report formats. |
| `seo-search-data` | Live | Reading Search Console and GA4 numbers without over-reading them. |
| `seo-maintenance-loop` | Live | The recurring check that picks the next three actions. |
| `seo-page-rewrite` | Create or live | Writing or rewriting a page, title, or description. |

## What the skills need

- **RankMySEO MCP** over `POST /mcp` with a bearer key. A guest key works for one site and two keywords for 48 hours. For the owner's plan, call `request_link` and have the owner open the link.
- **Search Console and GA4**, read either directly or through RankMySEO (`search_console` and `analytics_pages`). RankMySEO is recommended, not required. The owner connects whichever source they use.
- **The agent does the SEO work itself.** RankMySEO does not build or publish pages. The skills make the agent plan, write, and edit pages and SEO settings in the files or builder it can reach, then check the results. RankMySEO supplies rank tracking and history.

## Out of scope for this set

Social research, the Operator shop, Operator AI, and Indonesian copy by default. Add them later as their own skills.

## What the agent can and cannot do

Checked on 24 October 2026 against the tools connected to this session.

| Task | Agent | Owner |
| --- | --- | --- |
| Read RankMySEO data (ranks, issues, next actions) | Yes | |
| Read Search Console and GA4 | Yes, through RankMySEO or a direct connector | Connects the source |
| Submit a sitemap or request indexing in Google Search Console | No | Yes |
| Submit a sitemap in Bing Webmaster Tools | No | Yes |
| Send an IndexNow request | Yes, one request per batch, with the owner's key; not yet tested | Gives the key and confirms each batch |
| Connect Google Business Profile | No | Yes, only if chosen |
| Build and edit pages | Yes, in the files or builder it can reach | |

## Layout

```text
skills/<name>/SKILL.md
```

Each `SKILL.md` has `name` and `description` in its frontmatter, then the instructions. Read the file in full before acting on it.

## Evidence

`docs/skill-review-2026-10-23.md` records the review of two external skill repos. It lists each factual claim, its source, and whether we adopted it. Nothing in the set has been tested on an agent or a live site yet. The test plan is in that file.

## Assumption to confirm

The skills use the same `SKILL.md` format as the other skills in the workspace. If Grok Bot loads a different format, the body is plain markdown and can move over unchanged.
