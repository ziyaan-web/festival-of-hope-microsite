# Festival of Hope &mdash; Global Impact Microsite

A single-page public microsite for the International Baccalaureate's Festival of Hope. Designed as the global brand surface that answers the question "what is Festival of Hope and where is it happening" in one scroll.

**Live preview:** open `index.html` directly in any modern browser, or run a local server (see below).

## What's inside

```
microsite/
  index.html              one-file site (HTML + CSS + JS inline)
  data/
    foh-events.json       78 geocoded events, 2022-2027
  assets/
    img/logos/            IB, FoH (color + white + butterfly)
    img/videos/           6 YouTube thumbnails
    lib/                  Three.js, globe.gl, GSAP (self-hosted)
    fonts/                Google Fonts CSS reference
  HANDOFF.md              session-resumption doc
  README.md               this file
```

## How to run locally

```bash
cd "/Users/ziyaanvirji/IB Vault/programs/festival-of-hope/microsite"
python3 -m http.server 8088
# then open http://localhost:8088 in your browser
```

(File-protocol `file://` may block the JSON fetch and the YouTube iframes &mdash; use a local server.)

## Sections

1. **Hero** &mdash; Festival of Hope butterfly reveal animation, title, tagline ("Think boldly. Inquire bravely. Act *together*.")
2. **The Numbers** &mdash; 4 stat tiles with count-up animations (10,000+ young people / 90+ countries / 1,000+ schools / 10 regions)
3. **The Map** &mdash; 3D interactive globe of every Festival of Hope event since 2022, filterable by year. Falls back to a 2D world map on mobile or when reduced-motion is requested.
4. **In their words** &mdash; Six Festival of Hope event recap videos
5. **A connected movement** &mdash; Partner organisations (Roots & Shoots, Teach For All, UN, HundrED, Jane Goodall Institute, Ministries of Education for Rwanda, Colombia, Indonesia)
6. **Get involved** &mdash; Inquiry form (Monday.com) + email support@ib.org
7. **Footer** &mdash; IB logo + #festivalofhope + hope.ibo.org

## Brand system

Inherits the FoH brand guide locked palette and typography:

| Token | Value |
|---|---|
| Navy | `#091C36` |
| Cream | `#E9E9E1` |
| Vermillion | `#F05332` |
| Gold | `#FFD400` |
| Teal | `#458080` |
| Cyan | `#05B4C9` |
| Navy-Blue | `#144E8C` |
| Ink | `#333132` |

| Font | Role |
|---|---|
| Helvetica Neue (Helvetica, Arial fallback) | All sans |
| Playfair Display Italic | One accent word per headline |

## How to update

### Add or remove an event

Edit `data/foh-events.json`. Each event needs:

```json
{
  "name": "FoH Country/School Name",
  "country": "Country",
  "city": "City",
  "lat": 41.3775,
  "lng": 64.5853,
  "year": 2026,
  "status": "Confirmed",
  "format": "In Person",
  "group": "Active Pipeline"
}
```

Reload the page. The globe and event-count update automatically.

### Update the inquiry form URL

Search `forms.monday.com` in `index.html` (one occurrence) and replace.

### Update partners

Search `partners-strip` in `index.html`. Each partner is a `<div class="partner">` line. Add or remove as needed.

### Update headline numbers

Search `data-target` in `index.html`. Each `.big-num` has `data-target="10000"` and `data-suffix="+"`. Update both to change a tile.

## Browsers

Tested on: Chrome, Safari (recent versions). Mobile Safari falls back to 2D map. `prefers-reduced-motion` honored throughout.

## Pre-deploy checklist

Before pushing live:

- [ ] Self-host the Earth texture (currently loads from unpkg). Download `https://unpkg.com/three-globe@2.31.1/example/img/earth-night.jpg` into `assets/lib/` and update the `globeImageUrl(...)` line.
- [ ] Self-host Playfair Display Italic font files (currently Google Fonts CDN).
- [ ] Add a `CNAME` file with the chosen domain.
- [ ] Lighthouse audit: target Perf &ge; 80, A11y &ge; 95.
- [ ] Test on a real iPhone (not just dev tools).

## Deployment

Hosted on GitHub Pages with a custom domain. See `HANDOFF.md` for the deployment plan and pending steps.

## Licence

Content &copy; International Baccalaureate Organization 2026. Code MIT.
