---
title: Festival of Hope Microsite — Session Handoff
type: handoff-doc
program: festival-of-hope
created: 2026-05-06
status: gate-2-pending
---

# Festival of Hope Microsite — Handoff

A new Claude session in `~/IB Vault/` can resume by reading this file first.

## What this is

A single-page public microsite for the Festival of Hope, built as the "global impact page" Tim Logan and Jennifer Bahrami requested in the May 6 2026 sync (Granola id `e477b9f3-8cc4-42e7-a057-90047fe6fea4`). Mirrors the visual quality of the GYAF 2025 Impact Report v5 with a 3D interactive globe, butterfly hero animation, and the brand's locked palette and typography.

## Where things live

- **Project root:** `/Users/ziyaanvirji/IB Vault/programs/festival-of-hope/microsite/`
- **GitHub repo:** https://github.com/ziyaan-web/festival-of-hope-microsite (currently **private**, account: `ziyaan-web`)
- **Plan file:** `~/.claude/plans/https-notes-granola-ai-t-e477b9f3-8cc4-4-silly-wigderson.md`
- **Site:** `index.html` (~1,500 lines, single file, all CSS + JS inline)
- **Data:** `data/foh-events.json` (78 events across 39 countries, 2022-2027, geocoded)
- **Libs:** `assets/lib/` (globe.gl 2.34.4 self-contained with three.js, GSAP, three earth textures)
- **Logos:** `assets/img/logos/` (IB, FoH color, FoH white, FoH butterfly PNG + SVG)
- **Video thumbs:** `assets/img/videos/` (6 YouTube thumbnails)
- **Playbook PDF:** `assets/playbook.pdf` (compressed from 71MB to 6MB)
- **Domain:** **festivalhope.org** — Ziyaan to register at Cloudflare Registrar (~$11/yr)

## Locked decisions

1. **Palette:** FoH brand-locked. Navy `#091C36`, Cream `#E9E9E1`, Vermillion `#F05332`, Gold `#FFD400`, Teal `#458080`, Cyan `#05B4C9`, Navy-Blue `#144E8C`, Ink `#333132`. No other colors permitted.
2. **Typography:** Helvetica Neue (Helvetica → Arial fallback) for all sans, Playfair Display Italic for the single accent word per headline. NO Inter Tight (this is FoH, not GYAF).
3. **Voice rules** (from `~/IB Vault/programs/communications/brand/foh-brand-guide/`):
   - No em-dashes, no emojis
   - Use: youth agency, take action, young people, pathways to action
   - Avoid: empowerment, leadership-as-default, "students" as default, standalone "impact"
   - One Playfair italic accent per headline only
4. **Inquiry form URL:** `https://forms.monday.com/forms/6df9cd4818ce27c566397913432af965?r=euc1` (locked, Ziyaan provided in plan-mode Q&A)
5. **Contact email:** `support@ib.org` (per Ziyaan)
6. **Scope decision:** FoH numbers + partnership strip only. Do **not** add YAC applicant counts, youth ambassador counts, or IB Exchange resource counts (Ziyaan locked this in plan-mode Q&A).
7. **Tech stack:** vanilla HTML + CSS + JS, single file. Three.js + globe.gl for 3D map, GSAP for hero animation. No frameworks, no build step.
8. **No gradients, no drop shadows** in main UI per FoH brand mood (one minor exception: the scroll-progress bar uses a gradient as a tiny accent — acceptable per v5 precedent).

## What's done

- [x] Phase 0 — Brand guide read, event spreadsheets parsed and geocoded, JSON written
- [x] Phase 1 — Logos copied, YouTube thumbs downloaded (6/6), libs self-hosted (Three.js + globe.gl + GSAP)
- [x] Phase 2 — Full HTML build:
  - [x] Hero: butterfly SVG reveal animation (6 paths animate in sequence) + word-by-word title reveal + tagline
  - [x] Numbers: 4 stat tiles (10,000+ / 90+ / 1,000+ / 10) with easeOutExpo count-ups on scroll
  - [x] Globe: 3D rotating globe.gl with 78 events plotted, year-filter pills (All / 2022-2026), event count, hover tooltips, 2D SVG fallback for mobile and prefers-reduced-motion
  - [x] Videos: 6 YouTube embeds in lite-youtube pattern (thumb until clicked, then iframe)
  - [x] Partners: Roots & Shoots, Teach For All, UN, HundrED, Jane Goodall Institute, Ministries of Education (Rwanda, Colombia, Indonesia)
  - [x] CTA: "Bring Festival of Hope to your school" with vermillion primary button (Monday inquiry form) + secondary mailto button
  - [x] Footer: IB logo + brand line + hope.ibo.org link + #festivalofhope
  - [x] Sticky chapter nav (right side, dark/light theme aware)
  - [x] Scroll progress bar
  - [x] Reveal-on-scroll for every section (IntersectionObserver)
  - [x] Mobile responsive (single-column video grid, hidden chapter nav, 2D map fallback under 700px)
  - [x] `prefers-reduced-motion` honored

## What's pending (next session pick up here)

- [ ] **GATE 2 — Ziyaan reviews HTML.** Local preview is up in the Launch panel; user gives feedback or approves to ship.
- [ ] Mobile responsive QA on real iPhone (current build is dev-tools-tested only)
- [ ] Cross-browser test: Chrome, Safari, Firefox, Edge (last 2 versions)
- [ ] Self-host Earth texture — currently loads from `https://unpkg.com/three-globe@2.31.1/example/img/earth-night.jpg`. Download to `assets/lib/earth-night.jpg` and update reference before deploy.
- [ ] Self-host Playfair Display font — currently loaded via Google Fonts CDN. Download woff2 files to `assets/fonts/` for full offline portability.
- [ ] **GATE 3 — Domain shortlist + purchase.** Search Cloudflare Registrar for: `festivalof.hope`, `festivalofhope.world`, `festivalofhope.global`, `festivalofhope.earth`, `foh.global`. Present 5 options with prices, Ziyaan purchases manually.
- [ ] **GATE 4 — GitHub repo + Pages deploy.** Create repo, push code, configure Pages, add CNAME, DNS instructions for Ziyaan's registrar.
- [ ] Phase 6 — Live verification: open in mobile + desktop, screenshot, run Lighthouse audit, confirm Monday form opens.

## Open questions

- (none — all plan-mode questions resolved)

## How to resume in a fresh session

1. Open `~/IB Vault/` directory.
2. Read `programs/festival-of-hope/microsite/HANDOFF.md` (this file).
3. Re-open `index.html` in the Launch preview panel to see current state.
4. Ask Ziyaan: "I see the current state of the FoH microsite. Where are we — still iterating in GATE 2, or ready to move to domain search (GATE 3)?"
5. Pick up from there.

## Resources

- Plan file: `~/.claude/plans/https-notes-granola-ai-t-e477b9f3-8cc4-4-silly-wigderson.md`
- Granola meeting: `e477b9f3-8cc4-42e7-a057-90047fe6fea4` (May 6 2026, Tim + Jenn)
- GYAF v5 reference: `~/IB Vault/programs/gyaf/2025/impact-report-v5/`
- Alex birthday reference: `~/Sites/alex-25/`
- FoH brand guide: `~/IB Vault/programs/communications/brand/foh-brand-guide/claude-artifact-FoH_IB_Brand_Guide.md`
- FoH visual style: `~/IB Vault/programs/communications/brand/visual-style/foh.visual-style.md`
- Source spreadsheets: `~/Desktop/FOH All time Data/` and `~/IB Vault/programs/festival-of-hope/FoH_Events_*.xlsx`
