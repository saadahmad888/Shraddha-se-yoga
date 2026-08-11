# Image prompts — swap the artwork for AI photos

Every image on the site is a **local file in `assets/images/`**. Nothing is hot-linked, so
nothing can break. The nine artwork files are warm abstract light studies I generated
in the brand palette — a safe default, but real photography will always look better.

## How to replace one

1. Generate the image with the prompt below.
2. Crop/resize it to **exactly** the dimensions listed.
3. Save it with **exactly** the same filename, as `.jpg`, into `assets/images/`.
4. Done. No code changes — `index.html` already points at that path.

Compress before uploading (squoosh.app or tinyjpg.com). Target under 400 KB for the
three hero images, under 200 KB for the tiles. Then bump `const V = 'ssy-v2'` to
`'ssy-v3'` in `sw.js` so returning visitors get the new files instead of cached ones.

## Style preamble — paste this in front of every prompt

> Warm, editorial wellness photography. Deep espresso-brown and cream palette with
> honey-gold light — no cool blues, no teal, no grey. Soft directional morning or
> late-afternoon sun, gentle haze, fine film grain, shallow depth of field. Calm and
> restrained, not glossy or corporate. Indian setting and Indian people where people
> appear. Photorealistic. No text, no logos, no watermarks, no borders, no collage.

---

## The three hero backdrops

These sit **behind the headline**, which is white and sits on the **left third**.
Every hero prompt must keep the left side dark, simple and uncluttered, with the
subject and light on the right. Landscape, `2000 × 1250` (16:10).

### `hero-01.jpg` — 2000 × 1250
> A woman in her thirties holding a slow standing yoga pose in a bare, warm-toned room
> at sunrise. Shot from a distance so she occupies the right third of the frame; the left
> half is deep shadow with almost nothing in it. Strong low golden sunlight rakes across
> the floor from the right. Dark plaster walls, wooden floor, a single rolled mat.
> Silhouette-leaning exposure — her shape reads more than her detail.

### `hero-02.jpg` — 2000 × 1250
> Morning light pouring through a tall arched doorway into an empty yoga room. Dust
> motes in the beam, warm terracotta floor, deep brown walls. The arch and light are on
> the right side of the frame; the left side falls into near-darkness. No people. Quiet,
> temple-like, spacious.

### `hero-03.jpg` — 2000 × 1250
> A woman seated cross-legged in meditation on a terrace at dusk, seen from behind and
> slightly to the side, small in the right of the frame. Muted sage and olive tones with
> a single warm lamp glow. Still air, soft mist, distant blurred trees. The left of the
> frame is empty dark sky. Contemplative and very calm.

---

## Offer banner

### `offer-bg.jpg` — 1700 × 1000
> Warm honey sunlight flooding a yoga studio, shot low and wide with no people. Rolled
> mats stacked against a dark brown wall on the right, brass singing bowl catching the
> light. The left two-thirds is soft shadow so text can sit over it. Golden hour, hazy,
> inviting.

---

## Gallery tiles — all portrait, `900 × 1125` (4:5)

These carry a Sanskrit caption and a day badge, so leave the bottom quarter and the
top-left corner visually simple.

### `asana-01.jpg` — Sun salutation, day 01
> A woman mid sun-salutation, arms sweeping overhead, on a mat in a warm minimal room
> at sunrise. Full body, vertical framing, strong golden backlight behind her. Espresso
> walls, cream mat. Her face is not the subject — the shape of the pose is.

### `asana-02.jpg` — Tree pose, day 12
> A woman in tree pose, one foot to the inner thigh, hands at the heart, on a wooden
> floor in a dim warm room. Vertical full-body framing, single soft window light from the
> side, deep brown background. Steady and quiet.

### `asana-03.jpg` — Downward dog
> A woman in downward-facing dog on a cream mat, photographed from the side against a
> plain dark brown wall. Vertical framing, warm rim light along her back and legs, deep
> shadow behind. Clean and graphic — this pose is the brand's logo, so make the silhouette
> read clearly.

### `breath-01.jpg` — Alternate-nostril breathing
> Close crop of a woman's hands and lower face during alternate-nostril breathing
> (nadi shodhana), right hand raised to the nose, eyes closed. Vertical framing, warm
> low light from one side, dark brown background. Intimate and gentle, softly focused.

### `breath-02.jpg` — Yoga nidra
> A woman lying in savasana on a mat under a light blanket in a dim warm room in the
> evening, seen from above and slightly to the side. Vertical framing, one low lamp,
> long shadows, honey-brown tones. Deeply restful.

---

## Social share card

### `og-image.jpg` — 1200 × 630
This one already has type and the logo composed onto it, and it uses Shraddha's real
photo — **leave it alone unless you want to redesign the card in Figma.** If you do
rebuild it, keep: her portrait on the right, "From stress to strength." as the headline,
the logo top-left, and a 1200 × 630 canvas.

---

## Do not AI-replace these

| File | What it is |
|---|---|
| `shraddha-portrait.jpg` (940 × 1175) | Shraddha, "Meet Shraddha" section |
| `shraddha-square.jpg` (700 × 700) | square crop, spare |
| `shraddha-wide.jpg` (1200 × 800) | wide crop, spare |
| `practice-01.jpg` (900 × 1125) | warm sepia gallery tile of her |
| `practice-02.jpg` (900 × 1125) | gallery tile showing the branded tee |
| `logo.png`, `icon-*.png`, `mark-*.png`, `favicon-*.png` | her actual logo, extracted and cleaned |

All five photo crops came from the frame you sent, with the video caption cropped out.
Ask Shraddha for a proper set — a portrait, three or four poses, one studio wide shot,
and one aerial/silks shot — and drop them in over the tiles. Her own photos will beat
anything generated, and the aerial silks are a real differentiator that no stock or AI
image will capture honestly.

## A note on AI images of people

If you generate people, tell the client they're AI. A yoga studio's credibility rests on
the teacher being real, and a visitor who recognises a synthetic face on a wellness site
loses trust in everything around it. Abstract light studies are the safer placeholder
until real photos arrive — which is why the defaults I shipped have no faces in them
except Shraddha's own.
