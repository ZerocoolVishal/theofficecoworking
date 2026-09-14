# The Office — Coworking Space, Ambernath

Landing page for **The Office**, a coworking space in Ambernath West, Maharashtra.

**Live details:** Fixed desks at ₹2,999/month (launch offer, down from ₹3,499).
Private cabins available on enquiry.

G-65, Master Business Center, Wimco Naka
Kalyan Badlapur Road, next to Miraj Cinemas
Housing Board Colony, Ambernath, Maharashtra 421505

📞 +91 88500 13526 · ✉️ theofficeambernath@gmail.com
[Instagram](https://www.instagram.com/theofficeambernath/) · [Facebook](https://www.facebook.com/theofficeambernath/)

---

## Stack

A single static page. No framework, no build step, no dependencies to install.

- `index.html` — the entire site, one file
- Tailwind CSS via the Play CDN (compiled in the browser)
- Fraunces (display) and Inter (body), loaded from Google Fonts

## Running it locally

Open `index.html` in a browser, or serve the folder so the images resolve:

```bash
python3 -m http.server 4321
```

Then visit <http://localhost:4321>.

## Structure

```
index.html                          the page
images/hero-interior-cutout.webp    interior render, background removed (hero)
images/hero-interior-cutout.png     PNG fallback for the above
images/hero-interior-source.png     untouched original, kept for re-cutting
images/master-business-center.jpg   the building, used in Visit Us
images/og-cover.jpg                 1200x630 card shown when the link is shared
icons/favicon.svg                   scalable favicon
icons/favicon-16.png, favicon-32.png
icons/apple-touch-icon.png          iOS home screen
icons/icon-192.png, icon-512.png    web app manifest
site.webmanifest                    installable web app metadata
robots.txt, sitemap.xml             search engines
.claude/launch.json                 local preview server config
```

## Site address

Absolute URLs (canonical, Open Graph, structured data, sitemap) currently point at
the GitHub Pages address:

```
https://zerocoolvishal.github.io/theofficecoworking
```

Moving to a custom domain means find-and-replacing that one string in `index.html`,
`robots.txt` and `sitemap.xml`, and updating `start_url` / `scope` in
`site.webmanifest`. Share previews will not render until the site is actually
reachable at whichever address is set, because Open Graph requires absolute URLs.

## Editing

Contact details appear in several places — change all of them together:

| What | Where |
|---|---|
| Phone / WhatsApp | 7 links: `wa.me/91…` and `tel:+91…` |
| Email | contact card in the Visit Us section |
| Instagram / Facebook | contact card and footer (2 links each) |
| UPI ID for the token | the Book Your Seat block, in the `upi://` link and printed below it |
| Opening date | the countdown section, and the `OPENING` constant in the script at the end |
| Address | Visit Us section, footer, `og:description`, Maps link |
| Pricing | the Fixed Desk card, and the JSON-LD block at the end of the file |

Swapping a photo is one line — drop an `<img>` inside the `<figure class="photo-ph">`
and it covers the frame automatically.

## Notes

- Mobile-first; verified down to a 320px viewport
- On desktop the hero is capped to the viewport height so both calls to action
  and the photo stay above the fold on short laptop screens
- Scroll animations are progressive enhancement: the page renders fully with
  JavaScript disabled
- Ligatures are switched off for display type because Fraunces' decorative
  `ffi` renders badly in the word "Office"
- Structured data (schema.org `LocalBusiness`) covers the address, hours, phone,
  social profiles, amenities and desk price, so the business can appear in local
  search results
- A skip link is the first focusable element, for keyboard and screen-reader users

## Booking a seat

The space opens on 1st October. Until then the page sells pre-booked fixed desks:
a visitor pays a ₹500 token over UPI, sends the screenshot on WhatsApp, and the
seat is held.

Two limits worth knowing, both because this is a static page with no server:

- **It cannot verify a payment.** The button only opens the visitor's UPI app.
  The WhatsApp screenshot is what actually confirms a booking.
- **It cannot count remaining seats.** The copy says seats are limited without
  naming a number, because a hard-coded count goes stale the moment one sells.

UPI also lets the payer edit the amount, so ₹500 is prefilled, not enforced.

## Analytics

Google Analytics 4, property `G-QB4TTBKSGJ`, tagged in the head of `index.html`.
It only records real traffic once the site is reachable at a public address.

Local testing counts as traffic. To keep it out of reports, add an internal
traffic filter in GA under Admin → Data Streams → Configure tag settings →
Define internal traffic, or just ignore hits with a `localhost` hostname.

## Before going live

- Confirm the opening days (currently listed as Monday to Saturday, 8:00 AM to 10:00 PM)
- Check the amenity copy is accurate: ergonomic chairs and storage, housekeeping,
  business address use, cabins for 2–8 people, and the free trial day
