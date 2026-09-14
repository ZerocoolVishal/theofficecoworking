# The Office — Coworking Space, Ambernath

Landing page for **The Office**, a coworking space in Ambernath West, Maharashtra.

**Live details:** Fixed desks at ₹2,999/month (launch offer, down from ₹3,499).
Private cabins available on enquiry.

G-65, Master Business Center, Wimco Naka
Kalyan Badlapur Road, next to Miraj Cinemas
Housing Board Colony, Ambernath, Maharashtra 421505

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
images/hero-interior.jpg            interior render, used in the hero
images/master-business-center.jpg   the building, used in Visit Us
.claude/launch.json                 local preview server config
```

## Editing

Contact details appear in several places — change all of them together:

| What | Where |
|---|---|
| Phone / WhatsApp | 7 links: `wa.me/91…` and `tel:+91…` |
| Email | contact card in the Visit Us section |
| Address | Visit Us section, footer, `og:description`, Maps link |
| Pricing | the Fixed Desk card |

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

## Before going live

- Replace the placeholder email `hello@theofficecoworks.in` with a real address
- Confirm the opening days (currently listed as Monday to Saturday, 8:00 AM to 10:00 PM)
- Check the amenity copy is accurate: ergonomic chairs and storage, housekeeping,
  business address use, cabins for 2–8 people, and the free trial day
