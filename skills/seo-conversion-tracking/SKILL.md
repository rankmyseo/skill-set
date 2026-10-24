---
name: seo-conversion-tracking
description: Turn the owner's lead definition into GA4 key events, so the site can show which search pages lead to sign-ups, contacts, bookings, or purchases. Covers defining the actions, naming the events, marking them as key events, and keeping personal data out of event parameters. Use after the owner defines what counts as a lead, and before the first monthly report.
---

# Conversion tracking

Goal: each action the owner cares about is one GA4 event, marked as a key event, and the owner can see which pages lead to it.

Acceptance: the owner can read a report that shows, for each key event, the pages and channels that led to it, from the day the events were marked.

This skill sets up measurement. It changes the site's tags and events, so it needs the owner's yes and access to the site and to GA4.

## 1. Define the actions

Ask the owner, one or two questions at a time, what counts as success:

- Sign-up, account created
- Contact form submitted
- Booking made
- Purchase completed
- Tool result shown, for a free tool
- Phone or email link clicked, if the owner wants it counted

For each action, get the owner's answer to: is it a lead, a sale, or an engagement? That decides whether it is a key event.

Keep the list short. Three key events is a good start, and GA4 allows up to 30 on a standard property.

## 2. Name each event

- Use lowercase words with underscores, for example `contact_submit`, `signup_complete`, `booking_complete`.
- Use one name per action. Do not reuse a name for a different action.
- Write the name, the trigger, and the page or element where it fires in the tracking plan.

## 3. Keep personal data out

- Do not send names, email addresses, phone numbers, or any other personal identifier as an event parameter, a custom dimension, a campaign parameter, or part of a URL.
- Record only what the action is, and the page it came from.
- GA4 web streams can redact email addresses and some URL query parameters, but that does not protect every data path. Turn on the redaction setting and check the debug view.
- Privacy rules differ by country. Ask the owner to check them with their own adviser. You do not give legal advice.

## 4. Mark them as key events

- In GA4, go to Admin, then Events, and mark each event as a key event. An event that already exists can be starred. A new event can be created with the key event flag on.
- A key event counts from the day it is marked. It does not fill in past data. Record the date.
- Check that the owner has the permission level needed to mark key events. Editor or above is needed for an existing event. Marketer or above is needed for a new one.

## 5. Test before you trust it

- Perform each action once on the live site, with the debug view open in GA4.
- Confirm the event appears with the right name and page.
- Confirm no personal data appears in the event.
- Record the test date and the result.

## 6. Connect it to the pages

- Use the GA4 pages report to see which landing pages lead to each key event.
- Note when a key event is marked, so a change in the numbers is not blamed on the page.

## 7. Report it

Add the key event counts to the monthly summary (see `seo-reporting`). Keep the conversion numbers separate from the search numbers. Search Console clicks and GA4 conversions measure different things and do not add up.

## Do not

- Track an action the owner did not define.
- Send personal data to GA4, even in a parameter the owner thinks is safe.
- Backfill past data as if it were a key event.
- Count a page view as a lead.
- Set up tracking on the live site without the owner's yes.
