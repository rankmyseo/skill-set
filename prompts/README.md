# Prompt library

Copy-paste prompts for any AI assistant connected to the RankMySEO MCP server, such as ChatGPT, Claude, Cursor, or Grok. Use them when you cannot install the skills. With the skills installed, type the `/seo` command instead; it runs the same workflow with more checks.

Each use case is a file. Each file has one or more workflows, and each workflow is a few prompts you run in order. Replace the words in square brackets, such as `[site]` and `[keyword]`, before you send a prompt.

## How the prompts behave

- **They name the tools.** Every prompt says which RankMySEO tools to call, so the assistant does not guess.
- **They name the output.** Every prompt asks for one table with set columns, a sort order, and a row limit.
- **They chain.** A later step says: if the earlier step's table is already in this conversation, use it; if not, run that step first. You can start at any step.
- **They read before they write.** No prompt adds a keyword, a rival, or a site, queues a rank check, or spends social lookups without asking you first.
- **They do not guess.** A number the tools do not return is written as "not reported", never estimated.
- **Thresholds are working rules.** Where a prompt uses a cut-off, such as positions 4 to 20, it is a starting point you can change, not a measured rule.

Most prompts need the Starter plan or above. Ask the assistant to run `account_status` if a tool refuses; it says what the plan includes and when the next window opens.

## Use cases

| Use case | Workflows | Skill |
| --- | --- | --- |
| [Map your market](map-your-market.md) | Find your search rivals · Size the demand | `seo-competitors`, `seo-keyword-selection` |
| [Spot demand trends](spot-demand-trends.md) | Rising and falling searches · Seasonal calendar | `seo-trends` |
| [Close keyword and content gaps](close-gaps.md) | Keyword gaps · Content gaps | `seo-competitors` |
| [Monitor competitors](monitor-competitors.md) | Monthly watch · Read a rival's ads | `seo-competitors` |
| [Capture quick wins](capture-quick-wins.md) | Find quick wins · Plan a two-week sprint · Measure the sprint | `seo-quick-wins` |
| [Refresh and clean up pages](refresh-and-clean-up.md) | Refresh slipping pages · Pages that earn nothing | `seo-content-refresh` |
| [Write briefs that fit the results](write-briefs.md) | Brief a new page | `seo-page-brief` |
| [Diagnose a traffic drop](diagnose-a-drop.md) | Find where it fell · Find why | `seo-maintenance-loop` |
| [Improve product pages](improve-product-pages.md) | Pick the products · Fix the pages | `seo-product-pages` |
| [Build a 90-day roadmap](build-a-roadmap.md) | Gather, prioritize, and plan | `seo-roadmap` |
| [Report to a manager or client](report-to-a-manager.md) | Executive summary · Decision memo | `seo-reporting` |

## Not covered

Paid search cost, bids, and budget split between paid and organic need ad account data these tools do not have. The rival ads prompt shows which ads a rival runs, not what they pay.
