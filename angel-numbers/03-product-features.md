# 03: Product Features (what to implement)

Legend: **[Decided]** = settled in conversation. **[Proposed]** = a reasonable default suggested but not confirmed by the user.

## Product loop in one line

User notices a number → opens app → quiz personalizes → hard paywall → daily reading card + sighting log + notifications keep them returning.

---

## Feature 1: Onboarding quiz funnel [Decided structure, Proposed details]

The funnel is the conversion engine. It must sound like the brand voice from the first question, not generic wellness onboarding.

**Flow:**
1. **Number picker:** "What number keeps following you around?" Options: 111, 222, 333, 444, 555, 777, 888, 999, 11:11, other.
2. **Reflection prompt:** "Be honest: what were you thinking about the last time you saw it?" (free text or a few tap options; answer is used to personalize the paywall).
3. **Frequency/context:** how often, and where (clock, receipts, plates, dreams).
4. **Personalized reveal:** the construction animation plays (see `06`), then the chosen number and a short reading land.
5. **Commitment moment:** a "contract" screen with a checkbox: *"I'm done pretending I don't notice."* (Decided concept; this is the equivalent of the "I commit to myself" pattern from addiction-quit apps.)
6. **Hard paywall.**

**Requirements:**
- No account creation before the paywall.
- Quiz answers persist locally and feed paywall copy and the first daily reading.
- Back navigation allowed within the quiz; no skip route around the paywall.

## Feature 2: Paywall [Decided model, Proposed layout]

- Hard paywall: no dismiss path that grants access.
- Yearly plan (primary), 3-day free trial, optional weekly plan as a price anchor, restore-purchases link.
- Copy in the blunt-friend voice, personalized from quiz answers. Example: *"You've checked what 444 means four times this week. Something's going on. Let's actually look at it."*
- Uses the same visual system as the daily card; the geometry and (optionally) the staggered mark grid as a background texture. **This screen has not been mocked visually.**
- Implementation: RevenueCat + StoreKit (iOS first), then Play Billing.

## Feature 3: Daily reading card [Decided; canonical screen]

The screen the user sees every day. Layout, top to bottom:

1. **Header row:** italic wordmark ("noticed") left, date right (grotesk, muted).
2. **Hero zone:** the construction geometry (3 rings, 2 diamonds, tick marks, 3 accent vertex dots) around the numeral.
3. **Label:** small caps, letter-spaced, accent color. Format `[TRADITIONAL MEANING] ◆ [SHORT PHRASE]`, e.g. `ALIGNMENT ◆ THE THRESHOLD`.
4. **Body:** two-beat copy: a roman observation, then an italic accent-color challenge line.
5. **Footer:** hairline divider; left: stat ("Seen 4 times this week"); right: text CTA ("be honest →").

Night variant: same layout, tokens swapped (see `05`). The reveal animates every time the card opens (see `06`).

## Feature 4: Number content library [Decided need, Proposed schema]

Every number needs its own hand-written entry; a template with digits swapped will read as generic.

**Suggested entry schema:**
```json
{
  "id": "444",
  "label": "STABILITY ◆ THE FOUNDATION",
  "traditionalMeaning": "stability, foundation, protection",
  "tone": 3,
  "observation": "…roman paragraph…",
  "challenge": "…italic closing question…",
  "notification": "…short push copy…",
  "variants": ["optional additional readings so repeat views stay fresh"]
}
```

**Voice level per number** (see `04`): Level 1 gentle for grief/comfort numbers, Level 2 default, Level 3 max blunt for avoidance numbers (444, 999). Plan multiple readings per number so a user who sees 444 five times in a week is not shown the same text.

## Feature 5: Sighting log and stats [Proposed]

- One-tap "I saw this" with the number and an optional note.
- Powers the stat line ("Seen 4 times this week") and streak / milestone moments.
- Logging triggers a short celebration animation (the mark-burst motif; see `05`/`06`).
- Storage: local-first (SQLite / SwiftData / equivalent). No backend required for v1.

## Feature 6: Push notifications [Proposed]

- Copy is written to be screenshot-shareable. Example for 11:11: *"It's 11:11. You thought of it immediately. That's your answer. You didn't need the clock."*
- Daily notification at a user-chosen time; optional timed notifications at "angel hours" (e.g., 11:11, 3:33).
- Notification copy is part of the number entry schema above.

## Feature 7: Theming [Decided]

- Day and night themes via semantic tokens (`ground`, `ink`, `body`, `voice`, `hairline`, `whisper`), so switching is a value swap.
- Night is the primary real-world context (people check clocks at night). Night values are intentionally dimmed.
- Theme trigger (follow system vs follow sunset) is **not yet scoped**.

## Feature 8: Shareable cards [Proposed, not designed]

- Export a reading or sighting as an image using the geometry (or the staggered mark grid as an endpaper-style background).
- Natural organic distribution; also a UGC asset for the builder.

## Feature 9: App icon [Decided concept]

- The numeral on a dark or light ground, one dashed construction circle, one lit accent vertex dot.
- Optional premium touch: user can set the icon to their most-noticed number.

## Suggested MVP cut (one-week-ish scope)

Must ship: onboarding quiz → reveal → paywall → daily card → local sighting log → one notification time → day/night theme → ~10–15 number entries with 2 readings each.

Defer to v1.1: shareable cards, celebration burst, icon variants, timed "angel hour" notifications, additional reading variants, Android.

## Analytics worth instrumenting from day one [Proposed]

Quiz step completion, paywall view rate (target ≥80% of installs), trial start rate, download-to-paid (hard-paywall median is ~10.7% by day 35; if below ~3% after ~1,000 installs, iterate quiz and paywall copy before buying more traffic).
