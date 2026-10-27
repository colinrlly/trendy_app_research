# 08: Open Decisions and Next Steps

## Open decisions

| # | Decision | Options / notes | Who decides |
|---|---|---|---|
| 1 | **Accent color** | Terracotta (warm, celebratory) vs plum (literary-mystical, quieter). See `05` | Builder |
| 2 | **Ambient treatment on the daily card** | Recommendation: construction geometry as hero (the builder's repeated favorite); staggered grid as endpaper texture; diagonal wave as celebration accent only | Builder (leaning geometry) |
| 3 | **App name** | "noticed" is a placeholder. No trademark, handle, or domain check done. Explore Noticed, Seen, Again, Signal, Wake Up Call and similar | Builder |
| 4 | **Mobile framework** | SwiftUI (iOS-first, native `trim` animation) vs React Native/Expo | Builder |
| 5 | **Accounts in v1?** | Recommended: none (local-first, RevenueCat anonymous purchases) | Builder |
| 6 | **Celebration-burst wave in v1?** | Recommended: defer to v1.1 | Builder |
| 7 | **Theme switching trigger** | System appearance vs local sunset; flagged as a feature this audience would likely love; not scoped | Builder |
| 8 | **Typeface licensing** | Fraunces is sufficient for v1; premium faces (Ogg, Canela, Editorial New) only if budget allows later | Builder |

## Not yet designed

- Onboarding quiz screens (copy is drafted in `03`/`04`; no visual mock).
- **Paywall screen** (the most important unmocked screen; the geometry and optionally the mark grid should do real work here).
- Commitment/"contract" screen.
- Sighting-log screen and its celebration animation.
- Share-card export format.
- Settings (notification time, theme).

## Recommended build order

1. **Content test (no code):** write ~10 number readings in the voice (11:11, 111, 222, 333, 444, 555, 777, 888, 999, plus one comfort number at Level 1). If it flows, proceed; if it feels like homework, switch to the ADHD tax tracker fallback (`02`).
2. **Decide accent color and name** (or at least lock a placeholder and move on; both are cheap to change before launch).
3. **Mock the quiz and paywall** in the existing visual system.
4. **Build the MVP** in this order: design tokens and fonts → daily card with static geometry → construction reveal animation → number content JSON (10–15 entries, 2 readings each) → onboarding quiz → paywall via RevenueCat → local sighting log → one daily notification → day/night theme.
5. **Ship iOS-first** and test with 5–10 micro-creators plus self-made faceless slideshows and reveal screen recordings (`07`).
6. **Iterate on the funnel** using the targets in `07` before spending on traffic.

## Guardrails for whoever picks this up

- Don't keep generating new ornament and color variants. The option space is already large enough that more permutations make the choice harder, and the limiting factor now is deciding and building.
- Keep the one-coordinate-system rule for geometry and text (`06`).
- Every number needs hand-written entries in the voice; don't template them.
- Keep claims to reflection and wellness language; no supernatural or medical claims.
- The user has said they want to make money from one of their projects; the funnel metrics in `07` are how to judge whether this one is it.
