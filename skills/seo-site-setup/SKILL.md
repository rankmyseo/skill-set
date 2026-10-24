---
name: seo-site-setup
description: Technical and on-page setup for a website that is being built or fixed. Covers rendering, HTML structure, on-page basics, link attributes, robots.txt and AI crawler choices, sitemap naming, llms.txt, structured data validation, speed, languages, and measurement. Use before a site goes live, or when the owner asks what is missing.
---

# SEO site setup

Goal: search engines and AI tools can read every public page, every page says what it is, the markup validates, and the owner can measure it from day one.

Acceptance: for any public page, the owner can see the title, description, one H1, canonical link, and main text in the raw HTML. The schema validates with no errors. robots.txt matches the owner's answers.

Make the changes yourself, in the files or builder you can reach. If you cannot reach the site, write each change out exactly (where it goes, the old value, the new value, and the reason) and give it to the owner. If you do not know the stack, ask once.

## 1. Address and URL form

- Pick one host, with `www` or without it. Redirect the other with a 301 (permanent) redirect.
- Use HTTPS only. Redirect HTTP to HTTPS.
- Pick one URL form, with or without a trailing slash. Redirect the other form to it. The same page must not answer 200 on both forms.
- Each page sets a canonical link that uses the chosen form.

## 2. Rendering: main text in the first HTML response

- Put each page's text, title, description, and links in the HTML the server sends. Use server-side rendering, static generation, or prerendering. Prefer this over client-side rendering, where the browser builds the page with JavaScript.
- Why: Google's crawler runs JavaScript. In published tests, several AI crawlers do not, so client-rendered text can be invisible to them.
- Test: `curl -s https://example.com/page | grep -i "a phrase from the main text"`. If the phrase is missing, the page depends on JavaScript. Fix that before launch.

## 3. HTML structure

- Set `lang` on the `html` element.
- One `h1` per page. Headings follow in order: h2 before h3, never skip a level.
- Use landmarks: `header`, `nav`, `main`, `article`, `section`, `aside`, `footer`.
- Buttons are `button` elements. Links are `a` elements with an `href`.
- Every form input has a label. Every informative image has alt text. Decorative images get empty alt.
- Include the viewport meta tag so the page works on phones.
- Use real tables for tables and real lists for lists.

## 3b. Accessible names and ARIA (WCAG, and what agents read)

Why this matters for search and AI: WCAG requires every control to have a programmatic name and role. Browser agents read the page's accessibility tree, which holds those names and roles, to find buttons, links, and fields. A control with no name is invisible to both assistive technology and agents.

- **Use native HTML first.** A `button` already has keyboard support, a role, and states. A `div` with `role="button"` needs all of that rebuilt by hand. The first rule of ARIA is to use a native element when one fits.
- **Button with visible text:** the text is the name. Nothing else is needed.
- **Icon-only button:** add `aria-label` that names the function ("Close", "Add to cart"). Set the icon's SVG to `aria-hidden="true"`.
- **Link:** the link text says where it goes. Avoid "read more" and "click here". An icon-only link gets an `aria-label`.
- **Form input:** a `label` element linked with `for` and `id`. Placeholder text is not a label.
- **Image:** informative images get alt text that describes them. Decorative images get empty alt.
- **Match visible text:** when a control shows visible text, its accessible name must contain that text, with the visible words first (WCAG 2.5.3, Label in Name). A visible "Search" button named "Find products" fails for voice users who say "Search".
- **Name the function, not the look.** Name an X icon "Close". Start action names with a verb ("Edit John Doe"). Do not repeat the role in the name, so no "button" or "link" in the text.
- **aria-labelledby or aria-label:** if the label text already appears on the page, point to it with `aria-labelledby`. Use `aria-label` only when no visible text exists. Do not use both on one element.
- **Do not put `aria-label` on elements that prohibit naming,** such as paragraphs, spans, and plain divs.
- **Custom widgets** (menus, tabs, accordions, dialogs) need the right role, plus states such as `aria-expanded`, `aria-controls`, and `aria-selected` that update as the widget changes. Keep focus visible, and keep every control usable by keyboard.
- **Do not hide usable controls.** Never put `aria-hidden="true"` on something a person or agent can focus or click.
- **Overlays:** a cookie banner or popup must not cover the controls underneath it.
- **Use ARIA sparingly.** Wrong ARIA can do more harm than none, and pages with more ARIA have tended to show more detected errors.
- **Check it:** open the browser's accessibility tree for each key page, and confirm every button, link, and field has a name. Then run a keyboard-only pass.

## 4. On-page basics

- **Title:** unique to the page, under 60 characters, main keyword near the start.
- **Description:** unique to the page, 140 to 160 characters, saying what the reader gets.
- **H1:** matches the page's intent in plain words.
- **First paragraph:** answers the search in two or three sentences.
- **Canonical link:** points to the page itself, in the chosen URL form.
- **Open Graph:** title, description, and an image of about 1200 by 630 pixels for sharing.
- **Link text:** describes the target, for example "cost of rank tracking", not "click here".

## 5. Link attributes

- Internal links: a plain `a` element with no `rel` attribute. Do not put `nofollow` on internal links.
- Paid or affiliate links: `rel="sponsored"`.
- User-generated links, such as comments and forum posts: `rel="ugc"`.
- Other links you do not want to endorse: `rel="nofollow"`.
- Google treats these values as hints, not commands. To keep a page out of Search, use `noindex`. To keep a crawler off a path on your own site, use robots.txt.
- Several values can be combined, for example `rel="sponsored ugc"`.

## 6. robots.txt and AI crawler choices

- Serve `/robots.txt` at the site root, as plain text, with a 200 status.
- Allow public pages for search crawlers. Do not block CSS or JavaScript files.
- Add a `Sitemap` line that points to the sitemap file.
- Keep staging, preview, and admin areas out of the sitemap, and add `noindex` or a password.

**Ask the owner these three questions before you write AI rules. Do not guess the answers:**

1. Do you want your pages to appear in AI search answers, where an assistant searches the web and cites sources? Blocking those crawlers removes you from those answers.
2. Do you allow AI companies to train their models on your content? Blocking training crawlers does not affect whether your pages appear in AI search answers.
3. Do you allow AI tools to read a page when a person asks about it?

Other facts that matter for the answers:
- Google-Extended is the robots.txt token for Gemini training and grounding. It does not affect Google Search. Blocking it does affect Gemini answers grounded in your content.
- Record the owner's answers as Content Signals in robots.txt when the owner wants that (`ai-train`, `search`, `ai-input`).
- Before writing bot-specific rules, check each vendor's current crawler documentation for the names. Do not guess them.

After any hosting or CDN change, open `/robots.txt` again. Some one-click settings add rules that block search crawlers by accident.

## 7. Sitemap

- The file name can differ from `sitemap.xml`. Any name works if robots.txt points to it with a `Sitemap` line.
- List only canonical, indexable URLs that return 200. Keep `lastmod` accurate.
- Make sure the XML parses.
- Submit it in Search Console. Bing does not index a sitemap URL that only redirects.

## 8. llms.txt (optional, with an honest label)

- Put a file named `llms.txt` at the site root. Include a short summary of what the site is, who it serves, and links to the key pages, including pricing.
- Be precise about what it does. It is valid for some uses: developer tools and coding agents that read it when pointed at it, and Lighthouse's experimental agent audit that checks for it. Google Search does not use it, and Google's guide says it is not needed for Google's AI features. No major AI vendor has documented reading other sites' `llms.txt` files.
- Add it when the owner wants agent discovery, and say that is the reason. Do not promise rankings or AI citations from it.
- If the reference scan in section 14 marks it as missing, explain that it is an agent-discovery check, not a Google check.

## 9. Structured data (JSON-LD), validated

- Use JSON-LD. Mark up only what is visible on the page.
- Homepage: Organization and WebSite. Inner pages: BreadcrumbList. Posts: Article. Local business: LocalBusiness with a real address.
- Do not add FAQPage or HowTo for a search appearance. Google no longer shows those rich results. Structured data is not required for Google's AI features.
- Validate every template. Use the Schema.org validator for syntax and vocabulary. Use Google's Rich Results Test for the features Google still supports. The target is zero errors. Review warnings; do not ignore them.
- Validate again after every change to a template or a CMS plugin.
- A plain fetch can miss JSON-LD that JavaScript injects. Check the rendered page or validate the live URL.

## 10. Speed

- PageSpeed Insights shows a lab score (a simulated test) and field data (real visits). Use the lab score to find what to fix. Measure the result with field data.
- Field targets at the 75th percentile, on mobile and desktop: LCP 2.5 seconds or less, INP 200 milliseconds or less, CLS 0.1 or less.
- Google says chasing a perfect PageSpeed score for SEO may not be the best use of time. Start with the big items: image size and format, font loading, scripts that block rendering, and large JavaScript bundles.
- After launch, read the Core Web Vitals report in Search Console.

## 11. Images and media

- Compress images. Set width and height so the layout does not jump while the page loads.
- Lazy-load images below the fold. Do not lazy-load the hero image.

## 12. Languages

- One language per URL. Each language gets its own page. Research each language's keywords on its own.
- If you use hreflang: each version lists itself and its matches, the links are reciprocal, every target returns 200, and the codes are valid (`en-GB`, not `en-UK`).

## 13. Measurement, before launch

- **Search Console:** verify the domain with a DNS TXT record if the owner can edit DNS. It survives redesigns. Submit the sitemap. The Generative AI performance report appears once the site has enough AI impressions.
- **Search generative AI control:** confirm it is set to include the site.
- **GA4:** one tag on every page. Cookie consent can lower the counts, so tell the owner.
- **Conversions:** once the owner defines what counts as a lead, set up the key events with `seo-conversion-tracking`.
- **RankMySEO (recommended, not required):** `add_project` and `add_keyword` after the owner's yes. Search Console and GA4 can be connected in the dashboard or read directly.

## 14. Reference scan, after the build

- Scan the site at isitagentready.com. It scores robots.txt, the sitemap, AI bot rules, Content Signals, llms.txt, markdown negotiation, and other agent standards.
- Report the failing checks, in priority order. Fix only what the owner approves.
- Also run Lighthouse's Agentic Browsing category, available in Chrome 150 and later. It checks that every interactive element has an accessible name, that the accessibility tree is well formed, and that layout is stable. The category is informational for now, so report its results without a score.
- A failing check on llms.txt or on agent protocols does not mean a Google problem. Say so.

## Report back

List what is done, what is not, and what the owner must do personally (DNS, consent banner, builder settings, and the AI crawler answers). Label each item:

- **verified:** you checked the live page or file yourself
- **implemented but unverified:** the change is made but not live yet
- **blocked:** needs the owner's access or a decision, and you name it
