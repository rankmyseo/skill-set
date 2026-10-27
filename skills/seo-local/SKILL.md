---
name: seo-local
description: Local search for a business that customers visit, or that travels to customers in a set area. Covers the Google Business Profile the owner sets up, matching name, address, and phone on the site, asking for reviews within Google's rules, location and service-area pages, and LocalBusiness markup. Use when the business has a shop, office, clinic, or service area, or when the owner asks about Google Maps, map results, or reviews.
---

# SEO local

Goal: the business shows up for "near me" and "in [city]" searches with correct details, and every page and listing tells the same story.

Acceptance: the owner has a verified Business Profile with the right category, the site shows the same name, address, and phone as the profile, and the owner knows how to ask for reviews without breaking Google's rules.

Use this only when customers visit a place or the business travels to them. For an online-only business, skip it.

## How Google ranks local results

Google says local results depend mainly on three things:

- **Relevance:** how well the profile matches the search. Complete, detailed information helps.
- **Distance:** how far the business is from the person searching. The owner cannot change it.
- **Prominence:** how well known the business is, including links from other sites and the number of reviews and ratings.

Google also says no one can pay for a better local ranking. Tell the owner that, and do not promise a map position.

## 1. Business Profile (the owner does this)

The agent cannot create or connect the profile. Give the owner these steps and check the result with them:

1. Create or claim the profile at business.google.com and verify it.
2. **Name:** the real-world name, as on the sign, the website, and the receipts. No city, keyword, or slogan added. Google says extra words in the name can get the profile suspended.
3. **Category:** the fewest, most specific categories. The primary category should complete "This business is a ...", not "This business has a ...".
4. **Address:** the real place customers visit. A virtual office or rented mailbox is not eligible. One profile per location.
5. **Service-area business** (a plumber, a cleaner): hide the address and set the service area. Google says the area should generally stay within about two hours' drive of the base.
6. **Phone and website:** a number the business controls, local if possible. The website link goes to the business's own page for that location.
7. **Hours,** including holiday hours. Add photos of the real place, team, and work.

## 2. Name, address, and phone on the site

- Show the same name, address, and phone as the profile, written the same way, in the footer or on the contact page. Use text, not an image.
- If the business has several locations, each location page shows its own address and phone.
- After any change to the address, phone, or hours, update the profile, the site, and the markup together. Ask the owner which other listings they control (directories, social profiles, maps apps) and give them a list to update.

## 3. LocalBusiness markup

- Use the most specific LocalBusiness type that fits (`Dentist`, `Restaurant`, `Plumber`, and so on).
- Required by Google: `name` and `address`. Add `telephone` with the country code, `url` for that location, `openingHoursSpecification`, and `geo` when you have them.
- Mark up only what the page shows. One block per location page.
- Do not add the business's own star rating. Google shows review stars for LocalBusiness only on sites that collect reviews about other businesses.
- Validate it as in `seo-site-setup`, section 9.

## 4. Reviews, within Google's rules

Reviews count toward prominence, and Google says replying to them helps the business stand out. Google's policy is strict about how they are asked for. The owner may:

- Ask every customer for an honest review, with a link from the profile.

The owner must not:

- Offer anything for a review: money, a discount, a gift, or a free service.
- Ask only happy customers, or check satisfaction first and send only the happy ones to Google.
- Discourage or block negative reviews.
- Pressure customers to review on the spot, ask for specific words, or set staff a review quota.
- Write reviews themselves, through staff, family, or several accounts, or post on a rival's profile.

Reviews that break these rules are removed. If the owner asks for a "happy customers only" flow, say it is not allowed and offer the honest version.

Help the owner reply: thank the reviewer, answer the point they raised, and keep private details out. Draft replies for the owner to post; do not post them yourself.

## 5. Location and service-area pages

- One page per real location, with facts only that location has: address, hours, directions, parking, staff, photos, and the services offered there.
- A service-area business gets a page for an area only when it really works there and has something specific to say: jobs done there, travel time, local rules. Otherwise use one "Areas we serve" page with a list.
- Pages that only swap the city name are doorway pages under Google's spam policy. Use the checks under "Pages made from one template" in `seo-launch-plan` before writing more than a few.
- Put the city in the title and H1 only when the business serves that city.

## 6. Measuring local results

- Map results are not the same as the normal search results. RankMySEO tracks the normal results and does not record map positions. Say that when you quote a tracked rank.
- Search Console shows the site's clicks and the city queries people use. Filter queries by the city name.
- The Business Profile shows its own calls, direction requests, and website clicks. Only the owner can see them. Ask the owner to read them out each month, and record them in the report (`seo-reporting`).
- Tag the profile's website link with UTM parameters (for example `utm_source=google&utm_medium=organic&utm_campaign=business_profile`) so GA4 shows those visits apart from normal search. Ask the owner first, since it changes the link on the profile.

## Report back

List what is done, what the owner must do personally (the profile, listings elsewhere, review requests), and what is waiting on verification. Label each item verified, implemented but unverified, or blocked.
