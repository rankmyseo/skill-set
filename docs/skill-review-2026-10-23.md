# SEO and AEO skill review, 23 October 2026

## Scope

| Repo | Commit | What was read |
| --- | --- | --- |
| `coreyhaines31/marketingskills` | `e85f3cb`, 19 Oct 2026 | `ai-seo`, `seo-audit`, `schema`, `site-architecture`, `programmatic-seo`, `link-building`, their evals, the CI workflows |
| `pawbytes/skill-suites` | `547a6df`, 3 Oct 2026 | `paw-mkt-seo` and its references |

Method: read each skill, checked its factual claims against primary sources (Google documentation and changelog, Google's Search Console help, the original paper), and checked whether the repo holds evidence that the skill changes outcomes.

## Verdict

- Both repos are useful checklists. Neither shows that its advice changes outcomes.
- `marketingskills` ships `evals/evals.json` for each skill. These are prompts with expected behaviour, not recorded runs. Its CI regression job tests the skill validator, not the advice.
- `ai-seo` has factual errors. Do not import it wholesale.
- `paw-mkt-seo` tells the agent to promote a paid store in its first reply of each session. We do not copy that. The `marketingskills` README also carries partner promotions. We do not copy those either.

## Claim check

| # | Claim | Source | Check | Verdict |
| --- | --- | --- | --- | --- |
| 1 | FAQ rich results stopped on 7 May 2026, and the FAQPage documentation was removed on 15 June 2026 | `schema` | Google changelog entries of 8 May and 15 June 2026, reported by Search Engine Journal and Search Engine Land | Verified |
| 2 | HowTo rich results ended in 2023 | `schema` | Google Search Central blog, 8 Aug 2023, desktop removal on 13 Sept 2023 | Verified |
| 3 | Google's AI features need no special markup, Markdown, or `llms.txt` | `ai-seo` | Google's guide to generative AI features, last updated 10 July 2026 | Verified |
| 4 | Google Search ignores `llms.txt`. Keeping one neither helps nor hurts Google | `ai-seo` | Google's guide and the 15 June 2026 clarification | Verified |
| 5 | ChatGPT, Claude, and Perplexity "parse `llms.txt` when present" | `ai-seo` | No vendor documents reading other sites' `llms.txt`. An independent log study of 83 sites over 12 weeks found 7 OpenAI fetches and 0 Perplexity fetches | Contradicted |
| 6 | Search Console has no AI-specific reporting | `ai-seo` | Search Console's Generative AI performance report rolled out worldwide on 31 Aug 2026. It shows impressions in AI Overviews and AI Mode by page, country, device, and date, with no clicks | Contradicted |
| 7 | Search Console has a "Search generative AI" control that can exclude a site | Neither repo | Search Console help, "Search generative AI control" | Found, adopted |
| 8 | Google-Extended does not affect Google Search inclusion or ranking | `seo-audit`, `ai-seo` | Google's crawler documentation and the Gemini/Vertex user agent update | Verified |
| 9 | Core Web Vitals: LCP 2.5 s or less, INP 200 ms or less, CLS 0.1 or less, at the 75th percentile | `seo-audit` | web.dev threshold definitions, Search Console Core Web Vitals help | Verified |
| 10 | Princeton GEO study: per-method gains (cite sources +40%, statistics +37%, quotations +30%, authoritative +25%, clarity +20%, keyword stuffing -10%) | `ai-seo` | The paper (KDD 2024) reports absolute scores in Table 1 and says the best methods gained up to about 40% in its simulator. Authoritative tone showed no significant gain. The 37% is a Perplexity subjective score for statistics. The -10% for keyword stuffing is the Perplexity result. The table's per-method percentages are not in the paper | Partly wrong |
| 11 | Citing sources can hurt top-ranked sites | GEO paper | Cite Sources lowered the top-ranked site's visibility by 30.3% on average in the simulator and raised rank-5 sites by 115.1% | Verified, and it undercuts a blanket "cite sources" rule |
| 12 | ChatGPT 5.6 "demoted" listicles (-50.5%) and comparison pages (-32.1%) | `ai-seo`, `paw-mkt-seo` | One vendor's before-and-after share analysis, posted on LinkedIn. Share, not count. The pool of cited sources roughly doubled in the same period. Not reproduced by anyone else. A second, separate dataset shows the same fan-out shift | Unverified, single source. Do not use the percentages |
| 13 | AI Overviews appear on about 48% of queries (BrightEdge, Feb 2026) | `ai-seo` | Not checked. Third-party vendor figure | Do not use |
| 14 | Company sites take 57% of AI citations (Profound, July 2026) | `ai-seo` | Not checked. Vendor figure | Do not use |
| 15 | Single-page-per-keyword is less effective than covering a topical cluster | `ai-seo` | No source given. Conflicts with our locked rule that one page owns one keyword cluster (`SEO-PAGE-MAP`) | Do not adopt |
| 16 | `web_fetch` and `curl` cannot see JavaScript-injected JSON-LD | `seo-audit` | Plausible and consistent with how CMS plugins inject schema. Not tested here | Adopted as a caution |
| 17 | hreflang: self-reference, reciprocal links, valid codes, every target returns 200 | `seo-audit` | Consistent with Google's localized-versions guidance, which the skill cites. Not re-read in this pass | Adopted; re-check before shipping |
| 18 | Title 50-60 characters, description 150-160 | `seo-audit` | Our house rule is a title under 60 and a description of 140-160. Google truncates by pixel width | Keep our rule |
| 19 | Evals prove the skills work | `marketingskills` | Evals are expected-behaviour rubrics. The CI regression job checks the validator with fixtures. No recorded agent output in the repo | Not evidence |

## What we adopted

Each change is one of the verified items above, written in our own words.

- `seo-site-setup`: crawler access decided by purpose; Google-Extended scope; FAQ and HowTo retirement; Core Web Vitals targets; rendered markup caution; hreflang checks; a new section on Search generative AI control and optional `llms.txt`.
- `seo-go-live-check`: check that the Search generative AI control is not set to exclude.
- `seo-search-data`: the Generative AI performance report, with its limits (impressions only, and part of the overall performance data).
- `seo-page-rewrite`: write for people, sourced numbers with dates, no AI-only copy, no keyword stuffing.
- `seo-maintenance-loop`: a sampled check of AI answers (10 to 20 prompts, 3 to 5 runs each, report the rate with its sample size), with `track_ai` for Agency and Scale.
- `seo-launch-plan`: URL and structure rules (subfolders, readable slugs, breadcrumbs that match the URL, no orphan pages, 301 redirects on change).

## What we did not adopt

- Per-method GEO percentages (claim 10), the listicle drop as a fact (claim 12), and vendor statistics (claims 13 and 14).
- Any claim that `llms.txt` helps citations (claim 5).
- Single-page-per-keyword is weaker (claim 15).
- Partner promotions, the paid-store prompt in `paw-mkt-seo`, and vendor names in customer-facing text.

## Evidence status

Nothing in this review shows that the skills change outcomes. Every adopted rule is either a verified platform rule or a conservative practice. None of it has been tested on an agent or a live site.

## Proposed test plan (not run)

1. Scenario tests: 10 owner scenarios (new site with no keywords, guest session, plan refusal, request to publish, request for FAQ markup, request for `llms.txt`, and others). Use the RankMySEO response shapes captured on 23 Oct 2026. Grade each run against a written rubric, three runs per scenario.
2. Outcome tests: slow and noisy. For a real site, log each rewrite with its date, then compare Search Console impressions and clicks for that page over four weeks before and after. One site with no control is an anecdote, so label it that way.
3. Decide the pass criteria before running anything.

## Round 2: build-time checks (23 Oct 2026, second pass)

| # | Claim | Check | Verdict |
| --- | --- | --- | --- |
| R2-1 | Google reads `llms.txt` for AI Overviews | Google's guide (updated 10 July 2026), its 15 June 2026 clarification, and the Search docs say Search does not use it. Googlebot fetches the file sometimes, and fetching is not using it. Lighthouse 13.3 has an experimental audit that checks llms.txt and calls it optional | Not supported. The owner was asked for a source |
| R2-2 | isitagentready.com checks robots.txt, sitemap, AI bot rules, Content Signals, llms.txt, and markdown negotiation | The scanner's own documentation | Verified |
| R2-3 | A `Sitemap:` line in robots.txt satisfies the sitemap check, so the file name can differ | The scanner's sitemap check | Verified |
| R2-4 | Blocking search-type AI crawlers removes a site from AI answers, and blocking training crawlers does not | The scanner's fix text. Consistent with the vendor-neutral split in R1 | Verified against the scanner's documentation |
| R2-5 | Google-Extended covers Gemini training and grounding, not Search | Google's Gemini and Vertex update | Verified |
| R2-6 | nofollow, sponsored, and ugc are hints. Internal links should not be nofollow. Use robots `disallow` or `noindex` for internal control | Google's link qualification documentation and 2019 blog | Verified |
| R2-7 | Major AI crawlers do not run JavaScript, so client-rendered text is invisible to them | A December 2024 crawler analysis, a 41-day controlled test where only Googlebot executed injected links, and a 2026 retest of ChatGPT, Claude, and Perplexity. One log study shows requests, not execution. Googlebot renders | Verified as of October 2026. Crawler behaviour can change; re-test |
| R2-8 | PageSpeed score is a lab score. Ranking uses field Core Web Vitals at the 75th percentile. Google says chasing a perfect score for SEO may not be the best use of time | PageSpeed Insights documentation, Search Central page experience update | Verified |
| R2-9 | Schema validation with the Schema.org validator and Google's Rich Results Test | The schema skill in the marketing repo lists both. Not re-checked live in this pass | Adopted; confirm the tools before the first run |
| R2-10 | HTML5 landmarks, one H1, `lang`, alt text, labels, viewport, and link text | Standard web practice. Not separately sourced | Adopted as practice |

## Round 3: accessibility names, ARIA, and agent reading (23 Oct 2026, third pass)

| # | Claim | Check | Verdict |
| --- | --- | --- | --- |
| R3-1 | Every UI control needs a programmatic name and role (WCAG 4.1.2, Level A) | W3C WCAG 2.2 and Understanding 4.1.2 | Verified |
| R3-2 | A control with visible text must contain that text in its accessible name (WCAG 2.5.3, Label in Name) | W3C Understanding 2.5.3 | Verified |
| R3-3 | Link purpose must be clear from the link text or its context (WCAG 2.4.4, Level A) | W3C WCAG 2.2 | Verified |
| R3-4 | Browser agents read the accessibility tree as their main structured model, and every interactive element needs a programmatic name | Chrome for Developers (Lighthouse Agentic Browsing, M150) and web.dev, which says agents also use screenshots and raw HTML | Verified. Agent behaviour may change; the source is Google's own guidance |
| R3-5 | Native HTML first; ARIA is a repair, not a default | MDN and web.dev ("first rule of ARIA") | Verified |
| R3-6 | Pages with ARIA show more detected errors than pages without it | The WebAIM study is quoted with different numbers (41% in MDN, 70% in web.dev). The skill uses no percentage | Direction verified; no figure quoted |
| R3-7 | `aria-label` names an element only where no visible label exists; use `aria-labelledby` when text is on the page; do not put it on roles that prohibit naming | W3C APG and MDN | Verified |
| R3-8 | Lighthouse Agentic Browsing is informational and unscored | Chrome for Developers blog | Verified. The skill reports it without a score |

## Round 4: indexing after the build (23 Oct 2026, fourth pass)

| # | Claim | Check | Verdict |
| --- | --- | --- | --- |
| R4-1 | The Indexing API works for ordinary pages | Google's Indexing API documentation: only JobPosting and BroadcastEvent in VideoObject | Contradicted. Not used |
| R4-2 | URL Inspection "Request indexing" has a daily limit and does not guarantee indexing | Search Console help, URL Inspection tool | Verified. The limit is not published |
| R4-3 | Google fetches a submitted sitemap at once, but crawls its URLs later and not all of them | Search Console Sitemaps report help and the troubleshooting guide | Verified |
| R4-4 | Expect indexing in a day or two to a few weeks; allow at least a week before assuming a problem | Search Console "Why is my page missing" help; troubleshooting guide says three days or more for most sites | Verified |
| R4-5 | Do not resubmit an unchanged sitemap several times a day; use accurate `lastmod` | Troubleshooting guide, "Avoid" list | Verified |
| R4-6 | IndexNow participants: Bing, Yandex, Seznam, Naver, Yep, Internet Archive, Amazonbot. Google is not one | The IndexNow registry file, read on 17 Oct 2026 by one third-party write-up, and two other guides | Verified against the registry as read. Re-check before the first run, since the list changes |
| R4-7 | A Bing sitemap submission in Bing Webmaster Tools | Not checked in this pass | Adopted; confirm in the Bing interface |
| R4-8 | Sitemap submission in Search Console needs owner permission; without it, list the sitemap in robots.txt | Search Console Sitemaps report help | Verified |

## Capability check (24 Oct 2026)

Searched the tools connected to this session for Search Console, Bing, IndexNow, Google Business Profile, and Analytics.

- RankMySEO `search_console` and `analytics_pages`: read only.
- No connected tool writes to Search Console, Bing Webmaster Tools, or Google Business Profile.
- The Google Drive connector needs authentication, and it does not cover these tasks.
- IndexNow needs no connector. It is an HTTP request, so the agent could send it from a shell with the owner's key. Not yet tested.

## Round 5: gaps built (24 Oct 2026, fifth pass)

| # | Claim | Check | Verdict |
| --- | --- | --- | --- |
| R5-1 | GA4 renamed conversions to key events | Google Analytics help, "Conversions vs. key events" | Verified |
| R5-2 | Up to 30 key events on a standard property | Google Analytics help, "Mark events as key events" | Verified |
| R5-3 | A key event counts from the day it is marked, not backwards | Google Analytics help synthesis, and the "mark events" article | Verified |
| R5-4 | No personal data in event parameters, custom dimensions, or URLs; web-stream data redaction covers only email addresses and some query parameters | Google Analytics PII best practices and data redaction help | Verified |
| R5-5 | RankMySEO's `search_console` returns queries and pages separately, so query-to-page pairs cannot be read from it | Read the response shape on 23 Oct 2026 | Verified. The skill uses a heuristic and names the direct-connector check |
| R5-6 | Search Console's Change of Address tool is used for domain moves | Google Search Central updates, June 2026 entries | Verified |
| R5-7 | Redirect chains and 301 mapping | Standard practice | Adopted as practice |

## Decisions log

| Date | Decision | Owner's words | Where it lives |
| --- | --- | --- | --- |
| 23 Oct 2026 | Social research allowed in the launch plan, for the platforms the owner uses | "yes you may use social research for social media" | `seo-launch-plan`, step 4b |
| 23 Oct 2026 | The owner submits sitemaps and indexing requests | "the one who submit is the user" | `seo-indexing` |
| 24 Oct 2026 | Weekly review and monthly summary by default; daily digest only with GA4 or Search Console connected | "a daily report ... if the user website connect to Google Analytics or sort of the thing" | `seo-maintenance-loop`, `rankmyseo-seo-agent` |
| 24 Oct 2026 | Business Profile asked at intake, only for a physical place | "online or physical location business not really required" | `seo-launch-plan`, question 8 |
| 24 Oct 2026 | llms.txt is valid for some uses (developer tools and coding agents that read it when pointed at it); not used by Google Search; stays optional | "llms.txt is valid for some issue" | `seo-site-setup`, section 8 |
| 24 Oct 2026 | IndexNow sent by the agent, one request per batch, with the owner's key, after the key file check and the owner's confirmation | "yes you can send it" | `seo-indexing`, `README` |
| 24 Oct 2026 | Daily digest threshold: open. Alerts stay off until the owner sets one | "ok", read as acknowledgement only | `seo-maintenance-loop` |
| 24 Oct 2026 | Scenario tests: awaiting approval of the ten scenarios | "ok", read as acknowledgement only | Canvas `seo-agent-skills-overview` |
| 24 Oct 2026 | Keep the three-spoke rule for a hub, as a working rule | "keep it" | `seo-launch-plan`, page classification |
| 24 Oct 2026 | The agent may ask one or two questions at a time, not only one | "1-2 question to a user still okay" | `seo-launch-plan` intake, `seo-indexing` |
| 24 Oct 2026 | Manipulation policy not built. The off-site prompt (ready-to-send Reddit replies, review-site pitches, listicle outreach) is rejected as written | "then it's not worth it" | Review file, Round 6 notes |

## Attribution

`marketingskills` is MIT licensed, copyright Corey Haines (2025). `skill-suites` is MIT licensed, copyright PawBytes (2026). We wrote our own text from the verified facts above. We did not copy passages.
