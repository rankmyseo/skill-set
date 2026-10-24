---
name: seo-indexing
description: Hand off a finished batch of new or changed pages for indexing. Runs pre-submission checks, asks the owner which submissions they want the agent to make, gives the owner exact steps for Google Search Console and Bing Webmaster Tools, records what was submitted, and sets check-back dates. Use when a finished batch of new or changed pages is ready to submit, or when new pages are not showing in search.
---

# SEO indexing handoff

Goal: every new public page is submitted once, in the right places, with the owner knowing exactly what was done. Status is then checked on set dates, not resubmitted in a loop.

Acceptance: the owner can see which URLs went to which service, who submitted them, when, and what to check on each date.

Start only when the owner says the batch is live. Submitting a page that is not ready wastes the request.

## 1. Pre-submission checks (you run these)

For every URL in the batch:

- Returns 200. No redirect chain, no 404.
- Indexable: no `noindex`, and the canonical link points to the page itself, in the chosen URL form.
- Listed in the sitemap, with an accurate `lastmod`.
- Linked from at least one indexed page, such as the homepage or a hub. A page with no links is hard to find.
- Allowed by robots.txt for search crawlers.
- Schema validates with zero errors, and every control has an accessible name (see `seo-site-setup`).

If a URL fails a check, fix it or pull it from the batch, and tell the owner before you go on.

## 2. Prepare the batch

- Write one batch file: the URLs, the sitemap location, and the date.
- Update the sitemap once for the batch. Keep the same file name. Do not resubmit an unchanged file.

## 3. Check what you can do

Checked on 24 October 2026 against the tools connected to this session:

| Step | Can the agent do it? | Who does it |
| --- | --- | --- |
| Google Search Console: submit the sitemap | No. No connected tool writes to Search Console. RankMySEO's `search_console` reads only | Owner |
| Google Search Console: Request indexing | No. Same reason | Owner |
| Bing Webmaster Tools: submit the sitemap | No. No Bing tool is connected | Owner |
| IndexNow: send the batch URLs | Yes, per batch. The agent sends the HTTP request from a shell with the owner's key, after the key file check. The owner approved this. Not yet tested | Agent, with a yes, or owner |
| Google Business Profile | No | Owner, only if they choose it |

If the capability list changes, re-check it before you tell the owner what you can do.

## 4. Ask the owner

Ask up to two questions at a time:

1. **Who submits?** The owner has approved IndexNow from the agent, one request per batch. For each batch, ask: "Shall I send the IndexNow request for this batch?" Google Search Console and Bing submissions stay with the owner. Do nothing without a yes for the batch.
2. **Google Business Profile:** only if the business has a physical place customers visit. Ask: "Do you want Google Business Profile connected?" Do not push it for online-only businesses. The agent cannot connect it, so the owner does it and you give the steps.

If the owner says yes for this batch:
- Check that the key file loads at the site root, at `/{key}.txt`, before you send anything.
- Send the batch URLs in one request to a participating endpoint. One request reaches Bing, Yandex, Seznam, Naver, Yep, the Internet Archive, and Amazonbot. Google does not take part in IndexNow, so this does nothing for Google.
- Record the response code, and tell the owner it means the request was received, not that pages were indexed.

## 5. Owner steps (for anything the owner does)

**Google Search Console**
1. Confirm the property is verified. A domain property is preferred.
2. In the Sitemaps report, submit the sitemap once for the batch. This needs owner permission on the property. Without it, the `Sitemap:` line in robots.txt is the fallback.
3. In URL Inspection, inspect the homepage and the five to ten most important new pages, then click Request indexing. Do not request every page. Google does not publish the daily limit, and a request does not guarantee indexing.

**Bing Webmaster Tools**
1. Add and verify the site.
2. Submit the sitemap.

**Google Business Profile (only if chosen)**
1. Claim or update the profile, with the address, hours, and categories.

**Do not use:**
- The Google Indexing API for these pages. Google restricts it to job postings and livestream pages.
- Any service that promises guaranteed indexing. No service can promise it.

## 6. Record the submission

In the plan file, record:
- The date and the batch URLs
- The sitemap location
- Who submitted each item (owner or agent) and where: Google, Bing, or IndexNow
- The check-back dates: day 3, day 7, and day 21

You cannot keep a clock. Put the check-back dates in the plan file and in the owner's calendar. If the platform runs scheduled maintenance, add them there too.

## 7. Check back on schedule

- **Day 3:** check URL Inspection for each priority URL. Note what Search Console reports for each one.
- **Day 7:** Google advises waiting at least a week before assuming a problem. Check the Sitemaps report status and Bing's index status.
- **Day 21:** if pages are still not indexed, use the checks in `seo-go-live-check` for the waiting and broken states. Look at content, internal links, duplicate pages, and blocked crawling. Do not resubmit the same URLs in a loop.

Google says indexing takes a day or two to a few weeks for a new page. Give the owner that range. Do not promise a date.

## 8. Do not

- Resubmit an unchanged sitemap several times a day.
- Submit pages that are noindex, redirected, or returning errors.
- Tell the owner a page will be indexed on a given day.
- Submit a page to the Indexing API.

## Message to the owner

Use this when the batch is ready:

> Your batch is ready: [N] pages. Please do these:
> 1. Submit the sitemap in Google Search Console (Sitemaps report).
> 2. Request indexing for the homepage and the top [5 to 10] pages in URL Inspection.
> 3. Submit the sitemap in Bing Webmaster Tools.
>
> Two questions: do you want me to send the IndexNow request for you? And do you want Google Business Profile connected? If it is a physical place, I'll give you those steps too.
>
> Reply with the date you did each step. I'll note the check-back dates.

## Report back

List what was submitted, by whom, where, when, and the next check date. Label each item:

- **verified:** you checked its status yourself
- **implemented but unverified:** submitted, not yet checked
- **blocked:** needs the owner's access or a decision, and you name it
