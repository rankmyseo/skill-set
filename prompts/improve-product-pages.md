# Improve product pages

Make the product and category pages that sell easier to find, and check that Google can read their price and stock. Skill: `seo-product-pages`.

## Workflow: Pick the products

### Step 1: Priority products

```text
My shop is [site]. My best sellers are [product 1], [product 2], [product 3] (or ask me for them).

1. Run site_pages and find the product and category pages, with the main keyword and how many keywords each ranks for.
2. Run page_updates and note product pages marked tune or expand.
3. Run search_console with days: 28 for product pages with impressions but few clicks.
4. Run keyword_planner for each best seller's product type and poll until ready.

Return one table: Product or category | Page | Main keyword | Volume | Position or "not ranking" | Signal | Priority (high, medium, low).
Sort best sellers first, then by volume. Show up to 15 rows.

Write "not reported" for missing numbers.
```

### Step 2: Marketplace search terms (optional, costs lookups)

```text
If the priority table from the previous step is in this conversation, use it. If not, run that step first.

I want to see what shoppers type on marketplaces for my top three products. Tell me how many everyday lookups this will spend and wait for my yes. Run social_lookups first and reuse saved answers.

After my yes, run social_research tool ideas on [shopee or blibli] with each product type as the query. It answers queued first; call again with the same arguments about a minute later. If a platform says it is under maintenance, it spent nothing; do not retry it.

Return one table: Product | Marketplace term | Also in keyword_planner (yes or no).
```

## Workflow: Fix the pages

### Step 1: Page checklist

```text
If the priority table is in this conversation, use it. If not, run "Priority products" first.

Open each high-priority product page and check:
- Title and H1 name the product and the attribute shoppers search for
- A description written for this product, not only the manufacturer's text
- Specs, price, and stock visible in the HTML
- Several images with descriptive file names and alt text
- Shipping and returns stated or linked
- Real reviews only
- Product markup with name, image, and an Offer with price above zero and currency, in the HTML the server sends

Return one table: Page | Check | Pass or fail | Fix.
Show failures first.
```

### Step 2: URLs for variants and filters

```text
For my shop [site], look at how variants (size, color) and filters (price, brand) change the URL.

Check against Google's guidance:
- Variants that should appear in search have their own URL, as a path or parameter, not a #fragment
- Parameters use ?key=value joined with &, no repeated keys, no session or tracking parameters in internal links
- Each indexable page has a canonical to itself; an optional parameter is left out of the canonical
- Filtered lists that do not need to show in search are blocked in robots.txt, with one unfiltered list left crawlable
- A filter combination or category with no products returns 404, or noindex for an empty category

Return one table: URL pattern | Example | Problem | Fix.
Do not change robots.txt or templates until I approve.
```
