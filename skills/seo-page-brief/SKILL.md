---
name: seo-page-brief
description: Write a content brief for one new page before it is drafted, and collect the facts the owner must supply first (prices, team, proof, hours, location, and similar). Checks what ranks now, then sets reader, intent, angle, outline, schema type, links, and call to action. Use before writing any new page from zero.
---

# Page brief

Goal: the writer knows what the page must do, what it must say, and which facts are still missing, before a single sentence is drafted.

Acceptance: the owner can read the brief and see the reader, the job, the outline, the facts they owe, and the next action on the page.

Write a brief for each page in the page map. A brief is one file. Do not write the page until the owner has answered the facts questions that block it.

## 1. Identify the page

- **Page type:** money, tool, hub, or informational. Take it from the page map.
- **Owner keyword:** the primary keyword, with its validation status from `seo-keyword-selection`.
- **Alternates:** the two or three supporting phrases this page may use naturally.
- **Reader:** one sentence. Who lands here, and what do they want to know?
- **Next action:** one action the reader can take on this page. For a money page, it is the offer. For an informational page, it is the link to the money page or the tool.

## 2. Set the intent

State the question the page answers in the first screen. Then list the questions the reader will ask next, in the order they will ask them. Use this list to build the outline.

## 2b. Check what ranks now

Look at the pages that rank for the owner keyword before you set the outline. Search for it if you can browse; otherwise ask the owner to paste the top results. For a tracked keyword, `rank_compare` shows where saved rivals sit.

Note, for the top five results:

- **Format:** guide, list, comparison, product or category page, tool, local page, or video.
- **What they all cover:** the sections a reader expects to find.
- **What none of them has:** the first-hand detail, price, case, or local knowledge the owner can add.

Match the format searchers get today; a guide rarely ranks where the results are all product pages. Earn the place with the owner's facts, not by copying or rewording the rivals. Google asks for original value beyond what other pages say.

If the results show no clear format, or no rival you can read, say so in the brief.

## 3. Set the outline

- One H1, matching the intent in plain words.
- H2 sections, each answering one of the questions from step 2.
- For a hub: one short section per subtopic that answers it in brief and links to the page that owns it. Write to the answer, not to a word count; Google has none.
- For a money page: the offer, the proof, the price or the way to start, and the answers to objections, in that order.
- For a tool page: what the tool returns, its limit, and the link to the money page.

## 4. Set the links

- Links in: the pages that should link here, from the page map.
- Links out: the owner page for each related topic, and the next step for the reader.
- Anchor text describes the target, not "click here".

## 5. Set the structured data

Choose one schema type that matches the visible content. Use the rules in `seo-site-setup`. Do not add FAQPage or HowTo for a search appearance.

## 6. Set the call to action

One primary action per page. Name it, say where it sits, and say what the reader gets. The first screen shows it on money pages.

## 7. List the owner facts

Facts the page needs that the agent cannot know. Ask for them in one or two questions at a time, using the owner's own words. Mark each one as required or optional.

Common ones:
- Offer, with what is included and what is not
- Price, or how a price is set, and what is shown publicly
- Who runs the business, and the credentials that matter
- The byline: the real person who wrote or checked the page, or the business name if there is none
- First-hand detail: what the owner did, tested, or saw, and photos of it
- Proof: real customers, results, or reviews the owner is allowed to show
- Location, service area, opening hours, and contact method
- Legal details the owner must show, such as company name and address
- The date the page was last reviewed

Never invent these. Leave a bracketed placeholder, and mark the page as blocked until the required facts arrive.

## 8. Record the brief

Save it with the page map. The brief includes: the page type, the owner keyword, the reader, the intent, what ranks now and the angle, the outline, the links, the schema type, the call to action, the owner facts, and their status (answered, pending, or blocked).

## Hand off

When the brief is complete and the required facts are in, pass it to `seo-page-rewrite` for the draft. The draft follows the brief. Any claim that is not in the brief or in the owner's answers is removed.

## Do not

- Start a draft while a required fact is pending.
- Add a proof point, a price, or a credential the owner has not confirmed.
- Give a page more than one owner keyword.
- Add an outline section that does not answer a reader question.
