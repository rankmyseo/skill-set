---
name: seo-product-pages
description: Make product and category pages for an online shop easy to find in Google. Checks demand for each product, how rival product pages look, the page content, URLs for variants and filters, Product markup, and the Merchant Center feed. Use for any site that sells products online, before launch or when product pages get little traffic.
---

# Product and category pages

Goal: each product and category page answers what a shopper searches for, Google can read the price and stock, and variants and filters do not create a pile of duplicate URLs.

Acceptance: the priority products each have a target keyword, a page that passes the checklist, valid Product markup, and a note on whether they are in a Merchant Center feed.

## 1. Pick the products to work on

Start with what sells, not with the whole catalog. Ask the owner for the top products and categories by revenue or margin.

Then add search data:

- `site_pages`: product and category pages with the biggest keyword each ranks for and how many keywords it ranks for.
- `page_updates`: product pages marked `tune` or `expand` are the closest to more clicks.
- `search_console` with `days: 28`: product pages with impressions but few clicks.
- `keyword_planner` on product names and types: volume and difficulty.

Optional, costs everyday lookups: `social_research` tool `ideas` on `shopee` or `blibli` shows what shoppers type on those marketplaces, and tool `products` shows what is listed there. Ask the owner first, and run `social_lookups` first to reuse saved answers. A platform marked under maintenance answers at once and spends nothing.

| Product or category | Page | Keyword | Volume | Now | Revenue rank | Priority |
| --- | --- | --- | --- | --- | --- | --- |

## 2. Look at what ranks

For the top keywords, look at the pages that rank: product pages, category pages, or guides. If the results are mostly guides, a product page alone will struggle; plan a guide that links to it (`seo-page-brief`).

Note what the ranking product pages show that the site's page does not: sizes, materials, delivery times, return terms, photos from several angles, real reviews.

## 3. Product page checklist

- **Title and H1:** the product name plus the attribute shoppers search for (type, size, model). Write them with `seo-page-rewrite`.
- **Description:** written for this product, from the owner's facts. When many shops carry the same manufacturer text, Google shows one version of the duplicates; text only this shop has gives the page its own reason to show.
- **Specs:** a plain list of the facts a shopper compares.
- **Price and stock:** visible in the page's HTML, and the same as in the markup.
- **Images:** several, with descriptive file names and alt text (`seo-site-setup` section 11).
- **Shipping and returns:** stated on the page or linked plainly.
- **Reviews:** only real reviews from customers. Never write or buy them.
- **Links:** to the category, and to related products, with `<a href>` links and plain anchor text.

## 4. Category page checklist

- A short intro written for shoppers, above or below the products. Keep the products on the first screen.
- Products linked with `<a href>` links Google can follow, not only by script.
- Pagination with a unique URL per page.
- An empty category gets `noindex` or a 404 until it has products.

## 5. Variants, filters, and URLs

These rules come from Google's ecommerce URL and faceted navigation guidance:

- Words in the path that describe the product or category.
- Each variant that should appear in search gets its own URL, as a path or a parameter. Do not use a `#fragment` for a variant; Google does not index fragments.
- Parameters use `?key=value`, with no repeated keys.
- No session or tracking parameters in internal links.
- Each indexable page has a canonical to itself. A variant page whose only difference is an optional parameter points its canonical at the URL without it.
- Filters and sorting can make an endless number of URLs. Google's faceted navigation guidance: if filtered lists do not need to show in search, block their parameters in robots.txt and keep the product pages plus one unfiltered list crawlable. Filters held in a `#fragment` have no effect on crawling.
- Filtered lists that should show in search (a few that match real searches) use `&` between parameters, keep filters in the same order in a path, and return a 404 when a combination has no products.

## 6. Product markup

Use the rules in `seo-site-setup` section 9. For a page where the shopper can buy:

- Required: `name`, `image`, and `offers` with an `Offer` that has `price` (more than zero) and `priceCurrency`.
- Recommended: `availability`, a return policy, and shipping details. A shop-wide return and shipping policy can sit on the `Organization` markup instead of every product.
- Put the markup in the HTML the server sends, not only after scripts run.
- Ratings in the markup only when real reviews show on the page.

Validate with Google's Rich Results Test. Search Console reports merchant listing and product snippet problems under Shopping once Google has crawled the pages.

## 7. Merchant Center (owner step)

Structured data helps Google read product pages, but Merchant Center is required to appear in the Google Shopping tab. It also gives more control over when price and stock changes reach Google.

- A small shop that changes rarely can let Merchant Center build the feed from the site's pages.
- A larger shop, or one whose stock changes often, should upload a feed.
- Turn on automatic updates from the website in Merchant Center, so a sold-out product on the site does not stay "in stock" there.

The owner signs up and connects it. The agent can check that the feed's prices and stock match the pages.

## 8. Report back

- The priority table.
- Each priority page against the checklists, with what is missing.
- URL and markup problems with the fix.
- The owner's to-do: facts, photos, Merchant Center.
- Log each change in `seo-reporting`, then measure with `seo-quick-wins` section 6.

## Do not

- Write, buy, or invent reviews or ratings.
- Mark up a price or stock level the page does not show.
- Make every filter combination indexable.
- Rewrite the whole catalog before the priority products work.
