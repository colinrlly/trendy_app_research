# Angel Numbers App — Design Brief (First Pass)

> **For Claude Design.** This is a first-pass brief for a consumer iOS app. Generate a cohesive visual design + key screens from it. Brand name, palette, and copy are starting points — treat them as directional, not locked. Optimize hardest for the **onboarding → paywall** flow; that is the revenue engine.

---

## 0. One-line concept

A beautiful, modern app that decodes the **angel numbers** people keep seeing (111, 11:11, 444…) into a **personalized** message — powered by their **numerology** profile — and keeps them coming back with a daily number, affirmations, and a journal to track the signs they notice.

**Positioning:** the *focused, beautiful, honest* angel-numbers app — for people who care about the numbers, not a full astrology suite. The opposite of the dated, ad-cluttered, surprise-subscription apps that dominate the niche today.

---

## 1. Target user & emotional job

- **Who:** primarily women, Gen Z → early millennial, mobile-native, into manifestation / "that girl" spirituality / self-discovery. Sees 11:11 and wonders what it means.
- **Emotional job-to-be-done:** *"Reassure me that I'm on the right path and that these signs mean something — about me, specifically."* They want **meaning, comfort, identity, and a little magic**, delivered beautifully.
- **Mindset:** curious, hopeful, a bit anxious about love/money/purpose. Not looking for a textbook — looking for a gentle, personal nudge.

---

## 2. Brand direction

**Working name:** **Numa** *(placeholder — see alternatives below; swap freely)*
Alternatives to explore: **Numen** (Latin "divine presence" + "numbers"), **Halo**, **Synced / Synchronicity**, **1111**, **Wink** ("the universe winking at you").

**Aesthetic lane: "modern celestial premium."** Aspirational, calm, a little magical — but clean and grown-up. The numbers themselves are the hero element.

- **Mood:** dreamy night sky, soft auroras, starlight, warm metallic glow. Premium, serene, personal.
- **Primary palette (dark-first):**
  - Background: deep midnight indigo / near-black (e.g. `#0E0A1F` → `#141033`)
  - Aurora gradient accents: violet → indigo → soft rose (used behind hero numbers and CTAs)
  - Accent: warm champagne gold (`#E8C98B`) for highlights, the big numerals, premium markers
  - Text: starlight ivory (`#F4F1EA`) and muted lavender-grey for secondary
  - Optional light "serene" mode: warm ivory/cream background, periwinkle + gold — for everyday use
- **Typography:** an elegant **high-contrast serif** for display and especially the **large numerals** (the numbers should feel special, almost editorial); a clean **humanist sans** for UI/body. Numerals are a signature element — give them weight and air.
- **Texture/FX:** subtle film grain, soft glows/halos *around* numbers, sparse stars, smooth gradients. Restraint over clutter.
- **Tone of voice:** warm, affirming, second-person, lightly mystical but grounded and modern. Never preachy, never fear/doom-based. A touch of humility ("for reflection").
- **AVOID (this is how the tacky incumbents look — do the opposite):** literal cartoon angels & wings, gaudy gold clip-art, zodiac wheels, busy ad-style free-app layouts, comic-sans mysticism, doom/fear framing.
- **Reference points (premium end of the category):** CHANI (warm premium), Co-Star (confident editorial typography), I Am (serene minimalism) — plus a celestial twist of our own.

---

## 3. Information architecture

**Bottom tab bar (4 tabs) + onboarding stack:**

1. **Today** — daily home (personal number, affirmation, sign to watch, quick-log)
2. **Decode** — the permanent "type the number you keep seeing" lookup (the hook)
3. **Journal** — log & track number sightings (the retention loop)
4. **You** — full numerology blueprint + settings

Plus a **Library/Learn** section (reachable from Today/Decode): the index of number meanings, guides, 369 method, affirmation collections.

---

## 4. Onboarding quiz flow — THE REVENUE ENGINE

Long, personalized, quiz-style (Noom / Cal-AI pattern): ~18–22 light steps, a top **progress bar**, one decision per screen, building investment → a personalized **"aha" reveal** → **paywall after the aha**. Every step should feel effortless and a little delightful. Capture the viral hook (the number they see) on step 1.

**Step-by-step (each is its own screen):**

1. **Hook splash** — full-bleed cosmic gradient, brand mark. Headline: *"The universe is trying to tell you something."* Sub: *"Let's decode the numbers you keep seeing."* CTA: **Begin**.
2. **The hook question** — *"What number do you keep seeing?"* Large tappable chips: `111` `222` `333` `444` `555` `11:11` `777` `888` `000` `Another…`. (This is the UGC hook — capture it first.)
3. *"Where do you usually see it?"* — multi-select chips: clocks, receipts, license plates, phone, addresses, dreams, everywhere.
4. *"How often lately?"* — a few times a week / daily / multiple times a day.
5. **Belief interstitial** (no input) — *"That's not a coincidence. Repeating numbers are messages — let's find out what yours means."* CTA: Continue.
6. *"What's on your heart right now?"* — chips: Love & relationships, Money & abundance, Purpose & career, Healing & change, Spiritual growth. (Drives content personalization.)
7. **Birth date** — date picker. Framing: *"Your birthday unlocks your Life Path number — the key to making your readings personal."* (Core personalization input.)
8. **First name** (optional, skippable) — *"What should we call you?"* (Used for Expression/Soul-Urge number + personalized copy.)
9. **Calculation animation** — *"Reading your numerology blueprint…"* with ticking sub-steps (Life Path ✓ · Personal Year ✓ · Your number's message ✓) over a glowing animation. Builds anticipation.
10. **Micro-belief commitment** — *"Do you believe the universe sends signs?"* — Yes / Sometimes / I want to. (Co-Star-style identity nudge.)
11. *"How have you been feeling lately?"* — mood chips (hopeful, anxious, stuck, excited, searching). (Sets affirmation tone.)
12. *"Anything you're hoping to manifest?"* — short free text or chips (love, a new job, money, peace, a fresh start).
13. **Notifications opt-in framing** — *"Want your daily number + a sign to watch for each morning?"* CTA: **Allow** (triggers system prompt). Emphasize *granular control later* (anti-spam = brand value).
14. **Social proof** — *"Join thousands decoding their signs"* + rating stars (use real numbers once available; placeholder for now).
15. **Commitment screen** — *"You're ready to listen."* Single warm CTA: **See my reading**.

---

## 5. The "aha" reveal (the moment before the paywall)

A gorgeous, personalized payoff screen — this is what earns the subscription. Show:

- The number they entered, rendered **huge** in the hero serif with a soft halo: e.g. **`444`**.
- A personal line: *"You keep seeing **444**, [Name] — and as a **Life Path 7**, here's why that matters right now."*
- A **short, genuinely personalized teaser**: 2–3 sentences blending the number's meaning with their Life Path + their stated focus (love/money/etc.). It should feel *about them*, not generic.
- Their **numerology snapshot** as beautiful locked cards: Life Path number (revealed), Expression / Soul Urge / Personal Year (blurred + lock icon).
- A clearly-locked **"Your full reading"** section with a gentle lock and a *"Continue"* CTA → paywall.

The emotional beat: *"Oh — this actually knows me. I want the rest."*

---

## 6. Paywall (immediately after the aha)

Lead with value already delivered, then unlock the rest. **Transparency is a brand differentiator here** — the #1 complaint about competitors is surprise/opaque subscriptions, so be explicit.

- **Headline:** *"Unlock your full reading + daily guidance."*
- **Value bullets:** full personalized number reading · complete numerology blueprint · a daily number + affirmation · the number journal to track your signs · ad-free.
- **Plans:** **Annual — $39.99/yr (hero, "best value, ~$3.33/mo")** vs **Weekly — $6.99/wk (anchor, looks expensive)**. Annual pre-selected.
- **Trial:** offer a clearly-labeled short free trial variant (e.g. "7 days free, then $39.99/yr — we'll remind you before it ends"). Design must accommodate **A/B testing trial vs hard-paywall (no-trial)** variants.
- **Trust row:** "Cancel anytime," restore purchases, links to terms/privacy. No dark patterns — visible price, visible renewal date.
- CTA: **Start** / **Try free**.

---

## 7. Core app screens (post-purchase)

**Today (home)** — card stack on a soft cosmic background:
- "Today's number for you" — a hero numeral + one-line personal energy reading.
- "Your daily affirmation" — elegant typographic card (shareable → UGC surface).
- "A sign to watch for today."
- "The number you're tracking: 444" — with a quick **+ Log a sighting** button.
- Streak indicator.

**Decode (lookup)** — the permanent hook:
- Big input/chips: *"Type the number you keep seeing."*
- Result page: the number rendered large + halo, a general meaning, then a **"For you, Life Path 7"** personalized section, related numbers, and **+ Log this sighting**.

**Journal (retention loop)** — the feature nobody ships:
- **+ Log sighting:** number, where you saw it, how you felt, optional note.
- Timeline of sightings; **pattern insights** ("You've seen 444 seven times this month — most often on clocks").
- Streaks, gentle daily reminder.

**You (numerology blueprint + settings):**
- Full blueprint: Life Path, Expression, Soul Urge, Personal Year — each a beautiful card with a reading.
- **Settings:** *granular* notification controls (per the anti-spam promise — let users choose what & when), subscription management (transparent, with renewal date + easy cancel/restore), theme (dark/serene), name/birthday.

**Library/Learn:** index of angel number meanings (111–999, 11:11, mirror hours), short guides, the 369 method, affirmation collections.

---

## 8. Design-system notes

- **Components:** cards (soft, slightly translucent over gradient), large hero numerals with halo glow, chips/pills for quiz answers, progress bar (onboarding), lock badges (premium), bottom tab bar, primary CTA button (gold/aurora fill), social-proof stars.
- **Motion:** gentle — fades, soft glows, subtle number "shimmer," calm transitions. Nothing jarring.
- **Accessibility:** ensure contrast on the dark theme; numerals legible at small sizes; provide the light "serene" mode.
- **Shareability:** daily affirmation + number cards should be designed to look great as screenshots (free UGC + organic spread).

---

## 9. Out of scope for v1 (don't design these yet)

Community/forum, live psychic chat, AI chatbot coach, full astrology/birth-chart, Android-specific layouts (iOS-first). Note them as *future* but exclude from the v1 screen set.

---

### What I'd most like back from Claude Design
1. The **brand system** (logo/wordmark direction, palette, type, the hero-numeral treatment).
2. The **onboarding flow** screens (hook → a few quiz steps → calculation → aha reveal → paywall).
3. The **Today** home and the **Decode** lookup result screen.
4. The **paywall** (annual-hero + weekly anchor, transparent).
