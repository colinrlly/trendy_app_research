# 05: Visual Design System

## Design thesis

Literary and editorial, not cosmic. Warm paper tones, one confident accent, an expressive serif, and dashed construction geometry instead of stars and moons. It should feel like a beautifully printed almanac or field-notes journal. The geometry says "there is hidden order, and it's being revealed," which is numerology's actual thesis.

**Soft surface, sharp tongue:** keep the visuals warm and beautiful while the copy stays pointed. If both go soft, the brand drifts onto the pastel shelf; if both go hard, it's Co-Star.

## Palettes

### Day

| Token | Hex | Use |
|---|---|---|
| `ground` | `#FAF4EC` | Background ("blush bone") |
| `ink` | `#4A3F37` | Numeral, wordmark, primary text ("espresso") |
| `body` | `#5C5148` | Reading body copy |
| `voice` | accent (see below) | Labels, italic challenge lines, CTA underline, vertex dots |
| `hairline` | `#EADFCE` | Dividers, lighter ornament tone ("oat") |
| `hairline-strong` | `#DECFB8` | Darker ornament tone |
| `whisper` | `#A8988A` | Dates, stat lines (decorative contrast only) |

### Night

| Token | Hex | Use |
|---|---|---|
| `ground` | `#1E1A16` (card) / `#17140F` (full-bleed hero) | Background |
| `ink` | `#F0E8DA` | Numeral, primary text ("moon bone") |
| `body` | `#C9BEAD` | Reading body copy |
| `voice` | accent (see below) | Same roles as day |
| `hairline` | `#3E362E` (`#3A322A` hero) | Dim ornament tier |
| `hairline-strong` | `#4C4236` (`#453B31` hero) | Mid ornament tier |
| `hairline-hero` | `#5C4F3D` / `#6E5F49` / `#7A6B54` | Full-bleed hero-scale ornament (brighter so dashes stay visible) |
| `whisper` | `#8A7C68` / `#8A7E6F` | Dates, stat lines |

Night values are deliberately below max contrast: this screen is read in a dark room at 11:11 PM, not as a flashlight to the face.

## Accent color: OPEN DECISION

| Option | Day | Night | Character |
|---|---|---|---|
| **Terracotta** | `#C06A45` | `#D67E56` ("ember") | Warm, earthy, celebratory; pops against bronze ornament; reads friendlier |
| **Plum** | `#7A4A5C` | `#B98CA0` soft lift (`#C99DB0` brighter fallback) | Literary-mystical: old book bindings, wine, wax seals; quieter, blends more with bronze |

- Plum was introduced to lean "ever so slightly more mystical." The builder then asked to see terracotta again with the mark patterns and has not chosen.
- Alternatives considered: dusty amethyst `#776080` (too cool; drifts toward Co-Star's register), deep garnet `#8C3B3E` (barely more mystical than terracotta). A slightly redder plum `#82495A` is a possible hedge.
- Contrast: terracotta on blush bone is near the AA threshold, so use it for large/bold text, tracked labels, and underlines, never small body text. Plum at `#7A4A5C` is similarly borderline at small sizes. Both are fine for the vertex dots.
- **Pick one before building**; keep the other documented as the superseded option.

## Typography

**Fraunces** (Google Fonts, free, variable with `opsz` and weight axes): confirmed after a six-font comparison.

| Role | Settings |
|---|---|
| Hero numeral | Weight 300, 76–96px, line-height 0.95, letter-spacing -0.01em; use a high optical size |
| Reading body | Weight ~340, 16.5px, line-height 1.6 (low optical size) |
| Challenge line, wordmark, CTA | Italic, weight 400 |
| Labels / UI chrome | Plain grotesk (Inter or General Sans): ~12px, tracking 0.1–0.16em; the chrome recedes, personality lives in the serif |

Rejected: Instrument Serif (single weight, no roman/italic voice split, trendy), Cormorant (too delicate), Newsreader (great body, weak numerals; possible future body companion), Playfair Display (overexposed template serif), EB Garamond (wrong century). Premium alternatives if budget ever allows: Ogg, Canela, Editorial New, GT Sectra, Tiempos Headline; free: Zodiak, Sentient.

## The ornament system: three candidates, one hero

### 1. Construction geometry: HERO (repeated favorite)

Dashed concentric circles, inscribed diamonds, tick marks, and accent vertex dots. Circles mean the cycle (recurrence); diamonds mean the moment (the point of significance). Circle holds diamond holds number.

Card-scale reference (SVG viewBox `0 0 288 300`, center `144,152`):
- Circles: r = 50, 86, 118
- Inner diamond: `M144 66 L230 152 L144 238 L58 152 Z`
- Outer diamond: `M144 34 L262 152 L144 270 L26 152 Z`
- Ticks: `M144 30 v-10 M144 274 v10 M22 152 h-10 M266 152 h10`
- Vertex dots (accent, r≈2.2): `(144,34)`, `(230,152)`, `(58,152)`
- Stroke: 1px, `stroke-dasharray: 2.5 4.5`. Hero/full-bleed scale: 1.3px, `3 5`.

Rules:
- **Two-tone layering is mandatory:** alternate lighter/darker hairline tones across circles and diamonds so overlapping dashes read as depth, not clutter. Never flatten to one color.
- **Max 3 accent dots on a card-scale composition (4 on full-bleed cardinal compositions).**
- **Zoning:** geometry lives behind the numeral only. Once prose begins, geometry stops and the reading sits on clean ground.
- Full-bleed variant may add dashed **spokes** extending past the frame edge, implying the pattern continues.
- If the system ever reads "engineering paper," lighten the geometry; don't darken the ground. (A dashed isometric triangle lattice was tried and rejected for reading technical/masculine.)

### 2. Staggered mark grid: ENDPAPER TEXTURE (untested in that role)

A dense brick lattice (every other row offset half a cell) of four small marks: four-point spark, diamond, dot, thin cross. At ~22px columns / 20px rows it reads as printed endpaper or pressed-tin tile. It conflicts with the construction rings on the same surface, so use it as a full-bleed background for onboarding, paywall, or share cards, not on the daily card. Marks use varied dim bronze tones with accent on roughly 1 in 5. Natural implementation: an SVG `<pattern>` tile.

### 3. Diagonal flowing wave: CELEBRATION ACCENT (most delightful, weakest thesis fit)

Marks drift along a meandering centerline from top-left to bottom-right, widest and largest at the spine, collision-free. Derived from a vintage firework-label reference (single ink on kraft, hand-placed marks, irregular sizes). It makes the claim "serendipity / something streamed past," which is the opposite of the geometry's "hidden order," so it is best kept for sighting-log confirmations and streak milestones. If the builder decides this is the hero, resolve the accent color and how the reading text coexists with it first.

**Mark vocabulary (all wave/grid treatments):** four-point spark (never five-point; that reads horoscope), diamond, dot, thin cross; hand-jittered, never perfectly aligned.

## Fleuron

The small solid diamond doubles as the brand's typographic ornament: label separators (`ALIGNMENT ◆ THE THRESHOLD`), dividers, list markers.

## Icon

Numeral on a ground with one dashed construction circle and one accent vertex dot. Could vary per the user's most-noticed number as a premium touch.

## Other screens explored

- **Full-bleed "ceremonial open" screen:** large centered numeral, geometry filling the frame with spokes, four accent dots, tagline "SOMETHING IS ASKING TO BE SEEN." Suitable for a cold launch or as a transition before the daily card resolves; not for daily use.
- **Fully chromed "app screen" variant:** top bar (date, wordmark, close), numeral with geometry, label, reading line, divider, stat, and a filled pill button ("see your reading →", dark ink on lifted accent). Useful reference for how a primary button looks in this system; the quieter card remains the everyday screen.
- **Night variant of the daily card:** same composition, tokens swapped.

## Tokens: implement as semantic names from day one

`ground`, `ink`, `body`, `voice`, `hairline`, `hairline-strong`, `whisper`. Theme switching is then a token swap, not a refactor.
