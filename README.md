# DevStarLabs — marketing site

Production-ready static site: ten self-contained HTML pages, inline CSS/JS, no build step.
Open `index.html` directly in a browser, or deploy the folder to any static host
(GitHub Pages, Netlify, Vercel, nginx). External requests are limited to web fonts.

## Pages

| File | Purpose | Field colour |
| --- | --- | --- |
| `index.html` | Home: hero, channels, retainer process, pilot band, FAQ, contact | Lemon |
| `cloud-devops.html` | Managed Cloud & DevOps + ₹30,000/month rate card | Mint |
| `security.html` | Managed Security (honest "not a 24/7 SOC" positioning) | Lilac |
| `ai-automation.html` | Venue Lead Conversion System (pinned 5-step story, Tamil voice) | Pink |
| `outsourced-it.html` | Outsourced Technology Department, 7-service stack | Lemon |
| `government-enterprise.html` | Vendor dossier / procurement register | Paper + Lemon |
| `case-studies.html` | Honest empty state: reserved case-study slots | Lilac |
| `pilot.html` | Paid pilot offer ₹10,000–₹25,000 + booking form | Mint |
| `about.html` | Values + Year 1→4 timeline | Lemon |
| `contact.html` | Contact form, WhatsApp, email | Lemon |

Also included: `favicon.svg`, `sitemap.xml`, `robots.txt`, `og/og-*.png` (flat OpenGraph
images generated per page), this README.

## Fill before launch — 【…】 placeholder list

Search for `【` in the HTML. Everything below is a genuine unknown; nothing else is invented.

1. **Contact details** — `【email】`, `【WhatsApp number】`, `【city】` (header/footer/contact).
2. **JS contact config** — in every page's inline script, `CONTACT.wa` is `91XXXXXXXXXX` and
   `CONTACT.email` is `hello@yourdomain.example`. These power the form success buttons and all
   `wa.me` links. Replace both.
3. **Cities** — Home FAQ: `【cities covered】` for on-site work.
4. **Registration numbers** — Government & Enterprise page: DPIIT cert. no. and Udyam number,
   `【on issue】`.
5. **Pricing placeholders** — AI Automation: `【set-up amount】`, `【monthly amount】`;
   Outsourced IT retainer bands: `【…】` per row. (Cloud ₹30,000 and pilot ₹10,000–₹25,000 are
   real figures from the brief.)
6. **Calendar link** — pilot page: `【calendar link】`.
7. **Team bios** — About page: `【Name】`, `【Role and background】` slots.
8. **Case studies** — two reserved cards on Case Studies; fill only with measured, client-approved
   numbers.
9. **Domain** — canonical URLs, sitemap and OG images assume `https://devstarlabs.in`; change
   `BASE` in the build script or the URLs if the domain differs.
10. **Logo** — no logo file was supplied; the wordmark is typeset. Swap in a real logo when one
    exists.

## Forms

No backend is wired. Submitting a valid form opens a success panel with two prefilled
buttons — WhatsApp (`wa.me/…?text=…`) and email (`mailto:…`) — so enquiries work without any
server. To capture leads server-side, point the forms at Formspree or your own endpoint; the
JS only needs the `.fld-ok` panel kept for the success state. With JavaScript disabled, the
forms do not submit but all contact details are visible as text.

## Fonts & licences

| Font | Use | Source | Licence |
| --- | --- | --- | --- |
| Clash Display | Display/headlines | Fontshare (Indian Type Foundry) | ITF Free Font Licence (free for commercial use) |
| General Sans | Body text | Fontshare (Indian Type Foundry) | ITF Free Font Licence |
| JetBrains Mono | Labels, tables, notes | Google Fonts | SIL Open Font License |
| Anek Tamil | Tamil script (AI page only) | Google Fonts | SIL Open Font License |

`font-display: swap` is on; text paints immediately in the fallback stack. The ₹ glyph is
included in Clash Display (ITF is an Indian foundry), so prices render correctly at poster scale.

## Motion libraries

None. All motion is hand-written vanilla JS + CSS: IntersectionObserver reveals, sticky
pinning (Home retainer, AI venue story — 1024px+ only), an SVG line that draws and undulates,
a canvas-free SVG waveform, a cursor ring on fine pointers, native smooth scrolling, and
cross-document View Transitions (`@view-transition`) for page changes in Chromium. No WebGL,
no autoplaying media, nothing heavier than the fonts.

## Tamil strings (for a native-speaker check)

| String | Romanisation | Meaning | Where |
| --- | --- | --- | --- |
| வணக்கம் | vaṇakkam | "Hello / greetings" (standard polite greeting) | AI Automation panel, call-back step |

No other Tamil appears on the site.

## Accessibility & performance notes

- All content is readable with JavaScript off; pre-animation states only exist under `html.js`.
- `prefers-reduced-motion`: no smooth scroll, pinning, marquee, cursor, curtain, or wave
  animation; reveals become static.
- Nothing is hover-only; tap targets ≥ 44px; full-screen menu traps focus and closes on Esc.
- Text contrast: Ink on all four Field colours and on Signal; deep coral (#C2300A) for accent
  text on Paper; muted tones ≥ 4.7:1.
- Animate-only transform/opacity/stroke-dashoffset; looping animations pause off-screen and
  when the tab is hidden.
- Verified: no horizontal overflow at 375px on any page; both hero CTAs visible at 375×667;
  forms validate with designed error/success states.
- Honest-copy rule enforced: no invented clients, testimonials, metrics, logos or "live"
  status indicators; the only live detail is the IST clock in the footer.

## Structure note

The generator scripts (CSS/JS/page modules + build script) live outside this repo; the HTML
files here are the source of truth for deployment. Edit them directly, or regenerate from the
build system if you have it.
