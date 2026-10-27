# Brand spec — angel numbers app (working name: "noticed")

Status: v1 locked. This document is the single source of truth for the visual
and voice system. The canonical reference artifact is the daily reading card
(day and night variants), specified in full below. Everything else in this
doc is supporting system around that card.

---

## 1. Positioning

**Category:** angel numbers / numerology, but positioned against the category
norm, not inside it.

**What the category looks like:** pastel purple, cosmic gradients, celestial
iconography, gentle-oracle voice (Co-Star: cold-ominous; most others:
soft-affirming).

**What this app looks like:** literary and editorial. Warm neutral paper
tones, one confident accent, an expressive serif, dashed construction
geometry instead of stars-and-moons. Closer to a beautifully printed almanac
or a field-notes journal than a horoscope app.

**North star sentence:** *the friend who loves you too much to let you lie to
yourself.*

**The claim the visual system makes:** there is hidden order, and the app is
revealing it — not "something magical happened to you by chance." This is why
geometry (construction, instrument, pattern) is the ambient visual language,
and why the spark/wave motif was demoted to a rare celebration accent rather
than the default (see §6).

**Reflection, not prophecy:** the product doesn't claim the universe is
sending messages. It treats a repeatedly-noticed number as an occasion for
honest self-reflection. This is both the ethical line and the reason the
founder can write this content without believing in numerology literally —
the copy works whether the reader takes it as mystical sign or psychological
prompt.

---

## 2. Voice

**Register:** blunt but loving. Short, declarative sentences. Names the
user's avoidance specifically. Never hedges ("the universe might be
suggesting..."). Never scolds. Ends on a door, not a diagnosis.

**Not Co-Star:** Co-Star is blunt with indifference — a distant oracle that
doesn't care if you listen. This voice is blunt *with allegiance* — a friend
who's invested in you specifically. Keep ~85% of the punchiness of a cold
register; swap indifference for investment. That's the entire differentiator
from the category's other blunt option.

**Modulation levels** — the voice must flex by number, not stay at one
intensity everywhere:

- **Level 1 (gentle):** grief/comfort numbers. Never punch down at someone
  who's clearly hurting. This is not a brand exception — it's the rule that
  proves the "loving" half is real and not just a marketing wrapper on
  coldness.
- **Level 2 (default):** the friend who's onto you. Warm confrontation,
  ends with an invitation ("so what's the holdup?"). This is the voice for
  the canonical card.
- **Level 3 (max blunt):** reserved for avoidance-themed numbers (444, 999).
  Still never a command ("Move.") — always phrased as the user's own
  agency, even at max intensity.

**Two-beat copy structure**, used everywhere from daily readings to push
notifications: [observation, roman] + [challenge, italic in accent color].
The typographic split (roman vs. italic-accent) *is* the modulation made
visible — see §4.

**Words/phrasing to avoid:** "the universe is telling you," any hedge
language, any command-form imperative, cosmic-whisper vocabulary (aura,
vibration, divine timing).

---

## 3. Color

Two palettes, day and night. Both are token-mapped so theme switching is a
value swap, not a redesign.

### Day palette

| Token | Hex | Use |
|---|---|---|
| `ground` | `#FAF4EC` | background ("blush bone") |
| `ink` | `#4A3F37` | primary text, wordmark, the numeral ("espresso") |
| `body` | `#5C5148` | reading body copy |
| `voice` | `#7A4A5C` | accent — plum. Labels, italic challenge lines, CTAs, vertex dots |
| `hairline` | `#EADFCE` | dividers, lighter ornament tone ("oat") |
| `hairline-strong` | `#DECFB8` | darker ornament tone, mid-rings |
| `whisper` | `#A8988A` | muted metadata (dates, stat lines) |

### Night palette

| Token | Hex | Use |
|---|---|---|
| `ground` | `#1E1A16` | background (card contexts) / `#17140F` (full-bleed hero contexts) |
| `ink` | `#F0E8DA` | primary text, numeral ("moon bone") |
| `body` | `#C9BEAD` | reading body copy |
| `voice` | `#B98CA0` | accent — lifted plum (soft variant; see note below) |
| `hairline` | `#3E362E` / `#3A322A` | ornament, dim tier |
| `hairline-strong` | `#4C4236` / `#453B31` | ornament, mid tier |
| `hairline-spoke` | `#5C4F3D`–`#7A6B54` | full-bleed hero-scale ornament (brighter — see §7 visibility note) |
| `whisper` | `#8A7C68` / `#8A7E6F` | muted metadata |

**Accent history / decision record:** original accent was terracotta
(`#C06A45` day / `#D67E56` night, "ember"). Superseded by **plum** to nudge
the palette "ever so slightly more mystical" — plum's violet undertone reads
as old book bindings / wine / wax seals (a *literary* mysticism) rather than
category-standard purple. Two lift levels tested for night: soft (`#B98CA0`,
adopted) vs. brighter (`#C99DB0`, kept as fallback if soft under-performs on
real OLED blacks).

**Contrast notes:**
- Day: `ink` and `body` pass AA on `ground` at all sizes. `voice`
  (plum `#7A4A5C`) is borderline at small sizes — reserve for large/bold text,
  labels with letter-spacing, underlines. Never body-size long-form text.
  `whisper` is decorative-contrast only — metadata, never required reading.
- Night: values are deliberately dimmed below max contrast on purpose — this
  is a screen meant to be read in a dark room at 11:11pm, not a flashlight.
  Don't "fix" this toward higher contrast without remembering why it's dim.

---

## 4. Typography

**Display / numerals / voice moments:** **Fraunces** (Google Fonts, free,
variable — supports optical size axis `opsz` and weight axis). This is the
confirmed pick after a six-font bake-off (see decision record below).

- Hero numeral: weight 300, large size (76–96px depending on layout),
  line-height 0.95, letter-spacing -0.01em.
- Body reading copy: weight ~340, 16.5px, line-height 1.6.
- Voice/challenge lines and wordmark: italic, weight 400.
- Labels (small caps-style): plain grotesk, not Fraunces — see below.

**UI chrome / labels / metadata:** a plain grotesk — Inter or General Sans.
Kept deliberately boring; all personality lives in the serif. Letter-spacing
~0.1–0.16em on small label text (e.g. "ALIGNMENT ◆ THE THRESHOLD").

**Two-register copy in one card:** roman weight for observation, italic +
accent color for the challenge line. This is a type-level implementation of
the voice's modulation — don't collapse it to one style.

**Font decision record (rejected candidates, for context if revisited):**
- *Instrument Serif* — trendy, sharp, gorgeous numerals, but single-weight
  (can't do the roman/italic voice split) and risks dating fast.
- *Cormorant* — too delicate/gentle; fights the "blunt" half of the voice.
- *Newsreader* — great body italic, weak display numerals; consider as a
  future body-text companion in a two-serif system, never for the logo.
- *Playfair Display* — eliminated specifically for being the most
  overexposed serif in the manifestation/wellness Canva-template space.
  Audience will recognize it as a template.
- *EB Garamond* — literary but wrong century; reads "printer's classic," not
  modern editorial.

---

## 5. Ornament system — the geometry

**What it means:** the ambient dashed geometry is the visual expression of
"there is hidden order, and it's being revealed." Circles = the cycle
(recurrence, the number coming back); diamonds = the moment (the point of
significance, "you noticed"). Circle-holds-diamond-holds-number is the
system's whole cosmology in one glyph.

**Construction rules:**
- Dash rhythm: `stroke-dasharray: 2.5 4.5` (card scale) or `3 5` (hero/full-
  bleed scale). Stroke width 1px (card) to 1.3px (hero).
- Two-tone layering is mandatory: circles in the lighter hairline tone,
  diamonds one step darker (or vice versa per layer) — this is what makes
  overlapping dashed shapes read as *depth* rather than clutter. Never flatten
  to one tone.
- Vertex dots in `voice` color mark points of significance. **Cap at 3 per
  card-scale composition, 4 for full-bleed/cardinal compositions.** More
  than that reads as clutter, not constellation.
- The ornament zone is for *number territory only*. The moment body prose
  begins, geometry stops — reading text sits on clean ground. This zoning is
  what keeps the brand literary instead of tipping into "blueprint app."
- Full-bleed / hero-scale compositions may add a fourth layer: dashed spokes
  reaching past the visible frame edge, implying the pattern continues beyond
  what's shown. Card-scale compositions do not need this layer.

**Icon system:** numeral + one construction circle + one lit vertex dot, on
the lattice. Icon can vary per user's most-noticed number as a premium touch.

**Gender/tone calibration note:** an earlier isometric-lattice version of
this system (dashed triangular grid) was tested and rejected — it read
correctly "constructed" but tipped toward drafting-table/technical, which
skewed masculine against the intentionally warm, feminine-leaning palette.
Circles-and-diamonds reads celestial/jewelry instead of blueprint, and is the
adopted direction. **If any future exploration of this system starts to read
"engineering paper," lighten the ornament — don't darken the ground.**

---

## 6. The wave / mark motif — demoted to celebration-only

An earlier exploration exploded the ornament into a dense, flowing wave of
small scattered marks (sparks, diamonds, dots, crosses) inspired by vintage
firework-label ephemera. It's charming and produces excellent motion, but **it
is not the ambient identity** — it makes the wrong metaphysical claim
("something happened by chance / celebration") versus the geometry's claim
("hidden order, being revealed").

**Where it's allowed:** small, rare celebratory bursts only — logging a
sighting, hitting a streak milestone. Not the daily reveal, not the ambient
brand surface.

**Mark vocabulary** (kept for celebration-burst use): four-point spark
(never five-point — five-point drifts into horoscope-app stars), diamond,
dot, thin cross. Hand-jittered, never on a grid.

**Spacing rule (important — this was a real bug, fix it early):** marks
placed via naive random scatter will overlap and look messy, not
hand-set. Use **stratified sampling along the path** (divide the arc into N
equal segments, one candidate mark per segment) **plus collision rejection**
(candidate position must clear all placed neighbors by the sum of both radii
plus a fixed gutter, ~5px at this scale, or reroll). This combination is what
produces the "hand-set letterpress" quality instead of digital confetti.

**Generator parameters to expose:** mark count, gutter width, band breadth.
Denser + tighter gutter = festive (streak burst); fewer + wider gutter =
contemplative (not currently used, but available).

---

## 7. Motion

Two animation recipes, both cheap to implement natively (no physics engine,
no Lottie required for v1 — though Lottie export is a reasonable v1.1 path
if designers need to tune timing independent of code).

### 7a. Construction reveal (primary — use for the daily card)

The instrument builds *before* the number arrives. Order matters: structure
precedes meaning, enacting the brand's core claim every time the app opens.

Sequence (from the canonical card, ~3s total):
1. Rings trace in from center outward, **overlapping** (each starts before
   the previous finishes — this reads as ripples; strictly sequential reads
   as a loading spinner). Roughly: ring 1 delay 100ms/550ms duration, ring 2
   delay 350ms/650ms, ring 3 delay 650ms/750ms.
2. Diamonds draw edge-by-edge, small then large (delay ~950ms/600ms, then
   ~1250ms/650ms).
3. Ticks/spokes appear (delay ~1550ms).
4. Vertex dots settle with **overshoot easing** — this is the *only* spring
   in the whole sequence (delay ~1950ms, staggered ~100ms apart per dot,
   `cubic-bezier(0.34, 1.56, 0.64, 1)`). Restraint rule: if everything
   springs, nothing feels punctuated. One overshoot moment = the punctuation.
5. Number fades up with slight scale (delay ~2250ms), then label (~2450ms),
   then reading text (~2650ms), then challenge line (~2800ms), then
   footer/CTA (~2950ms+).

**Implementation:** the draw-on effect shown in web mockups uses an SVG mask
trick (solid stroke revealing a dashed path underneath, animating
`stroke-dashoffset` from 100 to 0 with `pathLength="100"` normalization).
**In SwiftUI this is simpler** — use `.trim(from:to:)` on the `Shape`'s path,
animated; dashes included natively, no mask needed.

**Visibility note (a real bug encountered — check this early in the real
build):** at hero/full-bleed scale on the darkest night ground, ornament
strokes can be tuned dim enough to disappear entirely rather than merely
recede. If a QA pass says "I can't see the geometry," lift the stroke color
toward the brighter end of the hairline range and confirm stroke-width is at
least 1.3px at that scale — don't just add opacity, actual hue-lightness
needs to move.

**Coordinate-system bug to avoid (also hit once — worth a permanent note):**
keep ornament (SVG) and text/UI (HTML) on **one shared coordinate system**,
not two independently-centered layers (e.g. SVG centered via explicit cy vs.
text centered via flexbox auto-centering on a different reference frame).
Mismatched centers is an easy, non-obvious bug. Prefer: set the SVG
`viewBox` dimensions equal to the container's actual content-box pixel
dimensions, then position all text elements with absolute pixel coordinates
in that same unit space. One coordinate system, no drift.

### 7b. Celebration burst (secondary — use for wave/mark motif only)

Marks pop in sequentially along the arc's parameter `t` (not randomly) —
duration ~1.1s end-to-end for the full sweep, each individual mark ~420ms
with overshoot easing (`cubic-bezier(0.34, 1.56, 0.64, 1)`), plus up to
~120ms of *per-mark* random jitter on top of the sequential delay. The
jitter is load-bearing: without it, the sweep reads as a mechanical cascade;
with it, it reads like sparks catching one at a time.

---

## 8. Canonical reference artifact — the daily reading card

This is the artifact to build first and match everything else against.

**Layout (card, ~300px wide mobile reference):**
- Header row: wordmark "noticed" (italic Fraunces, left) / date (grotesk,
  muted, right).
- Hero zone: construction-animated ornament (3 rings + 2 diamonds + ticks +
  3 vertex dots, per §5) surrounding the numeral. Numeral centered in the
  ornament's own center point — not the card's overall center — matching
  ornament and number to the same coordinate origin.
- Label below numeral: small caps grotesk, letter-spaced, `voice` color.
  Format: "[TRADITIONAL MEANING] ◆ [SHORT PHRASE]" (e.g. "ALIGNMENT ◆ THE
  THRESHOLD").
- Body: two-beat copy per §2 — roman observation, then italic-`voice`
  challenge line.
- Footer: divider hairline, then stat (muted, left — "Seen N times this
  week") and CTA (italic, underlined, `ink`/`voice` — "be honest →") on one
  row.

**This exact composition is theme-flexible** — the day and night palettes
in §3 apply directly to this layout with no structural changes, confirming
the token system works as designed.

**Explicitly not the canonical daily screen (kept as situational
alternatives, not replacements):**
- The full-bleed "ceremonial open" composition (large centered numeral, no
  card chrome, spokes reaching past the frame) — reasonable for a cold app
  launch or as a transition state *before* resolving into the daily card,
  not for daily/repeat use.
- The fully-chromed "app screen" variant (top nav bar, primary CTA button,
  stat + divider) — useful reference for how the system extends to a
  more conventional screen with navigation, but the quieter card above is
  the better everyday object. If a screen needs a primary button (vs. a
  quiet text CTA), that's the pattern to borrow from.

---

## 9. Open items / not yet decided

- Final app name (working name "noticed" used as placeholder throughout;
  candidates were explored in the "seeing/noticing" and "blunt-friend" name
  territories — no naming/trademark/handle-availability check has been done).
- Whether the celebration-burst wave motif ships in v1 at all, or is a v1.1
  addition once the core card is validated.
- License/typeface decision if moving beyond Google Fonts (Ogg, Canela,
  Editorial New, Zodiak/Sentient were noted as premium alternatives if
  budget allows later — not required for v1, Fraunces is sufficient).
- Auto dark-mode behavior (follow system vs. follow local sunset time) —
  flagged as a small feature this specific audience would likely love, not
  scoped yet.
