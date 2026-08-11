# Shraddha se Yoga — animated landing page (demo build)

A single-page, installable site for the yoga business behind
[@shraddha_se_yoga](https://www.instagram.com/shraddha_se_yoga/). Dark and light themes,
GSAP motion, all images local.

```
shraddha-se-yoga/
  index.html            the whole site — HTML, CSS and JS in one file
  manifest.json         PWA manifest
  sw.js                 service worker — offline shell
  robots.txt
  sitemap.xml
  IMAGE-PROMPTS.md      Gemini prompts to swap the artwork for photos
  assets/images/        every image, icon and the share card
```

---

## 1. Three things to replace before it goes live

Open `index.html`, find `CONFIG` at the top of the second `<script>`:

```js
clientPhone  : '910000000000',                  // real WhatsApp number, digits + country code
clientEmail  : 'hello@shraddhaseyoga.com',
clientAddress: 'Studio address line 1, Area, City, State 000000, India',
```

None of these were on the Instagram profile — the bio only says "DM to book" — so they're
placeholders. The WhatsApp button, contact card, footer, booking message and schema.org
data all read from `CONFIG`, so you edit once.

Until `clientPhone` is real, the WhatsApp button and the booking form fall back to opening
Instagram DMs and copying the request to the clipboard, so nothing dead-ends in the demo.

Also worth swapping for real content: the offer prices, the four testimonials, and the
credential chips in the Shraddha section (I guessed at Hatha/Vinyasa/aerial/therapy from
her posts — confirm with her). Three of the four stat figures are real, taken from the
profile: 113K reel views, 357 followers, 45 posts, 35-day ritual.

## 2. Deploy

Upload the whole folder to any static host — Netlify, Vercel, Cloudflare Pages, cPanel
`public_html`, GitHub Pages. Then update the absolute URLs in `<head>` (canonical,
`og:url`, `og:image`) and in `sitemap.xml` from `shraddhaseyoga.com` to the real domain.
**HTTPS is required** for the install prompt and the service worker.

## 3. What changed in this build

**The logo is now the real one.** I pulled it out of the profile-photo screenshot rather
than redrawing it, cleaned it to two colours sampled from the file (`#3F250E` espresso,
`#F5EAD8` cream), made the outside of the circle transparent, and rendered every size:
`logo.png` at 1024, app icons at 192/512, a maskable icon, an Apple touch icon, favicons,
plus cream-on-transparent and brown-on-transparent marks for overlays.

**Light mode.** Sun/moon toggle in the header. It remembers the choice, follows the OS
setting on first visit, updates the browser theme colour, and applies before first paint
so there's no flash of the wrong theme. It's a real second palette — warm cream ground,
espresso text, a darker gold that passes contrast on light — not an inversion.

**No more broken images.** Everything is a local file in `assets/images/`; the Unsplash
hot-links are gone. The nine artwork files are warm abstract light studies I generated in
the brand palette. See `IMAGE-PROMPTS.md` to swap them for AI or real photography — same
filenames, same dimensions, no code changes.

**Shraddha is featured.** From the frame you sent I cut a 4:5 portrait, a square, a wide
crop and a warm sepia version, with the video caption cropped out. She gets a dedicated
"Shraddha means faith" section right after the hero — portrait in a spatial card with an
offset gold frame and a logo name plate, bio, credential chips, pull quote and signature —
two gallery tiles, and the social share card.

## 4. Everything else

**Sections in order:** hero slider → marquee → Meet Shraddha → services → stats →
the 35-day ritual gallery with filters → offer banner → appointment → testimonials →
contact → footer.

**Motion.** GSAP 3 + ScrollTrigger drive the load sequence, slider crossfades, scroll
reveals, parallax, counters and pointer tilt. Motion (the vanilla core behind Framer
Motion) is loaded as a progressive enhancement for spring hovers; if that CDN is blocked
nothing breaks. Framer Motion proper needs React and a build step — say the word and I'll
port this to Next.js + Framer Motion instead of one static file.

**Signature element.** The breath ring in the hero. Tap *Start breathing* and it runs a
real 4-7-8 cycle for a minute with the cues changing as it goes.

**Installable app.** `manifest.json` + `sw.js` give a standalone window, offline shell and
long-press shortcuts to Book / Shraddha / Practice. An install bar appears after ~9
seconds; iOS gets the Share → Add to Home Screen hint instead, since Safari has no install
event. Mobile also gets a bottom tab dock and safe-area padding so it reads as an app.

**SEO.** Title, description, keywords, canonical, robots, sitemap, Open Graph and Twitter
`summary_large_image` pointing at `assets/images/og-image.jpg`, and
`HealthAndBeautyBusiness` JSON-LD with services, hours, founder and address.

**Demo gate.** Three minutes after load the site blurs and a locked panel appears with
your WhatsApp (+92 320 7906634) and isaadahmad.com. No close button — the only way on is
*Reload for 3 more minutes*, which restarts the timer. Change `demoMinutes` in `CONFIG`,
or delete the `gate()` block once the client has paid.

**Copy protection.** Right-click, drag, selection, copy/cut and the usual devtools
shortcuts are blocked outside form fields. Be straight with the client: this stops casual
copying, not a determined person, because the browser has to receive the HTML to render
it. Real protection is a takedown notice, not JavaScript.

**Quality floor.** Visible focus rings, `prefers-reduced-motion` fully respected, keyboard
arrows drive the slider, 44px+ tap targets, and if GSAP fails to load every section stays
visible instead of blanking. Render-tested in both themes at 1440px and 390px with no
console errors.
