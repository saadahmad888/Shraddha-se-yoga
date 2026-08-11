# Missing images — prompts

Three files are missing from your `assets/images/` folder. That's why those cards render
empty with grey alt text:

| Missing file | Size | Where it shows |
|---|---|---|
| `shraddha-portrait.jpg` | 940 × 1175 (4:5) | "Meet Shraddha" section **and** the last gallery tile |
| `practice-01.jpg` | 900 × 1125 (4:5) | Gallery tile — badge "Before class" |
| `practice-02.jpg` | 900 × 1125 (4:5) | Gallery tile — badge "Studio" |

**You already have these — I've re-attached them with this message.** They're real crops of
Shraddha from the video frame you sent, so drop them straight into `assets/images/` and the
three empty cards fill in. That's the right fix: they're photographs of the actual teacher.

The prompts below are only for the case where she wants a stand-in until she shoots a proper
set. Each one is self-contained — ratio, size, style and negatives are all inside the prompt.

Two things worth deleting while you're in there: `shraddha-square.jpg` and
`shraddha-wide.jpg` are no longer referenced by `index.html`. Remove them.

---

## Workflow reminder

1. Generate at the ratio the prompt names (generators can't take pixel sizes).
2. Crop and resize to the exact pixels with squoosh.app, photopea.com, or:
   ```bash
   magick input.png -resize 900x1125^ -gravity center -extent 900x1125 -quality 84 practice-01.jpg
   ```
3. Save with the exact filename into `assets/images/`.
4. Change `const V = 'ssy-v2'` to `'ssy-v3'` in `sw.js`, or cached copies will persist.

---

### 1. `shraddha-portrait.jpg`

| | |
|---|---|
| **Final size** | 940 × 1175 px (4:5) |
| **Generate at** | 3:4, then crop to 940 × 1175 |
| **Appears** | The "Meet Shraddha" card with the gold offset frame and name plate, plus the last gallery tile |
| **Upload first** | **Required if you want it to be her** — attach the original frame you sent me (the seated photo in the brown branded tee). Without it you'll get a stranger. |

```
Photorealistic editorial portrait photograph, 3:4 vertical aspect ratio, output at the
highest resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame camera,
85mm prime lens at f/2, natural window light only.

Subject: an Indian woman in her early thirties, a yoga teacher, seated upright and facing
the camera with a calm, closed-mouth, unforced expression — self-possessed rather than
smiling. Long dark wavy hair falling loose past her shoulders, thin round wire-frame
glasses, a plain dark espresso-brown long-sleeve fitted top, a fine gold chain at her
neck. Head, shoulders and upper torso in frame.

Composition: centred, head near the top third, shoulders and chest filling the lower
frame, framed so the top of her chest is visible. Vertical composition. Nothing in her
hands.

Setting: a plain pale warm-grey studio wall, completely empty — no props, no plants, no
furniture, no window in shot.

Light: one large soft window light from the front-left, wrapping gently around her face,
a soft shadow falling to the right, no hard edges. Gentle, natural, slightly underexposed
rather than bright.

Colour and mood: espresso brown, warm grey and soft cream. Absolutely no blue, no teal,
no cyan, no grey-blue cast. Grounded, credible, quietly confident — a teacher, not a model.

Detail: visible natural skin texture and pores, individual strands of hair, fabric weave
in the top, real reflections in the glasses, fine natural film grain. Sharp on the eyes.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage,
extra fingers, plastic or airbrushed skin, heavy makeup, HDR glow, oversaturation, a
wide toothy smile.
```

---

### 2. `practice-01.jpg` — "Before class"

| | |
|---|---|
| **Final size** | 900 × 1125 px (4:5) |
| **Generate at** | 3:4, then crop to 900 × 1125 |
| **Appears** | Gallery tile, badge "Before class", caption "श्रद्धा — Setting the intention" |
| **Upload first** | **Required for likeness** — attach the original frame you sent me. Also attach the `shraddha-portrait.jpg` you just generated so the same face carries across both tiles. |

This one is graded warm sepia on the live site, so it should read as a quieter, moodier
version of the portrait rather than a second headshot.

```
Photorealistic editorial portrait photograph, 3:4 vertical aspect ratio, output at the
highest resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame camera,
85mm prime lens at f/1.8, one soft light source.

Subject: a close crop of an Indian woman in her early thirties, a yoga teacher, in a quiet
moment before class — eyes closed or lowered, head tilted very slightly down, lips
relaxed. Long dark wavy hair, thin round wire-frame glasses, plain dark brown top.

Composition: a tight vertical crop from the top of her head to her collarbone, her face
filling most of the frame, slightly off-centre to the left. Keep the bottom quarter of the
frame simple and dark for a caption.

Setting: a deep warm brown background falling away to near black. Nothing identifiable
behind her.

Light: a single soft low light from the left, sculpting one cheekbone and the bridge of her
nose, the right side of her face falling into shadow. Low key, deep shadows, warm.

Colour and mood: strong warm sepia — espresso brown, amber and cream, almost monochrome.
Absolutely no blue, no teal, no cyan. Introspective, still, the breath before beginning.

Detail: visible skin texture and pores, fine facial hairs catching the rim light, hair
strands separated in the light, fine natural film grain. Sharp on the near eye and cheek.

Do not include: text, letters, numbers, logos, watermarks, borders, frames, collage,
plastic or airbrushed skin, HDR glow, oversaturation, smiling at the camera.
```

---

### 3. `practice-02.jpg` — "Studio"

| | |
|---|---|
| **Final size** | 900 × 1125 px (4:5) |
| **Generate at** | 3:4, then crop to 900 × 1125 |
| **Appears** | Gallery tile, badge "Studio", caption "आसन — With Shraddha" |
| **Upload first** | **Two files.** Attach the original frame you sent me for her likeness, **and** `assets/images/logo.png` so the mark on her t-shirt is her real logo rather than an invention. |

The original of this tile shows her branded tee with the gold logo and `#shraddha_se_yoga`
across the chest. That detail is worth keeping — it's free brand recognition.

```
Photorealistic editorial photograph, 3:4 vertical aspect ratio, output at the highest
resolution available, at least 1200 pixels wide. Shot on a 35mm full-frame camera, 50mm
prime lens at f/2.2, natural light.

Subject: an Indian woman in her early thirties, a yoga teacher, seated cross-legged on a
mat facing the camera in a studio, hands resting loosely in her lap, calm neutral
expression, mid-sentence as if teaching. Long dark wavy hair, thin round wire-frame
glasses. She wears a fitted dark espresso-brown long-sleeve t-shirt with a gold printed
logo across the chest — reproduce the logo exactly as supplied in the attached image, the
circular mark with the figure inside the letter S, plus small gold italic text beneath it.
Do not redraw or reinterpret the logo.

Composition: vertical framing from just above her head down to her lap, her torso centred
so the logo on the shirt sits near the middle of the frame and stays fully visible. Keep
the bottom quarter simple for a caption.

Setting: a plain pale warm-grey studio wall behind her, a cream mat beneath her, nothing
else in shot.

Light: soft even daylight from the front-left, gentle shadow to the right, no hard edges.

Colour and mood: espresso brown, gold, warm grey and cream. Absolutely no blue, no teal,
no cyan. Warm, approachable, professional — a real teacher in a real room.

Detail: visible skin texture, hair strands, cotton jersey weave in the t-shirt, the
printed logo sitting on the fabric with the fabric's own texture and folds over it, fine
natural film grain. Sharp on her face and the logo.

Do not include: any text other than the logo supplied, watermarks, borders, frames,
collage, extra fingers, plastic or airbrushed skin, HDR glow, oversaturation.
```

---

### 4. `og-image.jpg` — only if this one is missing too

| | |
|---|---|
| **Final size** | 1200 × 630 px (1.91:1) |
| **Appears** | The link preview on WhatsApp, Instagram, Facebook, LinkedIn and X |

Don't generate this one — image models can't render legible type, and it needs the headline
and logo on it. Two options:

- **Easiest:** use the `og-image.jpg` I sent, or temporarily point the three `og:image` /
  `twitter:image` tags in `<head>` at `assets/images/shraddha-portrait.jpg`. The preview
  will be a plain photo, which is fine.
- **Better:** rebuild it in Canva or Figma at 1200 × 630 — her portrait on the right, the
  logo top-left, "From stress to strength." as the headline, warm brown background.

---

## Checking your work

Open the page, press <kbd>F12</kbd> → **Network** → filter **Img**, and reload. Anything
listed in red is still missing. Every image the site needs is one of these seventeen:

```
logo.png              icon-192.png       favicon-32.png     apple-touch-icon.png
hero-01.jpg           hero-02.jpg        hero-03.jpg        offer-bg.jpg
asana-01.jpg          asana-02.jpg       asana-03.jpg
breath-01.jpg         breath-02.jpg
practice-01.jpg       practice-02.jpg    shraddha-portrait.jpg
og-image.jpg
```

Note that `icon-512.png` and `icon-maskable-512.png` aren't in that list because nothing on
the page loads them directly — `manifest.json` does, for the installed app icon. Keep them.
