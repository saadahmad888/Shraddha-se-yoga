# Image prompts — swap the artwork for AI photos

Every image on the site is a **local file in `assets/images/`**, so nothing can break. Nine
of them are warm abstract light studies I generated as a safe default. This file replaces
them with photography.

Each prompt below is **complete and self-contained** — the style rules, the aspect ratio
and the framing are all inside the prompt text. Copy one block, paste, generate. Don't
combine them or add a separate style line.

---

## First: why your last images came out the wrong size

Image generators don't accept pixel dimensions. They output a **fixed aspect ratio** at
whatever resolution the model uses, so asking for "2000 × 1250" gets you a 1024 × 1024 or
1408 × 768 image instead. The site's slots are not standard ratios either — 16:10 and 4:5.

So the workflow is always two steps:

1. **Generate** at the nearest ratio the tool supports (each prompt says which).
2. **Crop and resize** to the exact pixel size (each prompt says which).

For step 2, any of these works:

- **squoosh.app** — drag the image in, tick *Resize*, enter the exact width and height, export as JPEG at quality 80.
- **photopea.com** — free, browser-based, `Image → Canvas Size` to crop then `Image → Image Size`.
- **ImageMagick**, if you have it — this crops from the centre and resizes in one go:
  ```bash
  magick input.png -resize 2000x1250^ -gravity center -extent 2000x1250 -quality 82 hero-01.jpg
  ```

Then save with **exactly** the filename listed and drop it into `assets/images/`, replacing
the old file. No code changes — `index.html` already points there.

**One extra step people forget:** after replacing images, open `sw.js` and change
`const V = 'ssy-v2'` to `'ssy-v3'`. The service worker caches images, so returning visitors
keep seeing the old ones until that version string changes.

---

## Getting more detail out of the generator

If a result looks flat, soft or plasticky, these are the words that fix it — they're already
in the prompts below, but push them harder if needed:

- **Camera language:** *shot on a 35mm full-frame camera, 50mm prime lens at f/1.8, 1/200s*
- **Texture words:** *visible skin texture and pores, fine hairs catching the light, woven cotton weave, cracked lime plaster, worn teak grain, dust motes suspended in the beam*
- **Light direction:** *low side light from the right, hard rim light on the shoulder, deep falloff into shadow*
- **Resolution nudge:** *highly detailed, sharp on the subject, natural film grain, no smoothing*
- **What to forbid:** *no text, no watermark, no logo, no extra limbs, no plastic skin, no HDR glow, no oversaturation*

If the person's face looks wrong or generic, generate the shot **without a clear face** —
back-lit silhouette, seen from behind, head turned away, or cropped at the chin. Every
prompt below is written that way on purpose. It reads as more editorial *and* avoids the
uncanny-face problem entirely.

---

## When to upload a reference image first

Some prompts work better with an attachment. In Gemini, attach the file first, then paste
the prompt in the same message.

| Upload this | When | Why |
|---|---|---|
| `assets/images/shraddha-portrait.jpg` | Any prompt with a person in it, if you want it to look like **Shraddha** rather than a stranger | Gives the model her face, hair, build and colouring to match |
| `assets/images/logo.png` | Only for the optional "logo in the scene" add-on at the bottom | Generators cannot invent her logo correctly from a description |
| The image you generated previously | Every prompt after the first | Keeps the whole set in one consistent light and colour grade |

The uploads are marked on each prompt as **Upload first**. Where it says *none*, the prompt
works on its own.

---

# The three hero backdrops

These sit **behind the white headline**, which occupies the **left third** of the screen.
Every hero prompt therefore keeps the left side dark and nearly empty. If the generator puts
the subject in the middle, regenerate — a centred subject will sit under the text.

---

### 1. `hero-01.jpg`

| | |
|---|---|
| **Final size** | 2000 × 1250 px (16:10) |
| **Generate at** | 16:9, then crop to 2000 × 1250 |
| **Appears** | Hero slide 1 — headline "From stress to strength" sits over the left third |
| **Upload first** | *Optional:* `assets/images/shraddha-portrait.jpg` to make the woman look like Shraddha |

```
Photorealistic editorial wellness photograph, 16:9 landscape aspect ratio, output at the
highest resolution available, at least 2000 pixels wide. Shot on a 35mm full-frame camera,
50mm prime lens at f/2, natural light only.

Subject: an Indian woman in her early thirties standing in tadasana with both arms
stretched overhead and palms together, seen in three-quarter profile, wearing a plain dark
brown long-sleeve top and charcoal leggings, barefoot on a cream woven cotton mat.

Composition: she is placed in the RIGHT THIRD of the frame, full body visible, small in
the frame with plenty of room around her. The entire LEFT HALF of the image is deep, almost
empty warm shadow with only a faint gradient — no furniture, no objects, nothing there.
This empty left side is required.

Setting: a bare room with dark espresso-brown cracked lime-plaster walls and a worn teak
floor. A single rolled cream mat leans in the far corner. Nothing else.

Light: low golden sunrise light entering from a window at the far right, raking low across
the floor, rim-lighting the edge of her arms, shoulder and hair while her front stays in
soft shadow. Thick dust motes suspended in the light beam. Long shadow stretching left.

Colour and mood: warm espresso brown, cream and honey gold only. Absolutely no blue, no
teal, no cyan, no grey cast. Calm, quiet, restrained, editorial — not glossy, not
stock-photo cheerful, nobody smiling at the camera.

Detail: visible plaster texture, visible wood grain, woven mat texture, fine natural film
grain, sharp on the subject, soft falloff into the shadows.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage,
extra limbs, plastic or over-smoothed skin, HDR glow, oversaturation.
```

---

### 2. `hero-02.jpg`

| | |
|---|---|
| **Final size** | 2000 × 1250 px (16:10) |
| **Generate at** | 16:9, then crop to 2000 × 1250 |
| **Appears** | Hero slide 2 — headline over the left third |
| **Upload first** | *Optional:* the finished `hero-01.jpg`, as a style reference so the grade matches |

```
Photorealistic architectural interior photograph, 16:9 landscape aspect ratio, output at
the highest resolution available, at least 2000 pixels wide. Shot on a 35mm full-frame
camera, 35mm lens at f/4, natural light only. No people anywhere in the image.

Subject: morning sunlight pouring through a tall pointed stone archway into an empty yoga
hall, casting a hot wedge of honey-coloured light across a terracotta tile floor.

Composition: the archway sits in the RIGHT THIRD of the frame. The LEFT TWO-THIRDS falls
away into deep warm shadow and is almost completely empty — no furniture, no objects. This
empty left side is required.

Setting: dark brown lime-plaster walls with visible trowel texture, aged terracotta floor
tiles with worn edges, a small brass oil lamp sitting on the floor near the base of the
arch. Nothing else in the room.

Light: hard directional morning sun through the arch, thick dust motes suspended in the
beam, sharp bright pool on the floor falling off very quickly into darkness.

Colour and mood: warm espresso brown, terracotta, cream and honey gold only. Absolutely no
blue, no teal, no cyan, no grey cast. Still, temple-like, spacious, reverent.

Detail: visible plaster and stone texture, worn tile grout, fine natural film grain, sharp
where the light lands, deep clean blacks in the shadow.

Do not include: people, text, letters, numbers, logos, watermarks, borders, frames,
collage, HDR glow, oversaturation.
```

---

### 3. `hero-03.jpg`

| | |
|---|---|
| **Final size** | 2000 × 1250 px (16:10) |
| **Generate at** | 16:9, then crop to 2000 × 1250 |
| **Appears** | Hero slide 3 — headline over the left third |
| **Upload first** | *Optional:* `assets/images/shraddha-portrait.jpg`, and/or the finished `hero-01.jpg` for grade consistency |

```
Photorealistic editorial wellness photograph, 16:9 landscape aspect ratio, output at the
highest resolution available, at least 2000 pixels wide. Shot on a 35mm full-frame camera,
85mm lens at f/2, natural light plus one warm lamp.

Subject: an Indian woman in her early thirties seated cross-legged in meditation on a stone
terrace at dusk, photographed FROM BEHIND and slightly to the side so her face is not
visible, hands resting on her knees, spine long, wearing a dark brown shawl over her
shoulders.

Composition: she is small and placed in the RIGHT THIRD of the frame. The LEFT TWO-THIRDS
is empty dark sky and blurred foliage with nothing in it. This empty left side is required.

Setting: an old stone terrace, muted olive and sage foliage far behind her rendered as soft
out-of-focus shapes, a single small brass lamp on the ground beside her casting a low amber
pool of light.

Light: last light of day, very low contrast in the sky, with the brass lamp providing the
only warm accent on her shoulder and the stone. Keep the whole image warm — no blue hour
tones, no cold shadows.

Colour and mood: muted olive, sage green, espresso brown and amber. Absolutely no blue, no
teal, no cyan. Contemplative, hushed, end of the day, deeply still.

Detail: visible stone and fabric texture, soft mist in the air, fine natural film grain,
gentle falloff, shallow depth of field with the foliage well out of focus.

Do not include: her face, text, letters, numbers, logos, watermarks, borders, frames,
collage, extra limbs, HDR glow, oversaturation.
```

---

# Offer banner

### 4. `offer-bg.jpg`

| | |
|---|---|
| **Final size** | 1700 × 1000 px (17:10) |
| **Generate at** | 16:9, then crop to 1700 × 1000 |
| **Appears** | Behind the "20% off your first month" banner — heading, body copy and a countdown sit over the left two-thirds |
| **Upload first** | *Optional:* the finished `hero-01.jpg`, as a style reference |

```
Photorealistic interior photograph, 16:9 landscape aspect ratio, output at the highest
resolution available, at least 1700 pixels wide. Shot on a 35mm full-frame camera, 35mm
lens at f/2.8, natural light only. No people anywhere in the image.

Subject: an empty yoga studio flooded with late-afternoon honey sunlight, photographed low
and wide from close to floor level.

Composition: on the RIGHT THIRD, a neat stack of rolled cream cotton mats leaning against a
dark brown wall, with a brass singing bowl and a wooden mallet on the floor beside them
catching a bright highlight. The LEFT TWO-THIRDS is empty sunlit floor and soft shadow with
nothing in it. This empty left side is required — text will sit over it.

Setting: dark espresso-brown walls, a wide plank wooden floor with visible grain and a few
scuffs, one tall window out of frame on the right.

Light: low late-afternoon sun streaming in from the right, long soft shadows stretching
across the floor toward the camera, warm haze in the air, gentle lens bloom where the light
clips the brass.

Colour and mood: espresso brown, cream, brass and honey gold only. Absolutely no blue, no
teal, no cyan, no grey cast. Warm, inviting, lived-in, calm.

Detail: woven cotton texture on the mats, hammered texture on the brass bowl, visible wood
grain, fine natural film grain, sharp in the lit area.

Do not include: people, text, letters, numbers, logos, watermarks, borders, frames,
collage, HDR glow, oversaturation.
```

---

# Gallery tiles

All five are **portrait 4:5**. Each one carries a Sanskrit caption across the bottom and a
small day badge in the top-left corner, so keep the bottom quarter and the top-left corner
visually simple — plain floor, plain wall, no busy detail there.

---

### 5. `asana-01.jpg` — Sun salutation, day 01

| | |
|---|---|
| **Final size** | 900 × 1125 px (4:5) |
| **Generate at** | 3:4, then crop to 900 × 1125 |
| **Appears** | Large gallery tile, badge "Day 01", caption "सूर्य नमस्कार — Sun salutation" |
| **Upload first** | *Optional:* `assets/images/shraddha-portrait.jpg` to make the woman look like Shraddha |

```
Photorealistic editorial wellness photograph, 3:4 vertical portrait aspect ratio, output at
the highest resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame
camera, 50mm prime lens at f/2, natural light only.

Subject: an Indian woman in her early thirties at the top of a sun salutation, both arms
sweeping overhead and gaze lifted, chest open, standing barefoot on a cream woven cotton
mat. Full body from head to feet inside the frame, vertical composition.

Composition: she is centred, full length, with clear empty space above her hands and below
her feet. Keep the bottom quarter of the frame simple — just plain mat and floor — and keep
the top-left corner plain.

Setting: a dark espresso-brown plaster wall directly behind her, a worn teak floor.
Absolutely nothing else in the room.

Light: strong golden sunrise backlight from a window directly behind her, creating a bright
rim of light around her entire silhouette — along her arms, her shoulders and the loose
hairs around her head — while her front and face fall into soft shadow. Her face is NOT the
subject; the line of the pose is. A long shadow reaches toward the camera.

Colour and mood: espresso brown, cream and honey gold only. Absolutely no blue, no teal, no
cyan, no grey cast. Reverent, quiet, the very start of a morning.

Detail: woven mat weave visible, plaster wall texture, dust in the backlight, fine natural
film grain, sharp on the rim-lit edges.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage, extra
limbs, plastic or over-smoothed skin, HDR glow, oversaturation.
```

---

### 6. `asana-02.jpg` — Tree pose, day 12

| | |
|---|---|
| **Final size** | 900 × 1125 px (4:5) |
| **Generate at** | 3:4, then crop to 900 × 1125 |
| **Appears** | Gallery tile, badge "Day 12", caption "वृक्षासन — Tree, holding still" |
| **Upload first** | *Optional:* `assets/images/shraddha-portrait.jpg`, and/or the finished `asana-01.jpg` for grade consistency |

```
Photorealistic editorial wellness photograph, 3:4 vertical portrait aspect ratio, output at
the highest resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame
camera, 50mm prime lens at f/2.2, natural light only.

Subject: an Indian woman in her early thirties in tree pose (vrksasana) — right foot drawn
up to the inner left thigh, both palms pressed together at the heart, eyes lowered, spine
tall and steady. Wearing a fitted dark brown top and charcoal leggings, barefoot. Full body
from head to feet in frame, vertical composition, seen in three-quarter view.

Composition: centred, full length, generous empty space above her head. Keep the bottom
quarter simple — plain wooden floor only — and keep the top-left corner plain.

Setting: a warm dim room, deep brown wall behind her with soft uneven plaster texture, worn
teak floorboards with visible grain.

Light: one soft window light from the left, wrapping gently around her face and arms, the
right side of her body falling into shadow. Quiet and low-contrast rather than dramatic.

Colour and mood: espresso brown, warm taupe, cream and soft gold. Absolutely no blue, no
teal, no cyan, no grey cast. Balanced, focused, unhurried — the feeling of holding still.

Detail: visible skin texture and fine hairs, fabric weave on her clothing, floorboard
grain, fine natural film grain, sharp on her face and hands.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage, extra
limbs, plastic or over-smoothed skin, HDR glow, oversaturation.
```

---

### 7. `asana-03.jpg` — Downward dog, day 23

| | |
|---|---|
| **Final size** | 900 × 1125 px (4:5) |
| **Generate at** | 3:4, then crop to 900 × 1125 |
| **Appears** | Large gallery tile, badge "Day 23", caption "अधोमुख श्वानासन — Downward dog" |
| **Upload first** | *Optional:* `assets/images/logo.png` — **not to put the logo in the photo**, only so the generator matches the silhouette shape of the mark |

**This is the most important tile.** Her logo *is* a downward-dog silhouette, so the shape
in this photo should echo the shape in the logo. Ask for a clean, readable silhouette.

```
Photorealistic editorial wellness photograph, 3:4 vertical portrait aspect ratio, output at
the highest resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame
camera, 50mm prime lens at f/2.8, natural light only.

Subject: an Indian woman in her early thirties in downward-facing dog (adho mukha
svanasana) — hands flat and shoulder-width apart, hips lifted high, heels reaching down,
head hanging between her arms. Wearing a fitted dark brown top and charcoal leggings,
barefoot on a cream woven cotton mat.

Composition: photographed from the SIDE at mat height, camera low on the floor, her whole
body in profile so the pose forms one clean triangular silhouette against the wall. Full
body in frame, vertical composition, centred, with clear space above her hips. Keep the
bottom quarter simple — plain mat and floor — and the top-left corner plain.

Setting: a completely plain dark espresso-brown wall behind her that falls away to near
black. No furniture, no props, no windows visible.

Light: warm rim light from the right, tracing a bright continuous edge along her back, hips
and legs, so the outline of the pose reads instantly. Her front and face stay in deep
shadow — this is a shape, not a portrait.

Colour and mood: espresso brown, cream and honey gold, very high contrast with deep clean
blacks. Absolutely no blue, no teal, no cyan, no grey cast. Graphic, strong, iconic.

Detail: woven mat weave, tendon and muscle definition catching the rim light, fine natural
film grain, razor-sharp along the lit edge.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage, extra
limbs, plastic or over-smoothed skin, HDR glow, oversaturation.
```

---

### 8. `breath-01.jpg` — Alternate-nostril breathing

| | |
|---|---|
| **Final size** | 900 × 1125 px (4:5) |
| **Generate at** | 3:4, then crop to 900 × 1125 |
| **Appears** | Gallery tile, badge "Daily", caption "नाड़ी शोधन — Alternate nostril" |
| **Upload first** | *Optional:* `assets/images/shraddha-portrait.jpg` — useful here even though the face is cropped, so the skin tone and hands match her |

```
Photorealistic editorial close-up photograph, 3:4 vertical portrait aspect ratio, output at
the highest resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame
camera, 85mm macro lens at f/2, natural low light.

Subject: a tight vertical crop of an Indian woman's right hand raised to her face in
nadi shodhana pranayama — thumb gently closing her right nostril, index and middle fingers
folded to the brow, ring finger resting near her left nostril. Her eyes are closed and only
the lower half of her face, her hand and her wrist are in frame. The top of her head is
cropped out.

Composition: hand and lower face fill the upper two-thirds of the frame. Keep the bottom
quarter simple — plain dark background only — and the top-left corner plain.

Setting: a deep brown background falling off to black. Nothing identifiable behind her.

Light: one low warm lamp from the left, skimming across her knuckles, cheekbone and lips,
with the right side of the frame in near darkness.

Details on her: visible skin texture and pores, fine hairs catching the rim light, a thin
plain gold ring on one finger, a faded red thread bracelet on her wrist, neatly trimmed
unpainted nails.

Colour and mood: warm brown, amber and deep shadow. Absolutely no blue, no teal, no cyan,
no grey cast. Intimate, still, private — a moment you are almost intruding on.

Detail: macro-level skin and fabric texture, fine natural film grain, tack-sharp on the
fingers and lips, shallow depth of field with a soft background.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage, extra
fingers, malformed hands, plastic or over-smoothed skin, HDR glow, oversaturation.
```

> Hands are what generators get wrong most often. Count the fingers before you use it, and
> generate four or five versions of this one.

---

### 9. `breath-02.jpg` — Yoga nidra

| | |
|---|---|
| **Final size** | 900 × 1125 px (4:5) |
| **Generate at** | 3:4, then crop to 900 × 1125 |
| **Appears** | Gallery tile, badge "Evening", caption "योग निद्रा — Yoga nidra" |
| **Upload first** | *Optional:* the finished `breath-01.jpg`, as a style reference |

```
Photorealistic editorial wellness photograph, 3:4 vertical portrait aspect ratio, output at
the highest resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame
camera, 35mm lens at f/2.8, one practical lamp for light.

Subject: an Indian woman in her early thirties lying in savasana on a cream woven cotton
mat in a dim room in the evening — flat on her back, arms relaxed a little away from her
sides, palms up, feet falling open, a thin oatmeal-coloured wool blanket drawn to her ribs.
Her eyes are closed and her face is relaxed and turned slightly away from the camera.

Composition: photographed from ABOVE and slightly to the side, looking down along the
length of her body, full body in frame, vertical composition. Keep the bottom quarter of
the frame simple — plain floor and mat — and the top-left corner plain.

Setting: a worn teak floor, a dark brown wall at the edge of the frame, a small folded
towel under her head. Nothing else.

Light: a single low warm lamp just out of frame casting long soft shadows across the mat
and the folds of the blanket, the far side of the room dropping into darkness.

Colour and mood: espresso brown, oatmeal, cream and warm amber. Absolutely no blue, no
teal, no cyan, no grey cast. Deeply restful, heavy-limbed, the end of a practice.

Detail: wool blanket fibres and soft folds, woven mat weave, floorboard grain, fine natural
film grain, sharp on the blanket texture, gentle falloff into shadow.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage, extra
limbs, plastic or over-smoothed skin, HDR glow, oversaturation.
```

---

# Social share card

### 10. `og-image.jpg`

| | |
|---|---|
| **Final size** | 1200 × 630 px (1.91:1) |
| **Appears** | The preview image on WhatsApp, Instagram, Facebook, LinkedIn and X |
| **Upload first** | Not applicable — see below |

**Leave this one alone.** It already has the headline, the logo and Shraddha's real photo
composed onto it, and a generator cannot produce legible type. If you want to redesign it,
do it in Figma or Canva at 1200 × 630 and keep four things: her portrait on the right, the
logo top-left, "From stress to strength." as the headline, and a warm brown background.

---

# Optional add-on: putting the logo into a photo

Generators cannot invent her logo. If you want it on a studio wall, a banner or a t-shirt in
a generated scene:

**Upload first:** `assets/images/logo.png` **plus** the generated scene you want it added to.

Then use this as the prompt:

```
Using the second image as the scene and the first image as the exact logo artwork, place
the logo naturally onto [the plain brown wall behind her / the front of her dark brown
t-shirt / a small wooden sign by the door]. Reproduce the logo exactly as supplied — the
same cream circular mark with the figure inside the letter S — do not redraw it, do not
change its proportions, do not add or remove any part of it, do not add any text.

Match it to the scene: follow the perspective and curve of the surface, match the existing
warm light direction and intensity, add the same fabric or wall texture over it, and match
the film grain of the photograph. It should look printed or painted on, not pasted.
```

Check the result closely — the "S" and the figure inside it are easy for a model to mangle.
If it comes out wrong, composite it manually in Photopea instead.

---

# Do not AI-replace these

| File | Size | What it is |
|---|---|---|
| `shraddha-portrait.jpg` | 940 × 1175 | Shraddha, "Meet Shraddha" section |
| `shraddha-square.jpg` | 700 × 700 | square crop, spare |
| `shraddha-wide.jpg` | 1200 × 800 | wide crop, spare |
| `practice-01.jpg` | 900 × 1125 | warm sepia gallery tile of her |
| `practice-02.jpg` | 900 × 1125 | gallery tile showing the branded tee |
| `logo.png` | 1024 × 1024 | her actual logo, extracted and cleaned |
| `icon-192 / 512 / maskable / apple-touch / favicon` | various | app icons built from the logo |
| `mark-cream.png`, `mark-brown.png` | 512 × 512 | logo shape on transparent, for overlays |

All five photo crops came from the video frame you sent, with the caption cropped out.

---

# The better option

Ask Shraddha to shoot the set herself — a portrait, three or four poses, one wide studio
shot and one on the aerial silks. It costs an hour with a phone on a tripod near a window,
and it beats anything generated, because a yoga studio's credibility rests on the teacher
being real. A visitor who spots a synthetic face on a wellness site stops trusting
everything around it.

The aerial silks especially: it's her actual differentiator, it photographs beautifully, and
no generator will get the rigging, the wraps or the body weight in the fabric right.

If you do use AI images of people on the live site, tell her they're AI so she can decide.
That's her reputation, not the website's.
