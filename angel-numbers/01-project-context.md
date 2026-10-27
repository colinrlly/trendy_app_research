# 01: Project Context

## Why this project exists

The builder (Colin) is a senior full-stack engineer working solo. He wants a small mobile app that can make money and double as a training ground for TikTok/Instagram UGC marketing. The app is meant to be quick to build (target: roughly a week of focused work for an MVP), not a long obligation.

He chose the angel numbers app after reviewing several research passes and brainstorm batches, because nothing else beat it on the rubric below.

## The selection rubric (the criteria every idea was scored against)

1. **Mobile app, easy to build.** Mobile specifically for App Store / Google Play distribution and native subscription payments (StoreKit / Play Billing). Favor content + quiz + timer + journal + light personalization. Avoid backends, real-time features, marketplaces, social graphs, hardware, or heavy ML.
2. **Easily marketable via TikTok/Instagram UGC.** Trending niche, TikTok-native audience, natural hooks (POV, identity, relatable pain), faceless content possible, cheap micro-creators available.
3. **Impulsive UGC → purchase path.** Emotional onboarding quiz → commitment moment (checkbox "contract") → **hard paywall** with yearly subscription. Not freemium, not lifetime.
4. **No dominant incumbent**, checked at two levels:
   - *Direct:* no single app that is "the only option in users' minds."
   - *Parallel / one scope up:* no umbrella incumbent whose product already covers the niche as a feature.

## Decisions already made

| Decision | Value |
|---|---|
| Platform | Mobile only; iOS-first (Android monetizes worse for impulse subscriptions) |
| Monetization | Hard paywall, yearly subscription. No freemium, no lifetime deal |
| Price suggestion | $29.99–$39.99/year, 3-day trial, optional ~$6.99/week anchor |
| Audience | Skews female; design for her |
| Product stance | **Reflection, not prophecy** (see below) |
| Typeface | Fraunces |
| Hero ornament | Dashed circles-and-diamonds construction geometry |
| Voice | Blunt but loving |

## Product stance: reflection, not prophecy

The builder does not personally subscribe to numerology. That shaped a deliberate line the whole product holds:

- The app never claims the universe is sending the user messages.
- A repeatedly noticed number is treated as an *occasion for honest self-reflection*.
- Copy is written so it works under two readings: a believer reads it as a sign; a skeptic reads it as a psychological prompt.
- This is also App Store review and liability protection: wellness/self-reflection language only, no medical or therapeutic claims.

**Pre-build content test (recommended before writing app code):** write about ten number readings in the brand voice (two evenings, no code). If the writing flows, proceed. If it feels like homework that keeps getting avoided, the fallback idea is an "ADHD tax tracker" (see `02`).

## Builder context relevant to technical choices

- Strong in Python/Flask, React, GraphQL, PostgreSQL; no stated mobile framework preference yet.
- Has had a painful experience migrating authentication on another product, so **avoiding user accounts in v1 is a sensible default** (local-first, anonymous purchases via RevenueCat).
- Wants to practice UGC marketing, so faceless content formats matter more than anything requiring on-camera presence.

## Explicitly out of scope for this folder

- TimeTurnip (separate freelance time-tracking SaaS).
- Scriptorium (separate D&D session-prep plugin project).
- Other brainstormed app ideas, except as recorded rejections in `02`.
